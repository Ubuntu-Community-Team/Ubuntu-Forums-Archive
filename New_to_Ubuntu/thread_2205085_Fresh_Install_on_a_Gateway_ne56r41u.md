---
title: "Fresh Install on a Gateway ne56r41u"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by russell.dexter on 2014-02-11
Hey guys,

Not a total noob, but have been out of the Linux world for a bit mostly due to work (last distro was red hat.... yeah, that long) - but the nightmare of Windows 8 has convinced me to make the switch back to open source, at least where I can. 

Recently purchased a Gateway ne56r41u from a big box store, on the cheap side for sure:  Intel Pentium B960 / 2.2 GHz ( Dual-Core ), 4 gb ram and 500gb hard drive. 

So a couple questions.... want a total wipe with a kubuntu install (When I last left linux I was using KDE, and I have followed all the Unity / Gnome 3.0 controversies a little to think maybe I should just go with what I was familiar with.

My drive is currently partitioned like this:

*:Recovery                400mb
*:ESP                        300mb
*:                             128mb
C: Gateway                448.85GB                     
*:  $                           350mb
*: Push Button Reset   15.76GB                     

How should I partition?

The UEFI and secureboot mode of this machine has been slightly worried, but if I'm switching to totally Kbunutu, should I just cut it off and enable Legacy mode in the BIOS?

I have tons and years of photos stored with dropbox web storage, anyone use it on a Linux box successfully?

Thanks for your help and input!

Dexter

---

### Post by Bucky Ball on 2014-02-11
Dropbox works faultlessly.

I would back that stuff up or remove the drive if you can before proceeding.

First thing to do is shrink the C: partition as you currently have nowhere to put Kubuntu. Do this by booting into Win and using the Win software, DO NOT use Gparted as that could leave you with a non-functioning Win.

Once you have some free space (do not format it as NTFS, FAT or anything else) then you are ready to boot from the Kubuntu disk/USB and install it to the free space. Leave the disk set to UEFI and switch off in BIOS fastboot, secureboot and boot Win8 and switch of faststart in the software (hibernation essentially). Now you are ready to go. 

Boot from the installer and follow your nose. When you get to the partitioning section, choose 'Something Else' and partition manually. You will see the free space in there and your NTFS Win partitions (stay away from them). For Kubuntu you are going to need a couple of partitions at minimum. / = the OS and /swap which should be 2Gb or the size of you RAM if you hibernate.

There are more exotic schemes, it's up to you, but you don't have a heap of room on that drive. The / partition doesn't need to be more than about 20Gb if you are keeping your personal data on another partition. If you are keeping it in the /home directory inside / then you want to make / as big as you can. An option here is to use symlinks inside the /home directory to existing data directories on other partitions or even other drives. 

Here is a guide with pics for installing 12.04. Applies to most the newer releases. The difference is in step 3 you are going to choose 'Something Else' (look at that pic). This is VERY important. Don't let Kubuntu partition automatically.

Good luck and report back when you hit a brickwall. ;_

---

### Post by russell.dexter on 2014-02-11
Thanks for the reply,

Just to be clear, once I back up the photos and a few file to dropbox, which I can then transfer back to my local machine post install, I am planning to completely remove windows. 

Does that make a difference with partitioning?

---

### Post by Bucky Ball on 2014-02-12
Apart from the 'shrink Win with Win software', not a lot.

You could let Ubuntu partition your disk 'Automagically' in that case, but you might not be happy with what it spits out. It generally uses the whole disk for / to install Ubuntu to, with a /home directory inside that, and leaves a small /swap partition at the end. 

I prefer to do 'Something Else' and in your situation would create:

/ = 20Gb;
/home = big as you can get it;
/swap = 2Gb or size of RAM if you hibernate.

As I say, the permutations are endless. These mountpoints are defaults in the partitioner, but you can name mountpoint whatever you like. You MUST have at least / though (best to have a /swap as well).

BTW: If you are getting rid of Win, then set the disk to UEFI, Legacy, whatever you like. Ubuntu will install in either.

---

