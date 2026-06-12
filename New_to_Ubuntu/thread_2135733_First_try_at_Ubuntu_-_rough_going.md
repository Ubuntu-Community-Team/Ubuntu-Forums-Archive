---
title: "First try at Ubuntu - rough going"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by DetroitDoc on 2013-04-15
I'm a software developer and decided to make the jump to Ubuntu. I picked up a used Acer Aspire 5750-9851 (see the specs below). 

I installed Ubuntu 12.10 64-bit from a flash drive with no issues. I used the system for a couple of hours with no issues. During that time I checked the "Software Update" app and I applied all the recommended updates (220+ megs worth). 

At the end of that 2 hours the system locked up. I rebooted and it came back up and said a problem was detected. I filed an error report (or at least tried to). From here everything has gone down hill. For a few boots afterwards it would keep saying a problem was detected (I believe it was xorg crashing). Then during a boot it would give me a message about being in "low graphics mode" and then lock up. Now it just boots up to a black screen that says "[OK]" at the very top and locks up (the mouse moves but nothing else does anything).

What's really odd is that sometimes it boots to the grub menu and sometimes it doesn't. Why would it do that? I brought it up in recovery mode and ran fsck and "package repair". Neither one finds any problems. I created a flash drive with memtest+ on it and let it run over night. No memory errors were found.

Any other suggestions? I think my next move is going to be to re-install fresh and not apply the recommended updates for a while and see if it will stay up for a few days.


Acer 5750-9851 specs
Processor: i7-2630QM
Memory: 16GB
Hard Drive: Curcial 512GB SSD
Graphics: Intel HD
Chipset: Mobil Intel HM65 Express


Thanks!
Doc

---

### Post by Paqman on 2013-04-15
> **DetroitDoc said:**
> I think my next move is going to be to re-install fresh and not apply the recommended updates for a while and see if it will stay up for a few days.


That sounds sensible.

It sounds like you've got graphics driver problems. That's a bit unusual with Intel graphics, normally they Just Work. It's entirely possible the problem is hardware, especially if you got it second hand. A fresh install should help isolate that, as would running from the Live disk or a USB.

---

### Post by grahammechanical on 2013-04-15
If you choose the nuclear option of a fresh install, which is quick and effective, then do not tick the box to install third party software. That will install a proprietary video driver. I have experienced the issues you are having because of having a proprietary video driver installed. I have found the default open source Nouveau driver to be sufficient.

Recovery Mode>Resume will sometimes get us to a desktop without the loading of the video drivers. From there you can activate the Nouveau driver. That is if you can get to a desktop. If it is only the wallpaper, then right click the desktop and select Change wallpapers. That will open System Settings and in Software Sources>Additional Drivers tab you can experiment with other video drivers. Remember, most of those drivers are proprietary software. The Ubuntu developers cannot access the code. They cannot fix issues. They can only pass the bug reports upstream to proprietor of the driver.


Is there a discrete video adapter was well as the Intel HD adapter? You might be interested in this

[http://www.omgubuntu.co.uk/2013/04/intel-release-graphical-installer-for-their-linux-drivers](http://www.omgubuntu.co.uk/2013/04/intel-release-graphical-installer-for-their-linux-drivers)

Regards.

---

### Post by Bucky Ball on 2013-04-15
Welcome to the forums.

> **Paqman said:**
> 
It sounds like you've got graphics driver problems. That's a bit unusual with Intel graphics, normally they Just Work. It's entirely possible the problem is hardware, especially if you got it second hand. A fresh install should help isolate that, as would running from the Live disk or a USB.

+1. Does sound hardware-ish as the problem comes and goes. Try running from the LiveCD and see if you get any problems there.

PS: Just a tip; you will have better luck getting help if you use thread titles that describe and directly relate to your issue rather than generic ones. ;)

---

### Post by Paqman on 2013-04-15
> **grahammechanical said:**
> If you choose the nuclear option of a fresh install, which is quick and effective, then do not tick the box to install third party software. That will install a proprietary video driver. I have experienced the issues you are having because of having a proprietary video driver installed. I have found the default open source Nouveau driver to be sufficient.


Dude, he has Intel graphics, not Nvidia so wouldn't be using nouveau. The Intel drivers are in the kernel, no need to install or activate anything.

---

### Post by DetroitDoc on 2013-04-15
Thanks for all the replies guys!   

This model Acer Aspire only has Intel graphics.

The laptop was running windows successfully prior to me installing Ubuntu.   I did replace the drive with an SSD and Ubuntu is the only thing installed on it.

I'll try the following things when I get home tonight I'll try reinstalling without any proprietary packages and I won't apply all the updates and see if it stays up for a couple days.  If it does I'll apply the updates and see if that's what broke it.

---

### Post by Nr90 on 2013-04-15
You could also consider giving 13.04 a shot.
It's in beta now and pretty stable, it'll be released as the new stable pretty soon.

If it's locking up / giving graphic problems I suppose this could be kernel related and 13.04 runs a much newer kernel then 12.10.

---

### Post by DetroitDoc on 2013-04-15
Thanks again guys. If I have no luck with the reinstall I might try 13.04 or even 12.04.

Any thoughts to why the grub screen would pop up about 50% of the time on reboot? That seems really odd to me as well. This is the only O/S on the system so it shouldn't be popping up at all right? When I first did the install I rebooted several times and it did not come up.

Thanks!
Doc

---

### Post by Bucky Ball on 2013-04-15
As a new comer I would try 12.04 LTS. Definitely more stable at this point and better place to start (also is long-term support release so is supported until 2017). Although 13.04 has a newer kernel doesn't necessarily mean it will fix this problem. Strange though as Intel graphics should be working out-of-the-box. 

