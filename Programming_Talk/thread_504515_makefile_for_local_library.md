---
title: "makefile for local library"
date: 2007-07-19
forum: Programming Talk
---

### Post by Houman on 2007-07-19
hi there;

sorry about the vague ttile, but what i need to do is this:

I need to use a few small libraries in conjunction with my code, but i dont want to install these libraries on my system. In fact, i would like an arrangement as such:

home/stuff/myproject/  (in this folder all my source files and my makefile reside)
home/stuff/myproject/lib1  (in this folder all the sources for the library and its makefile reside)
home/stuff/myproject/lib2 (sources for lib 2 and its makefile)

previously i asked how i could link against a local library which is not installed in the system, the post is here:
[http://ubuntuforums.org/showthread.php?t=486026](http://ubuntuforums.org/showthread.php?t=486026)

Now my question is this, how do i maintain the three makefiles, and run the makefiles from the two local libraries from my main makefile? I dont want to have one makefule for everything so i think it would be best to run the other makefiles from my own project makefile (if its possible to run other makefiles from one makefile).


thank you ;

Houman

---

### Post by the_unforgiven on 2007-07-19
> **Houman said:**
> hi there;

sorry about the vague ttile, but what i need to do is this:

I need to use a few small libraries in conjunction with my code, but i dont want to install these libraries on my system. In fact, i would like an arrangement as such:

home/stuff/myproject/  (in this folder all my source files and my makefile reside)
home/stuff/myproject/lib1  (in this folder all the sources for the library and its makefile reside)
home/stuff/myproject/lib2 (sources for lib 2 and its makefile)

previously i asked how i could link against a local library which is not installed in the system, the post is here:
[http://ubuntuforums.org/showthread.php?t=486026](http://ubuntuforums.org/showthread.php?t=486026)

Now my question is this, how do i maintain the three makefiles, and run the makefiles from the two local libraries from my main makefile? I dont want to have one makefule for everything so i think it would be best to run the other makefiles from my own project makefile (if its possible to run other makefiles from one makefile).


thank you ;

Houman
The thread link you posted already answers your question about how to install libraries into path specified by you (by using the --prefix= option to configure).

As for calling other Makefiles from within your Makefile, check out the -C option to make.

So, a minimalistic top level Makefile will look like:
```
LIBS=lib1 lib2

libs:
        @for i in ${LIBS};              \
        do                              \
                $(MAKE) -C $$i;         \
        done

```
You can specify additional target information (for calling non-default targets) after $$i as well - like **$(MAKE) -C $$i libs**
HTH ;)

---

### Post by Houman on 2007-07-20
thank you for your reply;

the library that i speak of does not have a configure file (it just has a makefile and it has a whole bunch of classes in its source files that i need)

also i dont want to install it anywhere, i want to have it in a directory relative to my project diretory so i can move it to different computers and compile everything from scratch including the libraries;

regards

thanks (the c option to run another makefile does the job)

Houman

---

