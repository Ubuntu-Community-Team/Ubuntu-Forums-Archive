---
title: "Recommendations on Upgrading to 12.04"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by latinlightning on 2012-11-08
Hello fellow Ubuntu users,

I have two computers one of which was running 11.04 and another which is still on 11.04. I've been using this version since it came out and never had any problems. I used Update Manager on the first computer to upgrade to 11.10 and it seems like all is well. Now with my second one I'm not sure whether I should follow the same route to eventually get to 12.04 or if I should do a clean install.

Reason why I'm asking for opinions is because on this second computer I have some useful tools I use often such as Metasploit, Nmap, Wireshark, Wine and who knows how many other utilities. They're all pretty much applications I had to install from source. I'm also dual-booting w/ Windows XP but have no interest in keeping it. I have backed up my /home folder but perhaps there's a way to backup these other programs in case I were to do a clean install (/usr/local)? What I liked about upgrading using Update Manager is that it tells me what's no longer compatible with the new version of Ubuntu.

Could I please get some opinions on what would be the best/recommended solution?

Regards,

Jesse

---

### Post by atkrad on 2012-11-08
Hello
I recommended using Update Manager for upgrading

---

### Post by 2F4U on 2012-11-08
First of all, download 12.04 and burn it to a CD or USB. Then try it in a live session without installing it. That way you can see if there are any problems.

To get a list of installed software and reinstall it read through this post:

[http://ubuntuforums.org/showthread.php?t=261366&page=12](http://ubuntuforums.org/showthread.php?t=261366&page=12)

In place upgrades can be a mixed bag, so it is very important to have a good backup. Together with the list of installed software, you should be in a position to attempt an upgrade. If it fails, you can do a fresh install and add the software you need.

---

### Post by ty74 on 2012-11-08
I highly recommend ubuntu 12.04. I started with 11.10 and had many problems with it. I did have some trouble with 12.04 until I updated it enough. Plus 12.04 is long term supported which is great. I would recommend wipe it and install fresh. It always worked better for me that way, but if you have important data on your system back it or transfer it even if you decide to update. I think either way it is a risk I would say to make a backup disc of your current version if you like it, in case you don't like ubuntu 12.04.

---

### Post by Mark Phelps on 2012-11-08
The main reason you need a "good backup" BEFORE you do an upgrade is that there is no way to roll-back to the previous version once you do the upgrade.

So, if it's working great now, you do an upgrade, stuff no longer works -- you're faced with either having to fix what doesn't work or to reinstall from scratch.

My preference is to image off the current install using Clonezilla to an external drive or to another partition.  That way, if the upgrade goes poorly, I can reimage back to what I had in just a few minute3s.

---

### Post by deadflowr on 2012-11-08
Upgrading is an either/or situation.
Personally, I go the update manager route. but a fresh install is just as good.
The thing to remember is the update manager way upgrades all packages upgradable, so if you've installed a lot of extra stuff the upgrade will take a longer time to do.(I've done this and seen  considerable time added compared to an immediate upgrade from a fresh install, eg load 11.10 and quickly use the update manager to upgrade to 12.04).
Since you'll probably be upgrading to 12.04, which is a long-term-release, a fresh install might be good; if you plan on staying on it for a while.
Except for metasploit, the packages you listed are all available and in working order in 12.04. However there are tutorials on getting that one particular program up and running in 12.04.

I do like the earlier advice of download the ISO and run a live session to try it out first. I also think it is good to have the ISO so if you do go the update manger route and it fails somehow, you have a fresh disk available for re-installation.

---

### Post by mastablasta on 2012-11-08
fresh install is much fatser than upgrade, but you can do upgrade just as well. i would move to 12.04 and then you can stick with it for the next 5 years (that's more or less my plan).

---

### Post by vwbug on 2012-11-08
You could clone your drive as well for a backup. If the upgrade fails or you don't like it you can just restore it as it was.

---

### Post by monkeybrain2012 on 2012-11-08
If you have a separate /home partition it is much cleaner and faster to do a clean install than upgrade, save you many headaches down the road. Upgrade takes a few hours and a clean install about 20 minutes and you can be sure there are no corrupt or incompatible pieces left over which will give you problems later. It is much more likely that something may go wrong during upgrade than a clean install.

---

### Post by latinlightning on 2012-11-08
> **2F4U said:**
> First of all, download 12.04 and burn it to a CD or USB. Then try it in a live session without installing it. That way you can see if there are any problems.

To get a list of installed software and reinstall it read through this post:

[http://ubuntuforums.org/showthread.php?t=261366&page=12](http://ubuntuforums.org/showthread.php?t=261366&page=12)

In place upgrades can be a mixed bag, so it is very important to have a good backup. Together with the list of installed software, you should be in a position to attempt an upgrade. If it fails, you can do a fresh install and add the software you need.

Nice. I'll give this a good read later tonight.

I think I'm going with the majority and do a clean install and then use my backup to restore everything under my /home directory. When I upgraded my first computer using the Update Manager, it did take considerably long and I left it overnight. Then when I woke up I found out it didn't finish because it was waiting for me to continue when I guess it realized certain libraries were no longer needed in 11.10 so I had to click 'Continue' for it to finish.

I'll report on my outcome tomorrow.

-Jesse

---

