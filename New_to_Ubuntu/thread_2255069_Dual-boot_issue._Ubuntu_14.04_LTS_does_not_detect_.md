---
title: "Dual-boot issue. Ubuntu 14.04 LTS does not detect Windows 7"
date: 2014-12-02
forum: New to Ubuntu
---

### Post by michael-werker on 2014-12-02
Hello guys! First of all Id like to thank you for all the great work you are doing here. In order to fix this problem I have already browsed the forum and the internet for answers, however even though this problem has started many threads before I have been unable to solve it using the answers from other threads. I will tell you in what I did and hope you can point me in the right direction!

So, I want to instal Ubuntu 14.04 LTS next to Windows 7. I previously made a Ubuntu LiveUSB on this computer which I used from time to time but the speed and some other things made me decide to install it on a partition for good. 

When I open the Ubuntu installer and proceed with the installation I get:

> This computer currently has no detected operating systems.

I found this weird since Windows 7 is installed and I am using it. 

To solve the problem I have tried the following:

1. fixparts with "w"

2. Installed boot-repair and used the auto-repair function. It actually  seemed to have found Windows but the installer will still not find it. 
The info is here: [http://paste.ubuntu.com/9339626/](http://paste.ubuntu.com/9339626/)

3. Deleted the partition that is now marked as Unallocated to make sure there is enough space for Ubuntu to be installed. Some people also suggested that having 4 primary partitions may be a problem so that is another reason why I deleted this one. gparted looks like this: [http://i.imgur.com/D3DBIY1.png](http://i.imgur.com/D3DBIY1.png)

4. When I tried using fdisk to see what it spits out I got the following:

> Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2089403c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    62916607    31457280   27  Hidden NTFS WinRE
/dev/sda2   *    62916608    63326207      204800    7  HPFS/NTFS/exFAT
/dev/sda3        63326208   273041407   104857600    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 15.5 GB, 15504900096 bytes
255 heads, 63 sectors/track, 1885 cylinders, total 30283008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    30281727    15139840    c  W95 FAT32 (LBA)



5. When I use os-prober it just returns nothing. 


So I am at a loss. I am an amateur linux user so I am not sure what I should do next. My main problem is, that I use the Windows 7 partition for work. And even though I am not forbidden to change stuff on my computer it would be bad if I somehow could not access the Windows 7 OS anymore. I dont want to change anything to the Windows system, just have Ubuntu where I can do whatever I want without affecting Windows. And when I see that Windows is not found I ask myself what happens if I use the something else option and manually give Ubuntu what it wants. It is imperative that I at least get a boot selection upon start-up that lets me select between windows and ubuntu. When I used the LiveUSB it would start windows when the USB is not inserted and Ubuntu when the usb is inserted. If I go into the boot menu before the OS is loaded the first option still says "Ubuntu" even though I do not use the LiveUSB anymore. 

If you need more info please let me know. And if my question is somehow stupid please have mercy with a beginner, I have tried to solve this problem for several hours with the available info but to no avail. 

Thank you.

---

### Post by carl4926 on 2014-12-02
But if you proceed with the install and choose 'Something else' as shown here
[http://assets.ubuntu.com/sites/ubuntu/1245/u/img/download/desktop/install-ubuntu-desktop/image-installdesktoplongtermsupport-4.jpg](http://assets.ubuntu.com/sites/ubuntu/1245/u/img/download/desktop/install-ubuntu-desktop/image-installdesktoplongtermsupport-4.jpg)

When you see the partition manager - Isn't windows partition/s visible?
It wouldn't be the first time I have had this happen but I just install and it works just fine.

---

### Post by oldfred on 2014-12-02
You originally had the 4 primary partition limit.

You should just be able to use something else install option. I do prefer to use gparted to create partitions in advance, but it is only slightly easier and you still have to use Something Else.

Since only one drive, the default to install grub2's boot loader of sda (not ever a partition) should be ok. You can ignore all the discussion of changing boot loader to sdb or external drive.
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by michael-werker on 2014-12-02
Good morning and thank you two for your helpful replies! 

To answer [carl4926]("http://ubuntuforums.org/member.php?u=809261")[COLOR=#000000] :
[/COLOR]Yes the partition is visible. Windows is installed on a 100gb partition with a 200mb one reserved for boot and it seems that there are 30gb for diag. My fear was that since Ubuntu did not detect Windows, it might do something during the installation that might make it hard for me to access Windows 7. 

And [[COLOR=#C61919]oldfred[/COLOR]]("http://ubuntuforums.org/member.php?u=852711")[COLOR=#000000] : 
[/COLOR]So what you are saying is that even though the installer does not recognize my windows I can safely use the "Something else" option after I made the necessary partitions with gparted and still be able to switch back and forth between Windows 7 and Ubuntu? Thank you for that info! I was unsure if it was a safe thing to do and even though some people suggested it in other threads I didnt really get if it was a viable option to preserve an existing Windows 7. 

 If I install it like that, do I have to do something special to get a OS selection menu or will it pop up naturally? EDIT: Ah, I overlooked part of the links you gave me, sorry! It explains there how to deal with the boot process. Ill try it and report back with my results! Thanks!

---

### Post by michael-werker on 2014-12-02
Okay, So I used gparted to make the whole unallocated space an extended partion, in which I made a 20GB partition for Ubuntu, a 4GB partition for swap (as per the notebooks memory) and a 100gb partition for home. I returned the rest of the unallocated space in the extended partition to NTFS so I can use it in Windows as well. (which pops up fine there)

I set the 20GB to / and when asked where to install the bootloader I selecteced the 20GB partition where Ubuntu was supposed to be installed. In the links I read before that you can have multiple options to deal with the dual-boot situation. What I would ideally want is that unless I intervene, it should just boot windows, without any selection screen. I am fine with booting Ubuntu manually somehow. So I decided not to install over the location where the Windows bootloader is located. However, now it just starts Windows and when I look at the bios boot info, ubuntu and debian is listed but nothing will do for me. I suppose that the "Ubuntu" information that is already in there refers to the LiveUSB that I was previously using. 

I will try to fix the problem myself in the meantime, but if you have any insights it would be much appreciated! Can I add a boot info in the bios boot order that refers to my new Ubuntu installation?

EDIT: Trying to use grub for now, trying to fix with boot-repair. For future reference: [http://paste.ubuntu.com/9351845/](http://paste.ubuntu.com/9351845/)

---

### Post by yancek on 2014-12-02
> I set the 20GB to / and when asked where to install the bootloader I  selecteced the 20GB partition where Ubuntu was supposed to be installed

So your windows bootloader has no idea there is another operating system there.  A windows system will not be able to boot Linux unless you manually edit the boot files on windows.  If you have experience and feel comfortable modifying the windows boot files, that would be the best thing to do.   If not, another option is to install EasyBCD to your windows system which is a graphical front end you can use to modify the windows boot files.  EasyBCD is basically a front end modification of Grub to run on windows.

---

### Post by oldfred on 2014-12-02
BIOS only boots the drive MBR specified as the boot device.
And the MBR can only have one boot loader in it. So with one drive only one system boots.

Windows does not know nor care about Ubuntu so it will not boot Ubuntu. You can add third party tools to modify BCD, add an old version of grub which works with NTFS partitions, and forces you to install grub into the partition's boot sector so it can be chain loaded from the BCD, old grub4dos, to grub in partition. 
Grub2 does not recommend installing into a partition as it does not really fit. It converts to block lists or hard coded addresses. A grub update may change address, so then you need live installer to repair grub.

Unless you will only be using Windows and just want to experiment a bit with Ubuntu, it is better to install grub2's boot loader to the MBR and grub will offer to boot Ubuntu or Windows.Some that use EasyBCD do say it works, they they are mostly Windows users.

With BIOS the advantage of mulitple drives is then you have mulitple MBRs and can have different boot loaders in each MBR.
And with UEFI, it is designed to allow as many boot loaders as you want in one efi boot partition. It is like having many MBR all on one drive. Although some vendors are modifying UEFI to only boot Windows and we have to do work arounds to make those systems work.

---

### Post by carl4926 on 2014-12-03
Grub should have been set to sda
That's to the MBR
Just run the install again and set to sda

---

### Post by michael-werker on 2014-12-03
Alright, I am back! Sorry for the late response but I had to work in the meantime. 

Thank you again for all the help! Yeah as an Ubuntu newcomer I have not really dealt with boot issues on that level so far. This is a first for me. But I also learned a lot.

Now I have abandoned what I had previously imagined in favor of the standart grub. I have not reinstalled it but I have used boot-repair and grub-customizer and now I have a boot screen that will let me choose between Windows 7 and Ubuntu. This is not 100% what I wanted to do but at least both systems work for now and there do not seem to be any major problems. 

Which is the most important thing, everything else is really just the icing on my new dual-boot cake, if you will. 

My next step is to setup grub in a way that it boots into windows without displaying itself and only showing the selection after button input ( i read that it should work in some conditions with shift) but that is beyond my initial problem here so I will do that research for now and look through the forum for that kind of question later. 

Thank you again for providing such good advice to a total beginner. I hope that someday I can acquire more knowledge and be of help to other people as well! 

Have a nice day!

---

