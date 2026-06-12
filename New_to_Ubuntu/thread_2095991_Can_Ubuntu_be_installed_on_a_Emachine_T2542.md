---
title: "Can Ubuntu be installed on a Emachine T2542?"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by pilgrim64 on 2012-12-18
Greetings everyone from a new member! I'm having trouble installing Ubuntu on an Emachine T2542 with 512 ram and a 40 HD. Is this system not big enough? Currently it has an old windows XP service pak 1. This PC was given to me by a friend, so there is nothing on this I want to keep. I just want to use it for Ubuntu and wipe the hard drive and get rid of XP altogether.

I tried to burn it to disk but that wouldn't work. I installed windows installer, but when I chose Ubuntu as the OS, I got a system failed error message.  

Any hope I can get this to work or is it to the recycle bin? Thank you!

---

### Post by snowpine on 2012-12-18
Welcome to the forums!

Ubuntu's hardware requirements are detailed here:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Since your hardware is at the bottom end for Ubuntu, why not give Xubuntu or Lubuntu a try? These are the same "core" operating system as Ubuntu, but have lightweight interfaces with lower hardware requirements.

Anyway, if you want help troubleshooting the current situation, you'll have to give more details than "it didn't work." ;)

---

### Post by cmcanulty on 2012-12-18
try using a flash drive

---

### Post by ajgreeny on 2012-12-18
Definitely worth trying Lubuntu which I run on an older Acer Travelmate 2200 laptop with Celeron 2.0GHz and 512MB ram, similar to yours.

I admit it is not the fastest machine in the world, but it is quite usable and I can run any normal ubuntu applications in the repos with no problems, eg Firefox, Libreoffice, which you would have to add to Lubuntu as it has much more lowly alternative applications by default.

---

### Post by lykwydchykyn on 2012-12-18
> **pilgrim64 said:**
> 
Any hope I can get this to work or is it to the recycle bin? Thank you!

You can absolutely put that machine to work with Linux.  As mentioned, Lubuntu or Xubuntu would be a better fit than Ubuntu.

Can you elaborate on what "didn't work" when you tried to create an ubuntu CD?

You really don't want to do a WUBI install here.

---

### Post by MoebusNet on 2012-12-18
Perhaps these instructions on creating an Ubuntu CD/DVD will help:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

As noted, for older hardware the default Ubuntu DVD is not a good fit for your hardware because many older video cards have great difficulty running Unity 3D. Xubuntu or Lubuntu will not demand as much from your video card. Keep in mind that many of the systems from this era were not originally able to boot from USB; my 2002 Dell notebook needed a BIOS update to be able to do that. Once you have successfully burned a *buntu DVD (they no longer fit on a CD starting with 12.10 I believe) make sure you tell your BIOS to attempt to boot from CD/DVD first.

EDIT: The 12.04 version of *buntu may be a better fit for your system than 12.10 because some older video card drivers may not be available for you in 12.10. Also, if you need a non-PAE kernel those are not available in 12.10.

---

### Post by Autodave on 2012-12-18
> **pilgrim64 said:**
> Greetings everyone from a new member! I'm having trouble installing Ubuntu on an Emachine T2542 with 512 ram and a 40 HD. Is this system not big enough? Currently it has an old windows XP service pak 1. This PC was given to me by a friend, so there is nothing on this I want to keep. I just want to use it for Ubuntu and wipe the hard drive and get rid of XP altogether.

I tried to burn it to disk but that wouldn't work. I installed windows installer, but when I chose Ubuntu as the OS, I got a system failed error message.  

Any hope I can get this to work or is it to the recycle bin? Thank you!

I have the exact machine that you have and Xubuntu runs like a dream on it: videos stream w/o a problem.  I would stick with 10.4 though.....just in case.

---

### Post by pilgrim64 on 2012-12-18
Hey everyone, what a great site this is, so many replies so quickly. 

I tried burning Ubuntu from my Acer Aspire 5100 laptop first using Infrarecorder, and then Imgburn. The disk I used is a memorex DVD+R. They both seemed to burn ok, When I placed it in the ol Emachine, aka smoking 85' Pinto, and reboot, nothing. It just kept going to windows as normal. So I loaded Windows installer, but when I choose Ubuntu as the OS, I get this:

Uncompression error

--system halted:confused:

One poster said they have the same Emachine as me, that's encouraging. 
Before I try Lubuntu or Xubuntu, I will give it the ol college try for Ubuntu. I found a flash drive and will give it a go. Maybe there's still hope.

---

### Post by JHawk56 on 2012-12-18
> **pilgrim64 said:**
> ...reboot, nothing. It just kept going to windows as normal.
Is your BIOS set to try booting from the CD before the hard drive?

---

### Post by snowpine on 2012-12-18
Are you sure your computer has DVD capability? Google says your machine has a CD-ROM drive.

---

### Post by critin on 2012-12-18
> When I placed it in the ol Emachine, aka smoking 85' Pinto, and reboot, nothing. It just kept going to windows as normal. 

Sounds like you forgot to hit the Boot key while Bios was booting up.  You must 'boot' from the cd or usb flash, it won't 'just start' from the cd.  Try again and hit the boot key.  In my emachine its f10.

---

### Post by pilgrim64 on 2012-12-18
The front of the pc says it has: CD-RW 48x Max Write. 
Also: 2.50 GHz Intel Celeron processor, 3DIntel Extreme Graphics AGP. Not sure if this helps.

---

