---
title: "how to store a python-dictionary into a mysql-database"
date: 2014-11-23
forum: Programming Talk
---

### Post by dilbert_one on 2014-11-23
hi dear ubuntu experts

well i just dive into python and - therefore i need your help.

i want to do some practical and down to earth jobs with python. 

i have a little script that uses peewee in python - to connect to a db and store the datas that i have parsed
 
 
```


import urllib
import urlparse
import re
# import peewee
import json
from peewee import *


#from peewee import MySQLDatabase ('cpan', user='root',passwd='sx') 


db = MySQLDatabase('cpan', user='root',passwd='rimbaud') 

class User(Model):
    name = TextField()
    cname = TextField()
    email = TextField()
    url = TextField()

    class Meta:
        database = db # this model uses the cpan database

        
User.create_table() #ensure table is created


url = "http://search.cpan.org/author/?W"
html = urllib.urlopen(url).read()
for lk, capname, name in re.findall('<a rel="nofollow" href="(/~.*?/)"><b>(.*?)</b></a><br/><small>(.*?)</small>', html):
    alk = urlparse.urljoin(url, lk)

    data = { 'url':alk, 'name':name, 'cname':capname }

    phtml = urllib.urlopen(alk).read()
    memail = re.search('<a href="mailto:(.*?)">', phtml)
    if memail:
        data['email'] = memail.group(1)


# data = json.load('email') #your json data file here

for entry in data: #assuming your data is an array of JSON objects
    user = User.create(name=entry["name"], cname=entry["cname"],
        email=entry["email"], url=entry["url"])
    user.save()

```
    
note : i disabled the line in the code: 

```
 # data = json.load('email') #your json data file here

```

 doing so i get ahead and run the code: 
 

```

martin@linux-70ce:~/perl> python cpan_100.py
Traceback (most recent call last):
  File "cpan_100.py", line 27, in <module>
    User.create_table() #ensure table is created
  File "build/bdist.linux-i686/egg/peewee.py", line 3078, in create_table                                                                                                           
  File "build/bdist.linux-i686/egg/peewee.py", line 2471, in create_table                                                                                                           
  File "build/bdist.linux-i686/egg/peewee.py", line 2414, in execute_sql                                                                                                            
  File "build/bdist.linux-i686/egg/peewee.py", line 2283, in __exit__                                                                                                               
  File "build/bdist.linux-i686/egg/peewee.py", line 2406, in execute_sql                                                                                                            
  File "/usr/lib/python2.7/site-packages/MySQLdb/cursors.py", line 174, in execute                                                                                                  
    self.errorhandler(self, exc, value)                                                                                                                                             
  File "/usr/lib/python2.7/site-packages/MySQLdb/connections.py", line 36, in defaulterrorhandler                                                                                   
    raise errorclass, errorvalue                                                                                                                                                    
peewee.OperationalError: (1050, "Table 'user' already exists")                                                                                                                      
martin@linux-70ce:~/perl> 

```

WELL - it seems to be clear that i have some other issues now...

---

### Post by ofnuts on 2014-11-23
You may want to looka bit more into MySQL (and SQL in general database structure). Your data goes in a table (which should be created first, with defined columns...), this table is part of a Schema (which, in MySQL, is tne same as a database, while other SQL implementations Oracle, DB2...) have schemas as part of databases. The "users" in the DB are very often DB  specific (more related to applications that to real users).

PS: bad idea to type out your passwords on public forums, especially when they are associated with user 'root'. Unless you are setting uo a [honeypot](http://en.wikipedia.org/wiki/Honeypot_%28computing%29), in which case everything is fine :)

---

### Post by dilbert_one on 2014-11-23
hello ofnuts 

many thanks - will digg deeper in alll that

---

