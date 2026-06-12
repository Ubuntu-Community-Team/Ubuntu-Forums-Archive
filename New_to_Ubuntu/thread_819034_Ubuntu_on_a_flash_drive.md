---
title: "Ubuntu on a flash drive"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by KingTermite on 2008-06-05
OK...using [this tutorial]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/") I created an Ubuntu install on a usb flash drive.

It has you create a 750MB partition (to copy over the live CD ISO) and the rest of the drive on another partition.

All went well. I can boot to the flash drive and it appears like a liveCD (not quite what I expected).

Where do I go for a permanent install? Do I now boot the liveCD version and install to the other partition on the USB drive? If so, will it then use that partition to boot from and not the 1st?

Or is booting from there (with "liveCD" version) what is expected? Is that boot up the "persistent" version to be used?

I'm a little confused.

---

### Post by bumanie on 2008-06-05
If I correctly understand what you are asking, ubuntu on a usb oendrive does load like a live cd, the difference being that you can choose to save any changes made during a session. Like the live cd, ubuntu 'unpacks' off the usb drive. You must appreciate that the read/write speeds from and to a usb pendrive are far slower than off a hard drive, therefore speed is not going to be spectacular. If you want something quicker, you could try puppy linux which loads itself into your computer ram and runs from there - it is very quick, even on old computers.

---

### Post by KingTermite on 2008-06-05
> **bumanie said:**
> If I correctly understand what you are asking, ubuntu on a usb oendrive does load like a live cd, the difference being that you can choose to save any changes made during a session. Like the live cd, ubuntu 'unpacks' off the usb drive. You must appreciate that the read/write speeds from and to a usb pendrive are far slower than off a hard drive, therefore speed is not going to be spectacular. If you want something quicker, you could try puppy linux which loads itself into your computer ram and runs from there - it is very quick, even on old computers.

OK, then if that's the case, what happens when that 750MB runs out of room? If I install some packages, they will just go there, right? Should I size that partition bigger?

Oh...and I realize it will be a bit slower. I'm just playing around with the idea of taking it with me wherever I go. I tried pendrivelinux which didn't suit me. I may still try Pupply or DSL.

---

### Post by Lord Xeb on 2008-06-05
When you boot up the flash, you can go into the drop down menu and look for the 'install' application. That should help. Also, there is extra room formated in Fat32 for a reason. Any extra stuff goes there.

---

### Post by KingTermite on 2008-06-05
> **bumanie said:**
> If I correctly understand what you are asking, ubuntu on a usb oendrive does load like a live cd, the difference being that you can choose to save any changes made during a session.

> **Lord Xeb said:**
> When you boot up the flash, you can go into the drop down menu and look for the 'install' application. That should help. Also, there is extra room formated in Fat32 for a reason. Any extra stuff goes there.

OK....two responses and they "appear" to be contradictory to me. This is exactly what I was confused about.

Do I just "run" when the "liveCD" menu comes up or do I "install to hard disk" and select the other partition on the USB?

It seems to me it would make sense to run as "liveCD" because the whole point is that its portable and you want it to boot up on any computer.

So if you do run it that way, does it just "automatically" use the extra partition for the space it needs?

---

### Post by rockfarmer2 on 2008-06-09
> **KingTermite said:**
> OK...using [this tutorial]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/") I created an Ubuntu install on a usb flash drive.

It has you create a 750MB partition (to copy over the live CD ISO) and the rest of the drive on another partition.

All went well. I can boot to the flash drive and it appears like a liveCD (not quite what I expected).

Where do I go for a permanent install? Do I now boot the liveCD version and install to the other partition on the USB drive? If so, will it then use that partition to boot from and not the 1st?

Or is booting from there (with "liveCD" version) what is 
expected? Is that boot up the "persistent" version to be used?

I'm a little confused. If you install to a USB flash drive, the files are saved to the partition formatted as ext2. If you use the penlinux tutorial listed, and install to a 1GB flash, then the .ext2 parition would be about 250MB and your files would be saved there in either your documents or download folders.

---

### Post by walker9010 on 2008-06-09
Are you trying to boot off the USB flash drive without installing on to the hard drive of your system?

---

### Post by KingTermite on 2008-06-09
> **walker9010 said:**
> Are you trying to boot off the USB flash drive without installing on to the hard drive of your system?

Yes. The intent is to have my own portable "world" on a flash drive to carry around with me.

---

### Post by ayenack on 2008-06-09
It'll have to be a live install. If you were to do a full install then the system would be set up for the computer you were using when you installed and unlikely to be transferable to other computers. And you'd need far more space on the USB device.

