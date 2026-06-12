---
title: "ophcrack and qemu in windows"
date: 2007-04-05
forum: Other OS Talk
---

### Post by iammeagain on 2007-04-05
Ok, so my plan was to have as many ways to access slax as possible. I wanted it on bootable CD, a bootable flash drive, windows installer, etc. Just in case. Well one plan of mine was to run it through qemu off a flash drive or cd also. 

My problem is i don't know how to get to my hard drive for it to be able to read from it. I figure i need to mount it and all but first i need to know if it is hda or sdb, what the heck it is. I tried using "sudo fdisk -l" but it gives me nothing at all. Here are the basic steps i took to get as far as i did:

[SIZE="1"]it is from a guide at [http://www.pendrivelinux.com/2007/03/09/use-qemu-to-boot-linux-from-windows/]("http://www.pendrivelinux.com/2007/03/09/use-qemu-to-boot-linux-from-windows/")
[/SIZE]
   1. Download Qemu
   2. Extract Qemu to your portable flash drive
   3. Download your favorite Linux CD Image
   4. Rename your linux CD image Example: SLAX.iso to linux.iso and copy it to the Qemu directory on the flash drive
   5. Download the StartLinux.zip file
   6. Open the StartLinux.zip and extract the contained StartLinux.bat file to the Qemu directory on the flash drive
   7. Double click the StartLinux.bat file to boot linux directly from the portable flash device

Now i don't can't get the dumb drive mounted.

Any help would be awesome. Thanx

Also does anyone have an idea for just taking your home copy of Ubuntu and being able to turn it into an iso and make it bootable to put onto a dvd or flash drive allowing it to be a decent size. One idea is installing it to the flash drive and seeing if that works, has anyone tried that?

---

