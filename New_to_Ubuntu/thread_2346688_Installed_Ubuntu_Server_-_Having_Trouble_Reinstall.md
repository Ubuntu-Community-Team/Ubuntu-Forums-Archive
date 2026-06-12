---
title: "Installed Ubuntu Server - Having Trouble Reinstalling Windows"
date: 2016-12-17
forum: New to Ubuntu
---

### Post by wpgladden on 2016-12-17
Hi All - 

I am new to Ubuntu and Ubuntu Server, and I think I may have royally screwed up.  Here's hoping some of you all have some idea how to undo what I've done.  I have a NP700Z5C-S01UB Samsung Series 7 Chronos laptop.  In an attempt to execute something I did not fully understand, I installed Ubuntu Server 16.04 (I think) onto said laptop.  I have successfully installed Ubuntu Server.  However, I do not know how to use it and would like to re-install Windows 10 onto it.  This is the problem.  When I insert a bootable USB or a bootable DVD with a Windows ISO to reinstall Windows, the BIOS no longer recognizes these as bootable.  So it would appear I am stuck with Ubuntu Server installed with no way (that I know of) to reinstall Windows.  I am still interested in learning how to use Ubuntu but think that a side by side installation of Windows and Ubuntu Desktop would be a better place to start.  And so I ask: how do I reinstall Windows to a machine running Ubuntu Server 16.04 that does not recognize any kind of bootable media?

---

### Post by yancek on 2016-12-17
So what happens when you try to boot the windows iso from either the DVD or flash drive?
Have you tested the DVD and flash drive on another computer to see if it boots?
Are you sure you have the DVD/flash drive set to first bootable in the BIOS?
Did you have windows 10 installed using UEFI?  Did you install Ubuntu UEFI?
Ubuntu or any Linux installed does not have any effect on the BIOS.

---

### Post by wpgladden on 2016-12-17
1. Nothing happens.  It just loads Ubuntu Server.
2. I have tested both the DVD and flash drive on two other computers.  Both the DVD and flash drive worked on each of the two computers I tested them on.
3. Before I installed Ubuntu Server, the Boot Order was USB, CD/DVD, HDD.  I have not changed this.
4. The laptop itself came preloaded with Windows 7 and a BIOS with the capability to be upgraded to Windows 8/8.1/10 and use the UEFI boot.  Ubuntu Server was installed UEFI.

I recall the Ubuntu Server installation asking something along the lines of do you want to install using UEFI and then asked something else about the BIOS/UEFI settings.  All I know at this point is that I am not able to access the BIOS/UEFI to manually boot from an external device or to adjust any boot settings.  It is almost like Ubuntu is the only thing that the BIOS/UEFI sees and/or pays attention to.

---

### Post by mastablasta on 2016-12-19
if you overwrote the boot loade then ofcourse it is the only thing it sees. this not seeing the DVD might have something to do with UEFI ("secure boot" actually) being used. hard to say since i do not know much about it.

while you wait for this to be resolved you can easilly install the desktop version as long as PC is connected to internet. just run:
```

sudo apt-get ubuntu-desktop
```

type in the password for ubuntu user (you will not see anything typed) and press enter.

this command will install ubuntu desktop.

server is mean for servers which usually run headless (with no monitor attached) and so the command line interface is all you need.

---

