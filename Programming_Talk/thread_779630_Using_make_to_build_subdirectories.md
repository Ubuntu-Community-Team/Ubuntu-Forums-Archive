---
title: "Using make to build subdirectories"
date: 2008-05-02
forum: Programming Talk
---

### Post by DBQ on 2008-05-02
Hey Everybody.  I am trying to accomplish the following:  I have a directory at the root at which I have a makefile.  Also the directory
contains two subdirectories.  Each subdirectory contains two makefiles with
instructions on how to build their targets.  How can I use the Makefile at the root directory to tell the system to build the two targets in the subdirectories.  

Another words, when the user types make in the root directory, the make utility will go to the subdirectory, and act as if the user typed make while being in that directory.  Then it will repeat the same thing in 
the second subdirectory. 

Thank you for your help.

---

### Post by dwhitney67 on 2008-05-02
Thanks for making your question an easy one. :-)

Here's a sample Makefile implementing something similar to what you need:
```
DIRS = dir1 \
       dir2 \
       dirN


all:
        @for i in $(DIRS) ; do \
                make -C $$i $@; \
                if [ $$? != 0 ]; then \
                        exit 1; \
                fi; \
        done
```
The "make -C" instructs the make-command to change directory to the 'value' ($$i) in $DIRS.  Try it on the command line and you will see.  For example:
```
$make -C dir1 all
```
Checking the status of the Make will stop the whole procedure should the build of any directory fail.

---

