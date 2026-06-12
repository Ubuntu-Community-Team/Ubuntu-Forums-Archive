---
title: "Major Filesystem Errors! - Please Advise :("
date: 2011-11-07
forum: New to Ubuntu
---

### Post by mooboontu on 2011-11-07
I posted a thread several, several weeks ago and was instructed to completely rearrange my boot setup when that adjustment was completely irrelevant to my problem.

It's just that I have gotten the "general filesystems error" when I boot up.  I don't think the computer is hopeless, b/c I have been able to get into the files with the "encryptfs" type LiveCD login jazz.  It's just that the LiveCD access method won't work now.  I've gotten chroot stuff to work, and I'm now just tempted to update to Maverick.

I multi-boot and simply select whatever the heck I want at startup.  None of my OS's have a d_mn thing to do with each other because they all have their own hard drives, etc.

Does anybody have any ideas about how to efficiently and/or feasibly upgrade an entire OS thru the chroot stuff?

Also, my system used to work just fine with the "old" GRUB, but I'm told to upgrade it to GRUB 2 ... I can't seem to get that to work well cuz everything keeps telling me to use a CD.  I'm just confused with the command line method, etc.

Any advice would be awesomo.

---

### Post by LinuxCharms on 2011-11-07
Eh, when I ungraded my mom's computer I had similar problems. Something about when you upgrade and the system has had special tweaks it kicks it out and sends you into the mode you're in.
So, I recommend scraping it and installing Xubuntu. Very similar to Ubuntu, more user friendly, though. You can back up all your files from where you are.

---

### Post by mooboontu on 2011-11-07
> **LinuxCharms said:**
> Eh, when I ungraded my mom's computer I had similar problems. Something about when you upgrade and the system has had special tweaks it kicks it out and sends you into the mode you're in.
So, I recommend scraping it and installing Xubuntu. Very similar to Ubuntu, more user friendly, though. You can back up all your files from where you are.

That's the last thing I want to do.  Actually, I don't want to do that at all.

I have had filesystem issues before and had help working them out.  I prefer real solutions, honestly.  When it comes to computing, I don't like to take the easy "way" out and just start over.  One learns nothing from that.  Additionally, I have no interest in Xubuntu.

Even further, I have extremely important files in the OS that I need to keep at all costs.  And, as I stated, I am having trouble accessing said files with the LiveCD "access your private data.desktop" type maneuver.

But if anyone else does have some practical, pertinent and applicable ideas for my potential upgrade to Maverick, that would be suhweet.

---

### Post by wildmanne39 on 2011-11-07
Hi, if your drive is good and you just have a corrupt file system that has nothing to do with drive failing, and you have a separate home partition you can use a livecd to upgrade and just choose your home partition as the home partition for your new install and do not format that partition and all your files should be there when you are done.

I just did this two weeks ago myself. 

Also I do daily backups so if something does happen and I have to reinstall then all I have to do is restore my important files from my backup copy.
Thank you

---

### Post by mooboontu on 2011-11-07
> **wildmanne39 said:**
> Hi, if your drive is good and you just have a corrupt file system that has nothing to do with drive failing, and you have a separate home partition you can use a livecd to upgrade and just choose your home partition as the home partition for your new install and do not format that partition and all your files should be there when you are done.

I just did this two weeks ago myself. 

Also I do daily backups so if something does happen and I have to reinstall then all I have to do is restore my important files from my backup copy.
Thank you

Dude ... much appreciated :) ... I'm literally going to do that like, right now.  I'll just do a rain-dance first and hope and pray that I don't screw it up, lol.

---

### Post by mooboontu on 2011-11-07
> **wildmanne39 said:**
> Hi, if your drive is good and you just have a corrupt file system that has nothing to do with drive failing, and you have a separate home partition you can use a livecd to upgrade and just choose your home partition as the home partition for your new install and do not format that partition and all your files should be there when you are done.

I just did this two weeks ago myself. 

Also I do daily backups so if something does happen and I have to reinstall then all I have to do is restore my important files from my backup copy.
Thank you

... so, I must've spaced it on my Lucid Lynx install.  I redid a lot of stuff and it looks like I do not have a separate /home partition.  Crap ... is there any way around that?

---

### Post by wildmanne39 on 2011-11-07
Hi, one thing you might try first is to boot your computer and start's tapping the shift key as soon as it start up and see if you can get to the grub menu if you can choose recovery then recovery with networking of if it lists fix broken packages that is what you want to do.

You can try to recover your files using a livecd of ubuntu, then do a clean install, here is a link to help.
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Or if you can access the partition with the livecd that has your files you can just copy them to an external source like this.

Livecd use a root

```
sudo -i nautilus
```
opens the root file browser window in the live cd, no password required then copy and paste to external source.

There are people that have more experience with this then I do.
Thank you

---

### Post by mooboontu on 2011-11-07
thanks .. never thoughta that.  I like the idea and I just got done rebooting and trying that.  I didn't see any networking recovery or anything.  I think it's a great plan but all the reboot does is put me in "single-user mode" where I have to wing a bunch of commands and get denied by "read-only".

Basically ... do you know how I might do some repair like this while I have "CHROOT'd" into my drive?

I think that might work ...

---

### Post by wildmanne39 on 2011-11-07
Hi, here is a link for repairing grub from livecd and another program.
[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)
You can try what these two links mention.
Thank you

---

