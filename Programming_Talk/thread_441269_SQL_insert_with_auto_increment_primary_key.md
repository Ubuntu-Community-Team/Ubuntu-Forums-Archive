---
title: "SQL insert with auto increment primary key"
date: 2007-05-12
forum: Programming Talk
---

### Post by tc101 on 2007-05-12
Suppose I create this table

CREATE TABLE Person2 
(
PKey INT NOT NULL AUTO_INCREMENT,
PRIMARY KEY (PKey),
FirstName varchar(20),
LastName varchar(20),
Address varchar (20),
Age int
)

and I want to insert a row and set the primary key to the next available integer.  Do I have to list all the field names, like this

INSERT INTO Person2 (FirstName,LastName,Address,Age) VALUES("Bill","Smith","box 7",25) 

or is there a shorter way to do it, without listing the field names, something like this, although this doesn't work:

INSERT INTO Person2 VALUES(auto,"bob","blow","East Avenue",22)

---

### Post by Matakoo on 2007-05-12
In MySQL at least you can do something like this:

INSERT INTO Person2 (FirstName) VALUES ("John");

if you only want to add a row with just the first-name field filled in.

---

### Post by Matakoo on 2007-05-12
> **tc101 said:**
> 
INSERT INTO Person2 VALUES(auto,"bob","blow","East Avenue",22)

Maybe I should read better...that line above only need to be altered a bit into this:

INSERT INTO Person2 VALUES(null,"bob","blow","East Avenue",22);

Replace auto with null and add a semi-colon at the end in other words.

---

### Post by tc101 on 2007-05-12
Thanks Matakoo, that works.

---

### Post by BillyJo2002 on 2009-03-05
I had this issue in VB.net and struggled for hours to insert a record without an error being thrown associated with Autoincrement and not having NULL values applied to the Primary Key field. Eventually I discovered the following:-

[*]Open the offending table definition from Server Explorer
[*]Select the column you have assigned as the primary key
[*]In the column properties set the Identity Column as the Primary Key Column


i am not sure if its essential but also in the Dataset diagram window - I selected the same Dataset and set the same primary key column autoincrement seed and step to -1 (they had previously been 1) and of course, autoincrement needs to be set to True.

You should now be able to insert new records to the end of the table programtically without needind to specify the next record number - or indeed get NULL errors thrown!

---

