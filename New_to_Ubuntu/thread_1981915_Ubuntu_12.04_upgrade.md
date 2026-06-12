---
title: "Ubuntu 12.04 upgrade"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by TFSinclair on 2012-05-17
I have downloaded and burned to a disk Ubuntu 12.04. When I try to install  12.04 from the disk or from my "downloads" folder, both give the same error, ie: "could not detect the autorun file". So my question is this; how do I install 12.04 in place  my 10.10 OS?
I'm still an Ubuntu newbie so any help tailored to my limited knowledge will be greatly appreciated.:p
Thanks,
TFSinclair

---

### Post by Lisiano on 2012-05-17
If you want to install using the disk, you need to reboot your PC and boot using the disk, much like you did when you installed 10.10, although you will not be able to upgrade (I think) and you will only be able to replace 10.10 with 12.04

---

### Post by grahammechanical on 2012-05-17
This

> could not detect the autorun file

sounds like a Windows error message to me. Is it? Install disks for Windows programs have an autorun file that Windows detects and then runs the instructions inside the AUTORUN.INF file.

Ubuntu install disks created by writing/burning an ISO image to CD do not have an AUTORUN.INF file.

You need to give a fuller explanation of your system. Have you installed Ubuntu 10.10 inside Windows using the Wubi installer method? In this case you may have downloaded the wrong ISO image.

[http://www.ubuntu.com/download/desktop/windows-installer]("http://www.ubuntu.com/download/desktop/windows-installer")

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows]("http://www.ubuntu.com/download/help/install-ubuntu-with-windows")

If you have installed Ubuntu 10.10 by running the Live CD and then using the Install alongside option so that Ubuntu is on its own partition and not inside the Windows OS as is the case with a Wubi install, then you can upgrade in two ways.

1) Launch Update Manager and make sure that the settings are set to notify you of the next release of Ubuntu. Then you should be able to upgrade from 10.10 to 11.04 and then again from 11.04 to 11.10 and then again from 11.10 to 12.04. That is the way it is done.

Or you can do a fresh install over 10.10 by burning the 12.04 ISO image to CD and booting from it. You select Install Ubuntu and it may give you an option to upgrade 10.10 to 12.04. Or you select the Do Something Else option and then tell the installer to install 12.04 into the partition that 10.10 is installed in.

We need to know what your set up is in order to give you more accurate advice.

Regards.

---

### Post by TFSinclair on 2012-05-18
> **Lisiano said:**
> If you want to install using the disk, you need to reboot your PC and boot using the disk, much like you did when you installed 10.10, although you will not be able to upgrade (I think) and you will only be able to replace 10.10 with 12.04
Boy, did I feel foolish when I read your post! I was trying to install 12.04 straight from inside the disk and got so wrapped up in trying that the simple solution NEVER crossed my mind. 12.04 is now installed and running mostly fine. Thanks for your timely response with a simple solution to my complex thinking.

---

### Post by Lisiano on 2012-05-18
Don't worry, everyone experiences that sometimes.

---

