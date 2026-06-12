---
title: "Removing Double Quotation From Python String"
date: 2009-04-08
forum: Programming Talk
---

### Post by cmnorton on 2009-04-08
Does anyone have examples for removing (") characters from python strings?

#/usr/bin/python

import sys
import struct

stream = sys.stdin
line = stream.readline()
mylist = []

while len(line):
    line.strip('\n')
    line.replace('\"','')
    mylist = line
    print mylist
    line = stream.readline()

The line.strip works, but not the line.replace. I want to remove double quotation marks from names (first name, last name), so these quotes will not be uploaded into my informix database.

---

### Post by ajackson on 2009-04-08
I think both strip and replace return the modified string rather than alter the string, so you would need something like
```

line = line.strip('\n')
line = line.replace('\"','')

```
or even
```
mylist = line.strip('\n').replace('\"','')
```

---

### Post by WW on 2009-04-08
In Python, strings are immutable--you can't modify them in-place.  The strip() and replace() methods don't modify the string, but instead return a new string.  So you'll have to make your changes the way ajackson described.

---

### Post by cmnorton on 2009-04-08
Multi Bene! Thank you for your answers, ajackson and WW. I forgot about immutable strings. 

I am beginning to appreciate why people like Python. I can in a few lines replace many many lines of C code that append blank columns to an upload file so that its columns match the db table into which it is being imported and clean up the input, by removing quotes and new lines.

---

