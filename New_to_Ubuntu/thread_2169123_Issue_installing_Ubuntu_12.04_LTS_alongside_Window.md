---
title: "Issue installing Ubuntu 12.04 LTS alongside Windows 7 Professional"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by hector3 on 2013-08-20
[SIZE=2][SIZE=3]I know this might sound redundant some some of you since I know this issue might have been discussed somewhere else in the forums but I think my particular issue might be somewhat unique and well I'm really new to the world of Linux. Anyway here's my system information for my machine:

[/SIZE][/SIZE]OS Name	Microsoft Windows 7 ProfessionalVersion	6.1.7601 Service Pack 1 Build 7601
Other OS Description 	Not Available
OS Manufacturer	Microsoft Corporation
System Name	ODIN-PC
System Manufacturer	Hewlett-Packard
System Model	p7-1205
System Type	x64-based PC
Processor	Intel(R) Core(TM) i5-2320 CPU @ 3.00GHz, 3001 Mhz, 4 Core(s), 4 Logical Processor(s)
BIOS Version/Date	AMI 7.16, 10/5/2011
SMBIOS Version	2.6
Windows Directory	C:\Windows
System Directory	C:\Windows\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "6.1.7601.17514"
User Name	Odin-PC\Thor
Time Zone	Eastern Daylight Time
Installed Physical Memory (RAM)	8.00 GB
Total Physical Memory	7.98 GB
Available Physical Memory	5.65 GB
Total Virtual Memory	16.0 GB
Available Virtual Memory	13.1 GB
Page File Space	7.98 GB
Page File	C:\pagefile.sys


I checked the BIOS settings and during the boot order I see UEFI Windows Manager, but I'm assuming that having UEFI should not affect the system booting up Ubuntu. Anyway when I put the live CD and try to install it it won't recognize Windows 7 so I went back to Windows and shrunk my hard drive space and from that non-allocated space I created different partition. Rebooted, booted from live CD again, selected the different partitions that I just created to install ubuntu. Assigned one for /, another for /boot, another for swap and last one for /home. Installed without issues, rebooted machine, booted straight to Windows again, didn't give me an option to select OS like I want. Rebooted again with live CD, ran boot-repair since I thought it could be a GRUB issue and it gave me the following URL that I wrote down. [http://paste.ubuntu.com/6005875](http://paste.ubuntu.com/6005875)    Anyway it gave me a whole list of what that boot-repair application did and found out, I would like more input from what the boot-repair is telling me.

I also read from the forums that some people went ahead and reformat the whole drive, make one partition for Windows and leave another partition for Linux, and then once they do that, install Windows first and then they put the live CD and try to install ubuntu and at that point it would recognize Windows and then would make it easier to install ubuntu at that point and then make the system dual bootable and giving you a choice as to what OS you want to load. Anyway please keep in mind that I'm totally new to this, my whole life has been Windows so if you could break it down and make it dumb for me I would really appreciate it.  The BIOS in my system is made by HP as well, in case anyone wonders.

One more question, once I get all this sort out. Do you guys recommend creating different accounts on Linux, like one just for admin and one for just user. I do that on my Windows machine, renamed my admin account and rarely use it. I do all my work and surfing from my user account for security reasons. Does that rule still apply with Linux in general as well for security reasons while you are surfing and doing every day stuff.  

Sorry for being long winded, anyway thanks for taking your time in reading this and try to help me out as well.


Hector :)

---

### Post by Cheesemill on 2013-08-20
It sounds like you have installed Ubuntu in BIOS mode rather than UEFI mode. Take a look at the wiki page...

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2013-08-21
You have grub2's boot loader in the protective MBR and a bios_grub partition, so you did install in BIOS/CSM/Legacy mode, but Windows is in UEFI mode. To easily dual boot you need both in same mode and since you cannot convert Windows to BIOS mode you need Ubuntu in UEFI mode.
Boot-Repair can convert your install to UEFI mode by uninstalling grub-pc(BIOS) and installing grub-efi (UEFI). But you need to boot it in UEFI mode. 

What HP system? Some others that may be similar.
       HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
            HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

    

You should be able to boot Ubuntu by going into UEFI can turning off UEFI mode and/or turning on CSM/BIOS mode and choose the Ubuntu entry. You then cannot use any grub entries to boot Windows as you are in BIOS mode. To boot Windows you have to go back into UEFI and turn off CSM and/or turn on UEFI mode and choose the Windows boot entry. Not an easy way to dual boot.

---

