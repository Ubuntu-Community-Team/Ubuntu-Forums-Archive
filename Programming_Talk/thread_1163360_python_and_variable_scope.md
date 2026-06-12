---
title: "python and variable scope"
date: 2009-05-18
forum: Programming Talk
---

### Post by meg23 on 2009-05-18
I am trying to get a variable in python to have a scope of values. For instance:

x = 1,2,3,4,5

I then I want the program to loop using each value. How can I do this?

---

### Post by simeon87 on 2009-05-18
You can create a list like this:

```

x = [1, 2, 3, 4, 5]

```

And then to walk over the values:

```

for v in x:
    print v

```

---

### Post by meg23 on 2009-05-18
```
#! /usr/bin/python
a = '<a href="'
b = open('/home/moshe/Desktop/headlines.txt','r')
data = b.readlines()
c = '"</a>'
x = [1, 2, 3, 4, 5]
import os
print os.system("elinks -dump http://www.investors.com/NewsAndAnalysis/Section.aspx?sec=Business |grep -v Default | grep http | awk '{print $2}'> /home/moshe/Desktop/headlines.txt")
print str(a) + str(data[x]) + str(c)
```

I am trying to pipe those values of x into the data[x] and then have it reloop. Anything I am leaving out?

---

### Post by simeon87 on 2009-05-18
> **meg23 said:**
> ```
#! /usr/bin/python
a = '<a href="'
b = open('/home/moshe/Desktop/headlines.txt','r')
data = b.readlines()
c = '"</a>'
x = [1, 2, 3, 4, 5]
import os
print os.system("elinks -dump http://www.investors.com/NewsAndAnalysis/Section.aspx?sec=Business |grep -v Default | grep http | awk '{print $2}'> /home/moshe/Desktop/headlines.txt")
print str(a) + str(data[x]) + str(c)
```

I am trying to pipe those values of x into the data[x] and then have it reloop. Anything I am leaving out?

You're not walking over the values in the list x now. You're now passing x to data but x itself is a list. To walk over the values, you need to do (as an example):

```

x = [1, 2, 3, 4, 5]
for v in x:
    print data[v]

```

---

### Post by meg23 on 2009-05-18
Perfect. Thanks! I got it.

---

### Post by CptPicard on 2009-05-18
Just a note -- "[variable scope]("http://en.wikipedia.org/wiki/Scope_(programming)")" has a specific meaning in programming languages :)

---

