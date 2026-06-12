---
title: "Bug? X crashes on certain Firefox renderings."
date: 2005-01-06
forum: Repositories &amp; Backports
---

### Post by jdong on 2005-01-06
**NOTE**: Save all work before trying the procedure below. It will ZAP X, similar to the CTRL+ALT+BKSP key sequence.

I found a reproducable X crash. Before filing it to Ubuntu bugzilla, I'd like to confirm it.

1. Open up [http://ubuntuforums.org/favicon.ico](http://ubuntuforums.org/favicon.ico) in a new window / tab.
2. Scroll rapidly left and right by dragging the scrollbar.
3. X should crash, GDM should greet you to log in again! Yikes!


Configuration:

Firefox -- Latest Backport. (Someone with Warty firefox, please test!)
Warty + Backports
NVidia video card with NVidia 3-d drivers (self-compiled)
Kernel 2.6.10-cko1

---

### Post by randy on 2005-01-06
Didn't happen with the version of firefox that was in warty, but I've got an Intel video card.

---

### Post by gregorian21 on 2005-01-07
Doesn't seem to crach on mine.
 
  Configuration:
  
  Firefox -- Latest Backport.
  Warty + Backports (running the latest versions of all packages)
 S3 Savage4 
  Kernel 2.6.8.1-14

---

### Post by daniels on 2005-01-07
It's a bug in the nVidia binary driver -- you'll have to let them know.  Unfortunately, being a binary driver, I have no visibility into the driver, so I can't help you fix it at all.

---

### Post by eldados on 2005-02-09
I too have the same problem, firefox crash when i try to d/l a file. this is really annoying  :-?

---

### Post by neighborlee on 2005-03-16
[QUOTE=eldados]I too have the same problem, firefox crash when i try to d/l a file. this is really annoying  :-?[/QUOTE]
---------------

EDIT: I use nvidia-glx 6629 and I do NOT get the crash described here in this thread...
although as I say it does crash sometimes ( as it did in warty ) and takes X with it ( doesn't reboot though ).

===================================================
firefox 1.0.1 here in hoary preview release crashes for me too ( edit: not sure about that URL just yet but I will edit this if it does ) sometimes and takes X out ( doesn't reboot but makes X unuseable ).  just a FYI

cheers
nl
----

---

