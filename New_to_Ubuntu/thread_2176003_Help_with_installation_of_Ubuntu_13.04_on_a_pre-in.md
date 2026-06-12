---
title: "Help with installation of Ubuntu 13.04 on a pre-installed Windows 8 system"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by levi2 on 2013-09-22
I have an HP Envy desktop I got from Best buy.  I am having trouble installing Ubuntu 13.04 from either disk or USB.  When I go through the prompts for installation instead of getting a screen where I have choices to install alongside Windows, Replace Windows, or Something Else i get a blank grey page.  The only options I have are a plus and minus button.  How do I fix this and proceed with the installation?

---

### Post by oldfred on 2013-09-22
Is this an Ultrabook with a small SSD? They have Intel SRT which uses RAID that is then not seen correctly.

Be sure to turn off fastboot in Windows and/or UEFI also as that sets the hibernation flag and the Installer cannot see drive.

Use Windows to shrink Windows NTFS partition to make unallocated space for Ubuntu. Do not create partitions with Windows. Reboot Windows a couple of times so it can run chkdsk and make whatever repairs it does to its new size.

More info and links to lots of details on UEFI install in link in my signature.
       HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)

 Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

### Post by levi2 on 2013-09-22
I cannot find or edit the UEFI settings.  This is really pissing me off.  I have tried everything and it seems Windows 8 has my PC on lockdown.  I have an HP ENVY h8-1414 Desktop PC.  I have tried installing Linux Mint with the same result.  However, my linux mint disk wont show up when I try to boot from it.

---

### Post by oldfred on 2013-09-22
Another HP user posted this, does yours work this way?

 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by levi2 on 2013-09-22
Ok so when I try to install Linux Mint from a USB and/or External HD the installer will NOT recognize my partitions OR give me any option to install along side Windows or to erase Windows and replace Linux with it.  I need prompt responses please.

---

### Post by oldfred on 2013-09-22
We do not know much about Mint. I doubt it has the signed kernels that Ubuntu uses.

---

### Post by morgan4 on 2013-09-23
> **levi2 said:**
> I cannot find or edit the UEFI settings.  This is really pissing me off.  I have tried everything and it seems Windows 8 has my PC on lockdown.  I have an HP ENVY h8-1414 Desktop PC.  I have tried installing Linux Mint with the same result.  However, my linux mint disk wont show up when I try to boot from it.


You have to go into "Change PC Settings" at the bottom is Advanced Options, click "Restart Now," a new page will open and it is somewhere in there, think it says "Advanced Options" again, then "UEFI Firmware Settings." Your computer will then boot into Bios. 

I installed Ubuntu yesterday and yeah, Windows doesn't make it easy to find.

---

### Post by oldfred on 2013-09-23
Another HP user with two drives - see his last post where it installed it. He could only get it to work in BIOS mode so he has to go into BIOS/UEFI each time he reboots to different system.
 HP Envy 2 drive install i7 & 2 1TB drives
[http://ubuntuforums.org/showthread.php?t=2175877](http://ubuntuforums.org/showthread.php?t=2175877)

While Acer the process from Window is the same.

 Acer Windows 8 Video on getting into UEFI
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

You should have a key to directly boot into UEFI.

 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by levi2 on 2013-09-23
Ok so i got to the end of installing the linux mint/ubuntu/linux distro on an external HDD but when it gets to installing the grub it give me a fatal error.  I even tried converting my external HDD to a MSDOS partition table and it still didnt work.

---

### Post by oldfred on 2013-09-23
If a  UEFI system, I would stay with gpt partitioning. Linux will boot from gpt as long as you have a bios_grub flagged partition for BIOS booting or an efi partition with boot flag for UEFI booting. If you do not have either or both (just in case) then grub will not install correctly.

---

### Post by levi2 on 2013-09-24
Can you kindly explain to a lad how to correctly setup the partition(s) in my External HDD?

---

### Post by brianmartin-lucas on 2013-09-24
Windows 8 has two layers to the system, the apps or applications layer and the the familar windows 7 desktop look. You can try using the Ubuntu Windows installer which you can download Ubuntu and install it that way, or you can get a hold of a disk and when you boot up, go into settings and boot from your cd room and install it that way. For the second method you will need to go into BIOS and change the settings to boot from the CD ROM instead of the hard drive.

---

### Post by oldfred on 2013-09-24
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
Another advanced suggestion from TheFu - Post #6 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

---

### Post by Jonathan Precise on 2013-09-24
> **brianmartin-lucas said:**
> ... You can try using the Ubuntu Windows installer...

Please do not, and I mean **DO NOT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!** use the Ubuntu Windows installer!!! It has many known bugs, and is **NOT COMPATIBLE WITH UEFI** (windows 8, most of the time)**, AS IT USES GPT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!**

Boring explanation, feel free to skip: UEFI requires GPT (_**G**_UID _**P**_artition _**T**_able), and does not read MBRs. GPT is not compatible with Grub4DOS or WinGRUB. Ubuntu-windows-installer uses Grub4DOS. Ubuntu-windows-installer uses MBR. After install, you will reboot and get an error, either when selecting ubuntu (in the BCD boot-menu), **or even before reaching the BCD boot-menu, rendering your system (and windows 8) unbootable!!!!!!!!!!!!!!!!!!!!**!

---

### Post by levi2 on 2013-09-24
Did all this and still same error.  I just want to erase my external HDD and install linux mint, thats all.  But apparently Windows has royally ****ed up.

---

### Post by hargrave-a on 2013-09-25
My windows vers is only Win7. But my Ubuntu installation kept freezing when selecting the install location. So I partitioned the HDD with Partition Magic (free), keeping the Windows install as is, and the new ext4 partition which then allowed the install to work.

I don't know if it addresses your issue exactly but hopefully it helps in some way.

---

