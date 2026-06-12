---
title: "trying to install Lubuntu"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by gertrude97 on 2012-12-10
First post!! ):P

I am trying to install lubuntu onto an LG laptop model LS50e (quite old!) It has a Celeron M Processor 1.5GHz, 40GB hard drive and 238(?)MB RAM.

I boot from the CD and (after the gfxboot error), the "trial" screen comes up.

All is good so far..

When I press the "Install Lubuntu 12.10" button, the machine goes off and seems to try to install the program. However after 9+ hours, it still hasn't finished.

I get NO screens asking about drive partitions, or anything else. The screen "greys" out for a while, the mouse icon goes away, then the pretty blue background comes back, then goes away again for hours on end.

I want to totally get rid of the Windows XP that is already installed. Is the easiest way to do this is use GParted and delete the existing partition? Or should I just wait it out until the install asks me what I want to do? If the first option, then what format is best to use for the partition?

PS..I have installed Ubuntu 12.10 on my other portable (much newer), and had absolutely no problems!

Thanks for any direction you can give me.

---

### Post by ibjsb4 on 2012-12-10
A couple of things to try:

[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132")

[remove ubiquity-slideshow (post#12)]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568")

And welcome to the forums  :)

---

### Post by kurt18947 on 2012-12-10
I ran into a problem installing lubuntu on a machine older/weaker than yours.  I created a CD of an lubuntu alternative install.  Even then I needed a wired internet connection for the install to complete.  Lubuntu runs fine once installed.

If the notebook's hard drive is easily accessible, there is another method.  It requires an adapter to connect the notebook's hard drive to a desktop machine.  I've installed *buntu on a hard drive connected to a desktop machine.  I don't know if a USB enclosure would work or not, haven't tried it.  Once the installation is complete, shut the desktop down, disconnect the notebook's hard drive and reinstall in the notebook.  I did this and it worked.  *buntu unlike Windows doesn't have a registry so doesn't tailor the install to hardware installed on the orignal machine.  Don't install any proprietary drivers or anything while attached to a desktop machine - the laptop may not boot or may have graphics issues.

If the above are impractical,  you might try another distro.  PCLinuxOS and OpenSuSE install fine on the machine that didn't like the the *buntu installer.

---

### Post by irv on 2012-12-10
Just for the record I have an old no-name laptop with the same processor Celeron M Processor 1.5GHz, but my hard drive is a 160gig and my RAM is 1gig. I install Ubuntu Studio 12.04 on it and it is running OK. It boots a little slow, but one it is running it is usable. I only use it on a sound system for recording from a PA system through a Analog/Digital converter.

---

### Post by ibjsb4 on 2012-12-10
> **kurt18947 said:**
> I ran into a problem installing lubuntu on a machine older/weaker than yours.  I created a CD of an lubuntu alternative install.

The alternate-install-cd has been dropped with 12.10.

---

### Post by agxryt on 2012-12-10
> **gertrude97 said:**
> First post!! ):P

I am trying to install lubuntu onto an LG laptop model LS50e (quite old!) It has a Celeron M Processor 1.5GHz, 40GB hard drive and 238(?)MB RAM.

I boot from the CD and (after the gfxboot error), the "trial" screen comes up.

All is good so far..

When I press the "Install Lubuntu 12.10" button, the machine goes off and seems to try to install the program. However after 9+ hours, it still hasn't finished.

I get NO screens asking about drive partitions, or anything else. The screen "greys" out for a while, the mouse icon goes away, then the pretty blue background comes back, then goes away again for hours on end.

I want to totally get rid of the Windows XP that is already installed. Is the easiest way to do this is use GParted and delete the existing partition? Or should I just wait it out until the install asks me what I want to do? If the first option, then what format is best to use for the partition?

PS..I have installed Ubuntu 12.10 on my other portable (much newer), and had absolutely no problems!

Thanks for any direction you can give me.

Try 12.04 instead of 12.10.

12.04 will likely work better on your laptop anyways, I find it's a) less system intensive, and b) less buggy.

Your image could also be corrupted, I've had that happen before. Sometimes things don't get downloaded properly.

---

### Post by gertrude97 on 2012-12-12
Thank you, everyone. I have finally managed to install Lubuntu.

I used the Lubuntu 12.04 alternate install. Although I *did* have to run it twice. It seemed to stall halfway through the first run.

:D:D:D

---

### Post by audiomick on 2012-12-12
I suspect at least part of your problem was too little RAM. That is possibly why you had more luck with the alternate CD; it needs less RAM.

If you possibly can, try and get some more RAM for the machine. You will appreciate it.

---

### Post by irv on 2012-12-12
> **audiomick said:**
> I suspect at least part of your problem was too little RAM. That is possibly why you had more luck with the alternate CD; it needs less RAM.

If you possibly can, try and get some more RAM for the machine. You will appreciate it.

Yes, I concur Memory has gotten cheaper and is a good investment to improve speed. I recommend putting in the max. I have an older Dell Inspiron 1521 which came with 2 gig of RAM, the max is 4 so I installed 4 gig and added a SSD (solid state drive), and this old laptop runs like a new one. And it boots in 20 seconds from a cold boot. Everything loads much faster. These were two good investments, RAM and the SSD.

---

