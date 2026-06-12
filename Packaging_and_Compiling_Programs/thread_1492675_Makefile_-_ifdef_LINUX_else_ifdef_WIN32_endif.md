---
title: "Makefile - ifdef LINUX else ifdef WIN32 endif"
date: 2010-05-25
forum: Packaging and Compiling Programs
---

### Post by dodle on 2010-05-25
I've been looking over some makefile tutorials, but I haven't found anything that specifies how to check for which OS the app is being compiled.  

I want to tell make to set variables according to which platform is found.
example:
```
ifdef LINUX
OUT=myapp

else ifdef WIN32
OUT=myapp.exe

endif
```
Is there a way to do this?

**Edit:** Okay, I realized that this probably cannot be done.  That is what the configure script is for, amongst other things.

---

