---
title: "Include paths not set for g++"
date: 2010-02-25
forum: Packaging and Compiling Programs
---

### Post by imblack on 2010-02-25
I have this problem that the "glib.h" is in /usr/inlcludes/glib-2.0/ but I cant use it like

#include <glib.h> in my code, and therefore I am unable use pidgin-dev libraries to write my code.

How to include these directories so that g++ knows where to find these files?
I always have this problem please help.

Thanks,

---

### Post by lloyd_b on 2010-02-25
> **imblack said:**
> I have this problem that the "glib.h" is in /usr/inlcludes/glib-2.0/ but I cant use it like

#include <glib.h> in my code, and therefore I am unable use pidgin-dev libraries to write my code.

How to include these directories so that g++ knows where to find these files?
I always have this problem please help.

Thanks,

For any project requiring those, just add "-I/usr/include/glib-2.0/" to the g++ command.  This tells the compiler to add that directory to the list of directories to search for include files.

Alternately, if you set and export the environment variable CPLUS_INCLUDE_PATH with that directory, it will be automatically added to the search list.  Just type "export CPLUS_INCLUDE_PATH=/usr/include/glib-2.0/" before compiling (or add this to your ~/.bashrc file).

Lloyd B.

---

