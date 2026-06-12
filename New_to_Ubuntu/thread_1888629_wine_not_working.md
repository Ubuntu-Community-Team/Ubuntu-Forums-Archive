---
title: "wine not working"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-11-29
wine broken after 11.10 upgrade. I get 2 problems when I try to add application as soon as I try to browse to any folder it says wine has a problem and needs to close.The I sometimes also get an error that something is wrong with my temp folder. Before upgrade it worked fine. I also tried completely removing and reinstalling with no effect.

---

### Post by jjex22 on 2011-11-29
The temp folder could be a sign of read only issues - this is seeming to happen a lot with the upgrade at the moment - check none of your mounted partitions are read only - unlikely as you say you reinstalled, but I suppose it's possible you have things on different partitions causing conflicts.

If it's wine, Then the easiest thing to do is

sudo apt-get purge wine
sudo apt-get autoclean
sudo apt-get install wine

did you use remove before? most issues with wine involve it's configs, so basic reinstalling often returns the same errors, purge will remove the configs - autoclean isn't really necessary, but it can't hurt either.

---

### Post by cmcanulty on 2011-11-29
Same issue crashes whenever i try to navigate to a folder where the exes are. This 11.10 upgrade has me totally discouraged with Ubuntu I only did it so I could get to the 12.04 LTS but I think they are way off track everything is harder less useful and more time consuming. It's like they broke everything that was good.And I can't ever get my screen undimmed every tweak makes it worse.

---

### Post by jjex22 on 2011-11-29
I totally sympathise with the brightness - my laptop's just gone from automatically having 10 brightness settings to 0%,10%,100% brightness, So I'm back to xbacklight -dec 10% and inc 10% - yay.

It's weird that it still crashes after a purge and reinstall - did you check how your partitions are mounted in /etc/fstab?

---

### Post by cmcanulty on 2011-11-29
here is my fstab which I have never understood also I have been logging in and out all evening sometime there is an option for shut down and sometimes not. Often there is a logout icon but it does nothing. It's like they screwed up Ubuntu so much it is barely usable. I would never recommend it to my friends anymore 
```
# /etc/fstab: static file system information.
#
[CODE]# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b10cd0f2-7e31-44b7-a502-5685102041a9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=23e63f29-4c2a-47fd-bfe1-1f68bd9b687a /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=8e65462e-5b6d-41cc-8d61-f260d035f428 none            swap    sw              0       0
```[/CODE]

---

### Post by jjex22 on 2011-11-29
Well that's a default fstab! - unless you're trying to access files not on your / or /home partition that shouldn't be the problem - can you open the same file path okay in nautilus?

---

