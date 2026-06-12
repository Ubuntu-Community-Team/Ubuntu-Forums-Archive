---
title: "Virtualization"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by majexy033 on 2012-06-07
Please help me out!!!!!!!!!!!!!!!
I have a fully functioning Ubuntu 12.04 LTS, but still need some few Win7 stuff. I installed the virtualbox and tried to run Win7 on it. I allocated 512Meg for virtualbox. 
But the problem is that is have a .iso file of the OS but the virtualbox is failing to recognize and pick it.
Any idea as to what to do??????????????????????????...........:confused::confused::confused:

---

### Post by snowpine on 2012-06-07
A good first step is to verify the md5 checksum of the .iso you have legally purchased and downloaded from the Microsoft site, [as described here]("http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/checksum-for-win-7-iso-download/6f3b2f0f-b799-44db-96bf-0be61f068c1a?msgId=c16237c2-0858-466e-87c1-3fe3cf359781").

It would also be very helpful if you could describe what steps you have done so far, and *exactly* what happens when you try to boot the virtual machine. :)

(EDIT) is 512mb enough for Windows 7?

---

### Post by na5h on 2012-06-08
Windows 7 requires 1GB of RAM for the 32-bit version and 2GB for the 64-bit version.

You should have a look at this tutorial:
[https://help.ubuntu.com/community/VirtualBox/FirstVM](https://help.ubuntu.com/community/VirtualBox/FirstVM)

---

### Post by Paqman on 2012-06-08
> **snowpine said:**
> A good first step is to verify the md5 checksum of the .iso you have legally purchased and downloaded from the Microsoft site, [as described here]("http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_install/checksum-for-win-7-iso-download/6f3b2f0f-b799-44db-96bf-0be61f068c1a?msgId=c16237c2-0858-466e-87c1-3fe3cf359781").


This. And if it doesn't check out _do not_ use it. People seed infected OSes and software online all the time.

If you're short on RAM and need a Windows environment you could pick up a copy of XP pretty cheaply. It would run fine on 512MB.

---

