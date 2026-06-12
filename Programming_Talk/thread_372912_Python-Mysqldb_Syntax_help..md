---
title: "Python-Mysqldb Syntax help."
date: 2007-02-28
forum: Programming Talk
---

### Post by jvc26 on 2007-02-28
All is well now, I added a line cursor.execute("COMMIT") and that fixed the problem.
Thanks again,
Il

---

### Post by s1ightcrazed on 2007-02-28
OK - I'm not sure exactly what you are trying to do. Your SQL statement seems a bit off for what it sounds like you are trying to do. 

UPDATE pet SET owner = VALUES 'ownername' WHERE name = 'sweetie'

This says 'update a table named pet and set the column called 'owner' to a group to something if the column called name is = to 'sweetie'. 

Are you trying to insert multiple values into the owner column? Do you want the first row to be = to the first value in the tuple? So if your tuple is 'one, two, three' then you want the first row to get the value 'one' and the second one 'two' etc...etc..

I think a little more clarification is needed.

---

### Post by jvc26 on 2007-03-01
Sorry wasnt exactly clear on re-reading my question. Basically I have a value in a variable 'ownername' which I want to insert into table pet, under the row where 'name' = sweetie: I.e. a standard I item insert:
UPDATE pet SET owner = VALUES 'johnathon' WHERE name = 'sweetie'
But the value johnathon is stored in a variable named ownername. I want to know what the method is to insert this value into the table where the name (of the pet) is sweetie. I hope that makes it clearer.
Thanks,
Il

---

### Post by ghostdog74 on 2007-03-01
you could construct your sql statement first
eg
```

....
sql = "UPDATE pet SET owner = VALUES '%s' WHERE name = '%s'" %(ownername,sweetie)
print sql ##make sure its correct
cursor.execute(sql)
....
...

```

---

### Post by jvc26 on 2007-03-01
```

sql = "UPDATE pet SET owner = VALUES '%s' WHERE name = '%s'" %(ownername,sweetie)

```
Have I got this right: This command would set the cell under the column 'owner' to the value contained in 'ownername' where the value in the cell under 'name' is 'sweetie?

Basically what I want to be able to do (Here is the output of SELECT * FROM pet:)
```

+---------+--------------+-------------+-------+----------------+------------+
| name    | owner       | species    | sex  | birth              | death      |
+---------+--------------+-------------+-------+----------------+------------+
| Bob         | Charlie    | Dog          | M    | 1984-06-06 | 1992-04-04 | 
| Phil         | Thomas  | Dog         | M    | 1992-04-01   | NULL       | 
| Sweetie | Jane         | Hamster | F    | 1992-02-04   | 1993-02-07 | 
| Jane        | Gary         | Cat          | F    | 1994-12-01    | NULL       | 
+---------+--------------+-------------+-------+----------------+------------+

```
Is replace the value in the owner column 'Jane' with the value contained in the variable 'ownername' in the script.
Il

---

### Post by jvc26 on 2007-03-01
Right I've now tried:
```

#import modules
import MySQLdb

ownername = ""
newname = "esther"
#connect to db and create cursor
db = MySQLdb.connect(host="***.***.***.***",user="**********",passwd="*******",db ="test_run")
cursor = db.cursor()
#collect data from db
cursor.execute("SELECT owner FROM pet WHERE name = 'sweetie'")
row = cursor.fetchone()
ownername = row[0]
ownername = ownername + newname

sql = "UPDATE pet SET owner = VALUES '%s' WHERE name = 'sweetie'" %(ownername)
print sql ##make sure its correct
cursor.execute(sql)

```

This gives me the error:
```

Traceback (most recent call last):
  File "testUpdate.py", line 17, in <module>
    cursor.execute(sql)
  File "/usr/lib/python2.5/site-packages/MySQLdb/cursors.py", line 163, in execute
    self.errorhandler(self, exc, value)
  File "/usr/lib/python2.5/site-packages/MySQLdb/connections.py", line 35, in defaulterrorhandler
    raise errorclass, errorvalue
_mysql_exceptions.ProgrammingError: (1064, "You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''jackieesther' WHERE name = 'sweetie'' at line 1")

```

Any ideas? Thanks for your help, it was the closest to working thus far,
Il

---

