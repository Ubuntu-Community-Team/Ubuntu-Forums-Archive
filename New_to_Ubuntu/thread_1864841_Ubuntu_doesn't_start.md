---
title: "Ubuntu doesn't start"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by shico90 on 2011-10-19
Hello, when I opened the Ubuntu today. it doesn't start up. it just freezes at the purple screen.
when I pressed shift while opening, the grub opened, I choosed recovery mode but it freezes too after writing this line "loading initial ramdisk"
please help.

---

### Post by kemtnbkr on 2011-10-20
You have a few options.  If you don't have too many customizations, you could just do a fresh reinstall.  

Have you tried the 'boot to recovery terminal' option?  That might work; if that doesn't, I don't think your system will be rescuable.

---

### Post by ld114 on 2011-10-20
I am not an expert in this by any means, but will your system boot up from a 'live' disk (ie the one used to install Ubuntu from)? If it does, then the problem is most likely with your installation of Ubuntu on the hard disk than with a hardware problem. If you can't boot Ubuntu from the live disk (after a few tries) then you may have a hardware problem.

You might have a look at this thread from the Debian user forum (Ubuntu is based on Debian) and it might help. It suggests that this problem is to do with the grub bootloader...

The non-techie solution if you can boot from a 'live' disk, is to copy all your data on to an external hard disk, and then do a re-installation having re-formatted your disk.

There may be techie solutions to sorting out the bootloader, but I don't really know much about that. Hope this helps you figure out what is going on (I have found that learning to use Ubuntu is very much about that, though it is very satisfying after much googling and thinking to sort things out).

---

### Post by ld114 on 2011-10-20
Forgot the link to the thread:

[http://forums.debian.net/viewtopic.php?f=17&t=65926](http://forums.debian.net/viewtopic.php?f=17&t=65926)

---

### Post by kemtnbkr on 2011-10-20
Id114, you are correct.  If shico90 can boot successfully from a live USB or CD, it is either a hardware error with the hard drive, or somehow his boot file got messed up along the way.

Shico90, I'd try booting into the live environment as Id114 suggested, and if that works properly, then try mounting your primary hard disk.  If it mounts successfully, then you have a bootloader error, which is over my head :( (other than a reinstall).

---

### Post by wildmanne39 on 2011-10-20
Hi shico90, if you see the purple screen then that  means your grub is ok and you may have had an upgrade to your video card driver, I would try what this link recommends if the first parameter does not work try the next one and if you get booted into ubuntu check on your video card driver.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

---