### Post by snowpine on 2012-12-18
I recommend the USB method, or a smaller Ubuntu variant that fits on a CD (since your hardware cannot read a DVD).

---

### Post by pilgrim64 on 2012-12-18
> **critin said:**
> Sounds like you forgot to hit the Boot key while Bios was booting up.  You must 'boot' from the cd or usb flash, it won't 'just start' from the cd.  Try again and hit the boot key.  In my emachine its f10.

When I hit F11 it allows me to see the boot order which is:

CDrom
removable devices (floppy)
Hard drive
Network boot

---

### Post by JHawk56 on 2012-12-18
As another old comptuer user, I echo the opinion you may be happier with a lighter version of Linux. My PC is of the same generation as yours with specs in the same ballpark, but assuming yours has no upgrades other than the RAM, my hardware is a bit beefier.

--Athlon XP Barton 2500+ is the rough equivalent of a P4 2.5, whereas your Celeron 2.5 might be thought of as a stripped-down P4 2.5.
--I also have 512MB DDR RAM, but 64MB of yours is reserved for the integrated video.
--My hard drive is faster (and with with so little RAM, we use our hard drives a lot!)

I mention this only because you'll probably find Ubuntu (Unity) more of a grind than I did. It works, but is sluggish and sometimes even hangs awhile before any visible response. Lubuntu, on the other hand, is snappy.

I ran a quick comparison. In Ubuntu 12.04 and running only Skype and a single tab of Firefox (at my Facebook page), System Monitor showed 392MiB RAM in use, and 32MiB of the swap file in use. Doing the same in Lubuntu 12.04, the numbers were 260 and 14. Take away 64MB of your RAM for your video, and with Ubuntu you'd already be getting pretty close to your usable RAM limit and having to swap out to disk frequently.

Assuming your Ubuntu ISO is usable, you might as well go ahead with Ubunto and see for yourself. You can always add Lubunto or Xubuntu as an alternate desktop environment. That's what I did, and it was easy through Software Center. Doing it this way, you'll have the apps that are normally missing from Lubuntu.

Another solution is more memory, but I suspect even with 1GB you'd be happier with Lubuntu.

---

### Post by JHawk56 on 2012-12-18
I think snowpine nailed it.

---

### Post by audiomick on 2012-12-18
> **pilgrim64 said:**
>  The disk I used is a memorex [COLOR="Red"]DVD+R[/COLOR]. 

> **pilgrim64 said:**
> ... boot order which is:
[COLOR="Red"]
CDrom[/COLOR]
removable devices (floppy)
Hard drive
Network boot

It has already been pointed out, but I'll go it again. The machine can't read a DVD. If you don't want to go back to a version that fits on a CD, you'll have to figure out how to do the install from a USB stick.

---

### Post by pilgrim64 on 2012-12-18
> **audiomick said:**
> It has already been pointed out, but I'll go it again. The machine can't read a DVD. If you don't want to go back to a version that fits on a CD, you'll have to figure out how to do the install from a USB stick.

thanks for pointing it out again, I appreciate it.

---

### Post by JHawk56 on 2012-12-18
Lubuntu 12.10 fits on a 700MB (80-minute) CD-R. Also, there is an unofficial, more highly compressed ISO of Ubuntu 12.10 that fits on a CD-R: [https://code.google.com/p/ubuntucd/](https://code.google.com/p/ubuntucd/)

---

### Post by critin on 2012-12-19
>  I'm having trouble installing Ubuntu

If your version is 12.10, no, you most likely cannot run it.  I can't on mine.  12.04 2D or xubuntu runs great though.

---

### Post by MoebusNet on 2012-12-19
> **pilgrim64 said:**
> When I hit F11 it allows me to see the boot order which is:

CDrom
removable devices (floppy)
Hard drive
Network boot

Your BIOS does not seem to have a "boot from USB" option. It seems you will need to use a CD.

---

### Post by OSIsOpenSource on 2012-12-19
It worked on My IBM Thinkpad, that has almost exact hardware, concerning RAM and HDD. Except I upgraded to 1 GB. Anyways, Welcome!

---

### Post by lykwydchykyn on 2012-12-19
> **MoebusNet said:**
> Your BIOS does not seem to have a "boot from USB" option. It seems you will need to use a CD.

On some machines, the option only shows up when you have a USB storage device plugged in (many dells do this).  Or sometimes you have to enable it in the BIOS.

It's often called LS-120, so if you see that, you can sometimes boot to USB.

CD is always a safer bet, though.

---

### Post by Sef on 2012-12-19
> Originally Posted by audiomick  
It has already been pointed out, but I'll go it again. The machine can't read a DVD. If you don't want to go back to a version that fits on a CD, you'll have to figure out how to do the install from a USB stick.

Other options are available, e.g., a [network install]("https://help.ubuntu.com/community/Installation/Netboot"). For other options, click [here]("https://help.ubuntu.com/community/Installation").

---

### Post by pilgrim64 on 2012-12-26
> **JHawk56 said:**
> Lubuntu 12.10 fits on a 700MB (80-minute) CD-R. Also, there is an unofficial, more highly compressed ISO of Ubuntu 12.10 that fits on a CD-R: [https://code.google.com/p/ubuntucd/](https://code.google.com/p/ubuntucd/)

A lot of good suggestions from you all, I ended up going the 700mb CD-R route and loading Lubuntu. Works good thanks again!

---

### Post by JHawk56 on 2012-12-26
Glad you got it running!

---

