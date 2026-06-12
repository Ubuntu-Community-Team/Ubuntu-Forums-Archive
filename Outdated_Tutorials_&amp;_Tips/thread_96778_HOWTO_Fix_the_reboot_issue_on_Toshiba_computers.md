---
title: "HOWTO: Fix the reboot issue on Toshiba computers"
date: 2005-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by varunus on 2005-11-29
Thanks goes to Matthew Garrett for this fix.

A lot of people have reported reboot issues with Toshiba computers.  If one tries to reboot, the system goes through the shutdown procedure, and then goes to a black screen.  You have to turn the computer on and off to successfully reboot.  While not that bad of a problem, it is kind of annoying, and didn't exist in Hoary.  

Thankfully, there is a quick fix to this problem.

First, open up a terminal and type the following:
```
sudo gedit /boot/grub/menu.lst
```

Next, *maximize* the gedit window.  Gedit's word wrapping will mess up this file, and its needed to boot your system!

After this, find the line that looks like:
```
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot
```

Add the parameter "reboot=h" to the end of the kernel line, so it looks like this:
```
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash reboot=h
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot
```

This line will be 686 if you've installed the 686 kernel, or k7 with the AMD kernel.

Save and reboot, and the reboot issues should be gone!

This bug will be fixed by default in breezy.

---

### Post by Lizzy on 2006-02-14
Hei, :-)

I was happy to find a Howto about this issue, so i tried it out like described....but my Laptop still doesn't reboot. The screen goes black, i have to push the "enter"-button or any button.. first after that he reboots :-k :-k 
Any ideas? ;)  I would be greatfull


Cheers
Lizzy

---

### Post by varunus on 2006-02-17
You'll have to redo this every time you install a kernel upgrade; its possible that you upgraded your kernel and will have to redo it...

But any button makes it reboot?  That's odd...I'm not sure.  Dapper should fix the behavior completely though.

---

### Post by jmcwb on 2006-02-18
This fix didn't work for me either.  I'm running on a Toshiba Satellite 1805 laptop. 

I was puzzled by your comment that this would be fixed in breezy.  I've been running in breezy and it certainly doesn't appear to be fixed.

I figure that it has to be a software thing since xp (dual booted with ubuntu) reboots just fine.

:(

---

