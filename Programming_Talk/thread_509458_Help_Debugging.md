---
title: "Help Debugging"
date: 2007-07-25
forum: Programming Talk
---

### Post by Nekiruhs on 2007-07-25
Hey guys. I'm trying to write a practice program that will Get info from the user (Name Age Telephone), then write it to ~/InfoGet. Unfortunately, I keep running into an error with the split function of strings.  Anyone wanna help? its in python. The error message is a syntax one.

```
#!/usr/bin/env python
#NfoGet: Get Info and write to file

#Import statements

from os import system as s
import sys

class person(object):
    name = ""
    age = ""
    tele = ""
    def __init__(self):
        tempinfo = raw_input("Enter a Full Name, Age and Telephone # separated by commas: "
        nfo = tempinfo.split(sep=", ") #Heres where the error is
        object.name = nfo[0]
        object.age = nfo[1]
        object.tele = nfo[2]
While 1:
    temp = person()
    create(temp)
    s('echo ' + temp.name + ' ' +  temp.age + '' + temp.tele + ' >> ~/InfoGet')
    yesno = raw_input("More info? [Y/n]: "
    if yesno is '':
    	continue
    else:
    	break

```

---

### Post by Soybean on 2007-07-25
> **Nekiruhs said:**
> nfo = tempinfo.split(sep=", ") #Heres where the error is

Well, I tried just this line (after setting tempinfo to a valid string, of course), and the error I got was "TypeError: split() takes no keyword arguments." 

Ok, well, > sep=", " looks like a keyword argument (I don't know much python, but if anything in that line is a keyword argument, I figure it's that). Apparently, split doesn't take those. According to the python documentation ([http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)), split's first argument is sep anyway, so:

```
nfo = tempinfo.split(", ")
```
ought to do what you want, without the error. :)

---

### Post by Nekiruhs on 2007-07-25
You see, it works in the interactive session. But not in the actual code...

---

### Post by Soybean on 2007-07-25
Ah... it seems python gives somewhat confusing errors when you leave off closing parentheses. ;)

Note that this still doesn't work, but it's fixed the error you were asking about (and a couple of others). Like I said, I don't know much Python. I'm just good with confusing error messages, because I do a lot of STL programming. :D

```
#!/usr/bin/env python
#NfoGet: Get Info and write to file

#Import statements

from os import system as s
import sys

class person(object):
    name = ""
    age = ""
    tele = ""
    def __init__(self):
        tempinfo = raw_input("Enter a Full Name, Age and Telephone # separated by commas: "[COLOR="Red"]**)**[/COLOR]
        nfo = tempinfo.split[COLOR="Red"]**(", ")**[/COLOR]
        object.name = nfo[0]
        object.age = nfo[1]
        object.tele = nfo[2]
[COLOR="Red"]**while 1:**[/COLOR]
    temp = person()
    create(temp)
    s('echo ' + temp.name + ' ' +  temp.age + '' + temp.tele + ' >> ~/InfoGet')
    yesno = raw_input("More info? [Y/n]: "[COLOR="Red"]**)**[/COLOR]
    if yesno is '':
    	continue
    else:
    	break

```

---

### Post by Nekiruhs on 2007-07-25
Wow, thanks. It would have taken me forever to see that, lol. And I call myself a programmer....  Well, heres the finished file if anyone is interested.

```
#!/usr/bin/env python
#NfoGet: Get Info and write to file

#Import statements
from os import system as bash
import sys
import string

class person(object):
    name = ''
    age = ''
    tele = ''
    def __init__(self):
        userinput = raw_input("Enter a Full Name, Age and Telephone # separated by commas: ")
        info = userinput.split(", ")
        person.name = info[0]
        person.age = info[1]
        person.tele = info[2]
while 1:
    temp = person()
    bash('echo "' + temp.name + ' ' + '|' + ' ' + temp.age + ' ' + '|' + ' ' + temp.tele + '" >> ~/InfoGet')
    yesno = raw_input("More info? [Y/n]: ")
    if yesno is '' or yesno is 'y' or yesno is 'Y':
        continue
    else:
        break

```

---

