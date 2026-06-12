---
title: "Python SQLite Issues"
date: 2008-02-28
forum: Programming Talk
---

### Post by peterbrewer on 2008-02-28
Hi there.  I am using Python as part of a project.  I create a SQLite database in it and use the following code to generate a table.

```
	query.exec_("""CREATE TABLE title (
		id INTEGER PRIMARY KEY AUTOINCREMENT UNIQUE NOT NULL,
		name VARCHAR(40) NOT NULL)""")
```

After this I then use this code to add data to the table, which I know is added as it is viewable from a 3rd party app when I open the database,

```
	for name in ("Mr", "Mrs", "Miss", "Ms", "Prof", "Doctor", "Other"):
		query.exec_("INSERT INTO title (name) VALUES ('%s')" % name)
```

Then I use the following code to ask it to print out the data in the table.

```
	print "Titles:"
	query.exec_("SELECT id, name FROM title ORDER BY id")
	while query.next():
		id = query.value(ID).toInt()[0]
		name = unicode(query.value(NAME).toString())
		print "%02d: %s" % (id, name)
	QApplication.processEvents()
```

The issue is that all it prints are 7 lines with an id supposedly of 00 and no actual name.  It clearly has some access to the table as it prints those 7 lines but I am not sure what is wrong.  Any help would be hugely appreciated.

---

### Post by pmasiar on 2008-02-28
What kind of application are you trying to make? 
If you do web app, did you considered either Django or Turbogears? They both provide ORM (Object-relation mapper) which handles these issues for you, transparently. And you can use ORM separately, outside framework: SQLObject, SQLAlchemy, or Canonical's own: [https://storm.canonical.com/](https://storm.canonical.com/)

---

### Post by peterbrewer on 2008-02-28
I'm using QT as the interface and its part of my uni course.

---

### Post by pmasiar on 2008-02-28
Can you use ORM? Or course is oriented on learning hand-crafted SQL?

---

### Post by Martin Witte on 2008-02-28
this is the example from this site [http://www.devshed.com/c/a/Python/Using-SQLite-in-Python](http://www.devshed.com/c/a/Python/Using-SQLite-in-Python), on how to insert/retrieve data from a sqllite database
[PHP]from pysqlite2 import dbapi2 as sqlite
connection = sqlite.connect('/home/martin/test.db')
cursor = connection.cursor()
cursor.execute('CREATE TABLE names (id INTEGER PRIMARY KEY,name VARCHAR(50), email VARCHAR(50))')
cursor.execute('INSERT INTO names VALUES (null, "John Doe", "jdoe@jdoe.zz")')
cursor.execute('INSERT INTO names VALUES (null, "Mary Sue","msue@msue.yy")')
cursor.lastrowid
connection.commit()
cursor.execute('SELECT * FROM names')
print cursor.fetchall()
cursor.execute('SELECT * FROM names')
for row in cursor:
    print '-'*10
    print 'ID:', row[0]
    print 'Name:', row[1]
    print 'E-Mail:', row[2]
    print '-'*10[/PHP]

---

