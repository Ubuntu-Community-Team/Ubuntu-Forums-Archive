---
title: "Will any Linux Distro run on an Apple iMac G3?"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by crjackson on 2008-10-26
I have 2 iMacs I'd like to donate locally, but the old OS is nasty. They are iMac G3's (the blue/white all in one cube). Does anyone know of a linux distro that will run okay on these machines?

---

### Post by dracayr on 2008-10-26
Ubuntu should work, but slow. I would suggest Xubuntu

dracayr

---

### Post by SunnyRabbiera on 2008-10-26
Actually for powerPC based macs you may want to try Debian as it will probably be your best option.

---

### Post by igknighted on 2008-10-26
Anything with a PPC version should work

---

### Post by SunnyRabbiera on 2008-10-26
> **igknighted said:**
> Anything with a PPC version should work

yeh though Debian has a lot of packages and tools on its side, plus if you are familiar with ubuntu debian is easy enough to get into

---

### Post by crjackson on 2008-10-26
> **dracayr said:**
> Ubuntu should work, but slow. I would suggest Xubuntu

dracayr

I thought *buntu didn't support PPC's like the G3?

---

### Post by crjackson on 2008-10-26
> **SunnyRabbiera said:**
> yeh though Debian has a lot of packages and tools on its side, plus if you are familiar with ubuntu debian is easy enough to get into

Is there a specific build for low powered systems?

---

### Post by crjackson on 2008-10-26
> **igknighted said:**
> Anything with a PPC version should work

What distros support PPC besides the ones just mentioned? I've been googling for an hour and haven't found the information.

---

### Post by SunnyRabbiera on 2008-10-26
> **crjackson said:**
> What distros support PPC besides the ones just mentioned? I've been googling for an hour and haven't found the information.

There are not many left these days, with PowerPC pretty much dead there isnt much for it.
As for debian on a powerPC by fefault debian can be installed as a minimalistic system if needed.
Debian is a light distro.

---

### Post by crjackson on 2008-10-26
> **SunnyRabbiera said:**
> There are not many left these days, with PowerPC pretty much dead there isnt much for it.
As for debian on a powerPC by fefault debian can be installed as a minimalistic system if needed.
Debian is a light distro.

Great, I'll give that a spin. I don't suppose something like puppy would work?

---

### Post by igknighted on 2008-10-26
> **crjackson said:**
> I thought *buntu didn't support PPC's like the G3?

The ISO's are out there, they just aren't linked on the official page anymore.  A quick forum search should turn them up.  There have been PPC ISO's for every release I can remember.

---

