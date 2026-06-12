---
title: "configure anjuta to include sdl libraries to a project"
date: 2011-02-28
forum: Programming Talk
---

### Post by gufide on 2011-02-28
Hi everyone, no one know how to configure anjuta to include SDL libraries to a project? Thanks

---

### Post by Zugzwang on 2011-02-28
You can find the relevant documentation of the IDE here:

[http://library.gnome.org/devel/anjuta-manual/2.4/project-config.html.en](http://library.gnome.org/devel/anjuta-manual/2.4/project-config.html.en)

---

### Post by gufide on 2011-03-01
Good, I added my dependencies but all SDL function is "undefined reference" What should I do?

---

### Post by gufide on 2011-03-01
I got this output on build in the IDE:
```
Building in directory: /home/master/chipper/Debug
make
/bin/bash ./config.status --recheck
running CONFIG_SHELL=/bin/bash /bin/bash /home/master/chipper/configure --enable-maintainer-mode CFLAGS=-g -O0 CXXFLAGS=-g -O0 JFLAGS=-g -O0 FFLAGS=-g -O0 --no-create --no-recursion
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
configure: error: source directory already configured; run "make distclean" there first
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
make: *** [config.status] Error 1
Completed unsuccessfully
Total time taken: 1 secs
```

no one know what is this?

---

### Post by gufide on 2011-03-03
nobody?

---

### Post by Zugzwang on 2011-03-04
The error message is clear: You are supposed to run "make distclean" in your source directory.

---

### Post by gufide on 2011-03-04
I run it but I got always undefined reference to all SDL function... I added my modules and libraries: [ATTACH]185099[/ATTACH]

---

### Post by gufide on 2011-03-05
so... no one know where is the compiler and linker settings?

---

### Post by gufide on 2011-03-06
*bump*

---

### Post by Zugzwang on 2011-03-07
It look like noone is using Anjuta in conjunction with SDL here. I can only advise you to seriosly consider trying to build your application from the terminal first and see where things go wrong. Try to run the configure scripts from the terminal and observe how g++ is being called when building the project. Check which are the options given and see if the ones needed to get your project compiling with SDL are actually given.

---

