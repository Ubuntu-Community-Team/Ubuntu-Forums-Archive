---
title: "What's $(MAKE) or ${MAKE} actually in makefile doing ?"
date: 2018-03-11
forum: Packaging and Compiling Programs
---

### Post by abdulbadii on 2018-03-11
[COLOR=#242729][FONT=Arial]What's [/FONT][/COLOR]$(MAKE)[COLOR=#242729][FONT=Arial] or [/FONT][/COLOR]${MAKE} in makefile[COLOR=#242729][FONT=Arial] actually performing in entire [/FONT][/COLOR]make[COLOR=#242729][FONT=Arial] building process. is it invoking a process which is similar to sub-routine i.e. in simplest terms 'call a function', or is it starting a recursive process to the beginning of its own file ?[/FONT][/COLOR]

---

### Post by TheFu on 2018-03-11
Which "make" is being used?
gmake?  cmake?  They probably behave differently.
In gmake, it would call gmake with the arguments. Sorta recursive, but not really.  More like a system() call.  Often, it would be using a different default Makefile in a different directory (pwd).

---

### Post by abdulbadii on 2018-03-11
GNU make
Thanks a lot

---

### Post by TheFu on 2018-03-11
If you post the makefile and any includes, someone might be able to tell what it is doing.

I tend to create a makefile for each directory in my software projects, then at the top level directory, a makefile and controls building everything,packaging, and installation. Sometimes it will also perform DB setups or migrations from older versions of the software, updating the database tables as needed too.

Most software projects have these directories:
bin/
lib/
doc/
man/
inc/
test/
db/
conf/

Each of those would have a makefile to do something.  Docs? Makefile?  Sure - to translate a Markdown how-to into HTML or plain text. Might also take huge image files and optimize them for web viewing.  Doing that in a lib/ directory wouldn't make sense.

---

