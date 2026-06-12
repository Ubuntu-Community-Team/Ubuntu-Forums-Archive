---
title: "Debugging Python"
date: 2014-07-06
forum: Programming Talk
---

### Post by dilbert_one on 2014-07-06
hello

good day dear ubuntu-experts - well i am very glad to have such a great place where the idea exchange is possible.


 - at them moment some things go wrong here 
i have to find out what is happeining - and why the script fails to load the data into the db.... 

see the follwoing 


```

import urllib
import urlparse
import re

url = "http://search.cpan.org/author/?W"
html = urllib.urlopen(url).read()
for lk, capname, name in re.findall('<a href="(/~.*?/)"><b>(.*?)</b></a><br/><small>(.*?)</small>', html):
    alk = urlparse.urljoin(url, lk)

    data = { 'url':alk, 'name':name, 'cname':capname }

    phtml = urllib.urlopen(alk).read()
    memail = re.search('<a href="mailto:(.*?)">', phtml)
    if memail:
        data['email'] = memail.group(1)

    print data



```

This is what I got before stopping it via Ctrl+C Code: - THIS IS obviously a python dictionary 

$ python printer.py 
{'url': 'http://search.cpan.org/~wac/', 'cname': 'WAC', 'name': 'Wang Aocheng', 'email': '<snip>'}
{'url': 'http://search.cpan.org/~wade/', 'cname': 'WADE', 'name': 'James Wade', 'email': 'CENSORED'}



note: the database on the opensuse 13.1 mysql db shows the following struckure: 
```

--
-- Tabellenstruktur für Tabelle `cname`
--

CREATE TABLE IF NOT EXISTS `cname` (
  `cname` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `name`
--

CREATE TABLE IF NOT EXISTS `name` (
  `url` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `url`
--

CREATE TABLE IF NOT EXISTS `url` (
  `url` int(11) DEFAULT NULL,
  `name` int(11) DEFAULT NULL,
  `cname` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTIO

```


and the script is like that: 


```


import urllib
import urlparse
import re
import MySQLdb


db = MySQLdb.connect(host="localhost", # your host, usually localhost
                     user="root", # your username
                      passwd="rimbaud", # your password
                      db="cpan") # name of the data base

# you must create a Cursor object. It will let
#  you execute all the queries you need
cur = db.cursor() 


url = "http://search.cpan.org/author/?W"
html = urllib.urlopen(url).read()
for lk, capname, name in re.findall('<a href="(/~.*?/)"><b>(.*?)</b></a><br/><small>(.*?)</small>', html):
    alk = urlparse.urljoin(url, lk)

    data = { 'url':alk, 'name':name, 'cname':capname }

    phtml = urllib.urlopen(alk).read()
    memail = re.search('<a href="mailto:(.*?)">', phtml)
    if memail:
        data['email'] = memail.group(1)


# Use all the SQL you like
cur.execute("SELECT * FROM YOUR_TABLE_NAME")

# print all the first cell of all the rows
for row in cur.fetchall() :
    print row[0]
    

```
    
    
    but unfortunatly i get the following errors: 
    that let me think that ihave some database-errors: 
    
   < but wait: the tables and the database exist - (see above) 
```
    
    
    martin@linux-70ce:~/perl> python cpan2.py
Traceback (most recent call last):
  File "cpan2.py", line 34, in <module>
    cur.execute("SELECT * FROM YOUR_TABLE_NAME")
  File "/usr/lib/python2.7/site-packages/MySQLdb/cursors.py", line 174, in execute
    self.errorhandler(self, exc, value)
  File "/usr/lib/python2.7/site-packages/MySQLdb/connections.py", line 36, in defaulterrorhandler
    raise errorclass, errorvalue
_mysql_exceptions.ProgrammingError: (1146, "Table 'cpan.YOUR_TABLE_NAME' doesn't exist")
martin@linux-70ce:~/perl> python cpan2.py
Traceback (most recent call last):
  File "cpan2.py", line 34, in <module>
    cur.execute("SELECT * FROM YOUR_TABLE_NAME")
  File "/usr/lib/python2.7/site-packages/MySQLdb/cursors.py", line 174, in execute
    self.errorhandler(self, exc, value)
  File "/usr/lib/python2.7/site-packages/MySQLdb/connections.py", line 36, in defaulterrorhandler
    raise errorclass, errorvalue
_mysql_exceptions.ProgrammingError: (1146, "Table 'cpan.YOUR_TABLE_NAME' doesn't exist")
martin@linux-70ce:~/perl> python cpan2.py
Traceback (most recent call last):
  File "cpan2.py", line 34, in <module>
    cur.execute("SELECT * FROM YOUR_TABLE_NAME")
  File "/usr/lib/python2.7/site-packages/MySQLdb/cursors.py", line 174, in execute
    self.errorhandler(self, exc, value)
  File "/usr/lib/python2.7/site-packages/MySQLdb/connections.py", line 36, in defaulterrorhandler
    raise errorclass, errorvalue
_mysql_exceptions.ProgrammingError: (1146, "Table 'cpan.YOUR_TABLE_NAME' doesn't exist")
martin@linux-70ce:~/perl> 

```
i have to investigate what goes wrong here

