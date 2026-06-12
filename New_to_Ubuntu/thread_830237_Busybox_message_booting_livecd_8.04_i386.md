---
title: "Busybox message booting livecd 8.04 i386"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by skozzy on 2008-06-15
Starting off I had a working 7.10 ubuntu 64bit install, recently it was upgraded to 8.04 from an update, after the update the 3 hard drives on my Promise TX2 IDE PCI Card no longer apear and a boot of ubuntu since takes about 5 minutes before the log on screen. I got discuraged after a while and downloaded the 8.04 i386 ISO and planned on doing a fresh install. 

Now when I boot from the live CD I get an inital splash screen and it sits there for a while and open a screen showing "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

There is no error message apart from this. I am wondering if there is a problem with my this new version of ubuntu and my PCI hardware. I have downloaded other version of ubuntu and will try those after burning the cd's while I wait for any replies.

So, what might be going wrong people.

---

### Post by skozzy on 2008-06-15
In case I had a bad burn to the CD I reburned it and tried again. Same problem booting the CD drops me to Busybox.

Now I'm going to burn the 8.04 64bit ISO and see what happens

---

### Post by impert on 2008-06-15
There is a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190492](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190492)

Try using the boot option pci=nomsi

If this doesn't work you could try irqpoll though this has given some people trouble. 

Adding "all_generic_ide" at the end of your hardy kernel entry in menu.lst has also been suggested; this has solved the issue for some users.

Or you could just stick with Gutsy for a while.

---

### Post by skozzy on 2008-06-15
No joy with the amd64bit version either. I will try find my old v7.10 CD and see if it works.

---

### Post by skozzy on 2008-06-15
> **impert said:**
> There is a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190492](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190492)

Try using the boot option pci=nomsi

If this doesn't work you could try irqpoll though this has given some people trouble. 

Adding "all_generic_ide" at the end of your hardy kernel entry in menu.lst has also been suggested; this has solved the issue for some users.

Or you could just stick with Gutsy for a while.

Thanks for your reply, but I don't know how modify the CD ISO to get past the problem. I am re-downloading a v7.10 ubuntu and will install that again (if it works) 

But reading the link you posted I saw someone with my mainboard having the same problem. So thanks ..

---

