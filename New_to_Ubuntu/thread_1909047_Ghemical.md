---
title: "Ghemical"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by Darren01 on 2012-01-14
I installed ghemical via the software center.

Everything seemed to work but ...

the icon in the applications/science area has a red bar through it ???

clicking on this icon does not open up the software.

Can anyone help?

I'm keen to do some molecular modeling but the software isn't working.

Help, help ...

---

### Post by TeoBigusGeekus on 2012-01-14
Try to run it from terminal with
```
ghemical
```
(probably) and post any error messages you get.

---

### Post by Darren01 on 2012-01-15
Typing ghemical at the command line gives ...

ghemical: symbol lookup error: /usr/lib/libghemical.so.5: undefined symbol: _ZTIN2sc7RefBaseE

---

### Post by anewguy on 2012-01-15
To test, I installed this package from synaptic package manager in 11.10.  I double-checked the dependencies against those in the ubuntu ghemical page on the net.  I also get this error.  I would have thought that if it needed a command line arguement or something it would have said so rather than just abort like that.  I'll be checking lauchpad later to see if a bug has been reported.

Dave ;)

---

### Post by anewguy on 2012-01-15
Indeed, there is a launchpad bug report [here]("https://bugs.launchpad.net/ubuntu/+source/mpqc/+bug/885740").  It supposedly is a bug in package mpqc.  The current version listed in synaptic package manager for 11.10 is 2.3.1-7, and the launchpad page says it has been fixed in 2.3.1-10.  I personally don't know how to retrieve that program for 11.10 - perhaps someone else does.  I'll ask some others with far greater knowledge than me and see if they know.

Dave ;)

---

### Post by anewguy on 2012-01-15
Well, I opened my own thread to try to find out how to get the version of mpqc and got several responses.  Yes, the package is available from sources other than Ubuntu, but it also includes a ton of dependencies we would have to go hunting for elsewhere as well.

I think the best recommendation came from my friend forestpiskie - wait for release 12.04 (April of this year) or hope it comes in an update prior to that.  The update mpqc is in the list of packages for 12.04 (precise).

Other than that, we can try the other sources way if you want to - it would be new to me as well. 

 EDIT:  tried backports, no luck.  I think it's better just to wait (or even try 12.04 now if you are daring enough to try the bleeding edge!).

Dave ;)

---

