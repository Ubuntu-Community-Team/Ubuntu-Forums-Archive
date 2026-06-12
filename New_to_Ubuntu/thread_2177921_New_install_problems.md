---
title: "New install problems"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by Zachary_Kaiser on 2013-10-01
I have a computer with 300 GB of SSD space (C: )and a 1 TB (D: )HDD. I recently tried to install ubuntu onto my 1 Tb HDD by booting from a flash drive and choosing the erase all data option and directed it to my HDD because it was not detecting that I had windows and for some reason my HDD already had partitions. The install was successful, but when I reboot it does not show me the grub and just boots to Windows on my SSD. Even weirder when I do advanced boot up (windows 8 options) and click ubuntu under the device menu, it dosen't get past the loading screen and eventually black screens. I have tried using boot repair with my flash drive version to no avail (it didn't even download) and tried to create a grub using EasyBCD.
I don't know if this is helpful but my boot menu (from BCD)
Entry #1
Name: ubuntu
BCD ID: {b30d1691-2a6f-11e3-be99-806e6f6e6963}
Device: \Device\HarddiskVolume2
Bootloader Path: \EFI\ubuntu\shimx64.efi


Entry #2
Name: ubuntu
BCD ID: {b30d1692-2a6f-11e3-be99-806e6f6e6963}
Device: \Device\HarddiskVolume2
Bootloader Path: \EFI\Ubuntu\grubx64.efi


Entry #3
Name: UEFI: Network IPv4 Device 
BCD ID: {c34dac46-afbb-11e2-be7b-806e6f6e6963}
Device: Unknown
Bootloader Path: 


Entry #4
Name: UEFI: Network IPv6 Device 
BCD ID: {c34dac47-afbb-11e2-be7b-806e6f6e6963}
Device: Unknown
Bootloader Path: 


Entry #5
Name: Windows 8
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.efi

---

### Post by sharathcshekhar on 2013-10-01
The first issue you have raised, is not a problem at all. By default the windows boot loader will boot into ubuntu unless you go to the menu and change the boot device. From the next boot, I think you will boot into the OS you booted last time (I am not sure of this)
The second issue, might be because of your graphics driver problems. Can you turn off the "quiet splash" option in the kernel menu and boot into ubuntu and post the logs here? If not me, someone who is more well versed can help you. 
Before that, as a wild guess, try passing "nomodeset" param for the kernel and see if this resolves your issue.

---

### Post by Zachary_Kaiser on 2013-10-01
My computer is not booting into ubuntu but to windows 8 (on my SSD). Where can I go to change the boot menu? Also, could I install the drivers using try ubuntu on my flash drive?

---

### Post by whitesmith on 2013-10-01
> **Zachary_Kaiser said:**
> I have a computer with 300 GB of SSD space (C: )and a 1 TB (D: )HDD.First, we need to know your goal. Do you want to have Ubuntu on your system by itself, or do you want a dual-boot system with both? I suspect the second is your intention. Either way, I would put the operating system or systems on the SSD. These devices are much faster than conventional HDDs with moving parts. Give us more information and then we can offer solutions.

---

### Post by Zachary_Kaiser on 2013-10-01
I play alot of PC games so I wanted to have windows 8 on my SSD. I pretty much need the full SSD for my games because of the size. (I want them on the SSD for performance). I want to put Linux onto my 1 Tb HDD and use this OS as my normal operating system (internet work everything that isn' t a game). Speed isn't really an issue my normal operating system because my HDD has a decent speed (7200 rpm I believe).

In summary
SSD -->Windows 8 for gaming
HDD --> Linux for everything else

---

### Post by oldfred on 2013-10-01
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

I think boot repair should auto fix your system. But you may have to manually copy boot files from hard drive to SSD's efi partition. You do have efi partition on hard drive? Also have you looked in UEFI menu or one time boot key to see if you have an ubuntu entry?


 **Two Drive UEFI installs**
HP Envy 2 drive install i7 & 2 1TB drives
[http://ubuntuforums.org/showthread.php?t=2175877](http://ubuntuforums.org/showthread.php?t=2175877)
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

---

### Post by whitesmith on 2013-10-01
Here is what you need to know about dual-booting and partitioning: [https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions) It will  help you get started on the right foot. Which version of Ubuntu is best? I would recommend 12.04 LTS because of its stability and lifespan. How much RAM do you have, by the way?

---

### Post by Zachary_Kaiser on 2013-10-01
I have tried boot repair before, and for some reason the program didn't install (I was on try ubuntu). I am about to try it now, and will get back to you soon. I am writing this post to answer your question about efi partitions. I am posting a screen shot of my disk management setting on windows 8. Disk 0 is my SSD w/ windows 8 and Disk 1 is my HDD with Ubuntu
[https://docs.google.com/drawings/d/1DZWUDZFvHOALr9tkOFAvXoWBnem6zXrW6eNtjJUHhYY/edit?usp=sharing](https://docs.google.com/drawings/d/1DZWUDZFvHOALr9tkOFAvXoWBnem6zXrW6eNtjJUHhYY/edit?usp=sharing)

---

### Post by whitesmith on 2013-10-01
Don't forget to inform us about your memory. Insufficient RAM can cause issues. Other than that just follow **oldfred**'s advice. He knows what he's talking about.

---

### Post by Zachary_Kaiser on 2013-10-01
I just tried to install the boot repair and it did not install the command consle returned this
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.3%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20130820.1)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.3%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20130820.1)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I ran sudo apt-get update and got the same results

RAM shouldn't be a problem, I've got 32 Gb of it.
PS sorry about my noobishness I'm just learning how to really use a computer (not just surf the internet and download games lol)

---

### Post by oldfred on 2013-10-01
Did you install 32 bit?
UEFI only works with 64 bit version of Ubuntu.
The 32 bit version would only install in BIOS mode and you need UEFI boot mode if dual booting Windows in UEFI mode.
How new is system. The new Haswell really need the 13.10 even though it is still beta.

---

### Post by Zachary_Kaiser on 2013-10-01
My system is very new. It is an MSI GT70 and this version came out this June. I think I am going to download version 13 and use the erase all data and install option on my d-drive (currently it only has 12.04 LTS on it) Thanks for your help I well get back to you tomorrow to tell you if it worked or not. Sorry in advance for the probable double post.

---

