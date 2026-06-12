---
title: "packaging python program including glade file"
date: 2008-02-12
forum: Packaging and Compiling Programs
---

### Post by Megaqwerty on 2008-02-12
I have a python program which consists of a .py file, a .png, and a .glade file. It runs perfectly when the files are all in one directory. I was wondering:

1) How do I create a .deb for this (I have quite a bit of experience with creating "real" debs (i.e. without checkinstall or alien) when a setup.py or makefile is used. (also note that I have no idea how to create either file))?

2) What changes might I have to make to my .py file so that it will still be able to find the other files after they are installed?

Thanks,

Megaqwerty

P.S. I currently use: ```
self.gladefile = os.path.split(__file__)[0]+'/test.glade'
``` to access the glade file, 
and the glade file references the png simply like this: ```
<property name="pixbuf">logo.png</property>
```

---

### Post by 23meg on 2008-02-19
[http://www.debian.org/doc/packaging-manuals/python-policy/](http://www.debian.org/doc/packaging-manuals/python-policy/) may be a good starting point. I'd also be interested in input from others on this.

---

