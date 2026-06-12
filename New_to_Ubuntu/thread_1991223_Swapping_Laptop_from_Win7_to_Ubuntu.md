---
title: "Swapping Laptop from Win7 to Ubuntu"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by BigSmitty on 2012-05-30
I've been reading over these forums specifically to see if moving my laptop from Win7 to Ubuntu would be a good idea.

First off, the laptop specs:

Acer TimelineX 4830TG

i5-2450
8GB RAM
500GB HD
1GB discrete NVIDIA GT 540M

I build all my desktops but needed something for my hobby room / office for light application work.  I'm not worried about software issues with Win7 and Linux, but rather hardware compatibility, specifically my USB ports (2 2.0 and 1 3.0) and my memory card reader.  This laptop is going to be used primarily as a photo upload/edit and hobby blog machine.  As such, I have multiple digital cameras (Olympus, Fuju, Nikon and Sony) that I use and I need those photos to be transferred, edited (generally resizing, nothing more than that) and uploaded to my website for inclusion into my blog.

I know that NVIDIA makes a specific 32 and 64-bit driver for the card, and I'm assuming that the vast majority of the hardware on my laptop would be covered under the initial installation.  As a LINUX newbie I have no qualms about making the jump from Win 7; I just want to make sure my bases are covered before I do.

Thanks!

---

### Post by mikewhatever on 2012-05-30
You'll have to make a Live CD/USB and test. There is no other way to find out if 'the bases are covered' or not.

---

### Post by BigSmitty on 2012-05-30
Mike,

Thanks for the quick reply.  I already did the Live CD here at work, just waiting until I get home to give it a shot.

---

### Post by irv on 2012-05-30
I would suggest setting up a dual boot system. Leave Win7 on the PC, download the iso file for Ubuntu (I would use the 64bit for your hardware), burn the DVD, Boot with it and take the defaults for hard drive setup. I also have a 500 gig Hard Drive and I am running 3 operating systems on it so you will have more then enough room for 2. By doing it this way you will have a grub menu so you can boot into either or at startup.
EDIT: make sure you select "run along side other OS's"

---

### Post by Paqman on 2012-05-30
> **BigSmitty said:**
> I'm not worried about software issues with Win7 and Linux, but rather hardware compatibility, specifically my USB ports (2 2.0 and 1 3.0) and my memory card reader.

I've never heard of either of those giving anybody any trouble. Have a go with the LiveCD, but I'd put money on them working perfectly.

---

### Post by oldfred on 2012-05-30
I have not followed details but there are some issues with [B]nVidia Optimus.

[/B]Some turn one or the other video mode off and make it work. See also link on Bumblebee.

nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by BigSmitty on 2012-05-30
> **oldfred said:**
> I have not followed details but there are some issues with [B]nVidia Optimus.

[/B]Some turn one or the other video mode off and make it work. See also link on Bumblebee.

nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

I've been reading up on the Ironhide project while at work (slow day) and decided that I will probably switch the nVidia GPU off for Linux.  If I decide to dual boot, then I'll figure out from there, probably just enable from BIOS each time I'm going to boot to Windows.

---

### Post by idoitprone on 2012-05-30
> **BigSmitty said:**
> I've been reading up on the Ironhide project while at work (slow day) and decided that I will probably switch the nVidia GPU off for Linux.  If I decide to dual boot, then I'll figure out from there, probably just enable from BIOS each time I'm going to boot to Windows.

that post is old, and it works, since i have almost the same latop
follow this wiki
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

and dont forget to install bbswitch after your install bumblebee

```
sudo apt-get install bbswitch
```turn on intel powersaving features for sandybridge

```
sudo sh -c 'echo "options i915  i915_enable_rc6=1  i915_enable_fbc=1 lvds_downclock=1" >> /etc/modprobe.d/i915.conf'
```you should add```
 acpi_osi=Linux apci_backlight=vendor
``` to boot parameters  in grub default

---

### Post by Mark Phelps on 2012-05-30
Unike other, I have seen quite a few posts dealing with hardware problems related to the following:

> hardware compatibility, specifically my USB ports (2 2.0 and 1 3.0) and my memory card reader

Not so much the USB 2.0, but actually, the USB 3.0.  I have 3.0 ports on my desktop and they have been an endless source of problems with Ubuntu.  They didn't work reliably until I found new firmware for them (from Renesas) and was able to apply that -- in MS Windows.

As to memory card readers, they will either work or not.  If they don't, your only recourse will be to get a USB-based card reader.  Same problems with Ubuntu on my desktop -- can't see the internal card reader but can see the USB one.

As folks have said, the only way to know for sure is to boot using a LiveCD or LiveUSB.

---

### Post by BigSmitty on 2012-05-30
> **Mark Phelps said:**
> Unike other, I have seen quite a few posts dealing with hardware problems related to the following:



Not so much the USB 2.0, but actually, the USB 3.0.  I have 3.0 ports on my desktop and they have been an endless source of problems with Ubuntu.  They didn't work reliably until I found new firmware for them (from Renesas) and was able to apply that -- in MS Windows.

As to memory card readers, they will either work or not.  If they don't, your only recourse will be to get a USB-based card reader.  Same problems with Ubuntu on my desktop -- can't see the internal card reader but can see the USB one.

As folks have said, the only way to know for sure is to boot using a LiveCD or LiveUSB.

Mark,

Thanks for the help.  The USB 3.0 isn't a huge deal, as it only runs my 1.5TB external backup drive, which is USB 2.0/3.0 compatible.  Same with the card reader, I have a USB powered multi card reader available as well.  Not that either of these things not working is a deal breaker for installing Ubuntu, just wanted to clarify before trying it out.

Just tested the LiveUSB on my plant computer here at work (Windows XP SP3) and it booted up from the USB drive just fine, and everything looked ok at first glance.  Will take some time this afternoon to dig around before trying at home on the Acer.

---

