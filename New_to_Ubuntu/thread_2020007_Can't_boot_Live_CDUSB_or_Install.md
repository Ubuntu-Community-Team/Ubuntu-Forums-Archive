---
title: "Can't boot Live CD/USB or Install"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by Sheepe on 2012-07-07
Recently I've been trying to create a bootable disk backup of my system disk. I've typically used a LiveCD and then used GPartED in that to do so. (yes, I realize that's kinda asinine). In the process of going about this again, I've discovered that my computer will no longer boot LiveCDs or LiveUSBs properly. I can't even get any other software to properly copy the disk either.

Now, before you say "Oh, check your BIOS" I've done that. It actually boots to the CD/USB, but after setting up for about 5 seconds, it just hangs. Just goes full stop. Additionally, it seems to hang in different spots each time. Unfortunately, I don't even know where to begin to fix this problem. At first I thought it was my new sound card (ASUS Xonar), but pulling that changed nothing.

I've even tried installing rather than using a Live Boot. It does exactly the same thing.

Now the odd part is that the OCZ Toolbox boots just fine (I have a couple of SSDs). And my current installs of Win 7 and Ubuntu do as well. I'm just baffled at what is going on with my computer and why it won't boot LiveCDs/USBs

P.S. I understand that using a LiveBoot to backup my system disk is silly, but it's how I was doing it. I still haven't been successful, despite using a couple of tools. So if you got tips for that, that'd be awesome. (I've used Macrium Reflect, EASEUS Partition Manager, neither made a bootable disk)

---

### Post by doctorbighands on 2012-07-07
Are you trying to boot from a different live OS version than you have in the past? Check for the "silly" stuff first: bad download, bad format on the USB (I always format to fat16 to be safe), architecture mismatch, etc.

As far as cloning your system disk, why not (carefully, and after doing your homework) use plain ol' dd for the job?

---

### Post by Sheepe on 2012-07-07
Things I have tried:
11.04 CD (This worked originally, about a year ago)
12.04 CD
12.04 USB
12.04 WUBI

Architecture mismatch and bad download have been checked, I run an AMD64 system, and I've redownloaded multiple times. The CD and USB both boot to the prompt and ask if I want to run it Live, Install, Check Memory, etc. All of these options result in my system hanging. 

Last time I did it verbose, it said something about an I2C issue, so I think that might be my graphics card. I doubt it, though. (GTX 560Ti)

And can dd copy a currently in use disk?

---

### Post by Bucky Ball on 2012-07-07
Welcome. ;)

Boot from disk/usb to the screen with 'Try Ubuntu' 'Install' etc. Hit F6. You will be presented with some options. Choose 'nomodset'. Proceed to Live desktop or install.

---

### Post by Sheepe on 2012-07-07
That worked perfectly for the CD, but the USB doesn't have the F* options. So now I'm curious as to why that worked and how you knew?

Thank you very much!

---

### Post by Shadius on 2012-07-07
I believe the "nomodeset" option doesn't allow the graphics card to load the drivers, instead it loads the open source driver, Nouveau. I was looking for some information about "nomodeset", but I haven't found anything. I was hoping for a wiki page or something.

---

### Post by Karlchen on 2012-07-07
Good night, Sheepe.
> Recently I've been trying to create a bootable disk backup of my system disk. Yes, I do understand. This is how I backup my systems as well. Note, the systems (operating system and installed software, not the user data created by me).
To the best of my knowledge and based on my own experience, there is nothing which beats [**Remastersys**]("http://www.remastersys.com/ubuntu.html") (Thanks a lot to fragadelic).
Provided you install lupin-support and lupin-casper as well prior to using Remastersys this software will create a bootable ISO which can even be run from inside the ISO file (multiboot USB stick e.g.)

Kind regards,
Karl

---

### Post by oldfred on 2012-07-07
Bucky Ball is prescient. :) Or he just knew.

I also have had to add nomodeset but I add it to the command line in the USB.

This was for a different video, but shows the method:
If booting from USB it just may be easier to edit syslinux with whatever boot parameters you need like this:
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/)
simply edit “syslinux.cfg”

---

### Post by Sheepe on 2012-07-07
Y'all are wonderful! I've gotten the CD to work as I've needed. And dd has worked wonderfully and easily to copy my SSDs around. Thank you all very much!

---

### Post by Bucky Ball on 2012-07-07
> **Sheepe said:**
>  So now I'm curious as to why that worked and how you knew?



Wasn't aware the USB wasn't exactly the same. I guessed because you were getting blank screens so it pointed to a graphics issue. This command does stop the graphics being forced and the open-source drivers to load instead. That way you can install the correct drivers once the OS is installed.

The alternate CD rather than desktop is text based so that would work for you too, I don't doubt, without using the nomodset option, and this might cure your USB, too. ;) Good luck.

---

