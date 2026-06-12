---
title: "GRUB Screen error"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by skylar2 on 2014-04-25
I recently decided that I want to try out Ubuntu, so I decided to install it on a flash drive (16GB). I used the installer and desktop download from the official Ubuntu website.

When I tried to launch Ubuntu a black screen came up that said "GRUB ver2" or something similar. It allowed me to type commands, and I tried a few but nothing seemed to happen.

After a quick Google search of my problem, I found Boot Repair, which I tried to install on a CD, but it wouldn't allow me to choose it as an option pre-booting.

I am currently running Windows 8 (pre-installed on my laptop) on my MSI GE-70. 

Possible problems:
-Wrong download?
-There were a few other things on my flash drive, but I deleted them after realizing they were there.

Thank you so much for your help, I greatly appreciate it!!

---

### Post by oldfred on 2014-04-25
Did you download the 64 bit version. 
Pre-installed Windows has UEFI and gpt partitioning.
Best to turn off fast boot in Windows which is always on hibernation.
Ubuntu should work with secure boot on, but it may be better to have it off.

Boot-Repair is after you have installed, which you may have to run from a booted installer. But most of the issues that used to need Boot-Repair just to get system to work are now resolved.

What system brand & model
And what video card/chip. Some chips need extra  boot parameters although 14.04 only needs them for some chips. If nVidia you probably need nomodeset. It Intel it should just work.

Did you verify download with md5sum?
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

        Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by skylar2 on 2014-04-26
I did download the 64 bit version, and I just turned off fast boot.

I have the new 
[LIST]
[*][FONT=arial]Intel Core i7 4700MQ (2.40GHz). My graphics card is the [/FONT]NVIDIA GeForce GTX 765M 2GB GDDR5.
[/LIST]

I feel I need to stress that I am installing the operating system itself onto the flash drive, not just installing a downloader on it that will allow me to download it for my laptop. I also currently have no access to the Ubuntu operating system (so I can't access its programs) due to the fact that this is the first time I've tried to install it.

Thanks so much!

---

### Post by oldfred on 2014-04-26
If you want a full install on a flash drive, these are good instructions. You can install from one smaller flash drive as the install media to another flash drive or hard drive. And you do not have to make it both UEFI & BIOS. But if Windows is UEFI, often easier to dual boot if Ubuntu is also UEFI.

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

