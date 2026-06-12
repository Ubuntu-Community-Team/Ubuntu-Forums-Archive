---
title: "could not write bytes: Broken Pipes on boot"
date: 2014-03-12
forum: New to Ubuntu
---

### Post by matt71 on 2014-03-12
I know this pretty well know, but I've run into it and can't for the life of me work a way around it. I'm running 12.04 on 64bit.

I've been reading forums all day to try to fix this myself but nothing I've tried so far has worked. I can physically see my data when I go to root and ls -a, so I know everything is there and that the hdd isn't dead. I can also access my data when I use "try ubuntu" from the liveusb but I can't get my own os to load past the broken pipes error. If anyone could help, I'd be super greatful.

---

### Post by matt71 on 2014-03-12
After running Boot Repair, this is the output: [http://paste.ubuntu.com/7077925/](http://paste.ubuntu.com/7077925/)

---

### Post by ajgreeny on 2014-03-12
I am no expert in UEFI but it looks as if you have an incompatibility between the manner in which you installed Ubuntu and the way your UEFI is setup.

You do not appear to have Windows on the machine and if so it will not matter if you install in UEFI or legacy mode, but you must boot the install medium, USB or DVD in the manner that you have the machine setup, ie boot the USB in UEFI mode to install as UEFI, or boot the USB in legacy/CSM/BIOS mode if that is the way you want to install.

Oldfred is a forum member who seems to know more about this problem than anyone else who is around here, and with luck he may see this thread and try to help more than I can.

See [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") for lots more details on all this.

---

