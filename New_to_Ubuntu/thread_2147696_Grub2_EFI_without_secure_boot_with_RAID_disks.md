---
title: "Grub2 EFI without secure boot with RAID disks"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by Sasiraki on 2013-05-22
Hi,
i will say sorry now, because this is gonna be a verrryyyy long text.

First of all here are my (relevant) HDDs and how they are partitioned:

1. HDD
dev/sda
dev/sda1   <-- this is the partition I want to boot from
dev/sda2   <--this is my windows7 installation, no system-reserved partition used

2. HDD
dev/sdb
dev/sdb1  <-- here I save games etc. of Windows7
dev/sdb2  <--this is an extended partition of 20GB for my Linux
dev/sdb3  <-- here I installed Ubuntu 13.04
dev/sdb4  <-- here I will install Kali 1.0


Now my System:
Motherboard: ASrock Extreme4 Gen3, this is a UEFI Mainboard, which supports secure boot only in Beta BIOS, more to that later on
Graphic Card: ASUS ENGTX 560Ti, this Graphic Card doesn't support GOP, no VBIOS Update from ASUS supporting GOP, only for System Builders (maybe a system builder here who can give me the VBIOS supporting GOP?), has to do with UEFI and secure boot more information later on
RAM: G.Skill Ripjaws.X Series 4x4GB
CPU: i7-2600K


So. After you got my System Information, I will start with my problem.
My problem is, that i can't boot from GRUB2 Boot loader. I tried a lot of things. Here's a list:
1. Install 2.31A Beta BIOS, to support secure boot. I read that it's needed here: [http://wiki.ubuntuusers.de/EFI_Installieren](http://wiki.ubuntuusers.de/EFI_Installieren)
it's a German site. So i will translate the important paragraph into English. Here it says:


**Information before installation**
To install Ubuntu on a System with (U)EFI, you need to start the CD in EFI Mode. If the option
·         **secure-boot**
is enabled in the UEFI, Ubuntu will be installed with the signed kernel.

My problem is, that the Live CD doesn't start with secure boot enabled. I think it's because I enabled BIOS compatibility. If I disable it, I can't start because my Graphic Card doesn't support GOP protocol. So I can't try booting with secure boot and UEFI Mode (no BIOS compatibility).

2. So I tried to install without UEFI Mode. I didn't start disc in EFI Mode, but in RAID Mode (earlier I had a RAID and my BIOS is still in RAID mode, don't want to change it, because I think about making a raid again). Everything worked fine. The disc booted. I could use GParted in Live mode to partition my HDDs. Secure Boot is disabled, I flashed back to 2.30 BIOS, which doesn't support secure boot and no BIOS compatibility (runs normally in BIOS compatibility I think, hope you know what I mean).
I can also install Ubuntu, but during installation I get an error, that he couldn’t install GRUB. I rebooted from CD again. First I got an error, because he couldn’t mount Boot partition, after reboot everything went fine. I tried installing, but got another Error. It says, that he couldn’t make the directory “/boot/grub/i386-pc”. So I made it on my own. I’m not sure at the moment if I used sudo for admin rights. Will try tomorrow again to make sure I did. Even after I made the directory on my own, he tells me that he can’t make this directory (???). I don’t understand the world anymore. I looked a bit in the Ubuntu partition and saw, that there is a folder called “boot”. I tried copying it (it contains GRUB), but he couldn’t copy 1 file. Not sure which, ended with “config” or sth. like this. The rest was copied properly. When I tried to boot from my first HDD now, I got an Error: MBR Error 3. The boot flag was set on Boot partition /dev/sda1. If I set boot flag to Windows partition it boots Windows (of course, because UEFI loads Windows Boot loader).
 
I just don’t know what I could do now…I’m done with my knowledge so far. I read a lot of thread in different forums, but didn’t find a solution for my problem. Thanks again for reading this long text. :D. If sb. Knows the answer for my problem I would be much more thankful of course :D. I hope you can help me. Thanks for every answer.

Greeding Sasiraki

---

### Post by deadflowr on 2013-05-22
Does this thread help you at all

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by squakie on 2013-05-22
The i386 makes me think you got the 32-bit version of Ubuntu.  I don't know if it applies in 13.04, but in 12.04 and 12.10 you had to use the 64-bit version to get uefi support.  If you've messed around with bios mode vs uefi mode in the BIOS, I don't have a clue what you may have done along the way.

---

### Post by Sasiraki on 2013-05-23
I installed a 64-Bit Version of Ubuntu. I also don't know why it needs a folder i386. I also wondered about that. The problem is that i can't disable BIOS compatibility because my Graphic card doesn't support it. The VBIOS version supporting GOP protocol is only for System-Builders. If I enable secure boot and BIOS compatibility the CD doesn't start. I get a black screen after I choose an option in the GRUB menu. If I disable secure boot and enable BIOS compatibility I can't install grub. That's what I'm trying to do right now. But I get the Error, that he can't make this i386 folder. So there is no option for me to install this f****** GRUB Boot loader. Either the PC doesn't start after the GRUB menu or he can't install the Bootloader.

I hope you have some more tips for me. I will read deadflowr's link now. Maybe it can help me. If it helps me or there is anything new to know I will post it here.

Sasiraki

---

### Post by Sasiraki on 2013-05-23
Update:
I used the Boott-Repair disk to make a new GRUB. That worked, I can see GRUB on Bootup now, but i don't snow why it doesn't boot. If I select "Ubuntu" I just get a white line. It looks like this _ . I hope you know what I mean. I don't know how to describe it (I'm German and my English isn't perfect). After this nothing happens. Here's a link of what the Boot repair disk did.
[http://paste.ubuntu.com/5693973/](http://paste.ubuntu.com/5693973/)
It's the logfile of the Boot repair disk.
Here you can see all my partitions and the grub.cfg. I couldn't update it using "sudo update-grub" and I didn't know how to make chroot. Maybe sb. can give me the code for my specific System. The Boot repair disc writes into the MBR, but I don't know if it starts the GRUB from my Ubuntu Partition on boot or if the whole GRUB is in MBR. That's why I didn't know what and how to chroot. I tried editing the menuentry by using e and changed the line "[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd1,msdos3'[/COLOR]" into other partitions to boot from. No partition I tried worked also WIN7 didn't boot. Just this white line appears. What am I doing wrong?

---

### Post by fantab on 2013-05-23
First of all to be able to boot with UEFI you need 'GPT' partition table. And you have 'msdos' table on both Disks.
With 'msdos' UEFI will not work, so you HAVE to disable it in UEFI/BIOS setup.
YOU have to also disable 'secure boot' if you are not booting with UEFI.

Your problem is with RAID. I can't offer much help with that, however you should check this out: [https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html) and also add 'RAID' in your post title, it will attract proper help.

Good Luck...

---

### Post by Sasiraki on 2013-05-23
Will Windows work with GPT partition table? If I use GPT, in which mode do I have to install Windows? UEFI or RAID mode?
In the UEFI I can't enable or disable it. This is only posible in the latest Version 2.31A which is a BETA version. I think my UEFI runs normally in BIOS mode, because, like i said yet, if I use BETA BIOS and enable UEFI mode/disable BIOS mode the MB gives me he information that my Graphic Card doesn't support GOP protocol. So do I really need to use GPT in that case?
At the moment there are no RAID drives. I just use it because it could be, that I make a RAID for my data disk.
I changed the title of the thread as well. Just added "with RAID disks".

---

