---
title: "How to install drivers for mobile internet?"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by Carnivorum on 2012-04-17
Bs'd

I have a stick for wireless internet, from the provider pellephone. 

When I stick that thing in the USB, I get an icon on my desktop, of Join Air.  The same as in windows.  
The difference is, in windows it works right away, in Ubuntu not. 

I had a thing like that before, from Cellcom, and never got that one working.   But when I click on this icon, then I see folders named:  "Linux", "Mac", en "Windows", so it looks like that it should be possible to get it working in Linux.

When I click on the Linux folder, then I get another folder named:   /media/Join Air/Linux/PCL_PELISR.tar.gz

When I click on that one, I get four choices:   

tools

install.sh

Join_Air.tar.gz

zr

And that is where I get stuck.

How can I install those drivers?

---

### Post by coffeecat on 2012-04-17
By wireless, do you mean mobile internet, and is this a Huawei stick? If so, and if you are running a recent version of Ubuntu, it will most probably work out of the box without you having to install any driver. However, the fact that the pseudo-CD is automounting suggests that you may be running 10.04.

Some questions.

What model Huawei, if it is Huawei?
What version of Ubuntu?
Do you have the package usb-modeswitch installed?
With the device plugged in, if you click on the network manager icon, do you see a choice for mobile broadband.

By the way, the common language of the forum is English. You are more likely to get replies if your thread title is in English. If you post a translation (I don't want to rely on Google translate!), I can change the title for you.

---

### Post by Carnivorum on 2012-04-17
> **coffeecat said:**
> By wireless, do you mean mobile internet, and is this a Huawei stick? If so, and if you are running a recent version of Ubuntu, it will most probably work out of the box without you having to install any driver. However, the fact that the pseudo-CD is automounting suggests that you may be running 10.04.

Bs'd

I'm running 10.04 LTS

> Some questions.

What model Huawei, if it is Huawei?

Don't know if it is Huawei.  

I'll tell you what is written on it: 

Net stick ZTE   HSUPA USB stick
Model MF 190
CE 1588
ZTE corporation

Made in China

> Do you have the package usb-modeswitch installed?

Just now installed it.

> With the device plugged in, if you click on the network manager icon, do you see a choice for mobile broadband.

If I go to "Network connections" and click on "Broadband", then I don't have a choice in broadband.

> 

By the way, the common language of the forum is English. You are more likely to get replies if your thread title is in English. If you post a translation (I don't want to rely on Google translate!), I can change the title for you.

Thanks.  I tried to change it already, I thought It changed, guess it didn't work.

---

### Post by Carnivorum on 2012-04-17
.

---

### Post by coffeecat on 2012-04-17
> **Carnivorum said:**
> 
Thanks.  I tried to change it already, I thought It changed, guess it didn't work.

Only staff can edit a title. If you post the English translation, I'll do that for you.

> **Carnivorum said:**
> Bs'd

I want to switch to 12.04 LTS anyway.  I see it is now in final Beta, would it be worth it for me to upgrade now?

It's certainly worth trying 12.04 from the live CD or USB to see if your device will work. It's far more likely that 12.04 will come with a suitable driver. Rather than download the Beta, you can run a more up-to-date snapshot from a daily ISO, here:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

If the live session works OK for you, then there should be no problem upgrading to 12.04, so long as you are prepared for a few glitches in the last few days until final release. Hopefully few and minor. There are likely to be a few rough edges even after final release as 12.04 gets exposed to a wider range of hardware than was possible during the testing cycle and relevant bugs are fixed. Some people avoid installing a new version until it's been out for a month or two, and some people are happy straight away.

---

### Post by Carnivorum on 2012-04-17
> **coffeecat said:**
> Only staff can edit a title. If you post the English translation, I'll do that for you.

Bs'd

The translation is:  How to install drivers for mobile internet?

> It's certainly worth trying 12.04 from the live CD or USB to see if your device will work. It's far more likely that 12.04 will come with a suitable driver. Rather than download the Beta, you can run a more up-to-date snapshot from a daily ISO, here:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I'll give it a try, will take me an hour to download it. 

Can I install 12.04 from that CD?

> If the live session works OK for you, then there should be no problem upgrading to 12.04, so long as you are prepared for a few glitches in the last few days until final release. Hopefully few and minor. There are likely to be a few rough edges even after final release as 12.04 gets exposed to a wider range of hardware than was possible during the testing cycle and relevant bugs are fixed. Some people avoid installing a new version until it's been out for a month or two, and some people are happy straight away.

I don't like bugs and problems, would prefer to wait a while, but I'll see if it works.

---

### Post by coffeecat on 2012-04-17
> **Carnivorum said:**
> 
The translation is:  How to install drivers for mobile internet?

The forum software seems to be fighting me at the moment. Let's see if that does it. :?

> **Carnivorum said:**
> 
Can I install 12.04 from that CD?


You can do a fresh install from the CD. The only difference between the daily live and one of the betas is the versions of all the packages. They are being updated all the time during the testing phase, and a Beta is simply a daily from a particular date given some extra QA.

I believe you can update your 10.04 system directly from the 12.04 CD, but I haven't tried this myself.

> **Carnivorum said:**
> I don't like bugs and problems, would prefer to wait a while, but I'll see if it works.

I understand. The 12.04 testing cycle has been much smoother than most, but no one can guarantee that there won't be some issues after the final release, if only because 12.04 will be installed on a much wider range of hardware than during testing. If you do decide to install from today's daily and you keep up-to-date, you won't have to re-install when the final is released. One tip. Until release day, if Update Manager offers you a partial upgrade, be very cautious. See here:

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

This shouldn't be a problem after release.

---

### Post by chamber on 2012-04-17
If you extract the PCL_PELISR.tar.gz and cd to the location you may be able to run the install.sh from the command line.

I have to do something similar with my wireless usb dongle when a new kernal update is released.

You should just be able to do the following,

```
cp /media/Join Air/Linux/PCL_PELISR.tar.gz ~/Desktop
cd Desktop
tar xvf PCL_PELISR.tar.gz
cd PCL_PELISR
bash install.sh
```

This may work for you.

---

### Post by Carnivorum on 2012-04-29
> **Carnivorum said:**
> Bs'd

The translation is:  How to install drivers for mobile internet?



I'll give it a try, will take me an hour to download it. 

Can I install 12.04 from that CD?



I don't like bugs and problems, would prefer to wait a while, but I'll see if it works.

Bs'd

I installed 12.04, and it works fine.   Also my mobile internet works now. 


Thanks everybody for the help.

---

### Post by Carnivorum on 2012-05-01
Bs'd

I had in 12.04 an icon on my taskbar, with which I could switch from my cable internet to my mobile internet. 

But that icon has disappeared, and now I don't know how to start my mobile internet. 

How can I get that icon back?

---

### Post by Carnivorum on 2012-05-01
Bs'd

I found how to switch between wired and mobile internet,  I go to Applications - System tools - System settings - Network, and there I can manage it.  

But I would like to get back that icon on my taskbar, it's just a whole lot easier.

---

