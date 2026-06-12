---
title: "fglrx 8.10 install"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by andrenb91 on 2008-11-10
I have downloaded the newest version of the ati video driver from amd's website, but I can't install it because when I run the command...

''sudo sh ati-driver-installer-8-10-x86.x86_64.run''

... it says that I can't install it at all.

how can I install this driver then?? can somebody help me?

---

### Post by jbrown96 on 2008-11-10
That version doesn't support X server 1.5.0, which is what Intrepid uses. There is a beta version of 8.11 available from ubuntu. Check the hardware driver manager. It's the most up-to-date version. Until ATI releases 8.11 you won't be able to use anything from their website.

---

