---
title: "Which is the best OS for booting from a flash drive?"
date: 2008-09-27
forum: Other OS Talk
---

### Post by NintendoTogepi on 2008-09-27
And I'm a bit confused about how booting from the flash drive works in the first place, but where would be a good place to start out? (it has 2GB on it)

---

### Post by Frak on 2008-09-27
I guess PenDriveLinux would be good... since it was made for flash drives.

Anyways, go into your bios (usually a key combo on bootup), select boot options, then move your USB flash to the top. Save and reboot and it will always check for a USB drive first.

---

### Post by smoker on 2008-09-27
puppy linux is the best flash drive linux i've tried, and you can install straight to your flash drive from the live-cd: [http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by tgalati4 on 2008-09-27
Damn small linux works well.  Although it runs an older 2.4 kernel, I've been able to run Ubuntu binaries on it.

---

### Post by snowpine on 2008-09-27
First investigate your computer's bios to see if booting from USB is an option. Many older computers do not have this capability.

SliTaz is a very nice lightweight USB distro. The ISO is under 30mb so it will leave plenty of room on your drive for data. Also it is designed to minimize writes to the USB device, prolonging its lifespan.

Download SliTaz Cooking ISO: [http://slitaz.org/en/get/#cooking](http://slitaz.org/en/get/#cooking)
Burn to CD as image, reboot.
Play around with SliTaz Live CD. Do you like it? If so,learn how to make a Live USB here: [http://slitaz.org/en/doc/manuals/tazusb.en.html](http://slitaz.org/en/doc/manuals/tazusb.en.html)

---

### Post by enlightenment now on 2008-09-30
> **NintendoTogepi said:**
> And I'm a bit confused about how booting from the flash drive works in the first place, but where would be a good place to start out? (it has 2GB on it)
OzOS is the best and a derivative based on Ubuntu

see this How-To for ease of use:

******[How To: Prepare a bootable OzOS USB stick for installation]("http://cafelinux.org/forum/index.php/topic,1701.0.html")**

---

### Post by C.S.Cameron on 2008-09-30
I understand that Puppy, DSL and about a dozen other mini distros fit on a 2G drive with room to spare.
But these are just not the same as Ubuntu.
I just checked an Xubuntu install I have on a pendrive and it is taking up 1.6G.
On older machines your pendrive can be run using a boot CD.
See [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB).
My recommendation is to splurge $15 on a 4G model.
This thread has everything I know about booting from flash:
[http://ubuntuforums.org/showthread.php?t=922782](http://ubuntuforums.org/showthread.php?t=922782)

---

### Post by smoker on 2008-09-30
> **C.S.Cameron said:**
> I understand that Puppy, DSL and about a dozen other mini distros fit on a 2G drive with room to spare.
But these are just not the same as Ubuntu.
I just checked an Xubuntu install I have on a pendrive and it is taking up 1.6G.
On older machines your pendrive can be run using a boot CD.
See [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB).
My recommendation is to splurge $15 on a 4G model.
This thread has everything I know about booting from flash:
[http://ubuntuforums.org/showthread.php?t=922782](http://ubuntuforums.org/showthread.php?t=922782)

the good thing about a small distro like puppy or dsl though, is that you can also carry a fair amount of data on the drive as well, as well as save a fair amount of data. handy if you're using it on a host of different machines.

---

### Post by C.S.Cameron on 2008-10-01
I have just tried usb-creator.
You can download it here:
[https://launchpad.net/ubuntu/intrepid/i386/usb-creator/0.1.7](https://launchpad.net/ubuntu/intrepid/i386/usb-creator/0.1.7)
Makes setting up a "persistent" Flash drive a breeze.
It will install to USB directly from an iso on the desktop.
No CD's required.
Installed Xubuntu 8.10 onto a 2G flash and still have 1.2G free.

---

### Post by Frak on 2008-10-01
> **C.S.Cameron said:**
> I have just tried usb-creator.
You can download it here:
[http://launchpadlibrarian.net/180230...7Eppa1_all.deb](http://launchpadlibrarian.net/180230...7Eppa1_all.deb)
Makes setting up a "persistent" Flash drive a breeze.
It will install to USB directly from an iso on the desktop.
No CD's required.
Installed Xubuntu 8.10 onto a 2G flash and still have 1.2G free.
*cough*[http://launchpadlibrarian.net/18030793/usb-creator_0.1.7_all.deb](http://launchpadlibrarian.net/18030793/usb-creator_0.1.7_all.deb)*cough*

---

### Post by djhyland on 2008-10-02
Fedora has a very nice usb installer.  I've used mine quite a bit, it's even saved me at work when my provided Windows machine failed.

[[COLOR="Blue"]http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo[/COLOR]]("http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo") is the method I used to make mine; I think you may need a Fedora installation to use it, though.  There instructions for a persistent overlay are halfway down the page or so, with that you can update and add to your system as you like.

There is also a Windows-based installer at [[COLOR="Blue"]https://fedorahosted.org/liveusb-creator[/COLOR]]("https://fedorahosted.org/liveusb-creator").  You'll probably need a Windows install to use this, but I've heard rumors that it works under Wine as well.  I haven't tried either, but I imagine the results are the same as the first method.

---

### Post by Crimson_Wake on 2008-10-07
I'm also looking for a good version to boot & RUN from the USB.

I'm posting this with my 2GB USB pendrivelinux distro, but I'm using it WITHIN XP.  I have a wireless keyboard/mouse, and a USB external HDD, so when I try to boot to the USB, my BIOS gets confused and tells me it has an incorrect key/drive.  I haven't found a way around it just yet.

Anyway, I like the way Pendrivelinux (PDL) is setup, but it is slow.  Then again, that may be because I've never gotten it to load from boot.  The actual boot time in QEMU is about a minute, but applications take almost 10 seconds to load, and then navigating them is slow.

My questions are:
1 - Is everything slow because it is running from the USB through windows, and not from boot?
2 - Is there a way to get it to boot even with my USB accessories attached to the machine?
3 - What is a faster/better/more user friendly distro that can be run and booted from the USB.  I want to be able to run everything from the USB, and take it with me when I go.
4 - Is there a way to make PDL faster (am I just not enabling something that could make it faster?)

Thanks!

Blake

---

### Post by snowpine on 2008-10-07
> **Crimson_Wake said:**
> I'm also looking for a good version to boot & RUN from the USB.

I'm posting this with my 2GB USB pendrivelinux distro, but I'm using it WITHIN XP.  I have a wireless keyboard/mouse, and a USB external HDD, so when I try to boot to the USB, my BIOS gets confused and tells me it has an incorrect key/drive.  I haven't found a way around it just yet.

Anyway, I like the way Pendrivelinux (PDL) is setup, but it is slow.  Then again, that may be because I've never gotten it to load from boot.  The actual boot time in QEMU is about a minute, but applications take almost 10 seconds to load, and then navigating them is slow.

My questions are:
1 - Is everything slow because it is running from the USB through windows, and not from boot?
2 - Is there a way to get it to boot even with my USB accessories attached to the machine?
3 - What is a faster/better/more user friendly distro that can be run and booted from the USB.  I want to be able to run everything from the USB, and take it with me when I go.
4 - Is there a way to make PDL faster (am I just not enabling something that could make it faster?)

Thanks!

Blake

Hi Blake, if you computer is capable of booting from USB (not all are) then it's as simple as installing the OS to the pen drive (there are several methods) and making sure it has boot capability (using grub for example). Then you can press a key at bootup (F2 or F12 for example) to select which device to boot from.

As I mentioned in my previous post, I'm using SliTaz on a pen drive. It is a wonderful thing, but it is quite slow compared with the Live CD or a hard drive install. It's for emergencies or occasional use, not as an everyday operating system.

---

### Post by Crimson_Wake on 2008-10-07
Okie dokie.  I'll try removing my external HDD and such during boot.  I'll see if there's a way to make that happen.  I'm really just experimenting.  I have Xubuntu on my old hp laptop, but I'm looking for something portable and fun to take places.

I like PDL, but I wish I could make it a little faster when running from the USB.  I was looking at SLAX as well.  So many choices!

---

### Post by Tux Aubrey on 2008-10-08
The (UK) Linux Format mag did a recent review of usb booting various distros.  Their conclusions (from memory) wre that while the lightweight distros were definitely faster, Ubuntu had the edge in terms of detecting and working with a wider range of hardware.

I guess that is a pretty predictable conclusion - but one that may be important if you want to be genuinely mobile.

Just one other point - Doing a "persistent" install rather than simply having an iso on the usb carries a few gotchas.  I tried it recently from my main machine and totally borked grub.  It was probably totally my fault (I was suffering from a dose of dumb that day), but next time I'll physically disconnect my HDDs.

---

### Post by volkswagner on 2008-10-08
> **Crimson_Wake said:**
> Okie dokie.  I'll try removing my external HDD and such during boot.  I'll see if there's a way to make that happen.  I'm really just experimenting.  I have Xubuntu on my old hp laptop, but I'm looking for something portable and fun to take places.

I like PDL, but I wish I could make it a little faster when running from the USB.  I was looking at SLAX as well.  So many choices!

If you want speed, try a distro with a small footprint.  DSL and puppy both have a boot to ram option.  I don't think you can get any faster than running from ram.  Of course the machine needs to be up to the task.

---

