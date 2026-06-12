---
title: "Having Trouble with Ubuntu Dual Boot"
date: 2014-06-17
forum: New to Ubuntu
---

### Post by Jack_Ryan on 2014-06-17
Hello, 
I am honestly extremely new to Linux and have never used it before. I have a Lenovo IdeaPad Y500 and I tried to download Ubuntu Linux for Windows 8 last night and something went wrong. My C drive is Windows 8 and has over 800 GB of free space, my D drive is some random Lenovo drive with 22 GB free out of 25 GB (I don't even know what this drive is for). But when I downloaded the Linux it created a DVD E:// drive and it says 0MB free of 897MB. I tried to use Wubi to reboot the computer to load Ubuntu and it just gave me some firmware message that the OS doesn't exist or something along those lines. Does anyone know if there is some very obvious step that I am missing here? I apologize for sounding so inexperienced. Any insight will be greatly appreciated. 
Thanks, 
Jack

---

### Post by Jack_Ryan on 2014-06-17
Also I am willing to do research on whatever you reply with, and if you recommend booting from a USB I can also go to the store and buy one no problem. Just please help! :D

---

### Post by Bucky Ball on 2014-06-17
Welcome. Please forget about Wubi. That is not a dual-boot, that is Ubuntu inside Windows like any other program and is, as of recently, no longer supported here (or by Canonical). Please refer here:

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Now, if you'd like to talk about a dual-boot ... ;)

Firstly, boot into Windows 8 and shrink that C: drive. But before firstly, sit somewhere with a pencil, paper and beverage of choice and work out how you're going to go about dividing up the drive. How much do you need to shrink the Win partition. Oh, and always make sure you defragment the Win partition two or three times before shrinking. Essential. Power Defrag has more grunt than the default probably:

[http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml)

And always use the Win 8 software to do it (NOT Ubuntu's Gparted). When you've shrunk that partition, leave the rest free/unallocated space. DON't create partitions. No point. Ubuntu uses EXT filesystem and Win can't create them (or understand them beyond knowing the partitions exist and are 'healthy'; Win can't natively read/write to EXT).  

Download the Ubuntu Desktop ISO from here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Or the torrent of either 12.04 LTS or 14.04 LTS from third section down here:

[http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

... and burn that to disk/USB using your Win disk image burning software. (Nero?)

Ubuntu needs at least two partitions. 

/ = where the OS and all your personal data and settings goes: EXT4 filesystem;
/swap = 2Gb fine - equivalent to Win pagefile: swap space. 

There are many options for partitioning. For instance, you might like / to be 20Gb, and have a /home partition for all your personal data so it is separate from the OS (this has its advantages). You might like to use symlinks to link from your /home folder (which is by default inside / if you don't create the mountpoint /home) to existing folders on another parition. 

Any further questions, fire away, but aim for defragging and shrinking Windows, leaving the rest free space and burning the Live DVD/USB. 

And DON'T forget to backup any valuable data before commencing shrinkage or installation! Good luck. ;)

---

### Post by Jack_Ryan on 2014-06-17
Thanks! Ok so just to get things straight... If I'm going to boot the OS from my 64GB flash drive, do I still need to Defrag and partition? Can't I just load everything Linux-related onto the flash drive and keep it as a totally seperate entity? So when I boot with the USB at startup then it will just load my Linux OS as well as all of my applications and files? Or maybe it doesn't work that way... I'm sorry I'm very new to the Linux scene and my laptop lacks a disk drive so that isn't an option.

---

### Post by Jack_Ryan on 2014-06-17
I sort of lost you when it came to the partitions to be honest... Is there some sort of guide I can read through to walk me through the process? I hoped there would be some total noob information in the Absolute Beginner section haha I am (in all sense of the phrase) an "Absolute Beginner."

---

### Post by Bucky Ball on 2014-06-17
You made absolutely no mention of a 64Gb USB dongle that I could see. You only talked about the, what looks like, 1Tb drive. Where has that gone?

Any how, you are after a persistent install to USB. There is a lot of stuff out there concerning it, guides, etc., but I know nothing about it, sorry.

This might get you started:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Good luck. I'll stay tuned ...

PS: > **Jack_Ryan said:**
> ... If I'm going to boot the OS from my 64GB flash drive, do I still need to Defrag and partition? Can't I just load everything Linux-related onto the flash drive and keep it as a totally seperate entity? So when I boot with the USB at startup then it will just load my Linux OS as well as all of my applications and files? 

All correct. It will work exactly like this. You could even use it on different machines, except there could be driver issues, specifically graphics and wireless. You can certainly set it up for your machine so it works reliably.

There will be a speed loss booting on USB. You might like to go for something lighter like Xubuntu or Lubuntu.

---

### Post by PondPuppy on 2014-06-17
Here's a pretty good guide to installing Ubuntu 14.04 as a dual-boot with Windows 8. [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html). It's authored by Gary Newell.

There are a few things to think about:

1. Backing up your Windows installation and data, and making recovery media just in case
2. Working with secure boot / UEFI
3. Working with the boot program (on my system, for instance, the Windows bootloader allows me either Windows or to chainload Grub2, which can boot my Linux installations)

4. It's not as complicated as it looks, so don't be discouraged!

---

### Post by oldfred on 2014-06-17
Good advice above.
Many more useful links in the link in my signature. May seem like too much but only the first few links are essential unless some of the special cases apply. Plus detail info on links for backup, partitioning and other issues. 

Some others with the same computer.

 Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

      
 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

---

### Post by Jack_Ryan on 2014-06-18
Hey everyone thanks for all the helpful responses, I'm already loving the support from this community! I managed to use pendrive to download Ubuntu's Linux onto my recently purchased 16GB SunDisk 3.0 USB. Although the download and installation seemed to go flawlessly, I went to try to boot up using the F2 boot menu but for whatever reason it keeps just booting my Windows 8 OS, I haven't gotten it to go to Linux yet... Is there something I am supposed to configure either in the USB or on the boot menu to allow me to boot up the USB's operating system? I tried changing the booting preference list with USB on top but that didn't really help. Maybe it has something to do with the "Secure Boot" or Legacy vs. UEFI? Thanks in advance for your advice! Looking forward to getting started with my first Linux distro. :)

---

### Post by oldfred on 2014-06-18
Have you checked booting from one time boot key often f12 but varies? Some systems need both boot order in BIOS and one time key to get Ubuntu to boot.

Also some work better with secure boot off, although Ubuntu has the Microsoft signing key and should work.

If you installed Ubuntu in Legacy mode you can only boot from UEFI menu. Legacy/BIOS/CSM is not compatible with UEFI, so once you start booting in one mode you cannot change. And you may have to turn on or off UEFI or CSM mode in UEFI before changing to boot another system in different mode.

Post link to BootInfo report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Jack_Ryan on 2014-06-19
UPDATE: I seem to be getting closer and closer! I went to dual boot last night and it opened up an odd black firmware-looking screen that had the option to "Try Ubuntu without Installing." I thought at long last it was finally going to work!

Turns out after I click enter all I get is a dark blank screen, no sounds, no display. Just blank. I feel like I am so close to finally getting it working! I wonder if I should re-download the ISO file and start the process over maybe now that I'm more aware of what I am doing? Any advice would be great, hopefully there is a quick fix or a step that I missed somewhere. 

Thanks in advance! :p

---

### Post by oldfred on 2014-06-19
The links in post #8 discuss some of the issues.
It looks like you have dual video? And it boots with nVidia by default which needs nomodeset until proprietary driver is installed.

I have an old desktop with nVidia 9600GT and have to use nomodeset. Some laptops also just start with brightness at 0 and have to turn it up.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub menu) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by Jack_Ryan on 2014-06-19
Oldfred you are officially my savior! Proud to say I am now typing this response on my brand new Ubuntu Linux OS! Thanks for all the help, looking forward to learning Linux, see you around the forums. 
I'll look around for a way to close this thread but if you see it soon go ahead and close it for me. Thanks for your help again. 
-Jack

---

### Post by Bucky Ball on 2014-06-19
We don't close 'em here. We mark as solved to help future travellers. Glad you got it working and good luck. Enjoy!

Please post new threads with descriptive titles and in the appropriate forum for any future support requests. :)

---

