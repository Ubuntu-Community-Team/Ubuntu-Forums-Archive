---
title: "Grub-Installation /dev/sda FAILED"
date: 2016-07-03
forum: New to Ubuntu
---

### Post by zacmartin on 2016-07-03
I'm trying to install Ubuntu in my Windows 10 UEFI pc with dual boot using live USB. I was not aware that my legacy mode was disabled so for the first time my ubuntu installed perfectly. But in *efibootmgr *it was not showing ubuntu so I was not able to change the boot preference.
I want back to windows and deleted the partition which i had created and again went back to ubuntu using usb and tried to install it. Ever since then its giving this same error. Its been 4 days and I'm still not able to solve it .
Please help !

---

### Post by yancek on 2016-07-03
If your windows 10 is installed UEFI, then you must also install Ubuntu UEFI as explained in the Ubuntu documentation at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ajgreeny on 2016-07-03
See Boot-Repair in my signature below and from that run the Boot-info-script and post back here the pastebin link which it will give you.

I suspect yancek has given you the probable reason for the problem but that script should tell us all.

---

### Post by zacmartin on 2016-07-03
Thanks a lot Sir! @yancek
But I've already gone through all of this before posting my question here. I am creating partition from Windows (Disk Management) and there is one EFI partition but i'm not sure how do I make sure that Grub will install on this drive or am I not supposed to do it?

---

### Post by yancek on 2016-07-03
The Ubuntu EFI files go on the same EFI partition as the windows EFI files in a different directory.  Leave the space unallocated rather than trying to create a partition from windows.  You have to format the partition before or during the install and you can't do that with a standard windows system.  Booting and installing EFI is explained at the Ubuntu link I posted earlier.

---

### Post by ajgreeny on 2016-07-04
And do not make partitions with Windows that you will be using for Linux distros; Windows has a nasty habit of creating virtual partitions, similar to LVM, but they will not work for Linux and may not even be seen by Linux.

Much better to leave unallocated space and then create partitions using the Ubuntu installer or gparted in the live Ubuntu OS.

---

### Post by oldfred on 2016-07-04
How you boot install  media, DVD or flash drive is how it installs, or if you boot installer in UEFI mode it installs in UEFI mode.
And with Ubuntu's grub, it will only install to the ESP - efi system partition on drive seen as sda. So if you have an ESP, it will use it. Do not create another, only one ESP per device(normally).

---

### Post by zacmartin on 2016-07-08
@ajgreeny @yancek @oldfred Sorry for late response. I was sick. Here is my pastebin url : [URL="http://pastebin.com/j7CDSxHa"]http://pastebin.com/j7CDSxHa 



[/URL]

---

### Post by zacmartin on 2016-07-08
Also I click on recommended repair and my terminal was filled with a lot of **syntax error** statements and the boot repair froze at repairing **chroot**

---

### Post by oldfred on 2016-07-08
You have a HP UEFI system.

But Boot-Repairs error says your ESP - efi system partition sda2 is read only.
You can try chkdsk from Windows, you have to mount it in Windows.
Or run fsck from Ubuntu installer.

       dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda2
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

You should be able to mount sda2 from live installer, but if a user is in his install, Ubuntu mounts ESP as read-only. Details on editing fstab in link in my signature and here:
[http://askubuntu.com/questions/794725/can-i-remove-windows-boot-manager-from-dedicated-ubuntu-computer?noredirect=1#comment1197619_794725](http://askubuntu.com/questions/794725/can-i-remove-windows-boot-manager-from-dedicated-ubuntu-computer?noredirect=1#comment1197619_794725)

But HP has not been dual boot friendly. I violates UEFI standard and uses description as part of boot. And only valid description is "Windows Boot Manager". There are various work arounds. Many use the fallback or a UEFI:hard drive entry in UEFI which still can be booted. Not sure if any of yours are that now using the Windows boot file. But it is /EFI/Boot/bootx64.efi and can be either a copy of Windows bootmgfw.efi or Ubuntu's shimx64.efi.
 
Boot-Repair also sees all the HP .efi files for system maintenance or update and adds those to grub menu. Most do not want or need any or all of those and can edit the grub entries that Boot-Repair creates in new file /etc/grub.d/25_custom. 
      
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options. This saves the manual mount & copy that many others did.

 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try different USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079) [URL="http://ubuntuforums.org/showthread.php?t=2260681"]
