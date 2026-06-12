---
title: "Update procedure for newbie non-geek"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by morhin on 2012-05-11
Updating from 10.04 to 12.04.

I've been using 10.04 for several months and am thinking about moving to 12.04. But reading the forums has got me really spooked. Seems almost anything can happen including loss.

Is there a basic step by step process for newbie non-geeks that can be printed out and used? 

I mean like, step one.... turn on computer.

Thanks

Morhin

;-)

---

### Post by deadflowr on 2012-05-11
Personally, I find some of the FUD on upgrading overblown. The chances of An upgrade chunking your system are low.
That being said.

1)If at all possible, back-up your important data first.

2)I personally download\burn a fresh copy of ubuntu from ubuntu.com
This way I can testdrive it and see if I actually like it.
With a fresh copy of the lastest LTS and my freshly backed-up system I can proceed to number 3 without fear.

3)Follow this guide for network upgrade
[https://help.ubuntu.com/community/PreciseUpgrades]("https://help.ubuntu.com/community/PreciseUpgrades") 

You will find a lot of people prefer run fresh installs(with their fresh copies) over network upgrades. Though I network upgrade(and download fresh copy), the reasoning can be quite simple. A fresh copy can take considerable less time to download,burn, and install than a network upgrade(since a network upgrade will upgrade everything{well maybe not everything}, which means all of the packages you've downloaded through the software center).

If you cannot run steps 1 and 2 have no fear, as the chances of the upgrade going bad are pretty slim, and as bugs get fix they get slimmer everyday.
I hope this eases your mind.

Edit: As a quick warning, The latest Nvidia drivers have been known to not act well with compiz on some of the cards, so if you're running Nvidia graphics cards be warned. This however does not break your system, only makes full unity3d unusable, but unity 2d is still usable.

---

### Post by grahammechanical on 2012-05-11
Do not leave the upgrade unattended as you may need to give some input during the process.

As the upgrade runs Click on details and watch what is happening. You may need to OK something during the upgrade.

If you have broadband then the downloading of the packages will take about 10 minutes. Installing the packages will take longer. Update manager may say it will take about 4 hours but in a matter of seconds that will change to 3 hours, then 2 hours then less than 90 minutes. It will take about 60 - 70 minutes.

I base this on my experience last night upgrading 11.10 to 12.04 and I did not have any problems.

I did have to remove and then re-install Chromium in order to get Flash working. That is all so far.

Regards.

---

### Post by wilee-nilee on 2012-05-11
Yes back it up, and you will have to respond to the upgrade at the least it will ask for removal of old stuff not needed to finish.

---

### Post by traditionalist on 2012-05-11
> **morhin said:**
> Updating from 10.04 to 12.04.

I've been using 10.04 for several months and am thinking about moving to 12.04. But reading the forums has got me really spooked. Seems almost anything can happen including loss.

Is there a basic step by step process for newbie non-geeks that can be printed out and used? 

I mean like, step one.... turn on computer.

Thanks

Morhin

;-)

Backup all your data and then use this;

[http://www.remastersys.com/](http://www.remastersys.com/)

Although I am a newbie, it solved all my problems. If you have a backup of your system on DVD, and your data backed up,  then nothing can really go wrong, no matter what you do. You just insert the disk and reinstall and your system is exactly as it was when you backed it up.

You can even do a complete new install of a distribution and simply reverse it using your backup DVD. The backup DVD is also a live disc, so you can use it for repairs etc as  well.

---

### Post by souravc83 on 2012-05-11
It might be a little unpopular advice in this part of the town,
but if you are a newbie, I think it might be better not to upgrade to 12.04 right now. People are still learning the ropes on the new release, and it seems there are lots of problems with something not working/going wrong after going to 12.04.

I would upgrade to 11.10. That being said, it is also true, you never learn linux, until you tinker with your computer, fix things that are  not running. So, if you want to do that, then its totally worth it.

---

### Post by deadflowr on 2012-05-11
> **souravc83 said:**
> It might be a little unpopular advice in this part of the town,
but if you are a newbie, I think it might be better not to upgrade to 12.04 right now. People are still learning the ropes on the new release, and it seems there are lots of problems with something not working/going wrong after going to 12.04.

I would upgrade to 11.10. That being said, it is also true, you never learn linux, until you tinker with your computer, fix things that are  not running. So, if you want to do that, then its totally worth it.

I wouldn't call that unpopular advice. I'd call it sound. There is no rush for anyone to take such a gigantic leap like upgrading from 10.04 to 12.04, at this point. 
The amount of difference between the two is immense, and can almost feel overwhelming.
That being said your second point is also valid, learning anything comes with inherent risk. And accepting the consequences of that risk can bear very worthwhile fruit.
Me thinks?

---

### Post by ammofreak on 2012-05-11
Hi ):P
Bottom line: keep using 10.04. I am using 10.04LTS and have no desire to upgrade until the new 12.04 has gone through its' paces. Save yourself a lot of grief. If you desire the cutting edge of Ubuntu, then there is nothing I can post here to change your mind. I use 10.04LTS server with a desktop Gnome for development. I have worked out all kinks & let me tell you, it is a dream machine! I am thankful for the efforts that have gone into Ubuntu & hopefully I will contribute meaningfully in the future. End of story: best advice I can give...:)

---

### Post by bodhi.zazen on 2012-05-11
> **morhin said:**
> Updating from 10.04 to 12.04.

I've been using 10.04 for several months and am thinking about moving to 12.04. But reading the forums has got me really spooked. Seems almost anything can happen including loss.

Is there a basic step by step process for newbie non-geeks that can be printed out and used? 

I mean like, step one.... turn on computer.

Thanks

Morhin

;-)

