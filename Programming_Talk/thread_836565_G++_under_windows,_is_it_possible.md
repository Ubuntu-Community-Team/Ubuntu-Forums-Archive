---
title: "G++ under windows, is it possible?"
date: 2008-06-21
forum: Programming Talk
---

### Post by StOoZ on 2008-06-21
is there a way to use g++ compiler under windows?? (im using windows 2000).

---

### Post by justinhj on 2008-06-21
Yes, it is possible. I use it to build my windows version of emacs.

g++ and most of the gnu development tools are part of Mingw32

[http://www.mingw.org/]("http://www.mingw.org/")

---

### Post by Can+~ on 2008-06-21
Installing [devcpp](http://www.bloodshed.net/dev/devcpp.html) also installs mingw.

---

### Post by cmay on 2008-06-21
hi
dev c++ or wxdev uses gcc / g++ .
its a port of gcc. a cygwin fork.
if i renember correctly.
just renember that  the alternative ming runtime is installed also otherwise it will use the microsoft librarires.

---

### Post by forger on 2008-06-21
> **StOoZ said:**
> is there a way to use g++ compiler under windows?? (im using windows 2000).

[http://www.google.com/search?q=g++ compiler windows]("http://http://www.google.com/search?q=g++ compiler windows")
this might work:
[http://www.cmc.edu/math/alee/g++/g++.html](http://www.cmc.edu/math/alee/g++/g++.html)

---

### Post by geirha on 2008-06-21
I recommend you try [cygwin](http://www.cygwin.com/). It gives you a lot of the utilities you would find in a regular linux system, including g++.

---

### Post by cmay on 2008-06-21
[http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)

i forgot make sure the link got on the post also,sorry.
there is a MSYS package on that homepage for download that is t a minimal ming system and has small bash shell as i recollect
 and there is a linux version of devc++ also.

the newer wxdevc++ is a rad tool for WXwindows on windows and is updated more often this the org devc++ project here is dead i think. 
anyway just wanted to post the link propely.

---

### Post by JupiterV2 on 2008-06-22
I do not recommend you use cygwin or msys (mingw fork of cygwin) if you don't want to require each user of your software to install the cygwin/msys runtimes for your application to work.

Using devcpp (or some other IDE) or just installing mingw and running g++/mingw_make32 from a command line is the better way to go IMO.

---

