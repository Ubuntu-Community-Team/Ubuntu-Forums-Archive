---
title: "libversion needed to compile python module"
date: 2008-10-17
forum: Packaging and Compiling Programs
---

### Post by Antickon on 2008-10-17
Hi all,

I'm trying to build a python module using python's disutils. It runs the following command, which in turn results in an error:

```
g++ -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions build/temp.linux-i686-2.5/cid.o -lversion -o build/lib.linux-i686-2.5/cid.so
/usr/bin/ld: cannot find -lversion
```

It looks like i need the "version" library. I tried apt-get'ing libversion and did some googling without succes. All that turns up is "libversion-perl".

Where do I get libversion?

____________


edit: I'm an idiot. My setup.py script stated libraries=['version'], I removed that -- problem solved.
This is not the way I usually do things :p

---

