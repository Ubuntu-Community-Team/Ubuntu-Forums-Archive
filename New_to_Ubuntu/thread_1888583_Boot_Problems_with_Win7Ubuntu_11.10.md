---
title: "Boot Problems with Win7/Ubuntu 11.10"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by mcnnowak on 2011-11-29
Hello all. 

I installed Ubuntu 11.10 alongside my Windows 7 installation a while ago and now somethings gone wrong.

My computer used to boot into Ubuntu if the GRUB timed out at the boot screen with all the OS options. But for some reason it booted into the Samsung Recovery Mode Software Thing. So I just turned it off and on. When It turned back on, I got a slowly flashing screen with no GRUB or anything. 

So, having at least a little bit of Linux experience, I immediately booted into a LiveCD and googled my way to a solution. The solution was the boot-repair tool ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) and that fixed the problem temporarily. 

Eventually, I missed the time out again and the same thing happened. Ive fixed it for the third time now and was wondering how to change my boot order? 

Ive tried ```
 sudo apt-get install startupmanager 
``` and changing it using that doesnt work, It still defaults to the recovery tool

Any ideas?
Thanks in advance!

---

### Post by Mark Phelps on 2011-11-29
Startup manager doesn't work with recent GRUB2 versions.

Instead, install and use Grub Customizer.  See Link below:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

---

### Post by mcnnowak on 2011-11-29
Thanks!

---

