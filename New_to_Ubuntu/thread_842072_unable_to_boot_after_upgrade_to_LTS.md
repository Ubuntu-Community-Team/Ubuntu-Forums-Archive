---
title: "unable to boot after upgrade to LTS"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by toddq on 2008-06-27
I attempted to upgrade to the latest LTS from my dual-boot Windows Ubuntu.  Now I have tried several suggestions but that has only got me into more trouble.  Right now I cannot boot on either Windows or  Ubuntu.  It appears that the major problems are these I have no vmlinuz installed so I cannot boot into Ubuntu, the Chainload into GRUB 2 doesn't work for windows.  If I boot from my recovery disk I cannot see everything.  For example, my Desktop directory gives me a permission denied.  At this point, I would be satisfied with a complete reinstall if I could recover my directories (e.g., Desktop).  Is that possible?  What should I try? 

I have tried following the advice in the help section about redoing my grub by entering grub and setting up the boot partition but of course this didn't work because I don't have vmlinuz or anything in my boot directory.  However, I was surprised that it destroyed by ability to boot into windows which I still could do at that point.  I also tried Supergrub which did no harm but did no good either.

---

### Post by finer recliner on 2008-06-27
so when you turn on your computer, what happens exactly? it sounds like your BIOS load fine, and GRUB loads okay, but when you choose a partition (linux/windows) to boot to, something goes wrong (?). is there an error or anything? what happens?


to recover your files, try booting from you ubuntu install disk. this will make it act like a live disk. from there you should be able to mount your local paritions (your windows and linux paritions). once you do that, you can copy your personal files to a USB thumb drive or something. then do a fresh install (also from the live disk) if you want.

---