When the grub screen comes up and you choose Ubuntu does it then run normally?

---

### Post by DetroitDoc on 2013-04-15
> **Bucky Ball said:**
> When the grub screen comes up and you choose Ubuntu does it then run normally?

About half the time the systems boots right to the black screen with "[OK]" at the top.   The other half of the time it shows the grub screen first.  If I choose to boot Ubuntu it then boots to the same black screen with "[OK]" at the top.

Once in a while I can get it to boot up to the "low graphics mode" message but it locks up there.

Once in a great, great while it will boot up to the login screen, let me login and then report that xorg crashed.

Thanks!
Doc

---

### Post by Kopkins on 2013-04-15
> **DetroitDoc said:**
> Thanks again guys. If I have no luck with the reinstall I might try 13.04 or even 12.04.

Any thoughts to why the grub screen would pop up about 50% of the time on reboot? That seems really odd to me as well. This is the only O/S on the system so it shouldn't be popping up at all right? When I first did the install I rebooted several times and it did not come up.

Thanks!
Doc

Ubuntu configures grub to timeout at 10 seconds by defualt I believe. Then if go edit the grub config file and change the timeout to '0' the grub screen will not appear and you will go straight to booting the first option in the grub menu.

So , it should either show up all the time or none of the time.

---

### Post by Bucky Ball on 2013-04-15
Have you attempted to run it from the LiveCD yet (Try Ubuntu without installing) and does it run smoothly or start crashing then also?

---

### Post by craig10x on 2013-04-15
I'd try 13.04 if i were you...the newer kernels have had a lot of improvements that are intel related, so you may have less problems...12.04 doesn't have these newer kernels that 13.04 has been using...
You can get the iso from ubuntu daily builds...it will be up-to-date as of today...run it on live session first, and if all is ok, then you could install...

I have a recent toshiba with intel i3 and intel graphics and have been running 13.04 development for 2 months now and it's been great...and it will be going final next week anyway...if you install now, it will just ride into the final release with the updates you will get each day...

---

### Post by DetroitDoc on 2013-04-15
I reinstalled 12.10 and did not update the software.   I rebooted a few times and then finally evolution-calendar crashed (which appears to be a known problem).  I reported it and after that the laptop just boots to a black screen with [OK] or occasionaly "low graphics mode" and locks up.

I had been installing from a flash drive (USB).   I used UNetbootin to create the flash drive.   I noticed somethign odd when booting from the flash drive.  "Install Ubuntu" was listed multiple times.   I happened to have the book "Ubuntu Unleashed" which had a CD with 12.10 on it.    I installed from the CD included in the book and so far so good.   I've updated all the software as well.

I am curious if I experience another crash of something if thats the trigger that causes me to loose the desktop for some reason.

---

### Post by DetroitDoc on 2013-04-15
I just realized that the CD included in the book might be a 32-bit version.   I'm running 16GB.  Do I need to run the 64 bit version?


Here's the output from uname -a.  Is this the 32-bit version?
```
Linux todd-Aspire-5750 3.5.0-27-generic #46-Ubuntu SMP Mon Mar 25 20:00:05 UTC 2013 i686 i686 i686 GNU/Linux
```

"about this computer" shows 16 GB (15.7 actually) but I'm guessing i'm not utilizing all 16 gig.

---

### Post by lykwydchykyn on 2013-04-16
You don't *need* a 64-bit OS to use all 16Gb of RAM -- that's handled by the PAE function of the kernel.  However, it's probably going to make better use of the RAM if you do use 64-bit.

Next time X crashes on you, restart and check out /var/log/Xorg.0.log.old to see if any error messages pop out at you, probably near the end of the file.

---

### Post by White Rasta on 2013-04-16
I just did a lookup on your system specs
I'm sorry to say that Intel has a recall on your cougerpoint-m chipset

---

### Post by DetroitDoc on 2013-04-16
> **White Rasta said:**
> I just did a lookup on your system specs
I'm sorry to say that Intel has a recall on your cougerpoint-m chipset

That may be but I don't think that is the issue here.   Everything seems to run find under the 32 bit version of Ubuntu and Windows.

I'd be curious to know if I am affected though.  I found in windows you can check the chip's revision number as shown below.   I don't have windows on that system right now so I wonder if there is a way to find this out via ubuntu.

```

C:\Users\yourID>wmic idecontroller get deviceid
DeviceID
PCI\VEN_8086&DEV_1C03&SUBSYS_04941028&_REV_04_\3&11583659&0&FA

REV_04 = B2 of the Cougar Point chipset = Potentially BAD

```

---

### Post by DetroitDoc on 2013-04-16
It looks like I can check it with lspci.   It does look like I have the affected chipset.  

```

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])


```

However it sounds like the only impact over time is a slight performance degradation of SATA performance.   So I don't think this is a contributing factor to the issue I was having.

---

### Post by Bucky Ball on 2013-04-16
> **DetroitDoc said:**
> 
However it sounds like the only impact over time is a slight performance degradation of SATA performance.   So I don't think this is a contributing factor to the issue I was having.

How old is the chipset in this machine? Perhaps that's all they know about it for now. If they're offering a replacement or free repair, I'd take it. Perhaps it does have something to do with your issue.

I had a HP that was on the recall but just missed the deadline when mine started to die. Yes, first the wireless dies, that they know. Thereafter the motherboard dies, but it could be a week or two months later. For me it was a week.

---

