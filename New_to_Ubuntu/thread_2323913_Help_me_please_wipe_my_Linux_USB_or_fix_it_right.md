---
title: "Help me please wipe my Linux USB or fix it right"
date: 2016-05-09
forum: New to Ubuntu
---

### Post by Brad_Agera on 2016-05-09
I want to apologize in advance for how lengthy this is. I am running Ubuntu 14.04 that I installed directly onto a 32GB Toshiba flash drive. So it boots when I turn on my PC with F12. I partitioned it and gave Ubuntu 7GB of space for itself and the rest is FAT storage. Now this is the funky part. I installed it from a trial version off another 4GB USB, so both need to be plugged in for Linux to run. This whole set-up is more hassle then it is worth, so I want to erase my drives and start again later. My issue is that my Toshiba drive (this is the main one I am worried about) does not show up when I boot Windows. I was told that this is because it is now a non-Windows readable file, its now a Linux Hard Drive. So I go into the Boot Loader and open my Toshiba drive to boot Linux and go into Disks to reformat it with zero partitions and all FAT32 storage. So I click either do or do not overwrite files with 0's (same message comes up either way) and Empty with no partitions. I enter my password to Authenticate. When I do I get this message. 

Error Mounting Filesystem

Error unmounting /dev/sdc1: Command-line `umount  "/dev/sdc1"' exited with non-zero exit status 1: umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
 (udisks-error-quark, 14)

[ATTACH=CONFIG]268954[/ATTACH]

I started using Ubuntu on Friday and installed it to my USB last night. I didn't know that my extra 24GB NFTS partition would not show up as regular flash storage. So that is my issue. If someone could help me format it so the 24GB shows up as flash storage in Windows, Mac, and Linux that would be awesome. If that is not possible, how do I wipe the drive. Any help would be great!

---

### Post by Impavidus on 2016-05-09
So, if I understand it correctly, your computer has one internal drive, which is a 320GB Toshiba drive with Windows, and you didn't do anything to that and have no problems with that. So we won't be talking about that. Next there is a 32GB Toshiba usb drive, which you divided into 2 partitions. There is a 7.5GB ext4 partition with an Ubuntu installation and a 24.5GB NTFS partition. Or was it FAT? You also have a 4GB usb drive you use as a live usb (trial version), which you used to install Ubuntu.

I read that Windows may have trouble reading partitions on a usb drive other than the first partition. As the first partition on your 32GB usb drive is a Linux partition, Windows has trouble with that one too and therefore cannot access the 32GB drive at all. So that's why you don't see it in Windows. There is in Windows a utility for partitioning and formatting drives, which should be able to format this usb drive. The Linux utility in your Ubuntu system on the 32GB drive cannot format the drive, as it is the drive on which it is installed. The system cannot wipe itself. The disks utility on the 4GB Ubuntu live usb should be able to format the 32GB usb drive.

There should be no need to keep the live usb plugged in when booting the Ubuntu installed in the 32GB drive. Once installed, you only need the live disk to fix problems.

You may get access to the NTFS partition on the 32GB usb drive with Ubuntu if you make the NTFS partition the first partition, and put Ubuntu after that. I never tried that though, as I don't use Windows. I think that Mac by default can't access NTFS partitions (or that used to be the case), but that can be fixed. Else, FAT is understood by all systems. 7GB is rather small for a complete Ubuntu system.

I suggest you boot from the live usb and reinstall Ubuntu on the 32GB drive. Use manual partitioning, create a 16GB NTFS partition at the start of the drive and a 16 GB ext4 partition at the end. You may want a small swap partition, but I don't think you're going to use that. A swap partition allows for more graceful crashes in the unlikely event when you run out of memory, as the system will slow down before you see programs killed. To be really sure the installer won't put a boot loader on the internal drive, you can temporarily disconnect it.

---

### Post by Brad_Agera on 2016-05-09
That sounds exactly perfect. So then once I insert the USB the flash storage will be able to load since it is the first partition and the Ubuntu second partition won't even be visible. Is that what you are saying Impavidus? And furthermore, how do I set up partition 1 to be NTFS and then 2 become Ubuntu?

---

### Post by sudodus on 2016-05-09
I agree with *Impavidus*.

I know that Windows will be able to use the first partition on a USB drive, if it has a FAT32 or NTFS file system. In order to make it easy to access it also from MacOS, you should use FAT32, but you can add software in MacOS to read NTFS.

Linux has no problems reading, writing and booting from 'any' partition number. It is a good idea to install Ubuntu into the second partition (with an ext4 file system). You can use the description in the following link, but with the exception, that you make a first partition for file storage and transfer before creating the partition(s) for Ubuntu.

It is a good idea to share the drive space with 16 GB for file storage and 16 GB for the Ubuntu system.

If you want the drive to have a bootable system, that survives, there are a few things to consider:

- Do you want the pendrive to boot in UEFI mode, BIOS mode or both modes?

- Do you intend to boot the pendrive in one computer or in many computers?

- Should it work in computers with 32-bit or 64-bit hardware or both?

-o-

***Edit:*** Use ***gparted*** in the live Ubuntu system to edit the partition table.

In the Ubuntu installer, at the partitioning window, you should select ***Something else*** and select partitions manually.

---

### Post by Brad_Agera on 2016-05-09
Thanks *sudodus*. I honestly know almost zero about what you just asked. I have no clue about boot modes, and I know about 32 vs. 64 bit, but I think (with my minute knowledge) that it may be best to boot off both. And yes and want it to run off multiple computers. Being in school, that would make my life easier. I just need help with those partitions. Can I move them around, and if I must re-install how do I set the partitions so 1 is FAT32 (because we also have Macs, and I love Mac but too poor to afford it lol) and partition 2 become Ubuntu?

---

### Post by sudodus on 2016-05-09
I have made a system, that boots in UEFI and BIOS mode. See the following link. You can make something similar (but with a first partition for data).

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

If you find it too hard to make it yourself, there is another system, that already has that kind of first partition (with NTFS). It is not an installed system, but a persistent live system. See this link: [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

-o-

General description with links: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by Brad_Agera on 2016-05-09
Would you suggest using the installation tool in Ubuntu? Or a third party app?

---

### Post by sudodus on 2016-05-09
If you make your own installed system, I suggest that you create partitions with gparted, and after that install Ubuntu with its own installation tool (the icon on the desktop of the live system (it has the name ubiquity under the hood)).

If you make a persistent live system, I suggest that you use mkusb to create it.

---

### Post by Brad_Agera on 2016-05-09
Yeah, I want a live and persistent USB. Then all I need to do is plug in the USB and boot it up and it will be just as I left it.

---

### Post by sudodus on 2016-05-09
Then you can install mkusb into your current live system (it will only survive until reboot, but that is enough for it to create your persistent live system).

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

and you need the iso file available from the live system in a mounted partition of the internal drive or in a third external drive, where the first one is the live system (in your 4 GB pendrive) and the second one is your target drive, your 32 GB pendrive.

---

### Post by Brad_Agera on 2016-05-09
Woah. That sounds so confusing. I feel retarted asking but can you dumb that down to Below Basic with some step by step instructions...

---

### Post by sudodus on 2016-05-09
Let us do it stepwise :-)

1. Boot into your live Ubuntu system in the 4 GB pendrive.

2. Install mkusb in the live system.

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

3. Test that you can start mkusb.

You may want to read the quick start manual alongside the mkusb web page.

[mkUSB-quick-start-manual.pdf](http://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual.pdf)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

When you can run mkusb in your live system, we take the next step.

---

