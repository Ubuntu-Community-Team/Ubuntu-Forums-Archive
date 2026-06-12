---
title: "Need Help Moving GRUB On Triple-Boot System"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by Stephen Wayne Hamilton on 2012-12-07
My sistuation is that i've installed Win8 x64, WinServer2012 x64 and Ubuntu 12.10 x64. However, I would like to use the TrueCrypt system drive (C:\) encryption for 8 and Server. But it installs its' own bootloader to the MBR, and it's not compatible with a system that has Linux on it. It requires that the MBR contain only the Windows bootloader, and refuses to install otherwise. When I installed Ubuntu I used all default options and GRUB installed to the MBR. What I want to do now is move GRUB to somewhere else, then restore the default Windows bootloader, so that I can boot either of the Windows installs from their shared loader while still being able to use TC, and also still be able to boot Linux from GRUB. i read an article by a user here on the Ubuntu forums that had a similar situation. but i've also read other articles with varying advice and methods. So now i'm a bit confused on how to proceed.

So, how can i accomplish this? should i move GRUB to its' own partition, to the same partition that linux is installed on, or what?

Thanks!

EDIT: here are the results of my sudo fdisk -l command for anyone who cares to see it:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000dd4b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848  1304152441   651716797    7  HPFS/NTFS/exFAT
/dev/sda3      1362745344  1465143295    51198976    7  HPFS/NTFS/exFAT
/dev/sda4      1304154110  1362745343    29295617    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1304154112  1329287167    12566528   83  Linux
/dev/sda6      1329289216  1362745343    16728064   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 17.1 GB, 17129537536 bytes
255 heads, 63 sectors/track, 2082 cylinders, total 33456128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x09988a25

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8033568

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953523119   976760536    7  HPFS/NTFS/exFAT


Which of these partitions should GRUB be moved to? I'm thinking that SDA4 or SDA5 would be the correct partition to move it to but i'm not sure. SDA6 could also be a valid choice for all i know, despite it being listed as SWAP, so i would think not. I want to make sure to get this right the first time around or else i may end up with 3 OSes that wont boot at all, and another reinstall is the last thing i'd want to do.

---

### Post by Stephen Wayne Hamilton on 2012-12-07
bump

---

### Post by audiomick on 2012-12-07
Hallo.

Firstly, it's a bit early for a bump. Forum  etiquette is to wait a day or so. Remember that it is all volunteers here, and you have to wait for someone to happen on to your thread who can help you.

So, to your problem. I haven't used Truecrypt, but a quick glance here
[http://en.wikipedia.org/wiki/Truecrypt]("http://en.wikipedia.org/wiki/Truecrypt")

suggests that it should not be giving you any grief with grub. It is also Linux compatible, apparently, so I don't think using it can be relevant to your grub problem. This is, however, only my best guess. I don't know that for sure.

Windows does always overwrite the MBR when you install it. This is not related to Truecrypt. The easiest way to deal with this behaviour is simply to install all your windows installations first, then install your Linux. Grub will then be written to the MBR, and will take into account the windows installs and include them in its bootload process. Or at least it should....

If you have a Linux install that you want to keep, and need to install Windows after that, you need to replace Grub after the windows install.
Here are a couple of  pages with info on that
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

To your specific question of "where to put grub", I don't know of any reason not to let it install itself to the MBR of sda, i.e. just let it install itself where it wants to go.

---

### Post by Stephen Wayne Hamilton on 2012-12-07
@audiomick: the simple fact that you haven't even used Ubuntu means, to me, that you don't know how to help. just trust me, TrueCrypt DOES write info into the Windows bootloader AND it requires that it be unmodified (by another loader like GRUB, for instance).so.........i'm not asking whether I should leave GRUB on the MBR, i'm asking HOW to move it. I'm not asking for opposition or for reasons why I shouldn't move it, I already know why I need it moved, I just don't know the HOW of things.
 
And yes, the TC website DOES say that TC is Linux-COMPATIBLE, but that simply means it can be used within Linux, is all. what I said in the above paragraph still applies. don't believe me? then install it for yourself, you'll see..........
 
Installing 8 and Server 2012 is what I do first, and then Ubuntu, followed by TC, which then modifies the bootloader and inserts a bit of its' own code.......but not if a nonstandard loader like GRUB is there. TC will refuse to go any further if the latter is the case.

---

### Post by audiomick on 2012-12-07
> **Stephen Wayne Hamilton said:**
> @audiomick: the simple fact that you haven't even used Ubuntu

What on earth gave you that idea?  I've been using Ubuntu for about 5 years, and currently have 4 installs of different versions on 3 different machines. ;:)
I said I hadn't used true crypt...


>  TrueCrypt DOES write info into the Windows bootloader AND it requires that it be unmodified (by another loader like GRUB, for instance).so.. i'm asking HOW to move it.
...
 
Installing 8 and Server 2012 is what I do first, and then Ubuntu, followed by TC, which then modifies the bootloader and inserts a bit of its' own code.......but not if a nonstandard loader like GRUB is there. TC will refuse to go any further if the latter is the case.

Ok, this implies that you have re-installed more than once. From the output in your first post (which could have used code tags, by the way. The # button ...) shows two drives. From the look of things, all the OSs are on sda, and sdb is just one data partition. Is this the case?

What do you think of putting the Ubuntu install on sdb and leaving sda for the windows stuff?  

What I believe is possible, whether you put Ubuntu on sdb or not, is to install GRUB on the MBR of sdb. You have to tell the BIOS to boot from this drive first. If I have correctly understood what I have read, that will leave the MBR of sda intact. I believe you could even then remove sdb and have the computer still boot from sda, as long as the BIOS knows to look at that drive for a boot device.

As far as how, if you follow the instructions for re-installing grub in those links, or if you are doing a fresh install, there is a step where you can specify where to install grub to. The last time I did other than letting the installer put it where it wants is about 3 years ago, so I am a bit vague on exactly where that is, sorry.

I believe you can instal GRUB into a partition rather than the MBR of a drive, but I don't think that is what you want to do. Look here
[https://help.ubuntu.com/community/Grub2/Installing#Moving_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Moving_GRUB_2)
> If the user attempts to run the command with a specific partition (example: sudo grub-install /dev/sda6 ) a warning will be issued. Specifying a partition is not recommended due to the use of blocklists, which the developers consider unreliable. An option is provided on how to override this recommendation if the user still wishes to do so. 

I know that is all a bit vague, but I hope it still helps you.

---

### Post by oldfred on 2012-12-07
It looks like you have two drives.

Then just install grub to the other drive and when you want Ubuntu boot from that drive with your f12 or other one time boot key and leave the truecrypt Windows boot loader in the Windows drive. Not sure if grub can chain laod  to the truecrypt or not?

I have seen other users just use a flash drive or even CD with grub to boot. I actually have a full install of Ubuntu on a flash drive but have boot entries to boot my hard drive installs.

I do prefer to have install on same drive as boot loader ( or vice-versa) so each drive is independently bootable.

You can do this.
       sudo grub-install /dev/sdb
    
But grub remembers where to reinstall on major updates. Not sure if above command resets that or not:
       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

    
       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