[/URL] 
You can add your hard drive entry to boot fallback file:
 sudo efibootmgr -c -g -d /dev/[COLOR=#ff0000]sdX[/COLOR] [COLOR=#008000]-p Y [/COLOR]-w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'
 [COLOR=#ff0000]sdX[/COLOR] is drive,[COLOR=#008000] Y[/COLOR] is efi partition  


Mine was sda, and ESP is sda1, so I used -p 1 to get this:
Boot0001* UEFI hard drive    HD(1,GPT,c371fe4e-a6db-4c46-b056-a4eea609f81d,0x800,0x639c000)/File(\EFI\Boot\bootx64.efi)

---

### Post by zacmartin on 2016-07-08
Thanks a lot you your answer Sir @oldfred but to be honest I'm so noob to all of this that most of the things went over my head and I literally don't understand what all I am supposed to do.

---

### Post by oldfred on 2016-07-08
Step by step, then

First run the dosfsck from a terminal on live installer, and see if then Boot-Repair can get grub to reinstall correctly.

---

### Post by zacmartin on 2016-07-09
@oldfred 
I did dosfsck command and then boot repair.
Here is the link : [http://paste2.org/yB2J4ODF](http://paste2.org/yB2J4ODF)

and also got this on the dialog box:
An error occurred during the repair.

Please write on a paper the following URL:
[http://paste2.org/yB2J4ODF](http://paste2.org/yB2J4ODF)


In case you still experience boot problem, indicate this URL to:
boot.repair@gmail.com 

Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].

---

### Post by oldfred on 2016-07-09
Did you run this version with the -a parameter?

Must be unmounted
sudo dosfsck -t -a -w /dev/sda2
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

If so post it and what it outputs. You can copy from terminal in live installer to this thread. If long output use Forum's 'Go Advanced' and highlight code and click # to add code tags.

---

### Post by zacmartin on 2016-07-10
[COLOR=#000000][FONT=arial][I]@yancek
@ajgreeny
@oldfred

Here is the output before boot repair : [/I][/FONT][/COLOR]
[COLOR=#000000][FONT=arial]*ubuntu@ubuntu:~$ sudo dosfsck -t -a -w /dev/sda2*[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]*fsck.fat 3.0.28 (2015-05-16)*[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]*/dev/sda2: 728 files, 34205/65536 clusters*[/FONT][/COLOR]


[COLOR=#000000][FONT=arial]*Here is the output after boot repair :*[/FONT][/COLOR]

[COLOR=#000000][FONT=arial]*sudo dosfsck -t -a -w /dev/sda2*[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]*fsck.fat 3.0.28 (2015-05-16)*[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]*Orphaned long file name part "ubuntu"*[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]*Auto-deleting.*[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]*Performing changes.*[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]*/dev/sda2: 728 files, 34205/65536 clusters*[/FONT][/COLOR]

---

### Post by oldfred on 2016-07-10
HP is not dual boot friendly.

In Boot-Repair's advanced mode tick/check this:
       	'Use the standard EFI file' 

 	That will do this:Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 

Then from HP's one time boot key, escape then f9 and see if you can boot hard drive boot entry. Ubuntu may also work from that menu.
Then see if you can set hard drive boot entry to first in boot order.

---

### Post by zacmartin on 2016-07-11
@oldfred

Will this help : [http://askubuntu.com/questions/681422/grub-menu-not-showing-with-dual-boot-uefi-mode-installation](http://askubuntu.com/questions/681422/grub-menu-not-showing-with-dual-boot-uefi-mode-installation)

---

### Post by zacmartin on 2016-07-11
@oldfred

I am able to boot into Ubuntu by first pressing **ESC > F9 > Ubuntu , without doing** what you told me in your last reply.
But there is a problem. Earlier when I used to boot into Ubuntu with Live USB in order to **enable Wifi** I first had to select [B]Broadcom driver from Addition Drivers.

[/B]But now Broadcom driver is not appearing. The **Additional Drivers list is completely empty** and hence I am **not able to use my internet on Ubuntu**.

---

### Post by oldfred on 2016-07-11
All my systems have just worked for Internet. Do not know details. Many threads in forum.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
But start new thread with your details on model Wireless chip, see link above. But often you have to connect with Wired Internet which almost always works to be able to download correct drivers & other updates.

You do need Internet for Boot-Repair to work from inside your install.

---

### Post by zacmartin on 2016-07-11
@oldfred
Thank you Sir!
Please close the thread.

---

