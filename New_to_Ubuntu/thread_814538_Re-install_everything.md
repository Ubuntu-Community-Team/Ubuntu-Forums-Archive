---
title: "Re-install everything ???"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by bilbo.san on 2008-05-31
Hi
hope any of you had a similar situation.

I have Win and Ubuntu on the same pc and in different partitions on the same hard disk. Now I am forced to re-install Win again... but the thing is, Do I have to also install Ubuntu as well? 
When the pc starts, a message comes up asking which OS I wish to use, I understand that Ubuntu added this on the start up... would that be gone If I re-install Win?

help!
e.

---

### Post by TeoBigusGeekus on 2008-05-31
You don't have to reinstall Ubuntu, just grub (Ubuntu's bootloader):
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by bilbo.san on 2008-06-01
Thanks!!!

---

### Post by kansasnoob on 2008-06-01
I'd first delete the old windows partition using Gparted (partition editor).

One thing you might want to consider also is that your Windows partition will no longer see itself as Drive C. Since it sees but can't read the Ubuntu partition it'll assign itself a Drive letter designation of F or G normally (depending on the number of hard, ROM or RW drives). Normally this is not a problem but I've found a few older pieces of Windows software that don't want to install anywhere but Drive C.

---