### Post by ghostdog74 on 2007-03-01
> **Illuvator said:**
> Right I've now tried:
```

#import modules
import MySQLdb

ownername = ""
newname = "esther"
#connect to db and create cursor
db = MySQLdb.connect(host="***.***.***.***",user="**********",passwd="*******",db ="test_run")
cursor = db.cursor()
#collect data from db
cursor.execute("SELECT owner FROM pet WHERE name = 'sweetie'")
row = cursor.fetchone()
ownername = row[0]
ownername = ownername + newname

sql = "UPDATE pet SET owner = VALUES '%s' WHERE name = 'sweetie'" %(ownername)
print sql ##make sure its correct
cursor.execute(sql)

```

This gives me the error:
```

Traceback (most recent call last):
  File "testUpdate.py", line 17, in <module>
    cursor.execute(sql)
  File "/usr/lib/python2.5/site-packages/MySQLdb/cursors.py", line 163, in execute
    self.errorhandler(self, exc, value)
  File "/usr/lib/python2.5/site-packages/MySQLdb/connections.py", line 35, in defaulterrorhandler
    raise errorclass, errorvalue
_mysql_exceptions.ProgrammingError: (1064, "You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''jackieesther' WHERE name = 'sweetie'' at line 1")

```

Any ideas? Thanks for your help, it was the closest to working thus far,
Il

please check your sql statement:
```

sql = "UPDATE pet SET owner = VALUES '%s' WHERE name = 'sweetie'" %(ownername)
print sql

```

the statement would be like this when printed
```

UPDATE pet SET owner = VALUES 'jackieesther' WHERE name = 'sweetie'

```
i believe this is wrong. you can verify by executing this statement in mysql query tool. I believe it should be something like this
```

UPDATE pet SET owner = 'jackieesther' WHERE name = 'sweetie'

```
without the VALUES

---

### Post by jvc26 on 2007-03-03
Yup that worked out - thanks very much mate,
Il

---

### Post by jvc26 on 2007-03-04
The new problem: Here is my program its a simple thing which accesses a MySQL database to carry out movements in the game diplomacy. Note:: There are a few useless bits to it at the moment, they will be sorted out later, but the main issue is this statement:
```

#update the db
sql = "UPDATE unit_table SET current_province = '%s' WHERE owner = 'Russia' AND unit_type = 'A' AND ID = '1'" %(endpoint)
print sql
cursor.execute(sql)

```
This, when the code is executed, prints out a value of:
```

UPDATE unit_table SET current_province = 'Fin' WHERE owner = 'Russia' AND unit_type = 'A' AND ID = '1'

```
Which is correct (presuming you put Fin in as the province you wanted to move to. However, when you then look on the MySQL database, the entry for the unit on the unit_table's current_province has not changed. Any ideas why this is the case? Entering the MySQL statement alone (without the variable, as it appears in the printout) at the MySQL prompt updates the database correctly.

The whole script is here:
```

#import modules
import MySQLdb

#connect to db and create cursor
db = MySQLdb.connect(host="127.0.0.1",user="root",passwd="chan09",db ="diplomacy")
cursor = db.cursor()

#initiate variables
position = ""
unitType = ""
unitID = ""

#collect data from db
cursor.execute("SELECT ID FROM unit_table WHERE ID = 1")
row = cursor.fetchone()
unitID = row[0]

cursor.execute("SELECT current_province FROM unit_table WHERE ID = 1")
row = cursor.fetchone()
position = row[0]

cursor.execute("SELECT unit_type FROM unit_table WHERE ID = 1")
row = cursor.fetchone()
unitType = row[0]

#order the move
print "Your current position is", position
endpoint = raw_input("Where do you want to move to? ")

#update the db
sql = "UPDATE unit_table SET current_province = '%s' WHERE owner = 'Russia' AND unit_type = 'A' AND ID = '1'" %(endpoint)
print sql
cursor.execute(sql)

```

Thanks for any help on this,
Il

---

### Post by ghostdog74 on 2007-03-04
this statement: ```
UPDATE unit_table SET current_province = 'Fin' WHERE owner = 'Russia' AND unit_type = 'A' AND ID = '1' 
```, can you successfully update the table by typing interactively without using your script? ie using the command line  client.

---

### Post by jvc26 on 2007-03-04
Yup if you use that command normally then it works fine. I added a line at the end of the script:
cursor.execute("COMMIT")
and it worked fine.
Thanks for the help,
Il

---

