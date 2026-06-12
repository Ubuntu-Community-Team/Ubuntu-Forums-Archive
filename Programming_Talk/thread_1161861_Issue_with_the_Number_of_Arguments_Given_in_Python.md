---
title: "Issue with the Number of Arguments Given in Python"
date: 2009-05-17
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-05-17
Ey fellas I am having a problem with the number of arguments I am sending to the constructor of a class. Here is the relevant portions of my code:

```

#...
class event(object):
    date = ""
    part = []
    video = []
    members = []
    dvdNum = 0
    def __init__(d, p, v, c, m):
        members = m
        date = d
        dvdNum = c
        #if longer than a single digit, pass to parser
        if len(p) > 1:
            part = numParser(p)
        else: #append p converted to int to the end of the list
            part.append(int(p))
        if len(v) > 1:
            numParser(v)
        else:
            part.append(int(v))

#...

def makeObj(members, date, pt, vid, count):
    print "got here!"
    newone = event(date, pt, vid, count, members)
    allEvents.append(newone)
    printEvent(newone)

#...
count = -1 #iterates up and starts at -1 to compensate
#...
members = [] #list of strings
#...
pt = ''
vid = ''
date = ''
#...
makeObj(members, date, pt, vid, count)

#...

```
And here is the error I recieve:
```

Traceback (most recent call last):
  File "C:...JamVidParser.py", line 172, in <module>
    makeObj(members, date, pt, vid, count)
  File "C:...JamVidParser.py", line 36, in makeObj
    newone = event(date, pt, vid, count, members)
TypeError: __init__() takes exactly 5 arguments (6 given)

```

I have no idea why it thinks I am passing in 6 arguments when I am only passing in 5... Any help greatly appreciated!

---

### Post by Martin Witte on 2009-05-17
Your missing the reference to self in the __init__ method:

```
>>> class event(object):
	def __init__(self, d, p, v, c, m):
		pass

	
>>> x = event(1, 2, 3, 4, 5)
>>> print x
<__main__.event object at 0x949cd8c>
>>>

```

---

### Post by StunnerAlpha on 2009-05-17
> **Martin Witte said:**
> Your missing the reference to self in the __init__ method:

```
>>> class event(object):
	def __init__(self, d, p, v, c, m):
		pass

	
>>> x = event(1, 2, 3, 4, 5)
>>> print x
<__main__.event object at 0x949cd8c>
>>>

```
Ah! Can't believe I missed that. Thanks a bunch dude.

---

### Post by days_of_ruin on 2009-05-17
> **StunnerAlpha said:**
> Ey fellas I am having a problem with the number of arguments I am sending to the constructor of a class. Here is the relevant portions of my code:

```

#...
class event(object):
    [B]date = ""
    part = []
    video = []
    members = []
    dvdNum = 0[/B]
    def __init__(d, p, v, c, m):
        members = m
        date = d
        dvdNum = c
        #if longer than a single digit, pass to parser
        if len(p) > 1:
            part = numParser(p)
        else: #append p converted to int to the end of the list
            part.append(int(p))
        if len(v) > 1:
            numParser(v)
        else:
            part.append(int(v))

#...

def makeObj(members, date, pt, vid, count):
    print "got here!"
    newone = event(date, pt, vid, count, members)
    allEvents.append(newone)
    printEvent(newone)

#...
count = -1 #iterates up and starts at -1 to compensate
#...
members = [] #list of strings
#...
pt = ''
vid = ''
date = ''
#...
makeObj(members, date, pt, vid, count)

#...

```
And here is the error I recieve:
```

Traceback (most recent call last):
  File "C:...JamVidParser.py", line 172, in <module>
    makeObj(members, date, pt, vid, count)
  File "C:...JamVidParser.py", line 36, in makeObj
    newone = event(date, pt, vid, count, members)
TypeError: __init__() takes exactly 5 arguments (6 given)

```

I have no idea why it thinks I am passing in 6 arguments when I am only passing in 5... Any help greatly appreciated!

Is there a good reason for these variables to not be declared in the __init__ function? Because the way it is now all those variables will be shared with every instance of this class you make.

---

### Post by StunnerAlpha on 2009-05-17
> **days_of_ruin said:**
> Is there a good reason for these variables to not be declared in the __init__ function? Because the way it is now all those variables will be shared with every instance of this class you make.

Good call man, changed it to this:
```

class event(object):
    #date = ""
    #part = []
    #video = []
    #members = []
    #dvdNum = 0
    def __init__(self, d, p, v, c, m):
 #       print "in init:",self.part
        self.part = []
 #       print "in init2:",self.part
        self.video = []
        self.members = m
        self.date = d
        self.dvdNum = c
        #if longer than a single digit, pass to parser
        if len(p) > 1:
            self.part = numParser(p)
        else: #append p converted to int to the end of the list
            if p != '0':
                #print "PART2: ",p
                self.part.append(int(p))
        if len(v) > 1:
            #print "printing v inside the init func: ", v
            self.video = numParser(v)
            #print "after the numParser call: ", self.video
        else:
            #print v
            if v != '0':
                self.video.append(int(v))

```
And its working well. Thanks.

---

