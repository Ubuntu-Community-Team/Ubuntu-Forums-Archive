---
title: "Stuck at this spot in installing 13.10 on drives trying to do windows8 duel boot"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by Bushcraft Bill on 2013-11-05
I had to go to 13.10 as 12.04 would just lock up...

I am trying to install ubuntu 13.10 but have hit a roadblock as I do not know what to do with the setup I have 2 1tb drives I have the second one that I want to install ubuntu on but it is giving me so many choices I just do not have a clue on what to use for device and then it also asks me device for boat loader installation I have no idea what to use can someone help figure this out for me so I can continue with my install.. I am attaching screen shots 1 and 2 are the same just with 2 showing the rest of what 1 shows and 3 is were the other problem is that I dont know what to do with ether....
[ATTACH=CONFIG]247592[/ATTACH][ATTACH=CONFIG]247593[/ATTACH][ATTACH=CONFIG]247594[/ATTACH]

---

### Post by Bushcraft Bill on 2013-11-05
Is the first part where ubuntu will be installed and in the 3rd pic is that supposed to be the where windows 8 is installed and that is were it wants to put the boot loader? 
if this is correct then it takes a while for things to sink into my gray matter......
just want to make sure before I hit the install now button...

---

### Post by grahammechanical on 2013-11-05
It is wise to take your time. Installing Ubuntu is scary this way. In Linux nearly everything is called a device. So, when the installer ask you to select a device to install the boot loader on it is asking which hard disk. Here you have to be careful. If you install the bootloader (called Grub) onto the hard disk the Windows is on then it may mess up the loading of Windows.

So, here we go, in Linux sd = Sata Disk. sda = sata disk a, the first hard disk. sdb = sata disk b, the second hard disk. So, /dev/sda is the first hard disk and /dev/sdb would be the second hard disk. Which does not show in your picture but it will be there further down the list.

Partitions are also devices. So, sda1 through to sda5 are partitions 1 to 5 on the first hard disk. I can see from the picture that the second has at least one partition - sdb1. Now you made the right choice to install Ubuntu on sdb1 but the wrong choice (in my opinion) to install the Grub boot loader on sda for that is the disk with Windows on.

So, change the device to install the boot load on to sdb. Then when it comes to booting you can use the UEFI boot system to select which hard disk to boot from. If you select the Ubuntu one it should also give you a boot menu with Windows on it.

The next thing to understand it that you select the partition to install Ubuntu on as you have done (sdb1) but you the click Change. That will bring up a small dialog box with options. You will see a panel called Use As. It has a drop down menu. We usually choose Ext4 as that is a Linux file system.

Then we tick Format. Then we select a mount point. we select / from the drop down menu. That is what the installer is saying that you have not done in that third picture. We OK that and double check that we are not installing the boot loader into sda but onto sdb and we can then click Install now.

I have two hard drives and I make different installs of Ubuntu and this is what I do. But I do not have the complications of having Windows or a UEFI boot system. I have a BIOS boot system.

You might want to think about having a 20 - 25GB partition for Ubuntu and a second, larger partition for your data. You can give that a mount point of /home. It will need to be formatted - Ext4 will also do. Then if you need to re-install Ubuntu you can install ubuntu into the 20GB partition and format and also give the second, larger partition a mount point of /home but you do NOT format. In this way you will not overwrite your data and documents. And the reinstalled Ubuntu will pick up the same user settings as you already had.

Regards.

---

### Post by Bushcraft Bill on 2013-11-05
Thank you I will read that a few times and digest it all before going any further that was very informative and to the point..

---

### Post by Bushcraft Bill on 2013-11-05
OK I installed ubuntu to the 2nd drive and also put the installed the boot load on to sdb

So I have no idea on how to get the 2nd drive to boot ubuntu?

---

### Post by newb85 on 2013-11-05
You will have to make your system BIOS boot the second HDD, rather than the first.  Unfortunately, the function key to access the BIOS or select boot options on boot up is not the same across all manufacturers.  When you first turn your machine on (from fully powered down), the first screen you see should give you that information.  (I've had to boot up multiple times to read all the options before...)

Edit: oh, wait, if you already installed Ubuntu on the HDD, you probably know how to access the boot options already.  ;)

---

### Post by Bushcraft Bill on 2013-11-05
yes I just went in and their is no way to make it boot from the 2nd drive that I can see ](*,)

or can I change the drive names from like A to G and G to A would that work?

---

### Post by Bushcraft Bill on 2013-11-05
I put the boot load on to sdb drive along with Ubuntu but I have no way of getting the second drive to boot into ubuntu is it as easy as changing drive names from a to h and h to a ?

their is no drive specified in the bios so I cant pick drive 1 or 2 ether?

---

### Post by newb85 on 2013-11-05
Perhaps it would help if you gave some details on your hardware arrangement.  Are both of these HDDs internal?  Is this a destop, or a laptop?

---

### Post by Bushcraft Bill on 2013-11-05
Laptop is hp envy 17-j083ca with 2 internal 1tb drives pre installed windows8 drive 1 all windows drive 2 all ubuntu but cant get to it...

---

### Post by newb85 on 2013-11-06
I suppose it's possible HP set up your machine such that it's not possible to not from the second hard drive. In that case, you'll have to put Grub on the first hard drive.

---

### Post by oldfred on 2013-11-06
Did you install Ubuntu in BIOS mode or UEFI mode?
This shows boot screen of installer for both BIOS (purple) and UEFI (grub menu).
Then it may be video driver issue.

With two drives you need to make sure second drive is gpt partitioned. Ubuntu will boot with BIOS or UEFI from gpt partitioned drive, Windows will only boot from gpt partitioned drive with UEFI, but drive with MBR will only boot with BIOS/CSM mode.

I also suggest an efi partition on the second drive, so it could be fully bootable without first drive even if you install grub to efi partition on Windows drive. 

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Some now older examples of two drive installs in the link in my signature and lots of links to UEFI info.

---

