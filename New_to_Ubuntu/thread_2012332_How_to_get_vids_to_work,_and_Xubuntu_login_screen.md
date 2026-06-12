---
title: "How to get vids to work, and Xubuntu login screen"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by ebonygeek45 on 2012-06-28
I am out the box new to Xunbutu. The XP that came preinstalled on my laptop was always bogged down. So after using XP for 10 years I want something new. Something nothing like what I had and something that I don't spend time waiting for things to load. 

I first went with Ubuntu. Caught on to it and was loving it but it was at about the same speed as the XP I am running from was. Ok, I know that my system is not a power house so onto Xubuntu. I installed it through the terminal and uninstalled Ubuntu after I was done. 

To my first question;

I uninstalled Ubuntu right?? But to get to Xubuntu I come to Ubuntu's login page. I learned that you click the icon and then you are able to choose Xubuntu. Did I do something wrong or is that the way it works??

My next question ;

I am trying to get to some tutorials and the vids format is flv. I am guessing that is flash. My youtube online works fine. But, my youtube videos I download don't work at all. I get sound and a screensaver. I tried the application for restricted and it would not install. I tried doing a couple of things the threads said here and kept running into;

E:Unable to Locate Package

Ok so is E: a location like drive C:// or is E: for error...??

I had a problem with E: before when trying to install Xubuntu through the terminal of ubuntu. But I burned a CD and followed intructions and it loaded. 

Can someone explain how I get my youtube vids to work on Xubuntu??

I like Xubuntu's speed and so far the apps, I think it is a keeper.

---

### Post by mapes12 on 2012-06-29
You can't uninstall Ubu through the Terminal. If you are happy to go with Xubuntu (or any other Linux distro) without dual boot then best practice is to get a fresh installation media (CD or USB depending on how your system boots), make any changes to your BIOS to boot from the installation media then do a fresh install across the entire drive. This will delete any rubbish on the HDD and setup your system how it was intended.

For media playback I do the following:-

- Install xubuntu-restricted extras
- go to the medibuntu website and follow the instruction to load up the codecs
- install the VLC media player

EDIT: Make sure you back up the files you want to keep to an external drive or media stick or whatever before you start any of the above. Once your installation is how you want it you can then transfer them back.

---

### Post by ebonygeek45 on 2012-06-29
Is it a bad thing to dual boot. Other than the video problem of which I have done what you mentioned below but VLC got caught up in installation and froze, I didn't get a chance to try it again, also I am having a problem updating. But other than that it is working like a dream.   If doing the fresh install will get it to a better point I will do it though.

---

### Post by Bartender on 2012-06-29
> **ebonygeek45 said:**
> I uninstalled Ubuntu right?? But to get to Xubuntu I come to Ubuntu's login page. I learned that you click the icon and then you are able to choose Xubuntu. Did I do something wrong or is that the way it works??

It sounds like you installed the Xubuntu DE on top of Ubuntu.  If you can log out of Xubuntu and you find Ubuntu is one of the "log back in" choices then I'd say that's what's going on.  I've got Xubuntu installed from scratch on an old laptop.  I get the blue Xubuntu splash screen after the BIOS screen.  No mention of Ubuntu at all.

I'm pretty sure you can uninstall the Ubuntu DE, which should leave you with the Xubuntu DE, but I think it might be more straightforward if you simply start over with a Xubuntu CD and wipe the drive.

---

### Post by ebonygeek45 on 2012-06-29
Did a fresh install from bootable cd. Didn't have to worry about loosing anything because I didn't have much of my data there anyway. I'd rather do it now than when I really start getting to work on my projects. 

It worked out my problems with video, and VLC is running good. 

I am still having problems with updates though. 

But Xubuntu pulls up it's own login screen. 

Thanks guys your advice was right on point.

---

### Post by rai4shu2 on 2012-06-29
> I tried doing a couple of things the threads said...

Maybe you could point out what you tried. Sometimes, people on this forum give you questionable advice.

---

### Post by ebonygeek45 on 2012-06-30
> **rai4shu2 said:**
> Maybe you could point out what you tried. Sometimes, people on this forum give you questionable advice.

I really think the problem was installing Xubuntu on top of Ubuntu and attempting to remove Ubu from the terminal...really can't tell you where I found that but it was here on the forum. Some of the files for dependency might have been erased or conflicted with each other in the process. Thus the fresh install was the solution. 

Before I did that I tried; 

Installing the restricted file. 
----it wouldn't install. 

sudo apt-get update
----Updated fine

sudo apt-get upgrade
----For some reason it ran but wouldn't upgrade, and I am still having that problem.

My solution to the update problem was due to as I was told by drmrgd  "Linux kernels are not installed by a simple upgrade"

The code that cleared it up was;

```

sudo apt-get dist-upgrade

```

Like I said I am very new to any kind of linux although I've heard of it for years. For my 3rd day with it I think I am doing good. I can say I will only be using windows xp 
for my magic jack from here on out. I heard that Magic jack don't work with Xubuntu.

---

### Post by rai4shu2 on 2012-06-30
Okay. Well, if you ever want to change your mind about that:

[http://www.magicjacksupport.com/using-magicjack-on-linux-f15.html](http://www.magicjacksupport.com/using-magicjack-on-linux-f15.html)

---

