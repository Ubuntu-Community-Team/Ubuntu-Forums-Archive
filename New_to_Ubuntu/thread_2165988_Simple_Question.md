---
title: "Simple Question"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by clementchiew on 2013-08-07
I wanted to know that does Ubuntu take up hard drive space when used on a very light basis? I mean like surfing everyday, just some gaming and very few installations or applications. Windows used to do that to me and I gave up trying to find out what system files is taking up my hard drive space. I cleared everything I could (CCleaner full force, deleting remaining folders left behind from applications) but had no choice and reformatted it to get it back to original size. Therefore I switched to Ubuntu. But does Ubuntu take space like that and require "house cleaning" every few months?

---

### Post by cortman on 2013-08-07
If you're browsing the web it will be downloading stuff to the browser cache, so in that respect it will accumulate some extra files. Also, as software is updated it may grow a bit. I have never experienced Windows growing like you are saying, but I've never had Ubuntu or any other Linux system do it either.
To be honest hard drive space is next to free these days; is your problem that your hard drive gets full? If so a new drive may be in order. Otherwise I wouldn't worry about it.

---

### Post by uRock on 2013-08-07
As updates are completed there will be a gradual reduction of space, which is taken up by the packages downloaded by the installed. I run Bleachbit once every few months to clean up this space. Bleachbit can be install using the Ubuntu Software Center or via the command line using **sudo apt-get install bleachbit** in a terminal. Bleachbit can also be used to clean up temp files created by the browser and other applications. Bleachbit has to be run as root in order to remove packages created while updating the system.

---

### Post by Rob Sayer on 2013-08-07
I haven't used bleachbit or anything similar, but from what I've read on this and other forums I think they can cause more problems than they solve.  Particularly for novice users.  I'd personally go with a bigger HDd if you're having space problems.

If you're new to linux I'd recommend letting linux/ubuntu do your housekeeping for you.  It'll do a good job of that if you stick to software from the beta tested repos (ie. be very careful about adding ppa's that aren't on the standard default ubuntu software lists if you're a novice).

Linux is a lot more space efficient than windows anyway.

---

### Post by uRock on 2013-08-07
> **Rob Sayer said:**
> I haven't used bleachbit or anything similar, but from what I've read on this and other forums I think they can cause more problems than they solve.  Particularly for novice users.

I've been using Bleachbit for years. I've never had a problem caused by using it. :)

---

### Post by Mark Phelps on 2013-08-07
You mentioned "gaming" -- which I presume, means Windows gaming.  IF you intend to do that in Ubuntu, you're most likely going to be very disappointed.  Windows gaming does very poorly in Linux.  You have to use a Windows layer product known as Wine, and even then, the need for Direct X support, both in your video drivers and video chipsets, makes Windows gaming very difficult.

If that was one of the main reasons you switched to Ubuntu, then you'll be disappointed with the move.

---

### Post by ibjsb4 on 2013-08-07
> **uRock said:**
> I've been using Bleachbit for years. I've never had a problem caused by using it. :)

Same here, the only thing is to be sure about what you want cleaned (like cookies and passwords).  Also a rule of thumb is to pass on any cleaning option that gives you a popup when clicking on it.

---

### Post by mastablasta on 2013-08-07
> **Mark Phelps said:**
> You mentioned "gaming" -- which I presume, means Windows gaming. IF you intend to do that in Ubuntu, you're most likely going to be very disappointed. Windows gaming does very poorly in Linux. You have to use a Windows layer product known as Wine, and even then, the need for Direct X support, both in your video drivers and video chipsets, makes Windows gaming very difficult.

If that was one of the main reasons you switched to Ubuntu, then you'll be disappointed with the move.

then again maybe they are gaming with flash games or similar :-) also plenty of older games and strategy games don't really have that much penalty if you run them via wine. E.g. Diablo 2 runs perfectly for some time now... it all depends on selection of games.


now this aside i can say i have 8 GB dedicated to the OS and 1.5 GB is free. the most that is taken by updates is kernel updates. i think if you select only security updates you would get only kernel patches and few other security patvhes i imagine... at least that's how it is in Debian. so that won't make the OS part a lot bigger. 

an old mashcine i have with debian (Chrunchbang) on it still has over 12 GB left (out of 20 GB) and i filled it up quite well with soem data and programes.

another good part is that ext4 file system (the default, as wlel as some other file systems) doesn't get fragmanted like NTFS does in windows. i really didn't do much work on new netbook (win7 starter) yet filesystem was already 11% fragmanted (i defragmented it to prepare it for dualboot).

---

### Post by gordintoronto on 2013-08-07
Clement: Ubuntu is very light on disk space. You could probably run it on a 12 GB hard drive with no problems. Maybe every six months it would be a good idea to run this command: sudo apt-get clean.

That removes the files downloaded for system updates. Once the updates are installed, there is no need to keep the downloaded files.

I keep a 23 GB partition on my laptop for playing with new distros, and space has never been an issue.

---

### Post by clementchiew on 2013-08-08
its ok. I am not a heavy FPS or SC2 gamer. I am currently running Torchlight fine on Ubuntu 13.04. :) Yeah I cracked my head before trying to get the proprietary drivers. Gave up anyway. I switched because Windows is simply space inefficient and has horrendously slow boot-up time.

---

### Post by clementchiew on 2013-08-08
thanks. Will try it out. Hopefully it scrubs Ubuntu clean unlike Windows.

---

### Post by Jonathan Precise on 2013-08-08
Also, a good way to clean your system is with Ubuntu Tweak. Run the following code to add and launch Ubuntu Tweak:

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update && sudo apt-get install ubuntu-tweak && ubuntu-tweak
```

Then on the main page, select Start Janitor. Check all the boxes to the left, an then click on "clean". This will clean out all unneeded (space-consuming) "cruft" as they call it :smile:.

---

### Post by 3rdalbum on 2013-08-08
> **Jonathan Precise said:**
> Also, a good way to clean your system is with Ubuntu Tweak. Run the following code to add and launch Ubuntu Tweak:

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update && sudo apt-get install ubuntu-tweak && ubuntu-tweak
```

Then on the main page, select Start Janitor. Check all the boxes to the left, an then click on "clean". This will clean out all unneeded (space-consuming) "cruft" as they call it :smile:.

Best not to touch any "janitor"-style software unless you're actually experiencing low disk space. Some options can break things unless you know what you're doing. Merely using and updating an Ubuntu system will only increase disk use by a small amount. Unless you've got a tiny hard disk, leave well enough alone.

---

### Post by Jonathan Precise on 2013-08-26
> **3rdalbum said:**
> Best not to touch any "janitor"-style software unless you're actually experiencing low disk space. Some options can break things unless you know what you're doing. Merely using and updating an Ubuntu system will only increase disk use by a small amount. Unless you've got a tiny hard disk, leave well enough alone.

I've used Ubuntu Tweak for a long time (1-2 years) and it has kept my system clean. :)

---

