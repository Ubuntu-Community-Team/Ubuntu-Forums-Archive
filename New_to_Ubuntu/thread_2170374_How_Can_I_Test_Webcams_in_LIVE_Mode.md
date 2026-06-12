---
title: "How Can I Test Webcams in LIVE Mode?"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by 56es8lTI on 2013-08-26
I want to install 12.04 LTS on a laptop strictly to control ZoneMinder, but I need to see if the cameras and video capture devices will work with Ubuntu before I do a hard install.  I do not see an obvious way to test video devices in LIVE mode.

Can anyone help?

Thanks!

---

### Post by nenadlatinovic on 2013-08-26
Install Cheese if it's not on the live CD, and try it out.

---

### Post by 56es8lTI on 2013-08-26
> **nenadlatinovic said:**
> Install Cheese if it's not on the live CD, and try it out.  

Cheese is apparently not installed and I obviously can't install programs in the demo mode.  

Empathy (which is on the CD) can supposedly test webcams, but I see no configuration screen to do it.

---

### Post by howefield on 2013-08-26
> **56es8lTI said:**
> ...and I obviously can't install programs in the demo mode.

Not necessarily the case. You can install applications in Live CD/DVD mode, but obviously these will be lost on rebooting.

Give it a go, or you could make a Live USB with persistance, always handy to have one of those around anyway.

---

### Post by 56es8lTI on 2013-08-29
> **howefield said:**
>  or you could make a Live USB with persistance, always handy to have one of those around anyway.

OK, next part, then:

If my boot order is CD> USB> C drive...

Can I install Ubuntu as a true, fully-functional system install from the Live/Install CD onto a removable USB drive without having to try to set up dual-boot on the C: drive, and then just plug in the USB drive whenever I want to boot to Ubuntu rather than the Win OS on the computer's C: drive?

Seems like this *should* work. :-k

---

### Post by eternal243 on 2013-08-29
> **56es8lTI said:**
> OK, next part, then:

If my boot order is CD> USB> C drive...

Can I install Ubuntu as a true, fully-functional system install from the Live/Install CD onto a removable USB drive without having to try to set up dual-boot on the C: drive, and then just plug in the USB drive whenever I want to boot to Ubuntu rather than the Win OS on the computer's C: drive?

Seems like this *should* work. :-k

Yes the boot order is correct and it should be possible, I haven't tried though and I'm not at all sure on how you would do it.

---

### Post by 56es8lTI on 2013-08-30
> **eternal243 said:**
> Yes the boot order is correct and it should be possible, I haven't tried though and I'm not at all sure on how you would do it.

Doesn't it just ask you where you want the installation put from a list of the available drives during the first part of the install, or does it try to force a dual-boot if there's something already on the C: drive?

---

### Post by eternal243 on 2013-08-30
> **56es8lTI said:**
> Doesn't it just ask you where you want the installation put from a list of the available drives during the first part of the install, or does it try to force a dual-boot if there's something already on the C: drive?

Not sure, it might or it might not, as I told you I haven't tried but you are free to experiment with it if you like. I'm not sure the live cd allows installation directly to an usb-stick through the included installer. Also, be careful to not touch the windows-partition, since it could corrupt your windows installation. When you are installing from a live cd it will ask you where to put the boot record, and by default I think it will put it on the internal harddrive. I have no experience at all with USB installs, so maybe someone else can answer this. :)

---

### Post by 3rdalbum on 2013-08-30
Yes, there are two ways of doing it:

Use the USB Startup Disk Creator program on Ubuntu to create a LIVE-USB with Persistance - that's a part of the USB that can be used to save files and programs.

Or, run the Ubuntu installer. Use the "Something Else" option on the screen where it asks you how you want to install. Set the USB to filesystem Ext4 and its mount point to /

There's another button on that screen that allows you to set Advanced options. Click it and choose to install the bootloader to the USB instead.

I used that second method, admittedly that was in 2009 but I don't think it has changed much.

---

