---
title: "Dual Boot Windows 7 &amp; Ubuntu 12.04 LTS"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by DejaBOOM on 2013-03-12
Hello all:

I'm a noob to Linux, but would consider myself fairly well-versed in Windows.  I recently decided to take the plunge and check out Linux, particularly Ubuntu.  From what I hear, Ubuntu 12.04 LTS is a very stable version of Ubuntu compared to the newest and previous versions.  If you don't believe so or have some suggestions, please feel free to share!  But I digress...

The real reason I'm posting this is to figure out why I cannot create a dual boot setup of Windows 7 and Ubuntu 12.04 LTS.  I have already had Windows 7 installed on my machine for a couple of weeks now (I recently did a reformat and fresh install because I purchased a 500GB SSD and installed Windows 7 and my programs on it).  So, for the past couple of days I've been looking around to see which versions of Linux are the most attractive and stable and so far I've discovered:  Ubuntu 12.04 LTS (obviously), Linux Mint 14 Cinnamon, Elementary OS, and Zorin OS 6 Ultimate.  So, to start out my journey I thought I would stick to Ubuntu and see how it goes as I learn more about Linux.  So here's what my PC looks like:

ASRock Z77 Fatal1ty Professional Mobo
[Intel Core i7-3770K Ivy Bridge 3.5GHz (3.9GHz Turbo)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116501") Quad Core CPU
[XIGMATEK Aegir Mega Killer CPU Cooler]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835233087")
[KINGWIN Lazer 1000W Modular]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817121068") PSU
EVGA [SuperClocked GeForce GTX 570 (Fermi) 1280MB 320-bit GDDR5]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130595")
[CORSAIR Vengeance 16GB (4 x 4GB) 240-Pin DDR3 1600 (PC3 12800)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820145347")
Samsung 840 Series 500GB SSD (used for Windows 7 OS and programs)
[Seagate SV35 Series 1TB 7200 RPM Internal SATA]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148912") HDD (used for storing docs, pics, random crap, etc.)
Fantom 2TB External HDD

In Windows 7, I downloaded a little program called unetbootin, formatted a 2GB USB flash drive, and used unetbootin to create a bootable copy of Ubuntu 12.04 LTS for installation on my PC.  Since I already put Windows 7 on the SDD I wanted to install Ubuntu on the 1TB internal HDD.    I went under **Start** --> (right clicked on) **Computer** --> **Manage** --> **Disk Management**.  I chose to shrink the 1TB HDD to create a 100GB unallocated partition which I would use for Ubuntu purposes.  I restarted my PC, hit F11 to get to boot options, and chose to boot to the bootable USB I created with the Ubuntu installer on it.  First I tried the 'Try Ubuntu before installing' feature to make sure it worked and it did.  So, I rebooted and went back to Ubuntu installation menu and chose to install Ubuntu. However, when it came time to choose one of the options for where to install I noticed the window displayed the message "Ubuntu found no other OS on this computer" listed across the top.  I was only given the options of:  **Erase Disk and Install Ubuntu** or **Something Else**.  There was **NO** option **Install Ubuntu Along Side Windows 7 **provided.

I tried going back to Windows under Disk Management and creating a partition on the 500GB SSD (same partition Windows 7 boots from) and went through the exact same install steps to only find the exact same results.  Now even though each time I was not given the option to Install Ubuntu Along Side Windows 7 I still installed Ubuntu on the partitions I created.  Each time I did so by selecting the option **Something Else** and I created a 2GB swap partition, a 10GB root partition, and the remaining free space as the home partition.  Each time I did this the install went all the way through with no errors.  When the install finished it prompted me to reboot.  When the computer rebooted, however, it went straight to Windows 7 login each time.

I tried going into the BIOS and selecting different boot priorities, but they did not seem to matter.  I tried selecting the Boot Manager as having priority and that did not work, so then I tried going back to my SSD booting first and so on and so forth and nothing really made any difference.  I'm really not sure what is happening that Ubuntu is not recognizing Windows 7 as already being on my machine.  Any help any of you can give me is greatly appreciated.  Sorry this post was so long, but I wanted to be very thorough in explaining all the things I have tried.

---

### Post by arpanaut on 2013-03-12
Sounds like the Grub bootloader did not get installed properly.
Take a look at this link: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can install this in the live session "try" or you can dl the iso and put it on a usb and run the boot repair program,
at the end it will give you a pastebin link, copy and paste it here and that will give quite a bit of information to help solve this problem.

---

### Post by siddharth007 on 2013-03-13
I would suggest you run a virtual machine inside your Windows OS and run Ubuntu inside it.You can try [VMWare-Player]("http://www.vmware.com/products/player/") Its simple and easy.You can also follow this [link]("http://www.howtogeek.com/howto/11287/how-to-run-ubuntu-in-windows-7-with-vmware-player/")

---

### Post by newb85 on 2013-03-13
It sounds to me like you selected the 1TB HDD as the "Device for boot loader installation" when you installed Ubuntu, but your BIOS is still set to boot from the 500GB SSD.  These need to be the same.

---

### Post by DejaBOOM on 2013-03-13
> **newb85 said:**
> It sounds to me like you selected the 1TB HDD as the "Device for boot loader installation" when you installed Ubuntu, but your BIOS is still set to boot from the 500GB SSD.  These need to be the same.

I did try installing Ubuntu on the 500GB SSD (as I mentioned above) and it still did the same thing. Not to mention I also read somewhere that you could install Windows and Ubuntu on separate hard drives on the same machine, so why would it matter if both OSs are installed on the same drive I wonder? (I'm still trying to understand the dynamics of dual booting.)

---

### Post by fantab on 2013-03-13
OS on a SSD boots faster compared to that on HDD. That is why folks here who have SSD install their OS on SSD and the DATA on HDD.

YES, you can install any number of OS on any number of Hard Disks. 

You have windows installed on SSD, which means your Windows boot loader is installed on the SSD. If and when you install Ubuntu on the same SSD on a separate partition then Ubuntu/Linux will install its boot loader, GRUB on the SSD overwriting the Windows boot loader. This isn't an issue because GRUB can flawlessly boot Windows. But Windows boot loader cannot, AFAIK, boot Linux. If you want your Windows Boot Loader intact then you have no other option but to install Ubuntu and GRUB on HDD. But then you have change the Boot Order of your HDD in the BIOS to boot your HDD first, so that GRUB loads at boot and presents you an option to choose your OS. Since you have 500GB SSD, I would recommend that you install both OS on it.

If your Ubuntu install cannot see your SSD then there is some problem with the file system on your SSD. It could be anything. Does your machine has [**UEFI**]("https://help.ubuntu.com/community/UEFIBooting")? What is the [**Partition table**]("https://en.wikipedia.org/wiki/Partition_table") on your HDD? You can use Gparted, present your Ubuntu install media to find out what partition table it is using. There are tools to fix file system issues, if only we know for sure that it is a filesystem issue.

Edit: A similar problem was discussed [**HERE**]("http://ubuntuforums.org/showthread.php?t=1829035"), you might find it useful. Ask if you have doubts.

Good Luck...

---

### Post by Bucky Ball on 2013-03-13
Hit 'Something Else'. You want to install Ubuntu to the free 100Gb space anyway and that won't happen by default. Do it manually and set up the partitions and where to install that way. 

Don't bother creating a 100Gb partition for Ubuntu using Windows. Just leave free space. Ubuntu uses EXT* partitions and Windows can't create them. Ubuntu WON'T install on an NTFS or FAT partition. Windows also doesn't recognise EXT partitions so if you want to share info between Win and Ubuntu you are going to need a /share partition also. You can set that up manually by using 'Something Else'. (It doesn't have to be /share; you can call it what you like.)

You need to plan it if partitioning manually. You don't need 100Gb for the Ubuntu install, you'll only need about 20Gb (I've never used more than 15Gb). If you are intending to store all your personal data in there too, naturally it will need to be bigger, but with that mega setup that's not a good idea. Store all that stuff on another partition away from the Ubuntu partition (/). Ubuntu has no problem reading NTFS or FAT.

---

### Post by oldfred on 2013-03-13
With multiple drives & multiple installs, it is best to see details. If just a boot loader issue or many other issues it can also fix those issues. You can install into your current Ubuntu flash drive installer or download a full repair ISO.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by DejaBOOM on 2013-03-13
Correct if I am wrong (I am new to partition tables and their formats), but from what I see Windows 7 has a GUID partition table style which is UEFI.  Does this mean I need to convert from UEFI to MBR?

---

### Post by oldfred on 2013-03-13
It depends on which you want, but both Ubutnu & Windows need to be UEFI or BIOS based boot.

Windows only boots from gpt drives with UEFI.
Ubuntu will boot from gpt drives with either UEFI or BIOS.
If you want Windows in BIOS mode you have to reinstall with MBR partitioning and Windows does not correctly erase the backup gpt partition table so you have to use fixparts to erase the backup.

If you installed Ubuntu with gpt partitioning, Boot-Repair can convert to UEFI boot by un-installing grub-pc and installing grub-efi.

Best to see details, but it depends a lot on which you prefer. The new but not as well known UEFI with gpt partitiong, or the 30 year old but known BIOS with MBR(msdos) partitioning.

       Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by DejaBOOM on 2013-03-13
How can I get details then?  What would be your best recommendation?  Any specific tool I should use?  Any specific things I should be mindful and keep an eye out for?  Are there any logs I should be looking for?  Sorry, I am still very new to this.  I will try to do some more reading up on partitions, partition tables and how they operate.

---

### Post by DejaBOOM on 2013-03-13
I also found this, would this work?:

[h=2]"Identifying if the computer boots the HDD in EFI mode[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]This is possible only if you have already installed Ubuntu on the HDD, or by looking at the BIOS setup (see paragraph below).[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]From an Ubuntu installed on the HDD (neither liveCD nor liveUSB), open a terminal (Ctrl+Alt+T), then type the following command:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu] [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Remark: if the result is "Legacy boot on HDD", then either the BIOS is not UEFI type, or the BIOS is not set up to boot the HDD in UEFI mode."[/FONT][/COLOR]

---

### Post by fantab on 2013-03-13
The help you need to get "details" is provided as links in [oldfred's post #8]("http://ubuntuforums.org/showthread.php?t=2125070&p=12555800#post12555800"). Follow the instructions provided on those links and post back.

---

