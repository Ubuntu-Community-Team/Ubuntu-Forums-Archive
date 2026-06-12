---
title: "Missing NTLDR..."
date: 2008-04-23
forum: New to Ubuntu
---

### Post by camellochapin on 2008-04-23
Hi,

At the office I got a laptop with Vista OEM installed.  Due that most of the software we use runs only on XP I had to install XP also in a separate partition.  Because I don't like MS Operating systems... I decided to install linux (Xubuntu) on this machine for the daily usage...

Now the problem:  I don't know why but with GRUB I can access only Xubuntu and XP, not Vista.  While trying to access Vista from GRUB I get this error message:

> Missing NTLDR
> Ctrl+Alt+Del to reboot

I have GRUB configured for Vista and XP as follows:

```
# This entry automatically added by the Windows XP  installer for an existing
# windows installation

title           MS Windows Vista
root            (hd0,1)
makeactive
chainloader     +1

title           MS Windows XP
root            (hd0,0)
makeactive
chainloader     +1

```

Using Vista's recovery CD to repare it I get rid of GRUB, and that's what I don't want.  Reconfiguring GRUB... I get access to XP and Xubuntu... but not Vista.  I don't know if there is something wrong with GRUB configuration for Vista.  

What can I do to repair this "simple" issue?  Any further information you might require, just ask for it!  THANKS in advance!

---

### Post by milosz.galazka on 2008-04-25
Maybe [this]("http://neosmart.net/forums/showthread.php?t=924") will help.

---