1. Back up your data first.

2. Test 12.04 by running the live desktop CD. Make sure your hardware works.

3. Read the release notes.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

4. If all looks good, upgrade.

5. If upgrade fails, fresh install and restore your data.

---

### Post by bodhi.zazen on 2012-05-11
> **deadflowr said:**
> Personally, I find some of the FUD on upgrading overblown.

Your advice is sound, but ... 

Failed upgrades, however, are neither FUD or fun, it happens, usually because users are not prepared and do not read the release notes.

---

### Post by anewguy on 2012-05-12
Also, since you are running 10.xx, you therefore haven't had the unity desktop yet.  It is the default in 11.xx and in 12.04, and is very different from you are currently used to.  I would suggest you download/burn the ISO and test drive it for a while.  Not only will that get you used to using the Unity desktop, but it should help you know that you can update to 12.04.  There's one thing important to note:

- you can't "upgrade" from 10.xx to 12.04 - you have to upgrade to the releases in between first

- I personally don't advocate the "upgrade" route anyway - too many times I have had left over old libraries, old configuration files, etc., that caused problems.  My advice is to backup everything twice (there is such thing as media failure, and it's usually found when you are trying to restore from backups).  Then do a completely new install for 12.04.  Re-do the partitions, or if using the same partitions, at least mark them as to be formateed.

Just my 2 cents worth.

Dave ;)

---

### Post by Prescilla on 2012-05-12
I would advise you to do a clean install.
I'd have bad experiences with upgrades.
Some things mysteriously don't work anymore after upgrades.

---

### Post by anewguy on 2012-05-12
> **Prescilla said:**
> I would advise you to do a clean install.
I'd have bad experiences with upgrades.
Some things mysteriously don't work anymore after upgrades.

See my post above yours.  The screwy things that happen after doing an upgrade are almost always the result of old libs and configuration files being left behind in the upgrade.  

Some people have said the upgrade procedure has changed and has worked fine for a couple of releases minimum.  This has not been the case with myself and many others.  The old recommendation of backup and then do a complete install of the new release still holds true.

---

### Post by Shadius on 2012-05-12
Upgrading from 11.10 to 12.04 went well for me. Didn't come across any problems. My advice to you is to test out 12.04 first, because it is a change from 10.xx. Get familiar with it first before you decide to upgrade to it.

---

### Post by codingman on 2012-05-12
...Like get use to that unity thingy...
if you don't like it check out this link:
[http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm](http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm)

---

### Post by bodhi.zazen on 2012-05-12
> **codingman said:**
> ...Like get use to that unity thingy...
if you don't like it check out this link:
[http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm](http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm)

If you do not like unity ...

1. Try K/L/Xubuntu.
2. Install gnome-shell.

Why go though the hassle of removing unity ?

---

### Post by Shadius on 2012-05-12
> **bodhi.zazen said:**
> If you do not like unity ...

1. Try K/L/Xubuntu.
2. Install gnome-shell.

Why go though the hassle of removing unity ?

Agreed. No real need to remove Unity. I've installed Gnome Tweak Tool and am now using GNOME Classic since even Unity 2D was a bit slow for my computer. I like the Unity interface, but it was just too much for my computer to handle.

---

### Post by deadflowr on 2012-05-12
> **bodhi.zazen said:**
> Your advice is sound, but ... 

Failed upgrades, however, are neither FUD or fun, it happens, usually because users are not prepared and do not read the release notes.

 I agree as my choice of the term FUD seems hyperbolic.
 I would hope the OP uses all caution, and understands that even though net upgrades can be safe, there is a VERY real chance that something can go seriously wrong. 
 I would also hope the OP thoroughly reads up on the release notes and especially any known issues.
 I would also hope the OP follows Ubuntu's advice and holds off on upgrading until the after the first release point sometime around July. There's still just under a year before before 10.04 reaches end of life.

---

