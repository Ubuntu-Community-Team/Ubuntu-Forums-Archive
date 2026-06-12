---
title: "Added a software library package, can't find the *.h file"
date: 2007-07-15
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-07-15
I am trying to compile a piece of software that requires the curl library.  I did an "sudo apt-get install curl" to install the curl library.  However, after doing this and trying to rebuild my program, would not work.  So I wander over to /usr/include/ where I expect all my *.h files to be, but could not find curl.h.  What did I do wrong?  Do I have to use a flag with the apt-get install to make the library files available for compiling?

---

### Post by Paul820 on 2007-07-15
Did your use just curl or curl-dev? You need the dev files if your want the headers. Open synaptic and search for curl, then get the dev package.

---

### Post by trak87 on 2007-07-15
When installing libraries for the purpose of compiling programs look for libs with "dev" or "lib" in the title. For example, maybe you need to install libcurl3 or libcurl3-dev.

Go into Synaptic and do a search on "curl" and see what it finds. Chances are just the curl program isn't enough.

It's worth mentioning that doing programming will require the "build-essential" program as well.

---

### Post by SNYP40A1 on 2007-07-15
Thanks, that did the trick.  I'll look for the dev packages next time.

---

