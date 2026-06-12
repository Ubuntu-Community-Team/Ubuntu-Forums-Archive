---
title: "Anjuta Help!!!"
date: 2006-07-02
forum: Programming Talk
---

### Post by shawnrgr on 2006-07-02
hello, I am new to C but want to give it a whirl. I program vb.net and java currently. Very interested in coding for gnome. I downloaded Anjuta because everyone seemed to be raving about it. All I do is start the wizard to create a new gnome project. It gives me the classic hello world code already written. I compile all (works) then try to build all and i get this...

Building the whole Project: test2
make
make:*** No targets specified and no makefile found. Stop.
Completed ... unsuccessful

what am I doing wrong?
im new to linux, anjuta, and c. so please be nice ;)

---

### Post by Daverz on 2006-07-02
You can do gnome programming with Java.  

[http://java-gnome.sourceforge.net/cgi-bin/bin/view](http://java-gnome.sourceforge.net/cgi-bin/bin/view)

They have a video there showing how to do gnome development with eclipse.  You can even compile the java-gnome code to native binaries with gcj.

---

### Post by shawnrgr on 2006-07-02
--delete--

---

### Post by shawnrgr on 2006-07-02
ok, I found another post talking about certain development files. this solved alot of the previous errors I was getting. now it runs automake cleanly but when I try to run make this is what i get...

```
shawn@ubuntu:~/Projects/hello$ make
make  all-recursive
make[1]: Entering directory `/home/shawn/Projects/hello'
Making all in src
make[2]: Entering directory `/home/shawn/Projects/hello/src'
gcc  -g -O2  -o hello  main.o support.o interface.o callbacks.o -L/usr/local/lib -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_object_compat_control'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/libpango-1.0.so: undefined reference to `g_slice_free_chain_with_offset'
collect2: ld returned 1 exit status
make[2]: *** [hello] Error 1
make[2]: Leaving directory `/home/shawn/Projects/hello/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/shawn/Projects/hello'
make: *** [all-recursive-am] Error 2

```

---

