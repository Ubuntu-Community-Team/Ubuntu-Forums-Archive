---
title: "Installing Ubuntu Problems"
date: 2014-11-30
forum: New to Ubuntu
---

### Post by hayden6 on 2014-11-30
when i was installing Ubuntu on my computer it stops when all the dots are red. It says i have 2 errors when i check the disc, any idea how to fix this? i have duel booted it with windows 8.1 so i can get  to the USB i am using to install it.

---

### Post by zircon_34 on 2014-11-30
more specs are needed for help... hardware and Ubuntu version? How did you install Ubuntu and format your drive?

---

### Post by fantab on 2014-12-01
Do a [SHA256Sum Check ]("https://help.ubuntu.com/community/HowToSHA256SUM")on the downloaded ubuntu.iso file and confirm its integrity. Re-download Ubuntu if the test fails.
Re-burn the ubuntu.iso again.

---

### Post by Gordonbp531 on 2014-12-01
If your computer came with Windows 8 pre-installed then you must:
a) use a 64 bit version of Ubuntu as the 64 bit version is the only one that will install on a UEFI machine and
b) You need to create the free space on the hard disk WITHIN WINDOWS - don't use GParted to do it - that could possibly bork your Windows install.

---

