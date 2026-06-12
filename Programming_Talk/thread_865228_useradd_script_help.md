---
title: "useradd script help"
date: 2008-07-20
forum: Programming Talk
---

### Post by toolbox03 on 2008-07-20
How do you write a useradd script that can take arguments like -p -s -g

Usage is as follows:

useradd.py -P ./passwd -S ./shadow –G ./group 
–p \'abc: x :1234:100:ABC:/home/heads/abc:/bin/ksh' \
-s 'abc: Dmq73sfegHequI:6666:0:0:0:0:0:0'

Any examples or sample code?

---

### Post by WW on 2008-07-20
I don't know about the "useradd" functionality that you want to implement, but the command line arguments are available in the array sys.argv. E.g.

argtest.py
```

import sys

print "There are %d command line arguments" % len(sys.argv)
print "sys.argv=", sys.argv

```
```

$ python argtest.py one two three      
There are 4 command line arguments
sys.argv= ['argtest.py', 'one', 'two', 'three']
$ 

```

Existing modules for parsing command line arguments include [getopt](http://docs.python.org/lib/module-getopt.html) and  [optparse](http://docs.python.org/lib/module-optparse.html).

---

