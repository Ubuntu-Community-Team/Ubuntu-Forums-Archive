---
title: "boot up"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by openation1 on 2012-01-28
Hello, well I bought an external usb hard drive 1.0 tb for my desktop and I would like to install ubuntu 11.10 (64) on the external hard drive. so I can boot up from any of the hard drives. in one hard drive I am running 32 bit and in  the external I would like to run 64 bit. how can I do that ? any help will be gladly appreciated. thank you

---

### Post by grahammechanical on 2012-01-28
Here is a link:

[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

The first thing you should do is create a live CD/USB and boot from it and run the try Ubuntu option. Find out if it sees the external drive.

Any install of Ubuntu will put the Grub boot loader in the MBR of the hard disk. The boot loader of the last Ubuntu installed will become the main boot loader. In your case this will be on an external drive. If you disconnect that drive then you will not be able to boot into the Ubuntu on the internal hard disk.

So, after installing Ubuntu on to the external drive boot into Ubuntu on the internal drive and in a terminal run

```
sudo update-grub.
```

This will make the boot loader of the Ubuntu on the internal drive the main boot loader. In this way you will still be able to boot into the internal hard disk even if the external hard disk is disconnected.

Regards.

---

### Post by oldfred on 2012-01-28
You will need to do manual install, so you get the choice of which MBR to install the grub2 boot loader. You want to make sure you install to the external drive's MBR.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Double.J on 2012-01-28
> **openation1 said:**
> Hello, well I bought an external usb hard drive 1.0 tb for my desktop and I would like to install ubuntu 11.10 (64) on the external hard drive. so I can boot up from any of the hard drives. in one hard drive I am running 32 bit and in  the external I would like to run 64 bit. how can I do that ? any help will be gladly appreciated. thank you

Hi there! First, as grahammechanical says, check that you can boot off of USB, I suspect you probably can, but just check anyway ;) (if you can boot a usb stick you can boot a HDD)

Second one issue I've had with this, is that ubiquity (the ubuntu installer) may crash when installing the bootloader at the end of the install. If this happens - don't worry the install is fine, the bootloader just needs reinstalling :)

Another thing to consider is which distro you want in charge of the boot process? if you already have ubuntu installed, then Grub is your PC's bootloader. Grub is controlled from the OS that installs it. I would recommend having the internal Ubuntu managing the boot process - just makes it a bit simpler down the road :)

During the install, if you choose "something else" where it's asking about disk usage, you are able to choose where to install the bootloader - I'd recommend installing it to the EXTERNAL not internal HDD. This also makes the external HDD bootable - if something goes wrong with the internal set up, you can boot the external by selecting it in the bios boot order. It also means that if you change your mind and clear the drive for storage again, you internal is unchanged.

You could keep choosing between the drives in the bios... but this is annoying, so I'd recommend booting the internal ubuntu and running sudo update-grub as recommended by grahammechanical so that the internal ubuntu's grub can boot the external :)

AS for fixing the boot loader if the installer crashes near the end, boot up the live CD again, and use this guide to install the bootloader. Choose the advanced mode to make sure you don't install the bootloader to the internal drive... unless you want to :)

Another thing to consider may be where you want to put it on the disk - if you are also booting windows, and would like to use a chunk of the drive for NTFS, this partition should go as the first partition on the drive so windows systems can see it. If not, put your OS first

THat's about it really - you may want to set up a new shared /home partition so that both OS can use the same documents and pics etc - if you do this it is usually best practice not to use the same user name for both distros... I'd just add 64 to the end of mine!

All the best, hope it helps! :)

---

