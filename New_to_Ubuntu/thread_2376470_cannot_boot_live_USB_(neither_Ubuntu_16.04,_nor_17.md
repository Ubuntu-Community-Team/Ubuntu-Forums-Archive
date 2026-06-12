---
title: "cannot boot live USB (neither Ubuntu 16.04, nor 17.10)"
date: 2017-11-02
forum: New to Ubuntu
---

### Post by kujucuk on 2017-11-02
I have several problems. I'll tell the whole story.
I bought a new computer and created two partitions: One is Windows 10, the other Ubuntu 17. Ubuntu is a logical partition even though I didn't create a swap partition.
Problem 1: Whenever I access my Ubuntu partition from my Windows partition, the Ubuntu partition gets corrupted or something because I cannot boot it properly again. That's why I chose my Ubuntu partition's file system as XFS, so that I would not accidentally access its files from my Windows partition and corrupt it again.
Problem 2: I couldn't resize my Ubuntu partition. I've tried GParted from a live USB, I could shrink my Windows partition but not Ubuntu. Then, I got frustrated and tried doing it from my Windows partition, which unfortunately corrupted my Ubuntu partition again (Even though, I couldn't see my files from Windows, viewing my partitions via a partition manager was enough to corrupt it.).
Problem 3: To salvage my files, I used my old Ubuntu 17.04 disk image to create a live USB and access my files using that. Fortunately, I could see all my files; but when I tried to copy those files to my external Solid State Drive, it couldn't mount it because its file system was exFAT. I tried installing the necessary packages to mount it (which I don't know if you can do it on a live drive) but there was a problem.
Problem 4: I saw that there were changes to 17.10 so I tried creating a live USB of that instead. I could select it from the boot menu, but it soon froze and I had to force shut my computer. I tried the same with 16.04 created with both Rufus and Unetbootin with the same result. So even if I decide to forgo my data, I'm unable to install Ubuntu again!
What I want now is to boot Ubuntu from a live USB and mount my external Solid State Drive, which has exFAT file system, to copy my data to it; and then install Ubuntu again, this time taking care that I don't access my partitions while on Windows.
I'm also seeking a long term solution to my Problem 1 and would be pleased if you could tell me where I can get more support for that (my computer manufacturer?).
I'm a computer newbie, so please bare that in mind when answering :) Thank you.

---

### Post by yancek on 2017-11-02
Which version of windows, 10?
What software are you using to read/access the Ubuntu partition from windows since a default windows install is not capable of doing this?
Are you sure Ubuntu is on a logical partition?  If you do have windows 8/10 it will be using UEFI/GPT and there will be no logical partitions.
You can't modify partitions with Grub as it is only a bootloader.  Are you using GParted to do this?
If you want to shrink a windows partition for some reason, best to do that from windows if possible.
Viewing files from a partition manager will not corrupt your filesystem, some action will have to have been taken.
You can install packages on a live system if you have enough RAM and do NOT reboot as no changes are saved on reboot.
No idea why your usb freezes after booting, have you verified with an md5 checksum and/or tested the usb on another computer to see if it boots?

---

### Post by kujucuk on 2017-11-03
Yes, it is Windows 10 (edited)
I remember being able to read (and write) the files on my Linux partition on my old computer with Windows 7 if I'm correct. But yes, Windows 10 seems incapable of that. The first time I installed Ubuntu it had the usual Ext file system I believe, so I installed the program Ext2Fsd on my Windows partition, which I avoid using now (Back then, I had even made it start on boot!). But the problem is even worse, because even using a partition manager on my Windows partition is able to corrupt the Linux partitions.
All the partition managers show Ubuntu as a single logical partition in an extended partition, which is usually expected because it also contains the swap partition but in my case I didn't create a swap partition on installation because I thought my RAM was large enough. But I think you're onto something here because I remember being unable to properly boot the Windows 10 installation disk (It froze on boot, if I remember correctly, similar to Ubuntu now.) when I selected UEFI on BIOS (I have three options on my new computer: UEFI with CSM, Legacy, UEFI. Only Legacy worked so I've been using that since.). Was this actually a major problem that I didn't realize? Should I contact my computer manufacturer for this?
Sorry for the confusion. Yes, it is indeed GParted with GUI; I don't know why I typed GRUB there :D (edited)
I don't know if this is an important tip and I wasn't trying to shrink Windows. But since I can't shrink a mounted partition, are you suggesting that I create a new partition by shrinking another partition and install Windows there, just so I can shrink my old Windows partition? Because that seems to be the only option to me. This seems to be a minor point, but I still wanted to express my confusion :D
I'm of the same opinion that just reading my files from a different partition or using a partition manager to view my partitions shouldn't be able to corrupt some other partitions, but my Linux partitions get corrupted right after I take those actions and I'm similarly clueless as to why this is happening to me :(
Thanks for the info. Yes, I believe I have more than enough RAM (2x8GB=16GB, I believe.) as I've mentioned. Also, isn't there an option to dedicate some of the memory of the live drive to persistent storage? That would be cool, because I could just take my USB with me wherever I go and plug it into a computer to use it as if it were my own :) That would also mean that I could use Linux almost anywhere (Although my school's computer lab have restricted BIOS' :(). But back to the point, can I get the necessary packages to mount my exFAT SSD while on my live drive? It would be cool if you could point me to the instructions on how to do so :)
I don't know how to do a checksum but I downloaded two different disk images and created a live drive using two different software so there shouldn't be a problem with either. (...) I've just tested my live drive on another computer upon your suggestion and it worked, so there is a serious problem with my new computer I guess. Again, should I contact my computer manufacturer? Is this related to my legacy boot mode choice? If there is a deep problem with my computer, how can I rescue my data before doing a long term fix that may require re-installation?
By the way, thank you so much; now I'm not as hopeless as before :)

---

### Post by yancek on 2017-11-09
If you want to modify (shrink, enlarge) a windows partition, do it from windows or with windows software.
If you want to modify (shrink, enlarge) a Linux partition, you need to do it from a system which is not mounted which would mean using a 'Live' system on a DVD or flash drive.

If you can boot your installed Ubuntu or Ubuntu on a Live DVD or flash drive, do that and run the following commands to get info to post here.

```
sudo fdisk -l
sudo parted -l
```

Lower Case Letter L in the command.
To access an xfat filesyste from Ubuntu, I believe you need to install the following:

> sudo apt-get install exfat-utils exfat-fuse

You can do that with your Ubuntu flash drive and use it but you cannot reboot before using it as any changes is lost on reboot from a 'Live' system.

It really isn't a good idea to access a windows 'system' partition from Linux or a Linux 'system' partition from windows.  I've never done the latter as I'm not sure there is any software that really works well for that.  If you want to access a separate 'data' partition from both windows/Linux, create an ntfs filesystem on the data partition.  " Ext2Fsd" is windows software that is supposed to access Linux from windows, don't know if it is current or if it works with newer systems, I've never used it myself.

If you are using UEFI for windows and/or Ubuntu, you should be using GPT partitioning as windows won't do GPT without EFI.  If one system is EFI, they should both be EFI or booting is complicated.  If you are using GPT, there will be no Extended or Logical partitions as all partitions (up to 128) will be primary.

If you can boot windows 10, you should be able to use it's Disk Management tool to resize (shrink) it's partitions even while using it.  Did it myself with windows 10 recently.

You can create a persistent Live USB in several different ways with Ubuntu.  The easiest I have found is with mkusb, see the link below.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Doing an md5 checksum is explained in detail at the link below.  Basically, open a terminal and change to the directory in which the iso file resides and run:

md5sum Ubuntu.iso  (need the exact name of the Ubuntu.iso download, it's case sensitive)

---

### Post by kujucuk on 2017-11-09
Thanks for the good tips but my problem now is that I cannot boot from my Ubuntu USB. My goal is rescue my data on the corrupted Ubuntu partition. Since the partition has XFS file system, I cannot do this from Windows. I aim to boot a live Linux USB to read my old data, connect my SSD, and copy my data to the SSD, which has exFAT file system so I need the packages for that.
I turn on my computer. Press F11 to bring up the boot menu. Select my USB from the menu. Then I get the screen in the image titled IMG_0918.JPG in the following link: [https://mega.nz/#F!NfgBEJiT!-eNEuFh9PMGRkr69bVenOQ](https://mega.nz/#F!NfgBEJiT!-eNEuFh9PMGRkr69bVenOQ) This screen shows up only for a second. Then I get the screen in the image IMG_0915.JPG in the same link. Then the Ubuntu logo and loading screen shows up and freezes like in the image IMG_0917.JPG after which I have to force shut my computer.
This happens for both Ubuntu 16.04 and 17.10. It happens both when I create the USB with Rufus and with UNetbootin. But the same USB works on my old computer.
I used to be able to boot the Ubuntu 17.04 disk image, but unfortunately I couldn't download the packages for exFAT (The Terminal gave an error like the package didn't exist.) and so I downloaded the new version (Ubuntu 17.10) and deleted the old one. And now I cannot even boot Ubuntu from my USB. Should I try to find an old version like 17.04 and try that?

---

### Post by yancek on 2017-11-09
One of your images indicates a need to update firmware, I'm not sure how you would do that with your specific hardware?

Do you have multiple options in the BIOS to select the usb, one for UEFI and one for Legacy?  If it boots on another computer then the iso download and copy should be good.  I'd explore the BIOS for different boot options, can't think of anything else to try.

---

### Post by kujucuk on 2017-11-11
There aren't options when booting from the USB, but there are general options in the BIOS namely Legacy, UEFI, and UEFI with CSM. I've tried all and they freeze similarly.
I was able to rescue my data by booting from a Debian live USB, though. I've copied all my data and formatted my computer, so I'm good now. I still cannot use Ubuntu, though, but since this is my thread, I will mark it as solved. Thank you for your help.

---

