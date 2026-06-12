---
title: "Grub Error 24  I just want to start from scratch with this thing!!"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Indy452 on 2008-07-23
I admit I don't get the whole disk partitioning thing! I have tried reading about it and its just way over my head, I just can't get into it. 
I have this little laptop, an Averatec 3150  40GB hd and 256 ram.  Its fine for small stuff but I have somehow managed to destroy it:(  I have installed several different Linux distros on it over the past several months searching for the right one.  Well I want to use xubuntu or ubuntu on it but I can't install anymore and the boot screen says Grub loading error 24.  What can I do to fix this? I'm afraid I have jammed up some sort of partition and I would like to completely wipe this HD clean and start over and stay with Xubuntu forever.

Is anyone willing to help a poor old soul out?  I promise I'll be nice:)

Neal

---

### Post by kdb424 on 2008-07-23
If you want to keep all of the data you can reinstall any linux distro that came with grub, and it would fix that I'm pretty sure. If you want to try Ubuntu, or Xubuntu, and remove everything else, when you see the partitioning menu, tell it to take the entire disk, and it will erase everything, make 1 partition and install it. Just so you know, a partition pretty much tricks the hard drive to act like different hard drives so you can install different operating systems, and GRUB is a loader so you can choose what operating system you want. Grub isn't the only one, but one of the most popular, and my favorite. Any more questions on this subject? I'm your guy.

Edit: If you want to back up your data from your operating systems on the disk, and have external media, like an external hard drive, or you want to burn a CD/DVD with your data to back up on them, you can do so from Ubuntu right on the CD with no install. You can boot them as n operating system with no install, right on the CD, but it is slow, and not recommended for daily use, just to check it out, or back things up.

---

### Post by Indy452 on 2008-07-23
> **kdb424 said:**
> If you want to keep all of the data you can reinstall any linux distro that came with grub, and it would fix that I'm pretty sure. If you want to try Ubuntu, or Xubuntu, and remove everything else, when you see the partitioning menu, tell it to take the entire disk, and it will erase everything, make 1 partition and install it. Just so you know, a partition pretty much tricks the hard drive to act like different hard drives so you can install different operating systems, and GRUB is a loader so you can choose what operating system you want. Grub isn't the only one, but one of the most popular, and my favorite. Any more questions on this subject? I'm your guy.

Edit: If you want to back up your data from your operating systems on the disk, and have external media, like an external hard drive, or you want to burn a CD/DVD with your data to back up on them, you can do so from Ubuntu right on the CD with no install. You can boot them as n operating system with no install, right on the CD, but it is slow, and not recommended for daily use, just to check it out, or back things up.

I don't have a tich of data to back up. I have used the entire disk but the installs always freeze at 83% both xubuntu and ubuntu alternate install.

Do you think my hd could be going bad?  Is there a way to wipe it clean and have no OS? Then go in with a live xubuntu or alternate install cd and install.

Just so we are clear, no need to backup for me, I never had a chance to use any OS long enough to have anything worth saving. I do all of that on my desktop running Ubuntu.

Thanks, Neal

---

### Post by kdb424 on 2008-07-24
I recommend using Gparted. It is a special linux live Cd that is made just for partitioning and VERY easy to use. Just delete all of the partitions and apply. One it is done, try the installers again. If that doesn't work, if there is a check the CD on the main screen do that to make sure the CD is burned ok, and if it checks out fine, than there is something really wrong. I think that gparted will do it though.

---

### Post by zxscooby on 2008-07-24
In the partition editor you should be able to erase the existing partitions and/or delete the information on the existing ones. The grub error 24 points to a corrupted file system, that could be an indication of disk problems.

---

### Post by kdb424 on 2008-07-24
zxscooby. That's pretty much why I told him about gparted. Usually fixes problems, and when you delete all of the partitions, and make a new huge partition, that's an easy fix unless the disk has physical problems, which I doubt.

---

### Post by Indy452 on 2008-07-24
Where can I get a copy of this Gparted disk?  Is there a link to it from distrowatch?

So I just burn a copy of the latest and run it? I assume its self explanitory?  I'm obviously not that good at dealing with hd's and partition stuff so I'm taking your word on it that gparted is easy.

Can I run gparted from a live cd using the command line rather than burning another cd?

Thanks

Neal

---

### Post by oliviacond on 2008-07-24
> **Indy452 said:**
> Where can I get a copy of this Gparted disk?  Is there a link to it from distrowatch?

So I just burn a copy of the latest and run it? I assume its self explanitory?  I'm obviously not that good at dealing with hd's and partition stuff so I'm taking your word on it that gparted is easy.

Can I run gparted from a live cd using the command line rather than burning another cd?

Thanks

Neal

You can download it from here:
[http://exo.enarel.eu/mirror/partedmagic/](http://exo.enarel.eu/mirror/partedmagic/)

that is PartedMagic, pretty much the same with gparted but with more features.
if u don't want to burn it to CD, u can create a live USB.

---

### Post by coffeecat on 2008-07-24
> **Indy452 said:**
> Where can I get a copy of this Gparted disk?

<snip>

Can I run gparted from a live cd using the command line rather than burning another cd?



There's no reason why you shouldn't use the Gparted live CD, but Gparted is already on the Ubuntu live desktop CD. Just boot into Ubuntu with the live CD and go to System > Administration > Partition Editor and erase all you partitions and start over. Or if you've got the Xubuntu live CD, Gparted should be there somewhere. Then you can go straight to the installer without having to shut down one live CD and boot into another.

---

### Post by Indy452 on 2008-07-24
> **oliviacond said:**
> You can download it from here:
[http://exo.enarel.eu/mirror/partedmagic/](http://exo.enarel.eu/mirror/partedmagic/)

that is PartedMagic, pretty much the same with gparted but with more features.
if u don't want to burn it to CD, u can create a live USB.

I have downloaded and burnt a copy of partedmagic. I put it in and chose to run it at the default setting to eject the cd. Now when I ran it it loaded about 7/8ths and then ejected and now its frozen. What now?

---

### Post by Potatoj316 on 2008-07-24
seeing as you started the install im assuming you can boot the ubuntu/xubuntu live cd.  Just use gparted from there.

---

### Post by Indy452 on 2008-07-24
No I was just starting up parted magic is all. I figured it out anyhow my computer will not run live cd's very well for it only has just under 256 MB ram so I selected a different setting.

I'm now in the process of installing xubuntu from an alternate install cd so I'm counting on this working.  I have my doubts though, we'll see.

Neal

---

### Post by Indy452 on 2008-07-24
Well, It froze at 6% installing base system. WTF!!  This was a nice little laptop. I deleted the partitions, tryed to install again and the same ole crap. Nothing, froze, dirty shutdown as usual. 

What should I do?

Neal

---

### Post by gerben1 on 2008-07-24
Have you considered simply buying a new Hard Disk?
How large is the hard drive? Small hard drives are very cheap.

---

### Post by kansasnoob on 2008-07-24
> I don't have a tich of data to back up. I have used the entire disk but the installs always freeze at 83% both xubuntu and ubuntu alternate install.

That makes me think you have a dirty or faulty CD drive. It's simply not wanting to read past 83% on the disc. Since it's a laptop try a good CD/DVD drive cleaning device or try an external CD drive if you can beg, borrow or steal one!

I've been amazed at just how often I run across drive problems, even with fairly new drives! Smoke, dust bunnies, and just plain old dirt really take a toll quickly!

---

### Post by Indy452 on 2008-07-24
> **gerben1 said:**
> Have you considered simply buying a new Hard Disk?
How large is the hard drive? Small hard drives are very cheap.

I actually have but I seriously don't know how to open this little laptop case. Its a 40GBhd also.

---

### Post by Indy452 on 2008-07-24
> **kansasnoob said:**
> That makes me think you have a dirty or faulty CD drive. It's simply not wanting to read past 83% on the disc. Since it's a laptop try a good CD/DVD drive cleaning device or try an external CD drive if you can beg, borrow or steal one!

I've been amazed at just how often I run across drive problems, even with fairly new drives! Smoke, dust bunnies, and just plain old dirt really take a toll quickly!


Is it possible I need to clean the laser lens? If so how do you when there is no OS to open a media player?

Neal

---

### Post by kansasnoob on 2008-07-24
Actually, in hind sight, I must make two revisions to my previous statement:
(1)Don't steal a drive, (2)If you can borrow an external USB drive you may have to change settings in BIOS to boot from USB before it tries to boot from the hard drive.

---

### Post by gerben1 on 2008-07-24
> **Indy452 said:**
> I actually have but I seriously don't know how to open this little laptop case. Its a 40GBhd also.

if it turns out that the hd is broken, you may be able to find out how to replace it here:

[http://repair4laptop.org/disassembly_averatec.html](http://repair4laptop.org/disassembly_averatec.html)

---

### Post by kansasnoob on 2008-07-24
> **Indy452 said:**
> Is it possible I need to clean the laser lens? If so how do you when there is no OS to open a media player?

Neal

Generally you can open the drive electronically if you press the eject button while trying to boot.

If that doesn't work most drives have an access hole, but that's where laptops start to get fiddly. Have you ever torn apart a laptop? If not then you don't want to start on a machine you need.

I've fiddled around a lot and I've broken a lot of stuff learning, and I still break things!

Try a disc cleaner or even some canned air. Just don't spray any liquids into it!

Liquids and electricity do not mix!

---

### Post by Indy452 on 2008-07-24
> **kansasnoob said:**
> Actually, in hind sight, I must make two revisions to my previous statement:
(1)Don't steal a drive, (2)If you can borrow an external USB drive you may have to change settings in BIOS to boot from USB before it tries to boot from the hard drive.

I have a 2GB flash drive that really doesn't get used much. Are you suggesting I put Xubuntu on that and boot from it?

---

### Post by kansasnoob on 2008-07-24
Google your model of laptop + cd emergency eject.

---

### Post by kansasnoob on 2008-07-24
> **Indy452 said:**
> I have a 2GB flash drive that really doesn't get used much. Are you suggesting I put Xubuntu on that and boot from it?

I've never tried installing any Ubuntu from a flash drive. I have with Puppy Linux, which I personally don't care much for ............... but that's just a choice thing.

I bought Puppy on a pen drive here:

[http://www.linuxcdshop.com/linux/Puppy-Linux-USB-4-0-0.html](http://www.linuxcdshop.com/linux/Puppy-Linux-USB-4-0-0.html)

---

### Post by kansasnoob on 2008-07-24
While I was actually talking about a CD that you can plug in to USB, yeah, it looks like it's possible to install *buntu from a pen drive.

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I've just not done it.

---

### Post by egalvan on 2008-07-24
> **Indy452 said:**
> I admit I don't get the whole disk partitioning thing! I have tried reading about it and its just way over my head, I just can't get into it. 
... I would like to completely wipe this HD clean and start over and stay with Xubuntu forever.

Is anyone willing to help a poor old soul out?  I promise I'll be nice:)
Neal

From my "experience" files...

1)
Since you want to COMPLETELY wipe a hard drive:

use Darik's Boot and Nuke
   [http://www.dban.org/](http://www.dban.org/)

note: this WILL COMPLETELY ERASE YOUR DRIVE.

2)
after downloading ANY linux distro, CHECK THE MD5SUMS.
A bad download can cause much grief.

3)
after burning the ISO to a CD, boot it and run the "check cd media for defects" option. You may have a bad burn.


Not heeding points two and three have reduced my hair count.:(
Point number one is not always and option, eg dual-boot, up-grade, etc.

ErnestG:popcorn:

---