You might want to use one of the smaller distributions and have more space for your own files or, maybe buy a bigger USB media.

[Here's a tutorial]("http://icebuntu.6.forumer.com/viewtopic.php?t=24") I did a while back for [IceBuntu]("https://wiki.ubuntu.com/DerivativeTeam/Derivatives/IceBuntu") (a small distro based on Ubuntu.) It's still in development but should be usable for what you want.

Good luck.

[IceBuntu .iso download here.]("http://hosted.filefront.com/markp1989/")

---

### Post by issih on 2008-06-09
The tutorial you followed creates a so called "persistent" install.

This method creates a 750 mb partition which you copy data from the live cd into. The other "casper" partition is where anything new you install or files you create are installed. In essence you have created a live cd with "persistent" storage. In order for this persistence mechanism to work, you have to apply various kernel parameters at boot time, and also you must use a patched initrd.gz. If you followed the tutorial you linked to carefully you will have both these bits already done.

To launch choose the live option (not the install), if you did follow the tutorial accurately, you should be presented with an option that says:

Run Ubuntu in Persistent Mode saving and restoring changes

That option is the one you want, it will boot into ubuntu, and any changes will be saved back to the flash drive using the "casper" partition you created.

The other options will function exactly as the live cd did.

install is for installing to a hard drive, memtest for memory checking etc.

A persistent install can be used in any pc, as the system hardware is probed at boot time (just like a live cd). Therefore it is a much better bet if you want to be able to take the usb key about with you and just shove it into random computers. The other advantage (I think) is that the persistence mechanism attempts to minimise the number of write cycles the flash drive is put through, therefore prolonging its life.

A full install, treating the flash drive as if it was a normal hard drive is perfectly achievable, 

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

You will need a 4Gig or larger flash key though, and the system will not be happy being moved rom computer to computer, nor will ubuntu try to prolong the life of the flash drive.

---

### Post by KingTermite on 2008-06-09
> **issih said:**
> The tutorial you followed creates a so called "persistent" install.

This method creates a 750 mb partition which you copy data from the live cd into. The other "casper" partition is where anything new you install or files you create are installed. In essence you have created a live cd with "persistent" storage. In order for this persistence mechanism to work, you have to apply various kernel parameters at boot time, and also you must use a patched initrd.gz. If you followed the tutorial you linked to carefully you will have both these bits already done.

To launch choose the live option (not the install), if you did follow the tutorial accurately, you should be presented with an option that says:

Run Ubuntu in Persistent Mode saving and restoring changes

That option is the one you want, it will boot into ubuntu, and any changes will be saved back to the flash drive using the "casper" partition you created.

The other options will function exactly as the live cd did.

install is for installing to a hard drive, memtest for memory checking etc.

A persistent install can be used in any pc, as the system hardware is probed at boot time (just like a live cd). Therefore it is a much better bet if you want to be able to take the usb key about with you and just shove it into random computers. The other advantage (I think) is that the persistence mechanism attempts to minimise the number of write cycles the flash drive is put through, therefore prolonging its life.

A full install, treating the flash drive as if it was a normal hard drive is perfectly achievable, 

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

You will need a 4Gig or larger flash key though, and the system will not be happy being moved rom computer to computer, nor will ubuntu try to prolong the life of the flash drive.

Thanks. Finally enough detail that I understand the answer. Appreciate the newbie explanation. ;)

---

### Post by peakshysteria on 2008-07-12
But can this install run cross platform (OSX, Windows, Linux)? I started a thread about it [here]("http://ubuntuforums.org/showthread.php?p=5371657#post5371657"):

---

### Post by KingTermite on 2008-07-14
> **peakshysteria said:**
> But can this install run cross platform (OSX, Windows, Linux)? I started a thread about it [here]("http://ubuntuforums.org/showthread.php?p=5371657#post5371657"):

You are mistaking an important fact. It's not "running" from the main OS at all. It doesn't have to be cross-platform because its not "running" from the other platform. If a bootable USB device, then you are booting your own platform.

It should be able to run on any computer that can boot from USB because the OS on the hard drive never comes in to play at all. If you boot from USB before hard drive, then it should go from BIOS straight to USB boot device.

---

### Post by peakshysteria on 2008-07-14
Thanks man. That was the answer I was hoping for.

---

### Post by KingTermite on 2008-07-14
> **peakshysteria said:**
> Thanks man. That was the answer I was hoping for.

You're very welcome.

---

