---
title: "Howto copy encrypted /home partition to another encrypted partition"
date: 2006-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by zetetic on 2006-11-19
Hi
I'm only using Linux, for the first time in my life, since less than one mounth, so please correct any mistakes don't be too much critical if there's something wrong with this "Howto".
Excuse my poor english (it's not my native language).

The situation is this:

Suppose you have a LUKS encypted home partition, mounted on /home, on a pata drive.
You want to install Ubuntu (or another version of Ubuntu) on another drive (v.g. a sata drive). You want to encrypt the home partition on the sata drive and "clone" the contents of the home partion you have on pata drive.

Solution:

1 - Make a new installation of Ubuntu on another drive, with encrypted /home partition (with LUKS).

2 - Give your username the same name you have on the old installation. If, for instance, your username, in the old Ubuntu installation, is "mike", then use "mike" as your username on the new Ubuntu installation as well.

3 - Boot from Ubtuntu live CD or from Gnoppix.

4 - Open terminal and type:
$ sudo aptitude update
$ sudo aptitude install cryptsetup hashalot initramfs-tools

5 - Open and mount your source encrypted home partition (hda3 in this example):
$ sudo cryptsetup luksOpen /dev/hda3 cryptosourcehome
$ sudo mkdir /mnt/sourcehome
$ sudo mount /dev/mapper/cryptosourcehome /mnt/sourcehome

6 - Open and mount your new (destination) encrypted home partition (sda3 in this example):
$ sudo cryptsetup luksOpen /dev/sda3 cryptodesthome
$ sudo mkdir /mnt/desthome
$ sudo mount /dev/mapper/cryptodesthome /mnt/desthome

7 - Copy files over (a regular copy (cp) may not do the job completely, cause the “/home” directory could have hardlinks, softlinks, files and nested directories):
$ cd /mnt/sourcehome
$ find . -depth -print0 | sudo cpio --null --sparse -pvd /mnt/desthome/

8 - Unmount and close your LUKS encrypted /home partitions:
$ sudo umount /mnt/desthome
$ sudo cryptsetup luksClose cryptodesthome
$ sudo umount /mnt/sourcehome
$ sudo cryptsetup luksClose cryptosourcehome

Offcourse you can also use this "Howto" to put a backup copy of your encrypted /home partition on another encrypted LUKS partition! And if you place the backup LUKS encrypted partition on another drive, then if something bad happens to your /home partion, you just need to restore it from the backup!

And with this method all your /home files never hit a non-encrypted partition (which would be very unsafe).

regards,
zetetic

---