### Post by nerdtron on 2013-08-30
**[SIZE=4][COLOR=#000000]Install Mint/Ubuntu to a external harddrive or flash drive.[/COLOR][/SIZE]**

[http://www.youtube.com/watch?v=JKL1tmn-xC0](http://www.youtube.com/watch?v=JKL1tmn-xC0)

NOTE: This is a full blown install and not just a "creating a persistent file". You need at least an 8GB.

---

### Post by 56es8lTI on 2013-08-31
> **nerdtron said:**
> **[SIZE=4][COLOR=#000000]Install Mint/Ubuntu to a external harddrive or flash drive.[/COLOR][/SIZE]**

[http://www.youtube.com/watch?v=JKL1tmn-xC0](http://www.youtube.com/watch?v=JKL1tmn-xC0)

NOTE: This is a full blown install and not just a "creating a persistent file". You need at least an 8GB.

OK, I'll give it a try. 

Thanks!

---

### Post by 56es8lTI on 2013-08-31
Wow.

My biggest problem is only understanding about 15% of what the guy's saying, so a lot of the explanation is blowing past me.

What I don't get (because I can't understand him) is the manual partitioning rigmarole, as I thought that opting for using all available space on the selected drive automatically partitioned appropriately.  No?  :confused:

I'm going to be using a 80G small external drive, so there should be plenty of space.

---

### Post by nerdtron on 2013-08-31
> **56es8lTI said:**
> Wow.

My biggest problem is only understanding about 15% of what the guy's saying, so a lot of the explanation is blowing past me.

What I don't get (because I can't understand him) is the manual partitioning rigmarole, as I thought that opting for using all available space on the selected drive automatically partitioned appropriately.  No?  :confused:

I'm going to be using a 80G small external drive, so there should be plenty of space.

Let's try to make it simple then. If you can remove the internal hard drive first it would be a lot easier since there won't be any confusion and if you intend to use the whole 80GB drive for ubuntu, you don't have to do manual partitioning at all.

Here:
1. Remove the internal hard drive.
2. Boot to your USB flash drive (the Ubuntu installer).
3. Insert the 80GB drive.
4. Hit the installer wizard of Ubuntu.
5. Since there is technically only one drive (the 80GB), you can choose "Erase everything and install Ubuntu" option in the wizard.
6. Just continue with the installation and all partitions will be created and boot loader will be installed also on the external drive.

Basically the concept here is that the installer will be forced to install on the External 80GB drive since this is the only drive on the computer.
Goodluck.

---

### Post by 56es8lTI on 2013-08-31
> **nerdtron said:**
> Let's try to make it simple then. If you can remove the internal hard drive first it would be a lot easier since there won't be any confusion and if you intend to use the whole 80GB drive for ubuntu, you don't have to do manual partitioning at all.
I'm all for simplicity.

This was my original plan, but I thought there'd be an easier way than pulling the drive, which is not that readily accessed in this particular laptop...but I think I can do it.

> 
1. Remove the internal hard drive.
2. Boot to your USB flash drive (the Ubuntu installer).

Presumably, I can just boot to the Ubuntu CD.  I have no bootable Ubuntu flash drive.

> Basically the concept here is that the installer will be forced to install on the External 80GB drive since this is the only drive on the computer.

Yeah, you can't screw up a system that's not installed. ;)

Thanks!

---

### Post by eternal243 on 2013-09-01
Using a Live CD works fine instead of using an USB stick. =)

---

### Post by 56es8lTI on 2013-09-09
OK, here's the latest as of this evening:

With somewhat less drama and adventure than I usually encounter, I actually managed to bust open the laptop, pull the HD, plug in a USB external hard drive, install 12.04 onto the USB drive from the Live CD, get Ubuntu to run, put the Win7 HD back in and have an Ubuntu option without breaking anything.

**During the install, Ubuntu used my laptop's webcam to offer to take a picture of me, so I guess it works.**  Roundabout method, but it's there.

OK, here's the interesting part:  Despite changing the boot order for the USB-HDD to boot before the internal HDD, I found that the internal Win7 HDD booted anyway.

Can you guess why?

It took me a couple of minutes to figure it out.

At power-up, the USB-HDD isn't on long enough to spool up and be ready before failing in the boot order.

Solution?

Putting a music CD in the CD/DVD drive.  The CD/DVD drive is first in the boot order.  By the time the system sees it's not bootable, the USB-HDD is ready to boot.

[SIZE=5]IF IT'S STUPID AND IT WORKS, IT'S NOT STUPID! ;)[/SIZE]

---

