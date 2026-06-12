---
title: "issues with peewee and python"
date: 2015-02-24
forum: Programming Talk
---

### Post by dilbert_one on 2015-02-24
hello dear ubuntu-experts 



just some basics on issues i run into  while starting with python..


well this is somewhat difficult - why do i get these results!!?`

here the original posting

fairly new to python and to programming too.

I'm trying to connect to a MySQL database  using peewee and I can't get it to work. I'm new to databases so I'm probably doing something stupid, but this is what I'm trying: well i tried to get connection to a database in python with peewee but at a certain point the programme fails.

```
import urllib
import urlparse
import re
# import peewee
import json
from peewee import *
#from peewee import MySQLDatabase ('cpan', user='root',passwd='rimbaud') 
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



 the results:i am faded

```
martin@linux-70ce:~/perl> python cpan_100.py
Traceback (most recent call last):
  File "cpan_100.py", line 45, in <module>
    user = User.create(name=entry["name"], cname=entry["cname"],
TypeError: string indices must be integers, not str

```

well at the moment i wonder why i run into there errors

---

### Post by coffeecat on 2015-02-26
*Thread moved to **Programming Talk**.*

---

### Post by Gustaf_Alhll on 2015-02-28
As the error says:
```
TypeError: string indices must be integers, not str
```

What you did as a mistake was to extract a value from an array by using a string when you should use an integer instead. Still, that's not the issue.
Using arrays inside for-loops splits up the array into individual objects that then returns to the array once the loop's done. What you did was treat these objects as arrays, hence the error.
Ex. "for entry in data:" splits up the array "data" into "entry", which is an object. The loop runs as many times as the size of "data", to apply it to each "entry" inside "data".

To solve it, you need to replace:
    user = User.create(name=entry["name"], cname=entry["cname"],
    email=entry["email"], url=entry["url"])
with:
    user = User.create(name=entry, cname=entry,
    email=entry, url=entry)

I hope that solves your issue.
 - Gustaf

---

### Post by dilbert_one on 2015-02-28
hi gustaf 

many thanks  will try it out later the weekend and come back to report all the findings

again many thanks

---

### Post by dilbert_one on 2015-03-01
hello dear Gustaf

thx for the answer

```

import urllib
import urlparse
import re
# import peewee
import json
from peewee import *
#from peewee import MySQLDatabase ('cpan', user='root',passwd='rimbaud') 
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

user = User.create(name=entry, cname=entry,
email=entry, url=entry)
user.save()


```

got back the following 

```
IndentationError: expected an indented block                                                                                                                                        
martin@linux-70ce:~/perl> python cpan_1.py                                                                                                                                          
  File "cpan_1.py", line 35                                                                                                                                                         
    user = User.create(name=entry, cname=entry,                                                                                                                                     
       ^
IndentationError: expected an indented block
martin@linux-70ce:~/perl> 


```

what can i do?

---

### Post by dilbert_one on 2015-03-03
still stuggle with the errors

---

### Post by ofnuts on 2015-03-05
Since "user = User.create(...)" appears after a "for entry in data:" it should be indented(*).


 (*) for the rare case where you would want an empty loop, the loop body should just be a "pass" instruction.

---

### Post by dilbert_one on 2015-03-05
hello dear ofnuts 

many many thanks for the quick answer and the hints. 

just not sitting of my Notebook with python on it but want to answer you quickly, 


thanks for pointing into this direction - guess that this wrong indentation caused the issues. - and the error code also mentioned it. Many thanks dear Ofnuts for helping me. 


At the weekend i will try it out. 

greetings 
dil  

> "whitspaces in python are significant to the source code."
  Everywhere else, whitespace is not significant and can be used as you like, just like in any other language..... but Python is behaving in a  special way...


you helped me alot... :p

---

### Post by dilbert_one on 2015-03-12
hello again 

still struggle with the code - 

regarding the data that comes out - we can do like so... : to see the outcome ...

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


We can see the output here

```
$ python printer.py
{'url': 'http://search.cpan.org/~wac/', 'cname': 'WAC', 'name': 'Wang Aocheng', 'email': 'wangaocheng@hotmail.com'}
{'url': 'http://search.cpan.org/~wade/', 'cname': 'WADE', 'name': 'James Wade', 'email': 'james@holifield.com'}
^C

```

note: this is only a sample of output - before i did stop it via Ctrl+C


what do you say - how to do the assignment now....

---

### Post by ofnuts on 2015-03-12
What you get here is an array of dictionaries, each user corresponding to a dictionary. You can get at each user data with:
```

result[userIndex][filedName]

```

For instance:
```

# Yields 'WADE'
cname=result[1]['cname']

```

---

### Post by dilbert_one on 2015-03-14
hello dear ofnuts 

thanks for the reply 
i want to store the outcome in a mysql-db 
instead of printing it out to the screen

therefore in have the peewee to help me...

so in  the end all should go into the database

---

