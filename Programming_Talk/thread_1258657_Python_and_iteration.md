---
title: "Python and iteration"
date: 2009-09-05
forum: Programming Talk
---

### Post by filifunk on 2009-09-05
I thought iteration would mean that it would take an object and go over it line by line. And each line would be progressed when you press enter or something like that.

When I used 'iterating over the file object' as shown in a book I have, I wrote this code for a file entitled "97.txt" which is a book taken from project gutenberg.

```


In [9]: for i, line in enumerate(open('../97.txt')):
   ...:     print "%d: %s" % (i, line.rstrip())


```

and it still ends up printing the whole book (albeit one line at a time).  How would you create a program that allows python to only look at it one line at a time and only progresses when you press enter?

---

### Post by smartbei on 2009-09-05
You could stick a raw_input in there, which would make it wait for your input (an enter, in this case).
```

for i, line in enumerate(open('../97.txt')):
    print "%d: %s" % (i, line.rstrip())
    a = raw_input("")

```

---

### Post by nipunreddevil on 2009-09-05
use readline function ```

#!/usr/bin/env python

f=open('/home/nipun/1.txt')
ans='y'
while ans=='y':
	print f.readline()
	ans=raw_input("Do you want to read more line y or n")
	
	

```

---

### Post by filifunk on 2009-09-05
great answers!

---

