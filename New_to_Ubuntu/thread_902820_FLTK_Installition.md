---
title: "FLTK Installition?"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Xarver on 2008-08-27
I think FLTK looks interesting to learn,
and I want to install it but have no idea how...
I downloaded the tar.gz file and extracted it to the folder I want it in,
and I typed make in the terminal like it said in the readme
while the folder was open, and it didn't work... :confused:
```
'make: *** No targets specified and no makefile found.  Stop.

```

I'm trying to install it for g++.
My editor is SciTE [Not like that's important, anyway...]

Any help appreciated!

---

### Post by Sorivenul on 2008-08-29
First question: do you have build-essential installed.  
```
sudo apt-get install build-essential
```

If/once you have build-essential installed
```
cd /path/to/FLTK-source
```
where /path/to/FLTK-source is the directory you have the files in (specifically the Makefile).  

From there, you should be able to make then make install.

You should also be able to install libfltk1.1 libfltk1.1-dev and probably the libfltk1.1-doc from the repositories and work with the toolkit that way instead.

---

