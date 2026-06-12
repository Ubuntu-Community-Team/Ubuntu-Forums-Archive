---
title: "Not absolute, but beginner enough"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by Panama.Craig on 2012-03-13
Ok, so I am still learning a lot here and am really liking Ubuntu and a ton of its features.  I've been waiting a long time to migrate over to Linux and decided to choose Ubuntu as my OS because it or Gentoo seemed to be the main two that were reported to be capable of running SWTOR.  Now, I'm not dumb and know that if the right software is compiled correctly, in any distribution it should be able to run.  I downloaded 10.04 Ubuntu and installed it, but now I am wanting to start clean again with 11.10 and/or 12.04 *I remember it was up for Beta*.  The reason why, is I messed up all kinds of stuff while was trying to install SWTOR with Wine.

Now the thing is, I don't want to have to haul my near 2 1/2 foot tall, stainless steel case around the house to get my internet back.  It weighs over 50 lbs, I could do it, as I did it before, but I'm lazy.  I have the wireless driver backed up, it is the rt2870 driver.  I just want to ask.. All I should do is extract that driver somewheres and then do a ./configure, make, sudo make install after I cd to the folder I extracted it at.  Or am I missing a step to make sure the driver is installed and device is recognized?

---

### Post by Perfect Storm on 2012-03-13
There shouldn't be the differences between Linux Distro while running game via wine. The differences may be the driver (versions) for your video card and the versions of wine you're using.

Also if you haven't a Nvidia card (and installed restricted driver), it can be tough to get games work properly under wine (as close) to perfect.

It can be messy getting stuff working with wine, some stuff works out of the box others you need to tweak'n'hack a bit.


About your wireless card; It requires that you wire up your computer once as you need some libs/tools to compile the driver, then you should be ready to go afterwards.

When you have wired your computer, open the terminal and type;
```
sudo apt-get update && sudo apt-get upgrade
```
This will download and update your ubuntu.
Next tools to compile the driver;
```
sudo apt-get install build-essential
```
This meta-package will get the most common libs/tools to compile stuff.

Then;
```
cd /into/the/folder
./configure
make
sudo make install
```

---

### Post by Mark Phelps on 2012-03-13
Ubuntu 12.04, as indicated in the Release Notes, has "issues" and is intended only for use by Developers and Testers.  Even in the best of cases, it is not a good idea to mess around with a pre-release version unless you are prepared to deal with bugs and patches.

You would do better sticking with a released version, like 11.10.

---

