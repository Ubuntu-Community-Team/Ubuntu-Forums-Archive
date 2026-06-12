---
title: "Looking for advice"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by lintlicker on 2011-12-02
Hi,

I'm a new ubuntu convert.  I can't believe I haven't taken the plunge sooner.  Before I ask my questions, I will give you a brief history and description of my current situation.

I have always been a windows guy.  Windows makes logical sense to me (up to a point).  I have a laptop that I've been running windows vista on for a few years now.  A month or so ago my yahoo mail started sending spam to people.  I visited a spyware-busting forum (one of the big ones) in an attempt to locate and remove the infection.  It quickly became apparent that I had a Master Boot Record problem.  In the process of trying to fix the problem, I completely borked my windows.  Windows will not boot at all and I did not have a reboot cd (and frankly, 10 dollars for a new one is more than I'm willing to spend on windows).  This is when I decided to check out ubuntu, and quickly fell in love.

Ok, here's where I'm looking for some advice.  I'm a musician and I have some software installed in windows that I don't want to lose.  I figure that the day might come when I really want to fix boot up windows to do one thing or another. Having two operating systems means that I have two copies of flash, java, office software, etc.  
(I also can't figure out how to look at how much free disk space I have.  I think it shouldn't be a problem, but I would like to have as much free space as possible).

What can I do here?  Can I make a reboot cd from my recovery partition?  Can I shrink the windows footprint on my drive?  Can I just arbitrarily delete things from the windows partition and just assume it's going to make trouble, but just for windows?

Also, how does exotic hardware and ubuntu get along?  I have an audio interface that I would love to use, but I'm not sure how to go about installing the drivers.  Does ubuntu need drivers?  Do drivers have a fancy new name?

I feel like there's millions of gallons of information out there, but I can't find a good starting place.  I've just been reading and reading for about a week, and I still don't feel like I know anything.  Are viruses really not possible in ubuntu/linux?  I feel like that's a BIG assumption.  (I'm no programmer though)

Ok I'm rambling, so now I'm going to stop.  Thank you all in advance for any advice you can offer.

lintlicker

:guitar:
</arbitrary smiley use>

---

### Post by JRV on 2011-12-02
Welcome aboard.


> **lintlicker said:**
> Hi,

(I also can't figure out how to look at how much free disk space I have.  I think it shouldn't be a problem, but I would like to have as much free space as possible).

Press <CTRL>-<ALT>T to open a terminal, enter the following command:```
df
```

> 
  Can I shrink the windows footprint on my drive?  


Yes, open a terminal, enter the following command to install gparted:
```
sudo apt-get install gparted
```
Now run the command:
```
gparted
```
gparted will make it easy to shrink your Windows partition.
> 
Are viruses really not possible in ubuntu/linux?  I feel like that's a BIG assumption.  (I'm no programmer though)


Viruses are possible, but very unlikely.
No system is virus proof.

---

### Post by Stovey on 2011-12-02
> **lintlicker said:**
> ...Also, how does exotic hardware and ubuntu get along?  I have an audio interface that I would love to use..

Hi LintLicker.  Are you aware of the following sub-forum?  They can probably help you get your audio interface set-up.

[http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)

---

### Post by fantab on 2011-12-02
> **lintlicker said:**
> Ok, here's where I'm looking for some advice.  I'm a musician and I have some software installed in windows that I don't want to lose.  I figure that the day might come when I really want to fix boot up windows to do one thing or another. Having two operating systems means that I have two copies of flash, java, office software, etc.  
(I also can't figure out how to look at how much free disk space I have.  I think it shouldn't be a problem, but I would like to have as much free space as possible).

What can I do here?  Can I make a reboot cd from my recovery partition?  Can I shrink the windows footprint on my drive?  Can I just arbitrarily delete things from the windows partition and just assume it's going to make trouble, but just for windows?


Since you are New to Linux- Ubuntu... my advice to you would be to DUAL BOOT Ubuntu with Windows. This way you can still have those software you "don't want to lose" until perhaps you find Linux equivalents.

Firstly RECOVER your Windows. And from Windows use its Partition software to manage your partitions... create space for Ubuntu... remember you can have only 4 Primary Partitions.

Then Install UBUNTU. Since you are into Music I suggest you try **[UBUNTU STUDIO]("http://ubuntustudio.org/")** which is Ubuntu with all sorts of pre-installed studio software.

---

