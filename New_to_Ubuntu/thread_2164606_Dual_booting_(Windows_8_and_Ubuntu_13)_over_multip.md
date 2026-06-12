---
title: "Dual booting (Windows 8 and Ubuntu 13) over multiple drives"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by Jacob_Marshall on 2013-08-01
Hey, I'm really fond of Ubuntu, and I use it a lot through VM, however I am looking to install Ubuntu onto one of my physical drives in order to create a dual boot with Windows 8. I currently have 3 drives, SSD-Windows 8, HDD1-Storage, HDD2-Empty... I was looking at putting the installation of Ubuntu onto the HDD2 drive, however I was concerned about the way I would boot into each OS at startup. I would preferably like to keep Ubuntu away from the SSD at all costs, because it has a lot of work put into it, however HDD1 would be great as a sort of shared desk between the two installations.

Currently I boot straight into Windows 8 without any prompt, and because I'm an utter newbie with the technical side of Linux OSs, I wanted to first get an opinion from somebody who knows more about it than myself. I'd really love to know what is possible, the issues that this kind of setup may create and any other points that I may be missing.

I have a relatively high end PC, I have an Intel Core i7 (Ivy Bridge, 3.5Ghz), 16GB ram (2400Mhz), EVGA Nvidia GeForce GTX 680 Classified (1111Mhz, 4GB), and I am unsure if these details may prevent me from installing Ubuntu all together.

I really want to thank you in advanced for your support, these forums have helped me tremendously in the past, and you guys have a fantastic community. I'm grateful for anything you're able to provide me with, I do not expect any single one person to obtain all the answers :)

Cheers,
Jacob

---

### Post by Vladlenin5000 on 2013-08-01
The first thing to "worry" about is whether you have the already installed OS (Windows in your case) with UEFI or not. Please read (and understand) this before anything else:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Vladlenin5000 on 2013-08-01
This thread may also be helpful: [http://ubuntuforums.org/showthread.php?t=2164671](http://ubuntuforums.org/showthread.php?t=2164671)
The user apparently didn't follow the correct instructions mentioned before. If it happens to you there are good solutions discussed there.

---

### Post by oldfred on 2013-08-01
With multiple drives you need to partition and configure the Ubuntu drive the same as your Windows. If Windows is BIOS mode, you need Ubuntu in BIOS mode. If Windows is in UEFI mode then Ubuntu needs to be in UEFI mode. And with a new system like you have, you have UEFI but it has a compatibility CSM/Legacy/BIOS mode that is just like the old BIOS. 
Ubuntu will install in the mode that you boot install flash drive. So if you boot flash drive in UEFI mode it installs in UEFI mode. With nVidia you will need nomodeset either from accessiblity screen with BIOS or manually add to grub menu when you boot with UEFI.

You should partition drive with gpt partitioning even if Windows is BIOS as Ubuntu can use gpt with either UEFI or BIOS. Windows only boots from gpt partitioned drives with UEFI and both Ubuntu & Windows only Boot from MBR(msdos) partitioned drives with BIOS.

You need to have efi partition on your Ubuntu drive, but if booting from Windows drive it may install another folder into that efi partition. It will not modify the Windows folder. One advantage of UEFI is that each efi folder is like having mulitiple MBR's with different boot loaders. But with multiple drives you can also have multiple ESP or one efi partition on each drive.

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
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

   But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Links to how several users installed to a second drive with UEFI in the link in my signature.

If booting with BIOS press any key as soon as icons appear at bottom of screen and use f6 to add nomodeset. 
If booting with UEFI you get grub menu like after install and have to add nomodeset by editing grub menu. Use e and scroll to linux line. Replace quiet splash with nomodeset.
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by Jacob_Marshall on 2013-08-01
> **oldfred said:**
> With multiple drives you need to partition and configure the Ubuntu drive the same as your Windows. If Windows is BIOS mode, you need Ubuntu in BIOS mode. If Windows is in UEFI mode then Ubuntu needs to be in UEFI mode. And with a new system like you have, you have UEFI but it has a compatibility CSM/Legacy/BIOS mode that is just like the old BIOS. [...]

Thank you for all of that information, I will take my time in reading over all of the resources provided in order to assist with my lack of knowledge in this area. I will check back in once/if I have more questions.

> **Vladlenin5000 said:**
> The first thing to "worry" about is  whether you have the already installed OS (Windows in your case) with  UEFI or not. Please read (and understand) this before anything else:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Thank you so much for this information, I will give it a check out as it seems to be extremely important knowledge.

> **Vladlenin5000 said:**
> This thread may also be helpful: [http://ubuntuforums.org/showthread.php?t=2164671](http://ubuntuforums.org/showthread.php?t=2164671)
The user apparently didn't follow the correct instructions mentioned  before. If it happens to you there are good solutions discussed  there.

Thank you very much, I'll try and make sure that I do not do follow in the same footsteps :P

Cheers guys!

---

