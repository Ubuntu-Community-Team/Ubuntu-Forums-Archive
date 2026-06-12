---
title: "Remastersys Help"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by cbanakis on 2011-11-06
Has anyone successfully used this?

I'm running UNR 10.04

I finally managed to get everything working exactly how I want it.

I'm trying to create a backup now using the remastersys gui.

As far as I can tell, I am using the newest version of remastersys 2.0.18-1

Everything appears to work fine. 
But when I try to test the backup in a virtual machine, the installer errors out at ~93% saying "The 'grup-pc' package failed to install into /taget/."

It then asks me to try again on another hard drive, but has the same result.

Has anyone got this to work?

I have been looking through forums, and it seems like the solution is to ignore it, and manually install a bootloader?

Is there no way to get the backup to work without the need for a complex workaround?
I'm still a bit of a noob, so any help would be greatly appreciated.

Thanks

---

### Post by cbanakis on 2011-11-06
Has anyone tried relinux?
does it work the same way?

looks a lot more complicated, but if it actually works, maybe thats the tradeoff?

---

### Post by 4Orbs on 2011-11-07
When you created your backup with Remastersys, did you select "Dist Mode" or "Backup Mode"? I "THINK" the backup mode is very specific to the hard drive it has backed-up, because all the original partitions are still listed in the fstab file. On the other hand, dist mode will have all the packages and updates you've installed but it won't have your desktop customizations, user accounts, etc. unless you have placed the proper files from your personal user account into the /etc/skel directory. However, I could be completely wrong in my understanding of Remastersys.

Personally, I have found Clonezilla to be an excellent utility for making backup images of my current installation. The images can be saved and reinstalled from a usb flash drive or external hdd. Very quick and only takes one or two attempts to get the hang of it. Remastersys "Dist Mode" is great for making custom cd's to hand out to your family and friends.

---

### Post by robert shearer on 2011-11-07
Ubuntu forum member Fragadelic is the Remastersys dev.
You could post your question on the Remastersys forum.

[http://geekconnection.org/remastersys/forums/index.php](http://geekconnection.org/remastersys/forums/index.php)

:)

---

