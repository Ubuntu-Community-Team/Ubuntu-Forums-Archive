---
title: "Setting Up config.h Defines from configure Script"
date: 2012-11-13
forum: Packaging and Compiling Programs
---

### Post by dodle on 2012-11-13
Is there a way to change the defines in a setup.h file from the configure command? I have compiled an older version of guile in a Unix-like environment but after I run configure I have to manually edit the setup.h file to comment out the line:
```
#define HAVE_STRUCT_TIMESPEC 1
```
Because it is already defined in pthread.h and throws an error during make if I don't. So if I could do this from the configure command it would save me a step.

**----- Edit -----**

I understand that you can use something like "CFLAGS=-D<macro>" to define a macro. But can it be undefined for the config.h file without affecting the macro defined in pthreads.h?

---

