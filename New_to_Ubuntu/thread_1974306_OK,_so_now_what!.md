---
title: "OK, so now what?!?"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by PhreakShow on 2012-05-05
I have been using Ubuntu for about a year now, and have been pretty much thrilled with it, but when I attempted to update from 11.10 to 12.04, the update went through, and when I restarted, my usual login screen appeared. Unfortunately, all I get when I log in is a black screen where I can move my cursor... Any ideas, thoughts, suggestions, helpful hints? Please?

---

### Post by wilee-nilee on 2012-05-05
If you had a graphic driver installed for the last install it needs to be reinstalled again in a upgrade. Check this thread for getting into the desktop with nomodeset, and once in, if this works, update completely and check the additional drivers app. 

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by PhreakShow on 2012-05-05
Thanks for the lead, I will give it a try in the morning.  I'm cooked after an 80 hour week, and just don't have it in me tonight.  Will let you know how it goes afterwards, thanks again.

---

### Post by mastablasta on 2012-05-06
if you had graphics drivers installed you need to remove them before doing the upgrade.

---

### Post by Paqman on 2012-05-06
Can you log in to Recovery Mode?

---

### Post by PhreakShow on 2012-05-06
GRRRRR!   Tried modding the Grub w/nomodeset, still get the same thing... well almost...

Now I can see folders that I had, but locking up "collecting problem information"

---

### Post by PhreakShow on 2012-05-06
And how do I get to recovery mode?

---

### Post by 23dornot23d on 2012-05-06
Check your available diskspace first .... post the results of

[B]df


To get to recovery mode .... it is usually the second selection on your
grub menu ..... also

sudo apt-get clean
sudo apt-get autoclean

[/B]*these may help if it turns out to be a space issue in the / ( root ) partition.*

---

### Post by PhreakShow on 2012-05-06
Not a disk space issue, starting to annoy me greatly.
Using nomodeset, I can access folders, but cannot seem to get to a terminal.
I heard that 12.04 was supposed to be rather spectacular, but am not seeing it.
Is there any way I can revert back to 11.10 without wiping and reinstalling?

---

### Post by Mark Phelps on 2012-05-07
> **PhreakShow said:**
> Is there any way I can revert back to 11.10 without wiping and reinstalling?

Basically, NO.  Canonical has yet to go to the trouble of providing any kind of roll-back or restore capability to get your old install back.

---

### Post by 23dornot23d on 2012-05-07
I did try to highlight a possible change in the way people are told about the upgrade
and a easy way to try it out in a clean partition .....

[http://ubuntuforums.org/showthread.php?t=1858475](http://ubuntuforums.org/showthread.php?t=1858475)

Seems that a Roll back is one thing people should be able to do ..... but once you have completely merged 12.04 into 11.10 .... unsplicing this is then very difficult to do.

Many threads say that the upgrade can fail .... but many say that there are many successful ones that we never get to see because the ones that are successful never come back in droves to say how good it was ......

My worry has always been the one person that does not have a good experience ..... because I was always taught to think >>> what if it was me .......

* I now have enough experience to always have at least 2 versions of Linux on the same Drive .......

But how do I as one person let you know - when the message in the upgrade does not give any indication that it may fail ......

This is not as uptodate as I would like it to be .... but have a good look through some of
the Operating Systems that I have tried and try to research what will work best on your machine ...... often searching before you install can help and waiting and watching what is happening on the forum a month after the Newest Release helps too.

[https://sites.google.com/site/000menu/](https://sites.google.com/site/000menu/)

A clean install takes 30 mins or thereabouts ..... and is usually recomended - also if you can do it in a clean partition - you should be able to access all your previous work.

But always Backup Data before Upgrade or a Install ..... this is standard with all OSs

---

