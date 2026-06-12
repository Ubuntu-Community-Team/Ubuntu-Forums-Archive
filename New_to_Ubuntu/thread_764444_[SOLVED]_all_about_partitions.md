---
title: "[SOLVED] all about partitions"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-04-23
i have been dual booting vista and ubuntu for about 4 months now

the way i did it was having vista installed first and i added another partition with the built in partitioner on vista

my problem is that my vista has completely stopped working, it wont even boot into recovery mode anymore

after about a week of trying to fix vista ive decided to just reformat and reinstall 
(also maybe while the its formated  i will try out some other distros)

so basically i wanted to know, if i delete my windows partition (and my windows backup partition) with gparted will it affect my ubuntu partition at all?

the reason i ask is because  my windows partition is the one thats marked boot, so i have been afraid to delete my windows partition because im not sure if grub is installed on the windows partition or ubuntu partition

also the only windows vista cd i have is the one that came with my computer (it says it only will work with my computer)
will this reformat the entire harddrive if i use it or will it only install to a selected partition?

also will i have to reinstall the grub bootloader after i finish installing vista agian?

also ive tried asking this question on various windows forums, but everyone on those forums seems so clueless 
(like what is ubuntu...duhh, what is grub.. ect)
so anyway you guys are my only hope

---

### Post by Tatty on 2008-04-23
If you delete the partition it shouldn't affect your ubuntu installation.  Reinstalling windows though could be a problem.  The most obvious problem is that it will wipe out grub, but this can be fixed easily if you follow this link:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Im not sure, however, if reinstalling windows will wipe out your ubuntu installation.  Windows does like to be the only OS on the block.  I tried to install windows on a machine with some linux partitions a few months ago and the installer would just fail without any error messages.  It took a fair bit of googling to find out that it does that if it sees linux partitions - removing them solved the problem.
Although i have read many posts on here of people who have sucessfully installed windows on a machine with ubuntu already installed.

So i would say your grub is easily fixable, but pay close attention to what windows is doing when you install.  And definately back up everything you cant loose beforehand from every partition.

---

### Post by martrn on 2008-04-23
> **tjwoosta said:**
> the reason i ask is because  my windows partition is the one thats marked boot, so i have been afraid to delete my windows partition because im not sure if grub is installed on the windows partition or ubuntu partition

[...]

also will i have to reinstall the grub bootloader after i finish installing vista agian?


From : Wikipedia 
[Master boot record]("http://en.wikipedia.org/wiki/Master_boot_record")
A Master Boot Record (MBR), or partition sector, is the 512-byte boot sector that is the first sector ("Sector 0") of a partitioned data storage device such as a hard disk.

A Volume Boot Record is a type of boot sector, stored in a disc volume on a hard disk, floppy disk, or similar data storage device, that contains code for booting programs usually, but not necessarily, operating systems stored in other parts of the volume. 

Grub is a bootloader and its a two stage process.  It will load the first stage from and the first stage will be on the Master Boot Record.  There is nothing stored by grub in the windows partition.  For grub to boot a windows partition it will chainload it.  Ie it will invoke (or rather cainload) the Volume Boot Record of the windows partition, using the data that windows put their.

I only mention it becuase you have an idear that grub is stored on a partition.  The main bulk of grub is stored is installed to the Master Boot Record (MBR) of the drive, with some data stored on the ubuntu partition.

---

### Post by tjwoosta on 2008-04-24
thanks guys, it all makes so much more sense to me now.

---

### Post by apostate on 2008-04-25
> **Tatty said:**
> If you delete the partition it shouldn't affect your ubuntu installation.  Reinstalling windows though could be a problem.  The most obvious problem is that it will wipe out grub, but this can be fixed easily if you follow this link:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Im not sure, however, if reinstalling windows will wipe out your ubuntu installation.  Windows does like to be the only OS on the block.  I tried to install windows on a machine with some linux partitions a few months ago and the installer would just fail without any error messages.  It took a fair bit of googling to find out that it does that if it sees linux partitions - removing them solved the problem.
Although i have read many posts on here of people who have sucessfully installed windows on a machine with ubuntu already installed.

So i would say your grub is easily fixable, but pay close attention to what windows is doing when you install.  And definately back up everything you cant loose beforehand from every partition.

Hi,

Not to sound dire but..YES your disc will very likely wipe out Ubuntu to reinstall Vista. YES, it will bork GRUB in any event. I promise. And if you decide to play with other distros and such, it isn't Linux you need to worry about booting, but Windows. The Windows bootloader is stoopid.  It doesn't know what partition is what, and doesn't care-- it just counts forward a certain number of Win partitions and then goes...BOOT! So if you used to have a Recovery partition first, then Windows second, then Linux third, and you wipe out the recovery partition and use it...so you have Linux, Windows, Linux....the Windows bootloader will count forward to the second Windows partition and BOOT! -And it will fail because that isn't Vista anymore. oops.

Once the Win bootloader moves in, it is unwise to disturb its tranquility. So pick what you want where, and install Windows first, Linux(es) second and third. In your situation, if you can't fix Vista and need to use the dread OEM disc, you may just count on reinstalling Ubuntu and plan accordingly. Hopefully you have a seperate /home partition? This reduces the pain somewhat. A full version of Vista with a real installer would also help you to preserve your Linux partitions, and then you could use Super GRUB to fix your bootloader as Windows will squat on the MBR every time you  fix or reinstall it.

Hope this helps, somehow...

---

