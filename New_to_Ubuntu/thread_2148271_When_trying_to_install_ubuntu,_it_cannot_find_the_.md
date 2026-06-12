---
title: "When trying to install ubuntu, it cannot find the partitions I made from Windows"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by peterspliid on 2013-05-24
Hello, this is gonna be the first time I'll install and try out Linux, or Ubuntu for that matter.

I have already windows installed on my PC, and after using Disk Manager from Windows, I have created two partitions: one unallocated where I wish to install Ubunbtu, and one that I use for storage (I gave it the drive letter D). Screenshot 1 shows a clear picture of how it's set up. The problem arises when I try to install Ubuntu. I have burned a DVD with the latest version of Ubuntu. When I boot it up, and get to the option where it asks how I want to install it, it says that it can't detect any operating systems on the computer (screenshot 2), even though I have windows installed on the main drive. As illustrated on the screenshot, I choose 'something else', since I don't wanna delete my windows instillation, but it still can't seem to find the partitions I made from windows. (screenshot 3). How do I make ubuntu recognize the partitions?
 
I have googled this problem, but haven't seemed to find a solution that I understand. Some suggested a program called partfix (I think), which seems very complicated for me, and as far as I understand requires Terminal, which I do not have from windows. I would be very grateful for any suggestions on how to solve this. Thank!

- Peter

---

### Post by lethall1 on 2013-05-24
Try 
```
sudo fdisk -l 
``` from live cd. What is there?

---

### Post by lethall1 on 2013-05-24
may be you use GPT partition table?

---

### Post by Mark Phelps on 2013-05-24
Ubuntu has to be installed into a Linux filesystem -- and I don't recall Windows being able to create Linux filesystem partitions.  Even so, Win7 Disk Management can't understand Linux filesystem partitions, either.

You need to leave some space unallocated and create the Linux filesystem partitions from inside the installer ... but the screen about not detecting Win7 is alarming.

I would not continue until you get more detailed advice about how to examine the partitions, as you may have GPT partitioning, and I don't work with that.

---

### Post by deadflowr on 2013-05-24
You didn't happen to hit the new partition button, did you?

---

### Post by peterspliid on 2013-05-24
I get the following message:
> ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x6ea6e3bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   204799999   102296576    7  HPFS/NTFS/exFAT
/dev/sda3       204802048  1362745343   578971648    7  HPFS/NTFS/exFAT

I havent really dared to click anything from the installtion type window, as im scared of interferring with my windows installation. Any suggestions?

---

### Post by lethall1 on 2013-05-24
do you have uefi or bios?

---

### Post by grahammechanical on 2013-05-24
You need to read through this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

When you get to the section Converting Ubuntu into Legacy Mode note this comment:

> [COLOR=#333333][FONT=Ubuntu]If Ubuntu is installed on a GPT disk (you can check it via the 'sudo parted -l' command), use [/FONT][/COLOR][Gparted]("https://help.ubuntu.com/community/Gparted")[COLOR=#333333][FONT=Ubuntu] to create a BIOS-Boot partition (1MB, unformatted filesystem, bios_grub flag) at the start of its disk.[/FONT][/COLOR]

You have yet to install Ubuntu but the disk is GPT type.

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

I was searching for information about this earlier this afternoon. That link was the best that I could find. I have no experience installing on GPT disks.

You actually fail to tell us what version of Windows you have installed. If it is Windows 7 or 8 then that for link will be necessary information. You are possibly in the realm of UEFI, secure boot as well as GPT. Unfortunately manufacturers are not consistent in applying the specifications.

Regards.

---

### Post by lethall1 on 2013-05-24
there must not be any problem installing ubuntu in GPT, except grub installation. 
But you must switch off UEFI in your asus

---

### Post by ajgreeny on 2013-05-24
And in case your Windows is installed in UEFI, here is the ubuntu info on dealing with that type of installation.

I do not dual boot with windows but getting Xubuntu 12.04 onto a UEFI booting system was very easy when following these instructions.
[UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI")

---

### Post by peterspliid on 2013-05-24
Thanks everyone. Sorry I failed to inform you about the version of windows. I bought the computer this month with Win8 64bit preinstalled on it. However, since I really dislike Win8, I replaced it with Win7 (64bit) instead. It took me ages to find out how to boot from a CD, but after a lot of research I found out that I had to disable secure boot and fast boot from the BIOS. In addition I changed Boot mode form UEFI to Legacy, thus Win7 is installed in Legacy (I guess). I just changed it back to UEFI, and now I can't seem to boot at all. If the ubuntu DVD is in, I get to a black screen where I can choose to run or install ubuntu. If the DVD is not it, I just land straight at the BIOS window.

EDIT: I noticed that I'm booting every thing in Legacy, both Windows, Ubuntu and the CD. So that shouldn't be an issue?

---

### Post by peterspliid on 2013-05-24
I just tried download [fixparts]("http://www.rodsbooks.com/fixparts/"), which I read should solve this. I am however not quite sure how it works. I typed in sudo fixparts /dev/sda, and now its asking me if I want to delete some GPT signatures. Will this affect my windows installation? You can see the messages here. 

> ubuntu@ubuntu:~$ sudo fixparts
FixParts 0.8.4
Type device filename, or press <Enter> to exit: /dev/sda

Loading MBR data from /dev/sda

NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N):

Did I use the right syntax? And thanks everyone again for your support

---

### Post by lethall1 on 2013-05-24
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

> [COLOR=#000000]NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition![/COLOR]
The GPT signatures are probably left over from a previous partition table.Do you want to delete them (if you answer 'Y', this will happenimmediately)? (Y/N): [COLOR=#000000][FONT=Times New Roman]If you're not sure whether to delete the GPT data, don't do it; type [/FONT][/COLOR]**N**[COLOR=#000000][FONT=Times New Roman], exit from the program by typing [/FONT][/COLOR]**q**[COLOR=#000000][FONT=Times New Roman] at the main prompt, and investigate further. If you're certain you want to keep just the MBR partitions, go ahead and type [/FONT][/COLOR]**Y**[COLOR=#000000][FONT=Times New Roman]. If the stray GPT data was your only problem, you can then exit from the program by typing [/FONT][/COLOR]**q**[COLOR=#000000][FONT=Times New Roman], leaving the original MBR partition table untouched, although the errant GPT data will now be gone.[/FONT][/COLOR]

This command will destroy first blocks on you HDD, thats indicates partition table, thats mean it will make it from GPT to MBR, you would loose all your information

---

### Post by peterspliid on 2013-05-24
That was my initial thought as well, but after looking at this thread [http://askubuntu.com/questions/169530/this-computer-currently-has-no-detected-operating-systems-when-installing](http://askubuntu.com/questions/169530/this-computer-currently-has-no-detected-operating-systems-when-installing) with a guy having the same problem, that command seems to have fixed it?

EDIT I noticed that when I say no, I get these options. would they be of any help?
> 
FixParts 0.8.4

Loading MBR data from /dev/sda

NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!
The GPT signatures are probably left over from a previous partition table.
Do you want to delete them (if you answer 'Y', this will happen
immediately)? (Y/N): n

MBR command (? for help): ?
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit

MBR command (? for help

---

### Post by lethall1 on 2013-05-24
yea, it seems so, but > [COLOR=#000000][FONT=Times New Roman]* errant GPT data will now be gone*[/FONT][/COLOR]
i never used that program, excuse me, i only can judged by documentation.

---

