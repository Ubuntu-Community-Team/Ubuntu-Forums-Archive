---
title: "Updates for Lubuntu  on a USB"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by philpense on 2012-11-07
I am running Lubuntu  12.10 on a USB.  I find that everything I try to install fails.  This includes the package manager and software udater.  Is this a limitation of a USB install?  Guidance sought.

---

### Post by snowpine on 2012-11-07
Did you install to the USB, or create a Live USB? 
Live USB is basically meant as an intermediate step to evaluate and install the distro (not a permanent operating environment).

Anyway if you want to post some specific error messages, we can try to help. "I tried to install something but it failed" isn't an answerable question. :)

---

### Post by Linuxisfast on 2012-11-07
Did you give it persistent space while creating the USB? Otherwise whatever changes you make are wiped out on next reboot.

---

### Post by oldfred on 2012-11-07
Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

You probably need an 8GB flash drive to do a full install, but you can change to add persistence and update some things, but not kernel.

---

### Post by philpense on 2012-11-08
I believe that it was a simple iso burn to the usb... not the live install. Now I am not sure.  I have been able to launch it every day for five days.  Is there any to make certain which install I have?

---

### Post by oldfred on 2012-11-08
The ISO burn to a USB is usually a liveCD/USB. 

While the liveCD often asks as part of the boot whether you want to install or use live mode, the liveUSB boots and then shows an install icon. Full installs do not have the install option.

---

### Post by C.S.Cameron on 2012-11-08
Have a look at the files on the USB.
If there is a file named casper-rw, the install should be persistent.

---

### Post by alkh3myst on 2012-11-08
Philipsense, everybody's throwing jargon/buzzwords at you that you may not yet be familiar with. When you created a live USB, you have an option of reserving up to 4GB of space on the flash drive to store changes to your USB distro. This is the "persistence" "persistence file", "casper-rw" etc., that everybody's talking about. This file will remember the modifications you make, within the 4GB space limitation. **Come on guys, everybody's not a super L-K-X-Ubuntu geek, this is the Absolute Beginner's section!** It always bothers me when people try to explain stuff to others who are sincerely trying to learn, and leave out basic steps/concepts. With that said, our moderator has given you a wealth of links to help you set up persistence. Happy Lubuntuing. :)

---

### Post by amjjawad on 2012-11-08
> **philpense said:**
> I believe that it was a simple iso burn to the usb... not the live install. Now I am not sure.  I have been able to launch it every day for five days.  Is there any to make certain which install I have?


Long story short, have you used UNetbootin or application to create a bootable USB from the ISO of Lubuntu?

Or

You have followed [this]("http://ubuntuforums.org/showthread.php?t=1872303")? 


If you have used [UNetbootin]("http://unetbootin.sourceforge.net/") then this is a LiveUSB and NOT a real installation of Lubuntu.

If you have any question about Lubuntu, please ask ;)

---

### Post by amjjawad on 2012-11-08
> **alkh3myst said:**
> **Come on guys, everybody's not a super L-K-X-Ubuntu geek, this is the Absolute Beginner's section!** It always bothers me when people try to explain stuff to others who are sincerely trying to learn, and leave out basic steps/concepts. 

I do exactly know what you are talking about here. I've been there and I know how hard it could be.

It is really hard for those who have been here for ages to go easy and simple, specially those with lots of skills and experience. 
But yes, it is really necessary to go easy on a new comer. 

You have a valid point ;)

I guess not everyone can go so easy with new comers. It is a skill if you ask me :P

---

