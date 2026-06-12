---
title: "g++/gcc question"
date: 2007-05-31
forum: Programming Talk
---

### Post by commike37 on 2007-05-31
Ok, so I'm trying to include some headers in my code, but there are some problems.

Everything I need is somewhere in /usr/include/.  The problem is that it may be buried in a directory or two.  One of the packages I downloaded has some source code with this statement:
```
#include <libxml/somefile.h> 
```

The files it's trying to include are actually in libxml2/libxml/somefile.h.  So why can't g++/gcc just search not just /usr/include, but /usr/include/libxml2?  There are other files that have the same problem.  Granted, I could just use the -I flag, but I don't want to use an -I flag each and every time a header is in /usr/include/somedirectory.  

Is there a flag that will recursively search through each subdirectory in /usr/include and other search paths?

---

### Post by Blender on 2007-06-01
Well, that's the purpose of the almighty configure-script most packages come with. 
There are differences between different distros as well as between different Unix 
systems.
You have two choices, IMHO:
[LIST=1]
[*] Pass the include directories (the -I flag)
[*] Use a build system (such as GNU Autotools and CMake) that is able to find most of
the things for you.
[/LIST]

I, personally, use the first one for small projects (a single, short Makefile, at most) and CMake for everything else.

---

### Post by harun on 2007-06-01
Have you tried:

```

g++ -Wall `pkg-config libxml-2.0 --cflags --libs` test.cpp -o test

```

I am using libxml2-dev and no files are placed below the normal sub directories. Did you place them there yourself? If you did that it is ok, we would just need  to know that to help you.

---

