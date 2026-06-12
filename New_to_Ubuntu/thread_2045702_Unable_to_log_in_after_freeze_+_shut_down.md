---
title: "Unable to log in after freeze + shut down"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by dialectical1 on 2012-08-21
My firefox session froze, then the whole screen. So, I shut down the system. Now, whenever I log in - or rather, **try** to log in - it just reverts back to the same log-in screen. 

I've had that issue before, but none of the offered solutions have worked reliably except uninstalling unnecesary programs. I had enough extra space on the drive as of a few days ago, & I haven't downloaded anything since ... so could my bloated firefox session file be the cause? (Does firefox clean itself up when it shuts down normally, but not when it's forced to close?)

How would I clear out my last firefox session through the terminal? I don't know the name of my firefox profile, nor where said files are kept.

Thanks in advance for any help in allowing my computer to be functional!

---

### Post by marlow59 on 2012-08-21
did you try to boot on recovery mode and fix eventually broken packages, because I don't think that the problem is specific to firefox, if you cannot log in after a freeze, maybe it's Nautilus that is having a problem.

---

### Post by dialectical1 on 2012-08-22
Thanks for your reply? How would I go about doing that?

Also, I can't download anything, as it would make the low disc-space problem worse - so please let me know if fixing the packages would involve downloading new versions of them. 

Btw, My system is running a no-longer-supported version of Ubuntu for lack of disc space :/ (There's enough space on my system, just not on the Linux partition, and I've been quite unable to repartition it.)

---

### Post by dialectical1 on 2012-08-24
By the way, the log-in error is the one where - after inputting my password - the log-in screen reloads rather than letting me into my desktop.

---

### Post by dialectical1 on 2012-08-29
Also: My system is running version 9.10. (The kernel version is 2.6.31-22, if that's useful).

Before this happened, I had to remove all power sources (including the battery) due to an unresolvable freeze (originating in firefox, presumably) - so there's likely files that need to be cleared out ... I just don't know how to do that. (Any info on how to do that is saved on my useless machine.)

---

### Post by steeldriver on 2012-08-29
Have you tried logging in at a virtual terminal (Ctrl-Alt-F1 thru F6)? Have you booted into recovery mode and actually had a look at the filesystem usage (df -h)?

---

### Post by dialectical1 on 2012-08-29
> **steeldriver said:**
> Have you tried logging in at a virtual terminal (Ctrl-Alt-F1 thru F6)? Have you booted into recovery mode and actually had a look at the filesystem usage (df -h)?

I've logged into the terminal to try the few solutions I could find. None of them worked. Also, I've done the sudo apt-get clean and sudo apt-get autoclean to try to free up some space - no luck.

Here's the results of df -h

> file system: /dev/sda6 
        size: 5.4G
used: 5.1G
available: 0
use: 100%
mounted on: /  

file system : udev
size: 497M
used: 252k
available: 497M
use: 1%
mounted on: /dev
Clearly, my partitions are messed up - but as of yet, I've had little help repartitioning it. GParted won't let me touch the large, unused partition (the one mounted on /dev). If I could get that resolved, I could update to a current (and supported version) and have enough space that this log-in error wouldn't be a recurring issue. (Also, my cd-rom drive doesn't work, which limits my options.)

Thanks very much for helping me out!

---

### Post by NikTh on 2012-08-30
Hi , 
login to Console Mode (Ctrl+alt+F2) and try these commands 
```
sudo service gdm stop
sudo chown username:username ~/.Xauthority
sudo service gdm start
```**Where username replace it with your actual username**

Thanks

---

### Post by dialectical1 on 2012-08-30
My laptop functions again!! :) Thanks for your help :)

2 whole MBs of space :/

---

