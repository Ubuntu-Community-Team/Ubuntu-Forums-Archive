---
title: "Python array problem"
date: 2009-05-30
forum: Programming Talk
---

### Post by matmatmat on 2009-05-30
I have this program:
```

import os
from re import split
from re import sub 
class urlManager(object):
    def printAll(self):
        print "Name|\t|URL|\t|Description|\t|Rating|"
        p = ""
        for o in list:
            try:
            	p += o.printAll() 
            except:
            	p += o
        
	a = split("\|", p)
        return p  
             
    def writeToFile(self):
        f = open("urls.txt", "w")
        for o in list:
            try:
		data = o.printAll()  
	    except:
		data = o
            f.write(data) 
       
	f.close()
    def readFromFile(self):
	f = open("urls.txt", "r")
        u = []
	for line in f.readlines():
            line = line.split("|\t|")
            for l in line:
                da = []
                if l.endswith('\n'):
                        da.append(l)
                        print l.split("|")[0]

                else:
                        da.append(l)
                        print l
            u.append(da)
        print len(u)
        for i in range(len(u)):
                o = urlEntry(u[i][0], u[i][1], u[i][2], u[i][3])
                list.append(o)
	f.close()
	
    def firefoxStart(self, i):
	os.system("firefox %s" % list[i - 1].url)

class urlEntry(object):
    def __init__(self, nm, url, de="", ra=""):
        self.name = nm
        self.url = url
        self.description = de
        self.rating = ra
    def printAll(self):
        return "%s|\t|%s|\t|%s|\t|%s|\n" % (self.name, self.url, self.description, self.rating)
        
i = 0
list = []
add = urlManager()
add.readFromFile()
while i != "q":
    i = raw_input("Please enter you option add/list/open/quit [a/l/o/q]:\n")
    if i == "l":       
        p = add.printAll()
        print p
    if i == "a":
        name = raw_input("Please enter a name:\n")
        url = raw_input("Please enter a url:\n")
        description = raw_input("Please enter a description:\n")
        rating = raw_input("Please enter a rating out of 10 (eg 10/10):\n")
        a = urlEntry(name,url,description,rating)
        list.append(a)
    if i == "o":
        p = add.printAll()
        print p
        choice = raw_input("Enter a number for your choice (eg 1 for the first entry listed):\n")   
        add.firefoxStart(int(choice))	
add.writeToFile()   

```
when run:
```

$ python urlmanager.py 
a
a
a
a
s
s
s
s
2
Traceback (most recent call last):
  File "urlmanager.py", line 63, in <module>
    add.readFromFile()
  File "urlmanager.py", line 44, in readFromFile
    o = urlEntry(u[i][0], u[i][1], u[i][2], u[i][3])
IndexError: list index out of range

```
urls.txt is:
```

a|	|a|	|a|	|a|
s|	|s|	|s|	|s|

```
what am i doing wrong?

---

### Post by crdlb on 2009-05-30
In readFromFile, you're calling da = [] for each part of the list, so only the last part is getting added to the list of lines. Just move it up into the next outer scope, and it will work.

That said, you can greatly simplify that function: ```
    def readFromFile(self):
        f = open("urls.txt", "r")
        for line in (l.split("|\t|") for l in f):
                o = urlEntry(line[0], line[1], line[2], line[3])
                list.append(o)
        f.close()
```

You can use a regular loop if you're not comfortable with that generator expression there.

Also, don't use so many one-letter and two-letter variable names; it makes it hard to get meaning from them.

---

### Post by ssam on 2009-05-30
its best to loop over something, rather using range and len
instead of
```

        for i in range(len(u)):
                o = urlEntry(u[i][0], u[i][1], u[i][2], u[i][3])
                list.append(o)

```
do
```

        for part_of_u in u:
                o = urlEntry(part_of_u[0], part_of_u[1], part_of_u[2], part_of_u[3])
                list.append(o)

```
this may also work
```

        for part_of_u in u:
                o = urlEntry(*part_of_u)
                list.append(o)

```
and if you want to contract down into a list comprehension
```

                list_of_urls = [urlEntry(*part_of_u) for part_of_u in u]

```

also note that its a bad idea to call a list 'list', as it will hide the type list. for example try the following code

```

>>> list
<type 'list'>
>>> a = list((1,2,3))
>>> a
[1, 2, 3]
>>> b = list("hello")
>>> b
['h', 'e', 'l', 'l', 'o']
>>> list = []
>>> list
[]
>>> c = list(1,2,3)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'list' object is not callable

```

---

### Post by matmatmat on 2009-06-02
Thanks, when i run the other code:
```

$ python urlmanager.py 
Please enter you option add/list/open/quit [a/l/o/q]:
a
Please enter a name:
a
Please enter a url:
a
Please enter a description:
a
Please enter a rating out of 10 (eg 10/10):
a
Please enter you option add/list/open/quit [a/l/o/q]:
l
Name|	|URL|	|Description|	|Rating|
a|	|a|	|a|	|a|

Please enter you option add/list/open/quit [a/l/o/q]:
q
$ python urlmanager.py 
Please enter you option add/list/open/quit [a/l/o/q]:
l
Name|	|URL|	|Description|	|Rating|
a|	|a|	|a|	|a|
|

```
what's wrong with the regex (if that is what's wrong)?

---

### Post by ssam on 2009-06-02
its usually best to use the python string functions rather than regex.
[http://docs.python.org/library/string.html](http://docs.python.org/library/string.html)

---

### Post by matmatmat on 2009-06-04
bump

---

### Post by crdlb on 2009-06-04
What exactly isn't working? Did you remove the regex as ssam suggested?

---

### Post by matmatmat on 2009-06-06
EDIT:
It now works:
```

import os
from re import split
from re import sub 
class urlManager(object):
    def printAll(self):
        print "Name|\t|URL|\t|Description|\t|Rating|"
        p = ""
        for o in list:
            try:
            	p += o.printAll() 
            except:
            	p += o
        
	a = split("\|", p)
        return p  
             
    def writeToFile(self):
        f = open("urls.txt", "w")
        for o in list:
            try:
		data = o.printAll()  
	    except:
		data = o
            f.write(data) 
       
	f.close()
    def readFromFile(self):
        f = open("urls.txt", "r")
        for line in (l.split("|\t|") for l in f):
                o = urlEntry(line[0], line[1], line[2], line[3].strip("|")[0])
                list.append(o)
        f.close()
	
    def firefoxStart(self, i):
	os.system("firefox %s" % list[i - 1].url)

class urlEntry(object):
    def __init__(self, nm, url, de="", ra=""):
        self.name = nm
        self.url = url
        self.description = de
        self.rating = ra
    def printAll(self):
        return "%s|\t|%s|\t|%s|\t|%s|\n" % (self.name, self.url, self.description, self.rating)
        
i = 0
list = []
add = urlManager()
add.readFromFile()
while i != "q":
    i = raw_input("Please enter you option add/list/open/quit [a/l/o/q]:\n")
    if i == "l":       
        p = add.printAll()
        print p
    if i == "a":
        name = raw_input("Please enter a name:\n")
        url = raw_input("Please enter a url:\n")
        description = raw_input("Please enter a description:\n")
        rating = raw_input("Please enter a rating out of 10 (eg 10/10):\n")
        a = urlEntry(name,url,description,rating)
        list.append(a)
    if i == "o":
        p = add.printAll()
        print p
        choice = raw_input("Enter a number for your choice (eg 1 for the first entry listed):\n")   
        add.firefoxStart(int(choice))	
add.writeToFile()      

```

---

