---
title: "Can't Install SDL Dev"
date: 2010-03-15
forum: Packaging and Compiling Programs
---

### Post by sambo1972 on 2010-03-15
Hi,

I'm trying to compile a game from source, and one of the dependencies is SDL dev.  

I can't install SDL dev though because it seems to be dependant on an earlier version of the debian SDL package. The error message is:

libsdl1.2-dev:
  Depends: libsdl1.2debian (=1.2.13-4ubuntu4) but 1.2.14-0ubuntu1~karmic is to be installed

Should I remove libsdl1.2debian and replace it with libsdl1.2debian-all instead? 

Looking in Synaptic, that has the correct version, but I'm hesitant to mess with audio libraries under Koala since it was such a mess to get audio working to start with!

TIA

Sam

---

### Post by mc4man on 2010-03-16
> Should I remove libsdl1.2debian and replace it with libsdl1.2debian-all instead?
If you haven't got sorted out yet - no, probably not

What you should do is figure out where you got libsdl1.2debian (1.2.14-0ubuntu1~karmic) and get the same version # of libsdl1.2-dev

The current karmic repo version of libsdl1.2debian is  1.2.13-4ubuntu4
(lib and -dev version #'s must match

---

