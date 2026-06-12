---
title: "System crashes after Update"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by Javelin Dan on 2012-08-22
Running Lubuntu 12.04 on Mac “Graphics” G-4, 450 Mhz. processor, 20 GB hard drive, 1.5 GB RAM.
   
  This box is just a test mule, so none of this really matters other than as a learning tool. I had briefly installed Linux Mint PPC on this computer and decided that for my purposes, there was no advantage (and possibly some draw-backs), so I reinstalled Lubuntu. I installed Ubuntu Tweak (because of the nice GUI it displays for Computer Janitor), opened Synaptic, reloaded the repository, marked my upgrades, and updated. I then ran Computer janitor to clean the cruft. From that point, I could boot the system, but it would crash in short order no matter what I tried to do. I then re-installed Lubuntu without updating. Everything seems to be working normally now. 
   
  I searched the forums, and there seems to be plenty of complaints about crashes after updating. I’m wondering whether I should not update, or not run Computer Janitor, or both. Anyone care to weigh in?

---

### Post by mzaam on 2012-08-22
I think u should not run the janitor, it may delete needed thing.

however just try to update without running janitor and see are u still have problem

---

### Post by Javelin Dan on 2012-08-22
mzaam - I will try it and report back. Thanks.

---

### Post by blackmail on 2012-08-22
In the grub menu i think you can choose to boot in recovery mode, if you have an eth0 internet connection with DHCP, then you should be able to force an upgrade, and then the necessary files should be copied to the system again, mainly emulating a recovery thing.

Just boot in the recovery console and try:
```
sudo apt-get dist-upgrade
```
I have ubuntu 12.04, and killed it and just tried this and it worked :P
Try it, it may help :)

---

### Post by Rex Bouwense on 2012-08-22
Blackmail's posted suggestion should work, however, I have used Ubuntu Tweak on three different Lubuntu versions.  I cleaned the system with computer janitor and never had a problem.  I have also used bleach bit without problems.  Was there something else that you may have done other than clean the system?

---

### Post by blackmail on 2012-08-22
there are some times things that just happen for the fun of respecting murphy's laws (whatever can go wrong will go wrong)

So i don't like computer janitor, i like to use the terminal to clean my stuff and also there is really not much to clean. in comparison with windows, there really is not much to clean. a sudo apt-get autoremove after uninstalling stuff and also deleting the source files from compiled apps, as well as using magnet links instead of torrent files, and cleaning the /var folder from unused junk should be enough to keep the system running fast, and in most cases this should not be a thing to cause the computer to run slow.

---

### Post by Javelin Dan on 2012-08-23
Rex Bowense & blackmail -

This actually raises the question I originally asked myself when I decided to try this. When you update, you obviously see some pretty large packages being installed. You also see it configuring to delete unneeded packages. For a long time, I figured it was pretty much a wash. But some reading I'd done suggested there were bits and pieces of unneeded packages left behind after successive updates that could, at least in theory, slow down your computer over time. When I run Computer janitor after an update, it sometimes shows a significant amount of MB's it's removing. I figured this was a worthwhile maintenance procedure - no?

blackmail - While I sincerely appreciate your suggestions to clean my computer through the terminal, I'm afraid what you are suggesting is beyond my limited skills at this point. I've just crawled out of the swamp and am barely walking upright.

Rex Bowense - no, there was absolutely nothing else I did to affect this.

---

### Post by blackmail on 2012-08-24
just type in sudo apt-get autoremove, and the rest will be done, i think that gnome tweak also uses system commands to clean up the operating system...

ALso the autoremove command will show the packages and will clean ul any such thing that will be there and is no longer used, but it can mess up the system, sometimes there is a slight chance that the system doesn't detect correctly the fact that those libraries or packages are still needed by some program and it can brick your installation...

---

