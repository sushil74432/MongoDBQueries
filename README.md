# MongoDBQueries
## A non-exaustive list of some main queries that can be performed in Mongodb

```
//Select the database to use.
use('databaseName');
```

```
//Create a collection
 db.createCollection("sales");
```

```
//Insert one document in the sales collection
db.sales.insertOne(
    { 'item': 'abc', 'price': 10, 'quantity': 6, 'date': new Date('2014-03-01T08:00:00Z') },
); 
```

```
//Insert one document in the sales collection - different schema
db.sales.insertOne(
    { 'item': 'zkp', 'price': 10, 'quantity': 2, 'date': new Date('2014-03-01T08:00:00Z'), 'description' : "test description" },
);
```

```
//Insert a few documents into the sales collection.
db.sales.insertMany([
  { 'item': 'abc', 'price': 10, 'quantity': 2, 'date': new Date('2014-03-01T08:00:00Z') },
  { 'item': 'jkl', 'price': 20, 'quantity': 1, 'date': new Date('2014-03-01T09:00:00Z') },
  { 'item': 'xyz', 'price': 5, 'quantity': 10, 'date': new Date('2014-03-15T09:00:00Z') },
  { 'item': 'xyz', 'price': 5, 'quantity': 20, 'date': new Date('2014-04-04T11:21:39.736Z') },
  { 'item': 'abc', 'price': 10, 'quantity': 10, 'date': new Date('2014-04-04T21:23:13.331Z') },
  { 'item': 'def', 'price': 7.5, 'quantity': 5, 'date': new Date('2015-06-04T05:08:13Z') },
  { 'item': 'def', 'price': 7.5, 'quantity': 10, 'date': new Date('2015-09-10T08:43:00Z') },
  { 'item': 'abc', 'price': 10, 'quantity': 5, 'date': new Date('2016-02-06T20:20:13Z') },
  { 'item': 'xyz', 'price': 5, 'quantity': 23, 'date': new Date('2014-05-15T09:00:00Z') },
]);
```

```
//Find all matching item from sales collection
db.sales.find({item:"xyz"});
```

```
//Find first matching item from sales collection
db.sales.findOne({item:"xyz"});
```

```
//Find items with price greater than 10
db.sales.find({ price: { $gt: 7,} });
```

```
//logical operators like $and, $or, $not can be used 
db.sales.find({ $and: [{ price: 7.5 }, { quantity: 10 }] });
```

```
//Projections - Only return selected fields
//Return only first name and age of matching document
db.sales.find({ age: 25 }, { first_name: 1, age: 1 });
```

```
//Update one matching document
db.sales.updateOne({ item: 'xyz' }, { $set: { price: 30 } });
```

```
//Update many matching document
db.sales.updateMany({ name: 'xyz' }, { $set: { price: 30 } });
```

```
//Single field index
db.users.createIndex({ item: 1 });
```

```
//Compound index
db.users.createIndex({ item: 1, price: 1 });
```

```
//Deletes the first document from the collection that matches the condition
db.sales.deleteOne({ firstName: 'John' });
```

```
//Remove multiple documents that matches condition
db.sales.deleteMany({ item: 'xyz' });
```

```
//remove entire collection named users
db.users.drop();
```
