---
title: "[SOLVED] for anyone who's interested ... using Ubuntu with MSI K9NGM4-F V.2 mobo"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-05-23
was trying to install Ubuntu 7.10 on a MSI K9NGM4-F V.2 motherboard based system (Anthlon64 2.4GHz AM2 cpu) and kept having the install hang up and not make it to the Desktop so I could double click the Install Icon. The Solution?

When booting from the CD (it's called Live CD) a list of choices are given. Choose "Start Ubuntu in Safe Graphics Mode" and that will get you to the Desktop where you can click on the install icon. Everything runs normal from there. I believe this all has to do with Ubuntu 7.10 not being able to recognize the newer 7025 on-board graphics of the MSI K9NGM4-F V.2 mobo and for some unknown reason, when you select safe graphics from within the install process - it hangs up.

This Motherboard works well with Ubuntu 7.10 and Restricted Drivers loaded with no problems   {8 ^,

---

### Post by oedha on 2008-05-23
try to boot from livecd again
press F6
edit the syntax by...delete quiet-splash
then press enter to boot
how was it........
maybe you should try ubuntu-8.04

EDIT : i have MSI K9AGM3-FIH and works fine in ubuntu-7.10 and 8.04

---

