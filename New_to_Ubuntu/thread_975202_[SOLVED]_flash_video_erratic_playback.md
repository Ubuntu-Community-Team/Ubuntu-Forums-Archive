---
title: "[SOLVED] flash video erratic playback"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by fiskking on 2008-11-08
recently downgraded from Flash 10 back to 9.  

system:

Gutsy Gibbon
memory: 1gig
pentium 4 1.8ghz
firefox 3
disk space 8 gig

when starting firefox, videos play flawlessly ever since I downgraded back to flash9.  But after 10min. videos begin to bog down increasingly (skipping on playback).  Is this a result of Firefox 3.0?  I have heard that this browser use a lot of cpu to do functions.

---

### Post by philinux on 2008-11-08
I just opened 10 tabs at once. FF when t0 76% then back to 4% very quickly.
Flash 10 is very good from my experience.

---

### Post by fiskking on 2008-11-08
figured out what the problem was.. when I had first upgraded to flashplayer 10, I did not rm the old libflashplayer.so before installing.  I just removed the one I had, and upgraded back to flashplayer 10.  All is well.

---

