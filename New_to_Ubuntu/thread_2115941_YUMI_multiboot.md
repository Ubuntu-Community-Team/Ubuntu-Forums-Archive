---
title: "YUMI multiboot"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by tone640 on 2013-02-14
I am trying to create a multiboot USB drive with YUMI, but am stuck with it.

I have a 32GB flash drive to which I added various ISOs with YUMI.  It is formatted as FAT32, I am running YUMI in Windows 7, and have been told each time that I have successfully added an ISO.  

After this didn't work, I tried to add only Ubuntu 12.10 and Windows 7 on their own, to no avail.  The ISOs I am using work when I use UltraISO to create a bootable USB, but I cannot get YUMI to work at all.  All I get is a flashing underscore after selecting to boot from my flash drive. :confused:

Thanks in advance for any advice you can offer.

---

### Post by oldfred on 2013-02-14
Welcome to the forums.

Do not know about yummi.

But I know grub2. And since I one of those who is like the person with only a hammer and then thinks everything is a nail, I use grub2 to boot everything. Grub2 will not directly boot Windows installer, but I do have it booting my Windows repair flash drive and on that same drive I created another partition to boot other ISOs from grub.

       MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Label partition & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb

---

### Post by schragge on 2013-02-14
Never tried to make a multiboot USB with Ubuntu and Windows 7, but some months ago I successfully built a multiboot USB with half a dozen small Linux distributions like Puppy, Clonezilla Live and SystemRescueCD using YUMI.

There are other options on [their website]("http://www.pendrivelinux.com") like XBOOT and SARDU. Have you tried them? [UNetbootin]("http://unetbootin.sourceforge.net/")?

---

