---
title: "G++ problems"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by network.burner on 2011-10-04
Hey guys m pretty new to C++ and till now i was using DevC++ on windows.. Now that i know that G++ exists for ubuntu i wanna learn how to use it.
I tried searching through the thread and experimenting but no thread says anything about these errors:

```
rahul@Rahul:~/Desktop$ sudo ./1.cpp
sudo: ./1.cpp: command not found
```
and
```
rahul@Rahul:~/Desktop$ g++ 1.cpp
1.cpp:1: fatal error: iostream.h: No such file or directory
compilation terminated.

```

please help me out on using g++

---

### Post by d2btoo on 2011-10-04
Check your source file i.e. 1.cpp ....

Hint: maybe it's should read **#include <iostream>** rather than **#include<iostream.h>** ;)

---

### Post by snip3r8 on 2011-10-04
g++ 1.cpp -o appname

---

### Post by Birchle on 2011-10-04
> **snip3r8 said:**
> g++ 1.cpp -o appname
And after this, ./appname

If you have any other files that should be included (such as header implementation files, but not the actual .h files), you have to list them, too.
g++ 1.cpp imp.cpp third.cpp -o appname

It took me way too long to figure that out.  Hopefully this makes it faster for you!

---