---

### Post by bapoumba on 2014-07-06
*Thread moved to **Programming Talk**.*

---

### Post by spjackson on 2014-07-06
[FONT=arial]You have tables called "cname", "name" and "url". You do not have a table called "[COLOR=#000000]YOUR_TABLE_NAME". Therefore this line will fail.
[/COLOR]```
cur.execute("SELECT * FROM YOUR_TABLE_NAME")

```

[/FONT]

---

### Post by ofnuts on 2014-07-06
> 
This is what I got before stopping it via Ctrl+C Code: - THIS IS obviously a python dictionary


No it's not. This is [JSON]("http://en.wikipedia.org/wiki/JSON")..

For the rest your problem is likely more with MySQL than with Python (so your topic title is not attracting the right people here).

Did you try to access the table from some interactive application? I don't know MySQL but in other DBs (Oracle, DB2) the tables are in a "Schema" (called "cpan" in the syntax you use) and there is nothing in what you show that demonstrates that you tables are created in this very schema.

---

### Post by dilbert_one on 2014-07-06
hello dear ofnuts hello dear spjackson



well i thought that i have created the tables....;

But to talk from the very beginning . i am tryin go dive into the technique of mysql with Python which is supposed to be easier than 
Perl. Perl is the only language that looks the same before RSA-Encryption and after RSA-Encryption.  ;-) 

for learing-things Python is supposed to be the best - isn ´t it!?`

what is wanted: - i want to add to the following scrit a little addition - so that i do not print out the dataset but store it into a mysql-db. 

note: on my opensuse version 13.1 a mysql db is up and running. 

and i also installed MySQLdb

here the script that gathers data: 

```


import urllib
import urlparse
import re


url = "http://search.cpan.org/author/?W"
html = urllib.urlopen(url).read()
for lk, capname, name in re.findall('<a href="(/~.*?/)"><b>(.*?)</b></a><br/><small>(.*?)</small>', html):
    alk = urlparse.urljoin(url, lk)

    data = { 'url':alk, 'name':name, 'cname':capname }

    phtml = urllib.urlopen(alk).read()
    memail = re.search('<a href="mailto:(.*?)">', phtml)
    if memail:
        data['email'] = memail.group(1)

    print data



```
    well should i go with MySQLdb or should i use peewee?!

I recently discovered another jewel in the Python world: peewee. It's a very 
lite ORM, really easy and fast to setup then use. 
Friends told me that it should makes my day for small projects or stand alone apps easier, 
where using big tools like SQLAlchemy or Django is overkill:

```

import peewee
from peewee import *

db = MySQLDatabase('jonhydb', user='john',passwd='megajonhy')

class Book(peewee.Model):
    author = peewee.CharField()
    title = peewee.TextField()

    class Meta:
        database = db

Book.create_table()
book = Book(author="me", title='Peewee is cool')
book.save()
for book in Book.filter(author="me"):
    print book.title

Peewee is cool

```


what do you suggest - do you suggest to use peewee or the other bridge? 

i love to hear from you

btw: i also have found a good article here:  [http://ubuntuforums.org/showthread.php?t=2233070&p=13066559#post13066559](http://ubuntuforums.org/showthread.php?t=2233070&p=13066559#post13066559)

---

