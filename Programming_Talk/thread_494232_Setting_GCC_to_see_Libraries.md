---
title: "Setting GCC to see Libraries"
date: 2007-07-06
forum: Programming Talk
---

### Post by christoforever on 2007-07-06
Hey i come from a mostly java background. While more or less teaching myself C, i've run into a problem. I've been using anjuta which is fantastic, and does the trick. But i like using gedit for programming. Anyway i was wondering how to set gcc to see my libraries, or rather gtk, or glib libraries or any other libraries. There must be a file i can alter to set gcc to see extra libraries permanently. Just dont know how to go about doing so.

sincerely and with thanks ahead of time,
Chris Dancy

---

### Post by Mr. C. on 2007-07-06
There are a number of considerations.  Can you be more specific ?

There are standard library paths (eg. /lib, /usr/lib), the environment variable LD_LIBRARY_PATH, options you specify at link time, etc.

```
man ld.so ldconfig
cat /etc/ld.so.conf
```

MrC

---

### Post by christoforever on 2007-07-07
Say if i wanted to set GCC to see   /home/dancy/Mylib How would I go about making gcc look at that path?

---

### Post by christoforever on 2007-07-07
i.e:  gcc points to /usr/include    for all its C header files.  So if i wanted to gcc to point at  /usr/include/gtk
what would i do to make gcc point at this library permanently?

thanks again,
Chris Dancy

---

### Post by Mr. C. on 2007-07-07
Use -I and -L and -l (the letter ell ) for include file search directory and library search directory. These are compile and link time options; for -L, it is not a runtime configuration.

```
man gcc
```

MrC

---

