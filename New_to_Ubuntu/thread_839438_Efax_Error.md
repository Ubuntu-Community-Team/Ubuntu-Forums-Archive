---
title: "Efax Error"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by necronzero on 2008-06-24
I have a Gateway GT3035m

when i try to send a fax i get this errors.

My modem: Modem 56K ITU V.92

efax-0.9a: 11:41:40 opened /dev/ttyS0
efax-0.9a: 11:41:46 sync: dropping DTR
efax-0.9a: 11:41:50 sync: sending escapes
efax-0.9a: 11:41:56 Error: sync: modem not responding
efax-0.9a: 11:41:56 failed page /home/frenrihr/Desktop/ps.ps.001
efax-0.9a: 11:41:56 finished - no response from modem

any clues on how to fix this?

---

### Post by SupraGuy on 2009-08-12
Wish I had a solution for you, but I just have a similar problem.
 
Ubuntu 9.04 Jaunty.  Modem is an older external unit connected to /dev/ttyS0
 
```
# fax send MYFAXNUMBER test.ps
test.ps is postscript...
efax: Wed Aug 12 16:03:36 2009 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 03:36 opened /dev/ttyS0
efax: 03:43 sync: dropping DTR
efax: 03:47 sync: sending escapes
efax: 03:53 Error: sync: modem not responding
efax: 03:53 done, returning 4 (no response from modem)
There were errors (see MYFAXNUMBER.efax.log).
```
 
Looks like the same thing to me.
 
I got it to work once, right after power cycling the modem, but not again.

---

