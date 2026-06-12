---
title: "Add GRUB to windows system"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by saj0577 on 2008-05-21
Hey,

I have a problem with one of my windows machine which I cant convert to ubuntu just yet and i was wondering is there anyway I can install grub on it and only grub so I can handle the select menu how I am use to and how i want too.

Is this possible?

Saj

---

### Post by volkswagner on 2008-05-21
You can install grub via the live cd.  You should give more info.  Do you have other Operating systems on you pc?  Did you have a problem with a previous dual boot?

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by kellemes on 2008-05-21
> **saj0577 said:**
> Hey,

I have a problem with one of my windows machine which I cant convert to ubuntu just yet and i was wondering is there anyway I can install grub on it and only grub so I can handle the select menu how I am use to and how i want too.

Is this possible?

Saj

This is only possible if you install GNU/Linux besides it.. dual boot.
With a stand alone Windows install this will not work since Grub needs to store it's settings in your GNU/Linux boot-partition.

---

### Post by saj0577 on 2008-05-21
Okay so i need to edit the windows boot loader uff windows...

Saj

---

### Post by kellemes on 2008-05-21
> **saj0577 said:**
> Okay so i need to edit the windows boot loader uff windows...

Saj

Why is that?
Anyway, somewhere in the control center of Windows you can configure the bootloader.. forgot the steps actually, long time ago ;-)

---

### Post by saj0577 on 2008-05-21
The computer only has on OS and it gives u an option of the OS or the OS (both options identical).

And i want to automate it.

Saj

---

### Post by eriqjaffe on 2008-05-21
> **saj0577 said:**
> The computer only has on OS and it gives u an option of the OS or the OS (both options identical).

And i want to automate it.

SajIf it's XP (or 2000, for that matter), just edit the c:\boot.ini file, either removing the extraneous entry or lowering the timeout (which is ignored if there's only one OS entry):

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

Vista's a whole other ballgame, though.  I don't know how to edit its' bootloader.

---

### Post by saj0577 on 2008-05-21
Yeha its xp.

Thanks il mark as solved when i have tried and succesfully done it.

Saj

---

### Post by eriqjaffe on 2008-05-21
I should've mentioned that the boot.ini is hidden **and** protected, so you'll need to unhide & unprotect it before you can edit and save it.

There's also a GUI for it built-in to XP, but I can't remember how to get into it off-hand.

---

### Post by saj0577 on 2008-05-25
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

