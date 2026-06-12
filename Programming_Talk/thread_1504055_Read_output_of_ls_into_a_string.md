---
title: "Read output of ls into a string?"
date: 2010-06-07
forum: Programming Talk
---

### Post by Zorgoth on 2010-06-07
How can I read the output of ls into a string so that I can use C++ to read all the files in a directory?  Also, is there a way to make it so C++ will know which objects are folders?

---

### Post by radeon21 on 2010-06-07
You probably don't want to use *ls* to read into a directory with C++.  Take a look at POSIX functions like *opendir()* ([http://www.opengroup.org/onlinepubs/009695399/functions/opendir.html](http://www.opengroup.org/onlinepubs/009695399/functions/opendir.html))

I'm not an expert at all, but I think this is the direction you should be going.  Good luck!

---