### Post by markharding557 on 2008-10-26
debian fully supports macs
[http://www.uk.debian.org/ports/powerpc/]("http://www.uk.debian.org/ports/powerpc/")

---

### Post by crjackson on 2008-10-26
Wow, there are too many images. I'm downloading this one does it look like the correct version to you guys?
[http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/debian-40r5-powerpc-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/debian-40r5-powerpc-xfce-CD-1.iso)

---

### Post by halitech on 2008-10-26
just checked Distrowatch

[http://distrowatch.com/search.php?category=All&origin=All&basedon=All&desktop=All&architecture=powerpc&status=Active](http://distrowatch.com/search.php?category=All&origin=All&basedon=All&desktop=All&architecture=powerpc&status=Active)

Does the MAC have a wired internet connection? If so, you could probably get away with downloading this instead : [http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/debian-40r5-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/debian-40r5-powerpc-netinst.iso)

---

### Post by Crafty Kisses on 2008-10-26
I'd suggest Debian or Xubuntu.

---

### Post by LunaticHiatus on 2008-10-26
Arch Linux, Debian, Fedora, Fennix, Gentoo, Mandriva, OpenSuse, Source Mage, Yellow Dog and all forms of Ubuntu all support Power PC 

I suggest Xubuntu since it would be quite a bit lighter of a desktop then KDE and Gnome and you seem to be already fimilar with ubuntu

---

### Post by crjackson on 2008-10-26
> **LunaticHiatus said:**
> Arch Linux, Debian, Fedora, Fennix, Gentoo, Mandriva, OpenSuse, Source Mage, Yellow Dog and all forms of Ubuntu all support Power PC 

I suggest Xubuntu since it would be quite a bit lighter of a desktop then KDE and Gnome and you seem to be already fimilar with ubuntu

I looked at yellow dog which I found on google, but there site doesn't mention support for the G3, it supports higher classes of the of the G series though.

I really didn't think Xbuntu supported PPC anymore.  I've got the debian iso now, so I'll give it a spin in a day or so. Looks like I've go a few I can test out.

---

### Post by crjackson on 2008-10-26
> **halitech said:**
> just checked Distrowatch

[http://distrowatch.com/search.php?category=All&origin=All&basedon=All&desktop=All&architecture=powerpc&status=Active](http://distrowatch.com/search.php?category=All&origin=All&basedon=All&desktop=All&architecture=powerpc&status=Active)

Does the MAC have a wired internet connection? If so, you could probably get away with downloading this instead : [http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/debian-40r5-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/debian-40r5-powerpc-netinst.iso)

It does, but I'd rather burn it locally.

---

### Post by Xiong Chiamiov on 2008-10-26
If you're wanting lightweight, and willing to do some learning, [Arch Linux]("http://www.archlinuxppc.org/") would be fantastic, as it allows you almost complete control over your system (almost because there's always Gentoo).  The base install will give you the minimum to run, and a few tools for building packages, but that's about it.  If you don't have internet available on those computer, however, it could be a little bit more interesting, as you'll need to download the packages for, say, a desktop environment on another computer.

---

### Post by crjackson on 2008-10-26
> **Xiong Chiamiov said:**
> If you're wanting lightweight, and willing to do some learning, [Arch Linux]("http://www.archlinuxppc.org/") would be fantastic, as it allows you almost complete control over your system (almost because there's always Gentoo).  The base install will give you the minimum to run, and a few tools for building packages, but that's about it.  If you don't have internet available on those computer, however, it could be a little bit more interesting, as you'll need to download the packages for, say, a desktop environment on another computer.

Not really looking for something that will be much effort. These will be donated and need a simple install and a decent desktop. Debian with xfce or xbuntu (if it will work) would be great.

---

### Post by Xiong Chiamiov on 2008-10-26
> **crjackson said:**
> Not really looking for something that will be much effort. These will be donated and need a simple install and a decent desktop. Debian with xfce or xbuntu (if it will work) would be great.
That's why it depends on the ratio of speed vs. fast-up.  I personally didn't like XFCE at all until I tried it on something other than Xubuntu, because Xubuntu has made it quite un-lite.  So, if you end up needing more speed out of them, then going with something with a little more control over what you have in it is an option.  If the performance is fine, though, then stay with what's familiar to you.

---

### Post by crjackson on 2008-10-26
> **Xiong Chiamiov said:**
> That's why it depends on the ratio of speed vs. fast-up.  I personally didn't like XFCE at all until I tried it on something other than Xubuntu, because Xubuntu has made it quite un-lite.  So, if you end up needing more speed out of them, then going with something with a little more control over what you have in it is an option.  If the performance is fine, though, then stay with what's familiar to you.

Okay thanks - Primary objective is friendliness and usability. These boxes will only be used for internet access and maybe playing music and grabbing email. I'm going to drag one out of the closet this week and try debian with xfce. Then I'll try Xbuntu just to compare. I'm really only familiar with Ubuntu, so I don't want to stray too far. No doubt someone will call for help. I can probably handle anything debian but that's it.

---

### Post by o.sliepen on 2008-10-27
Hello,

I have an orange ibook shell (300mhz, 3gb hd, 256 ram) and installed ubuntu 6.06 dapper drake on it, and I must say I really prefer it to the old non-supported OS9! It's a real upgrade on a cool-looking ibook.
I'm quite impressed, and this is my first Linux attempt.
Anyway, I encountered a few problems, so there might besomebody  able to help me here ? :

-in firefox: where can I find the missing plugins? Especially flash player... and which version should you choose (will any Linux version of the plugin do the trick??)

-certain keyboard - signs don'y work: all the signs that required the "option" (alt) key:
€ sign, @ sign etc.
I played around with the keyboard preferences, but gave up on it...any suggestions?
This is a swiss - french keyboard, but i must have encountered similar problems with the "option" key...?

-i cant play mp3s etc directly from sites...any suggestions from anyone?

thanks.

---

### Post by crjackson on 2008-11-02
Okay, so I drug this thing out of storage and fired it up. I have an old Gateway USB keyboard attached (never had the original), and an Xbuntu CD ready to go. The only problem is I don't know how to tell this thing to boot from the CD drive, and I can't find a key combination that will take it to the BIOS set-up screen.

Any suggestions?

---

### Post by crjackson on 2008-11-02
well - I've tried rebooting while holding 'C', 'c', 'shift+c', shift+C', 'ctrl+c', 'ctrl+C', 'alt+c', 'alt+C'

Nothing I've read about seems to work. Can anyone offer some help?

---

### Post by crjackson on 2008-11-02
After spending the last hour or so with Google, it seems what I'm trying to do is not possible. So I guess it's off to the trash bin with this Mac. It's a shame, as my wife was actually looking forward to running Linux on this machine.

---

### Post by crjackson on 2008-11-03
Anybody? Feel free to jump in with a hint or two...

---

### Post by tjniels on 2008-11-03
Yes, Debain is great for PPCs, I personally have it installed on an iMac G3, you could probably find the thread if you look.  The computers you are describing are actually PowerMac G3s, I believe, the iMacs sport an all-in-one form factor.

On a mac, whether using OS X or OS 9, the key to boot from a CD or DVD is the "c" key.  If booting from the CD while holding "c" does not work, you probably either have an incorrectly burned CD, aka not bootable, or your non-apple keyboard is getting in the way.  The latter seems unlikely, as non-apple keyboards are supported, and typing "c" still registers as a "c" for the computer.

Many people just create a burn folder with the ISO in it, this results in a non-bootable CD.  For the CD to be bootable, at least I know this for OS X, you can put the ISO on the desktop, open disk utility, select the image, and click "burn image".  This can probably also be done by right clicking on the ISO file and selecting "Burn as CD" or something like that.  As for windows I don't know, but it should be similar.  I hope that helps.

Debian is fast enough even with Gnome, IMO, and looks nicer as well IMO.  If you are only using it for internet, it doesn't really matter, but I'd go with Gnome for the more modern feel.  Don't lambast me for suggesting Gnome over Xfce, it's just an opinion.

EDIT:  Apologies, I just saw how many posts you have and I'm guessing you already know the things I wrote above.  I still hope it helps, though.

---

### Post by crjackson on 2008-11-03
> **tjniels said:**
> Yes, Debain is great for PPCs, I personally have it installed on an iMac G3, you could probably find the thread if you look.  The computers you are describing are actually PowerMac G3s, I believe, the iMacs sport an all-in-one form factor.

On a mac, whether using OS X or OS 9, the key to boot from a CD or DVD is the "c" key.  If booting from the CD while holding "c" does not work, you probably either have an incorrectly burned CD, aka not bootable, or your non-apple keyboard is getting in the way.  The latter seems unlikely, as non-apple keyboards are supported, and typing "c" still registers as a "c" for the computer.

Many people just create a burn folder with the ISO in it, this results in a non-bootable CD.  For the CD to be bootable, at least I know this for OS X, you can put the ISO on the desktop, open disk utility, select the image, and click "burn image".  This can probably also be done by right clicking on the ISO file and selecting "Burn as CD" or something like that.  As for windows I don't know, but it should be similar.  I hope that helps.

Debian is fast enough even with Gnome, IMO, and looks nicer as well IMO.  If you are only using it for internet, it doesn't really matter, but I'd go with Gnome for the more modern feel.  Don't lambast me for suggesting Gnome over Xfce, it's just an opinion.

EDIT:  Apologies, I just saw how many posts you have and I'm guessing you already know the things I wrote above.  I still hope it helps, though.

Thanks for you reply, it is an all in one form factor translucent off greenish / clearish plastic case.

As you can see above, pressing and holding the c key during power up didn't work.

It's bootable, I've made thousands of bootables from iso's.

Keyboard is a gateway usb. It was the only usb keyboard in the house. Since the c is pretty standard on any keybord, I wouldn't THINK this is the problem but who knows.

---

