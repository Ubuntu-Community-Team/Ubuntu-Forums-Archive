---
title: "Screens found, but none with a usable configuration."
date: 2012-03-14
forum: New to Ubuntu
---

### Post by jeffraymond24 on 2012-03-14
I'm a first time Ubuntu user. I installed Ubuntu 11.10 using the alternate installer since the normal one refused to work. Installation was smooth, but when I selected to boot it for the first time from the Grub menu, I get a black screen, but I can hear the login screen sound. 

When I run Ubuntu in recovery mode, I discovered a couple error messages, including "Screens found, but none have a usable configuration" and "No screens found". When checking the disk for errors, it gets to the message "Start loading fallback graphics device" with a red "fail" next to it. As an absolute beginner, I have no idea how to handle this, despite reviewing several similar threads with zero success. 

Computer specs:
Gateway NV55S20u
4 GB DDR3
AMD Quad-Core Processor
AMD Radeon HD 6520G 512 MB Graphics (suspected problem)

---

### Post by MSPdwalt on 2012-03-14
You're probably right about the AMD (ATI) card being the issue.  If you do Ctrl+Alt+F1 can you get to a console?

If you can you may be able to install the amd drivers, reboot, and see if it likes you.

---

