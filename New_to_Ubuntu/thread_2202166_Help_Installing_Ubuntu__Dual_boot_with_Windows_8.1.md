---
title: "Help Installing Ubuntu / Dual boot with Windows 8.1!"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by Oliver_Chaplin on 2014-01-27
Hey There

I was wondering if I could get some help installing ubuntu from a USB drive so that it dual boots with Windows 8.1
I have three disks in disk management, as seen here:
[http://i.imgur.com/rlBSKvp.png](http://i.imgur.com/rlBSKvp.png)
I'm not exactly sure what Disk 1 is but its there for some reason.

I want to install ubuntu to Disk 2, and I want it to be able to dual boot with Windows 8.1

My bios is the UEFI type, and Disk 0 and Disk 1 are formated as GPT type disks, whereas Disk 2 is formated as MBR type.

When I open the ubuntu installer, it doesn't detect Windows, and it will only let me choose "Erase contents of disk", and "Something else"
When I choose something else, it will only let me install ubuntu to Disk 2 (called sdd in ubuntu), which is ok because I want to install it here.

The installer will let me install the bootloader to sda (which is Disk 0) and any partition on sdd (Disk 2)
but it wont let me choose what partition of sda (Disk 0) to install it to, only sda (Disk 0) itself.

Another point is that my computer has Intel Rapid Storage Technology.
Here is a pic of the setup:
[http://i.imgur.com/RrUECFW.png](http://i.imgur.com/RrUECFW.png)
Disk 0 is being accelerated, and Disk 1 is in a SATA array as you can see in the picture, with Disk 2 being the unaccelerated disk.

I have a few questions regarding how I should Install Ubuntu
[LIST=1]
[*]How would I partition Disk 2 to install Ubuntu alongside Windows
[*]Would it be possible to install multiple linux distributions to Disk 2, and if so how would I partition that?
[*]Where do I install the bootloader to? and how is would this work with multiple linux distributions
[*]How do I do all of this while still being able to boot Windows 8.1
[*]Is it possible to remove the linux distributions and restore the Windows boot loader?
[/LIST]

As you can tell I'm pretty inexperienced with this stuff, and I would greatly appreciate the help!
I have searched other forums but I can't find someone with the same situation as me!

Thanks :)

---

### Post by oldfred on 2014-01-27
If sdc, your third drive is MBR(msdos) formatted you will not be able to dual boot from grub menu. But can only dual boot by going into UEFI/BIOS and turning on BIOS/CSM/Legacy boot mode to boot from BIOS/MBR drive and selecting sdc drive. And then to boot Windows you have to go into UEFI and turn on UEFI mode to boot Windows. Some have one time boot keys and auto switch as long as secure boot is off.

Do you have a lot of data on sdc or can you reformat to gpt partitioning. Generally easier if all systems are UEFI or all are BIOS, but you can use it as it is if you want.

How you boot install media is how it installs, so you have to know if in UEFI mode or BIOS mode when booting. Your flash drive may show in UEFI menu twice, once as UEFI and once as something else, but it is not always clear.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
You still need to have secure boot off, and fast boot off to avoid dual boot issues in Windows. 

It is a bit more advanced but you can install every Linux install in a 10 to 25GB / (root) partition and then have all data in /mnt/data partition. Do not share /home with multiple installs as each install may change settings.
This can be done if UEFI or BIOS.

With BIOS boot, you install grub2's boot loader to the MBR. And if installing in sdc or third drive you will want it installed into the MBR of sdc. Then it does not change anything on Windows drive. Many suggest removing/disconnecting Windows drive so you do not make any mistakes, but  if careful using Something Else  or manual install, you can install with other drives connected. Do not use any auto install options. Also if in UEFI mode every system installs into a separate folder in the UEFI, somewhat like having many MBRs on one drive. But still better to have Ubuntu's efi partition on sdc if in UEFI mode.

With multiple drives and correct installation, you do not modify Windows at all, other than the settings like fast boot and secure boot.

Post this from terminal in live install flash drive and let us know if you want UEFI or BIOS installs on sdc.
sudo parted -l

Note that you are in Absolute Beginners, but a multi-drive, multi-install with both BIOS and UEFI is not just a quick simple install. I have lots of links to more info in signature on UEFI installs (may be too much but tries to cover lots of different cases). You may have to do some research to understand everything and we can help you when you get stuck.

Also what video card/chip? Often boot parameters need to fully boot.

---

### Post by Oliver_Chaplin on 2014-01-27
No I do not have much data on sdc at all, as a matter of fact it's practically empty. So if it is easier I will happily partition it again and make it GPT type.

I've been to the UEFI page before and when I boot the USB drive it comes up with that screenshot of the UEFI boot (grub looking thing) so I think it is booting in UEFI mode.

I know how to turn secure boot off, but how do I go about disabling fast boot?

If I were to install 3 linux distributions, how would I exactly partition sdc, as in how many partitions do I need separately for each OS, and how many can be shared, and the sizes for each partition?

I don't understand where you want me to enter that terminal command from exactly, but I will if it helps :)

Thank you so much for your help its made it a lot easier for me and it seems to make a bit of sense now :)

I have an Intel i7 3630QM quad core processor which has inbuilt Intel HD Graphics 4000.
I however also have a dedicated NVIDIA GeForce GT 650M which uses optimus (which never works properly) to enable and disable itself.
Not sure if thats what you needed but there is a little info I can give :)

---

### Post by oldfred on 2014-01-27
I would backup what data you have on sdc and convert to gpt.

        I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
If not familar with gparted.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

One advantage of gpt is that you only have one partition type, no primary, extended nor logical.

Some suggestions on partitioning. I would have efi, as many / (root) partitions of 25GB, at least one Linux ext4  data partition. Not sure if you have NTFS partition(s) on other drives for shared data, but if not then anther data partition with NTFS format. No /boot nor shared /home partitions due to possibility of conflicts. Info below is standard suggestion with /home, probably best not to have that if you have data partition(s).


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
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

   But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Oliver_Chaplin on 2014-01-27
Thanks for the information! It was really helpful :)

I will give it a try installing it now after sdc has been turned into a GPT disk.

Can multiple installations of linux share the same swap space?

So my proposed setup will be:

1. EFI System Partition (300MB) [FAT32 with /boot]

then for each separate install of Linux:

1. 30GB [ext4 with /]
2. 100GB [ext4 with /home]

then a shared 8GB swap space (if possible)

Do you think this setup will work? Also what is the difference between primary and logical partitions?
Also when should I create and format the partitions? Should I create unformated partitions for / and /home and then format each one when I install the individual linux distributions?

---

### Post by oldfred on 2014-01-28
The efi partition is not /boot, it is more like the MBR in BIOS installs and has efi boot files. But it does have boot flag which is just how parted or gparted set it as the ESP or efi partition. In gpt partitioning it uses very long GUIDs to actually define partition types, so boot flag actually assigns a GUID for efi.

A /boot has grub menu and Linux kernels and with most desktops does not need to be a separate partition.

You can share swap if you do not hibernate nor encrypt /home. Otherwise one system will overwrite the other. If you have lots of RAM like 8GB you only need 2GB of swap as you may never use it. And if dual booting best to not even think about hibernating. Ubuntu boots very quickly anyway.

In gpt there is only one partition type. 
With MBR partitioning from 30 years ago you can only have 4 primary partitions. They then modified it to allow you to convert one primary to an extended partition which is a container for as many logical partitions as you want. Windows only boots from primary partitions, but Linux will boot from logicals as well.

 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

