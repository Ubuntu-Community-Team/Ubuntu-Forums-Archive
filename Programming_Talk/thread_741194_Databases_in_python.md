---
title: "Databases in python"
date: 2008-03-31
forum: Programming Talk
---

### Post by shifty2 on 2008-03-31
I'm trying to create a basic database in python and was wondering if there were any good tutorials to get started on? As well as the advantages/disadvantages of different types of database (thats worded appalingly but I mean should i choose mysql or another type of database). 

Its not going to be some horrendously complicated database, so the easier the better please :-)

---

### Post by CptPicard on 2008-03-31
Well.... the only "type" of database you have these days is the relational database which is accessed through SQL. It doesn't really matter which actual implementation you choose. MySQL is popular, personally I prefer PostgreSQL. But if you want it to be lightweight and easy, SQLite is probably for you.

---

### Post by pmasiar on 2008-03-31
SQLite is the best SQL database for just goofing around. No need to run/admin server.

If you go with Django Web app framework, you hardly need any clue about SQL, all will be generated automagically for you. TurboGears is notch more complicated but allows for more control (standard difference between Dj and TG in approach).

---

### Post by Quikee on 2008-03-31
Just use an Object Relational Mapper (like Turbogears and Django do if I am not mistaken) if you don't want to mess with SQL and be database independent (or at least as dependent as the ORM tool is). 

[SQLAlchemy]("http://www.sqlalchemy.org/") for example is pretty nice (there is also [storm]("https://storm.canonical.com/") which was developed by canonical). Here is an example that uses in memory SQLite as a database (in a comment there is an example to change the database to postgresql - this is all it is needed to change the database used):

[PHP]#!/usr/bin/env python
#-*- coding: utf-8 -*-

import logging
from sqlalchemy import *
from sqlalchemy.orm import *

logging.disable(logging.CRITICAL)

engine = create_engine('sqlite:///:memory:', echo=True)
#engine = create_engine('postgres://scott:tiger@localhost:5432/mydatabase')

class Person(object):
	@staticmethod
	def table(metadata):
		return Table('person', metadata,
			Column('id', Integer, primary_key=True),
			Column('name', String(40)),
			Column('surname', String(40)),
		)
	@staticmethod
	def mapper():
		mapper(Person, Person.table(metadata), properties={'addresses': relation(Address, backref='person')})
		
	def __init__(self, **keywords):
		for (key, value) in keywords.iteritems():
			setattr(self, key, value)

class Address(object):
	@staticmethod
	def table(metadata):
		return Table('address', metadata,
			Column('id', Integer, primary_key=True),
			Column('street', String(40)),
			Column('personId', Integer, ForeignKey('person.id')),
		)
	@staticmethod
	def mapper():
		mapper(Address, Address.table(metadata))
	
	def __init__(self, **keywords):
		for (key, value) in keywords.iteritems():
			setattr(self, key, value)

## init
metadata = MetaData(engine)
Person.mapper()
Address.mapper()
metadata.create_all(engine)

## main - save
Session = sessionmaker(bind=engine, autoflush=True, transactional=True)
session = Session()
person = Person(name = "Scott", surname = "Tiger")
address = Address(street = "Someplace - First steet 21")
person.addresses.append(address)
address = Address(street = "Second Street 1")
person.addresses.append(address)
session.save(person)
session.save(address)

## main - load
person = session.query(Person).filter_by(name='Scott').first() 
print person.name + " " + person.surname
for address in person.addresses:
	print "\t", address.street[/PHP]

---

### Post by shifty2 on 2008-03-31
Thanks for the help everyone. I'm going to have a look into the sqalchemy and see what happens. Time to do some reading....

---

### Post by pmasiar on 2008-03-31
With TG, you have SQLAlchemy, **and** model, all in proper places, even a tool to edit your data -- but Django has even better tool to browse/edit data, even if ORM is worse. Pick your poison. :-)

---

### Post by LaRoza on 2008-03-31
> **shifty2 said:**
> I'm trying to create a basic database in python and was wondering if there were any good tutorials to get started on? As well as the advantages/disadvantages of different types of database (thats worded appalingly but I mean should i choose mysql or another type of database). 

Its not going to be some horrendously complicated database, so the easier the better please :-)

See my wiki.

If you don't need a database server (multiuser) use SQLite.

You can read up on the various solutions on Wikipedia, to date, I haven't seen a bad database solution, but they aren't all equal.

---

### Post by Can+~ on 2008-03-31
sqlite3 is great for start learning SQL in a safe environment, and great for building databases for local applications, like a music player, a GTD app, etc.

---

### Post by LaRoza on 2008-03-31
> **Can+~ said:**
> sqlite3 is great for start learning SQL in a safe environment, and great for building databases for local applications, like a music player, a GTD app, etc.

It comes with Python I believe as well, making the application portable.

---

### Post by bvmou on 2008-04-01
I have to second the sqlite suggestion: it is built in, you don't have to make type declarations, it implements lots of the SQL standard, it is widely used and extremely cool.  Here is an example of interactively creating and populating a database, using only built-ins and basic commands:

```
Python 2.5.2 (r252:60911, Mar 12 2008, 13:36:25) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sqlite3
>>> conn = sqlite3.connect('mydb.db')
>>> cur = conn.cursor()
>>> cur.execute('create table phrasebook (english, french, spanish)')
<sqlite3.Cursor object at 0x81a2bf0>
>>> phraselist = {1:['hello', 'bonjour', 'hola'], 2:['eat', 'manger', 'comer'], 3:['pizza', 'pizza', 'pizza']}
>>> for key in phraselist:
...     cur.execute("insert into phrasebook values %s" % str(tuple(phraselist[key])))
... 
<sqlite3.Cursor object at 0x81a2bf0>
<sqlite3.Cursor object at 0x81a2bf0>
<sqlite3.Cursor object at 0x81a2bf0>
>>> cur.execute('select * from phrasebook')
<sqlite3.Cursor object at 0x81a2bf0>
>>> a = cur.fetchall()
>>> a
[(u'hello', u'bonjour', u'hola'), (u'eat', u'manger', u'comer'), (u'pizza', u'pizza', u'pizza')]
>>> conn.commit()
>>> 
```

Then at an sqlite3 prompt you can work with the results:

```
user@host:~$ sqlite3 mydb.db
SQLite version 3.4.2
Enter ".help" for instructions
sqlite> select * from phrasebook;
hello|bonjour|hola
eat|manger|comer
pizza|pizza|pizza
sqlite> 

```

Very approachable, and very useful :)

---

