---
title: "Problem installing GRUB - permission denied"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by amelie on 2008-09-04
Hi all! 
I'm trying to install Grub and following the INSTALL file I wrote 'make install' after other commands in the Terminal
But I have the errors 1 and 2 : no permission, install recursive error or something like that...
help me please :( 
Thanks in advance

---

### Post by Elfy on 2008-09-04
What grub are you trying to install? Where did you get it from?

---

### Post by Nepherte on 2008-09-04
It is much easier to install grub from the live cd / repositories depending on why you are installing grub. It is complaining about permissions because you don't have root priviliges. Place sudo in front of make install, but I suggest you look at the before mentioned solutions first.

---

### Post by Pro-reason on 2008-09-04
> **amelie said:**
> Hi all! 
I'm trying to install Grub and following the INSTALL file I wrote 'make install' after other commands in the Terminal
But I have the errors 1 and 2 : no permission, install recursive error or something like that...
help me please :( 
Thanks in advance

I don't understand.  There's not enough information.

“Installing GRUB” can mean two things: (1) adding the software to your Linux installation just as you would add any other program, (2) using that installed application to install the GRUB bootloader to your MBR.

This talk of “make install” makes it sound like you mean the former.  It sounds like you are compiling and installing GRUB from source.  Unless you are an expert (in which case you wouldn't be asking us for help), why would you do that?  GRUB is available in the repositories, and is installed by default.

If you want to install the bootloader to the Master Boot Record of a hard drive, then you are doing it wrong.

---

### Post by amelie on 2008-09-04
Hi again :) 
I install grub because I want to fit another OS on my hard disk and that's what my tutorial says (blush) I didn't know there were repositories, I just downloaded grub-0.97.tar.gz or sth like that and extracted it :) pro-reason -> “Installing GRUB” can mean two things: (1) adding the software to your Linux installation just as you would add any other program -> that's what I'm doing, and yeah, I'm not a PRO as you see :P
but still I'm loading different OS-s i think i'm in fact trying to  "install bootloader to the Master Boot Record of a hard drive"

---

### Post by Elfy on 2008-09-04
Does the other os not say that it is going to install grub that would be the normal behaviour afaik.

Perhaps you could sya which os it is - or paste the part of the tutorial which says install grub.

No need for blushing either...

---

### Post by Pro-reason on 2008-09-04
Follow this guide:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

It will explain how to use the live CD to install GRUB to the MBR.

But hang on a moment... you already have Ubuntu installed, right?  In that case you almost certainly are currently booting up with GRUB on your MBR.

All you need to do is add the new operating system to your */boot/grub/menu.lst* file.

You will only need to follow the above guide if the new OS overwrites your MBR.

Perhaps you could be less cagey about the other OS you are installing, and what your current set-up is.

---

### Post by amelie on 2008-09-04
Thank you Pro-reason - I know found out what my problem is =)
The first time I tried the command boot/grub/menu and etc it didn't work and i decided I haven't an installation of grub, so I started installing :) but I forgot that the command worked a while later :) I think I should just continue :) 
and yeah, thanks, I'll need the guide - i'm installing windows because many programs don't run on Linux :)

---

### Post by Elfy on 2008-09-04
Yea all you need to do is reinstall grub once you have installed the other os :)

Simple procedure - the thread pro-reason gives alos goes into other stuff you shouldn't need to worry about, if for some reason it doesn't install - get supergrub it should do it for you. Weel worth having around as a tool anyway as is partedmagic

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by maniheer on 2008-09-04
I was gonna say use the Live CD, too late now

---

