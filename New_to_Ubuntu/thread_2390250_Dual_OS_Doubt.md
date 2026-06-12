---
title: "Dual OS Doubt"
date: 2018-04-27
forum: New to Ubuntu
---

### Post by online-paystub on 2018-04-27
Hello everyone,

I m new to this forum and newbie in using Ubuntu os.
I recently bought new Dell Laptop and my doubt is that Can we install Win10 and Ubuntu on the same system?

---

### Post by Autodave on 2018-04-27
Yes you can: it is called dual-booting. In fact, some people here have 3 or more operating systems on the same machine.

---

### Post by Autodave on 2018-04-27
What you need to do first is to down load a version of Ubuntu that you want to try. Create a bootable medium: either DVD or USB stick. Next, boot the machine to the medium that you created and try it: don't install it yet. If everything works (Keep in mind that it will be much slower operating that way), then come back here for guidance on proceeding further with installation.

---

### Post by yancek on 2018-04-27
Start by reading the official Ubuntu Documentation on the subject at the link below:

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by online-paystub on 2018-04-28
Autodave, I know that we can run dual OS and I have used systems in my College with the dual os.

> **Autodave said:**
> Yes you can: it is called dual-booting. In fact, some people here have 3 or more operating systems on the same machine.

---

### Post by online-paystub on 2018-04-28
can I download ubuntu online and convert it to bootable USB? 
After we create a bootable drive, the installation process will be done automatically like Windows or do I need to enter some ubuntu commands? :confused:



> **Autodave said:**
> What you need to do first is to down load a version of Ubuntu that you want to try. Create a bootable medium: either DVD or USB stick. Next, boot the machine to the medium that you created and try it: don't install it yet. If everything works (Keep in mind that it will be much slower operating that way), then come back here for guidance on proceeding further with installation.

---

### Post by online-paystub on 2018-04-28
Thanks, Yancek for providing the source. I googled and got so many links but was scared to follow but thinking to give it a try.

> **yancek said:**
> Start by reading the official Ubuntu Documentation on the subject at the link below:

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by leunam12 on 2018-04-28
What you need to do is create a backup image of what you have installed on your computer right now either by using the native windows System Image Backup tool 
or a third party application such as Clonezilla. You are going to need a removable hard drive to store this backup image.
The next step is to shrink the Windows partition using the Disk management tool in Windows. the purpose of this is to free up some space in your hard drive
to install Ubuntu. Once you shrink the partition you have to run CHKDSK on the drive, otherwise you may encounter problems while installing Ubuntu.
After those 3 steps are completed now you can go to the Ubuntu official documentation for UEFI installation and follow the instructions there. You will have to chose "something
else" at installation and create the partitions that you need to install Ubuntu. I usually create three partitions: a small one for system files (mounted at /) I don't need more than
24GB for this one. Then I create a 2GB partition for SWAP at the end of the unallocated space. 
The third partition is for data and configuration files, this is the HOME partition and it is mounted at /home.

UEFI needs an EFI partition, follow the steps very carefully on the documentation. Feel free to experiment, if things go wrong and you mess things up all you have to do is restore the image that you 
created in the first step and everything will be just like it was originally.

---

### Post by online-paystub on 2018-04-30
Is it required to create a backup if someone is not using the licensed OS?


> **leunam12 said:**
> What you need to do is create a backup image of what you have installed on your computer right now either by using the native windows System Image Backup tool 
or a third party application such as Clonezilla. You are going to need a removable hard drive to store this backup image.
The next step is to shrink the Windows partition using the Disk management tool in Windows. the purpose of this is to free up some space in your hard drive
to install Ubuntu. Once you shrink the partition you have to run CHKDSK on the drive, otherwise you may encounter problems while installing Ubuntu.
After those 3 steps are completed now you can go to the Ubuntu official documentation for UEFI installation and follow the instructions there. You will have to chose "something
else" at installation and create the partitions that you need to install Ubuntu. I usually create three partitions: a small one for system files (mounted at /) I don't need more than
24GB for this one. Then I create a 2GB partition for SWAP at the end of the unallocated space. 
The third partition is for data and configuration files, this is the HOME partition and it is mounted at /home.

UEFI needs an EFI partition, follow the steps very carefully on the documentation. Feel free to experiment, if things go wrong and you mess things up all you have to do is restore the image that you 
created in the first step and everything will be just like it was originally.

---

### Post by leunam12 on 2018-05-02
You only need a backup if you want to be able to revert to your original configuration in case something goes wrong. You can easily delete or wipe out a partition if you don't know exactly what you are doing.

---

### Post by oldrocker99 on 2018-05-02
From 2011 to 2013, I dual-booted, and the **only** problems I had were with Windows 7.

Once Steam for Linux came out, I deep-sixed that malware magnet and have been 100% Linux since then.

---

### Post by hrsetrdr on 2018-05-02
> **online-paystub said:**
> Is it required to create a backup if someone is not using the licensed OS?

Required?   Can't see why.

I didn'tt have a use for Windows[10] so when I got my Dell Inspiron 15 7567 I just blew it off the hard-drive.

However, later on I _did_ need Windows to update the BIOS, as updates were Windows executables *only*.  So I went to the Dell support site and downloaded the [Dell OS Recovery Image]("http://www.dell.com/support/article/us/en/19/sln299044/how-to-download-and-use-the-dell-os-recovery-image-in-microsoft-windows?lang=en"). Installed it on the original hybrid hdd, did my BIOS updates, then removed the drive and archived it.

I picked up a nice uber fast [Samsung 960 EVO M.2 nvme]("https://express.google.com/product/8637638234672005030_5821909300542685024_6136318?mall=Rockies1&directCheckout=1&utm_source=google_shopping&utm_medium=product_ads&utm_campaign=gsx&dclid=CODIncTA6NoCFYSIYgod-2kAQQ") drive for the Dell, boot up crazy fast.

---

### Post by online-paystub on 2018-05-03
Okay so let me take a backup of my OS then I will be back. 
Thanks, leunam12. :D

> **leunam12 said:**
> You only need a backup if you want to be able to revert to your original configuration in case something goes wrong. You can easily delete or wipe out a partition if you don't know exactly what you are doing.

---

### Post by online-paystub on 2018-05-03
The person told me that even if you install the dual OS, the Ubuntu won't run on full screen. :(


> **oldrocker99 said:**
> From 2011 to 2013, I dual-booted, and the **only** problems I had were with Windows 7.

Once Steam for Linux came out, I deep-sixed that malware magnet and have been 100% Linux since then.

---

### Post by online-paystub on 2018-05-03
This seems cool. Thanks, hrsetrdr. 
but by installing Dell OS Recovery image, will it make our OS genuine if the Original OS was licensed?



> **hrsetrdr said:**
> Required? Can't see why.

I didn'tt have a use for Windows[10] so when I got my Dell Inspiron 15 7567 I just blew it off the hard-drive.

However, later on I _did_ need Windows to update the BIOS, as updates were Windows executables *only*. So I went to the Dell support site and downloaded the [Dell OS Recovery Image]("http://www.dell.com/support/article/us/en/19/sln299044/how-to-download-and-use-the-dell-os-recovery-image-in-microsoft-windows?lang=en"). Installed it on the original hybrid hdd, did my BIOS updates, then removed the drive and archived it.

I picked up a nice uber fast [Samsung 960 EVO M.2 nvme]("https://express.google.com/product/8637638234672005030_5821909300542685024_6136318?mall=Rockies1&directCheckout=1&utm_source=google_shopping&utm_medium=product_ads&utm_campaign=gsx&dclid=CODIncTA6NoCFYSIYgod-2kAQQ") drive for the Dell, boot up crazy fast.

---

### Post by online-paystub on 2018-05-04
leunam12, Done with backup. what next sir? :KS

---

### Post by online-paystub on 2018-05-04
Hey, @hrsetrdr

Reading the Guide given on Dell OS Recovery Image. it is quite tough for the non-IT background people.

but with the help of you all, I will succeed.

---

### Post by leunam12 on 2018-05-04
The next step is to make room on your hard drive for the Ubuntu installation; you have to shrink the partition where Windows is installed. 
The best way to do this is in Windows using the Disk management utility. After shrinking the partition you have to run CHKDSK. The next step after that is to boot from your Ubuntu USB stick to install it. Make sure you read an understand the official documentation for booting and installing in UEFI mode.

---

### Post by oldfred on 2018-05-04
Your Dell has its product key inside the UEFI, so if you reinstall Windows in UEFI mode, it will automatically use that license.
       Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key) 
    
If a Dell you may need to change UEFI drive setting from RAID to AHCI. But install AHCI driver into Windows first as it does not have that driver.
       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en) 
    
See also link in my signature. 9 easy steps to install :) 
And if you do not understand any step link to lots more info.
I found with my Dell it wanted a Windows backup, a Dell Backup and I did a full backup with Macruim Reflect. Backups took several days as I had to run to store for more flash drives. After shrinking Windows, actual install took 10 Minutes.

---

### Post by deanr2 on 2018-05-05
[COLOR=#000000]*After those 3 steps are completed now you can go to the Ubuntu official documentation for UEFI installation and follow the instructions there. You will have to chose "something*[/COLOR]
[COLOR=#000000]*else" at installation and create the partitions that you need to install Ubuntu. I usually create three partitions: a small one for system files (mounted at /) I don't need more than*[/COLOR]
[COLOR=#000000]*24GB for this one. Then I create a 2GB partition for SWAP at the end of the unallocated space. *[/COLOR]
[COLOR=#000000]*The third partition is for data and configuration files, this is the HOME partition and it is mounted at /home.*[/COLOR]

This is one of the scariest things to do as a newbie in my experience and took a lot of nerve and watching and re-watching of YouTube videos along with countless failures.

And then I learned that you can just create free space in Windows and the Ubuntu installation will automatically install in that free space when you select the 'Install alongside windows' option. Alternatively, you can resize during the installation with a simple graphical slider. Swap space automatically installs as the size of your RAM, I believe, and grubs and boot menus etc. are all taken care of.

It seems to be taken for granted by many Ubuntu/Linux users that resizing partitions and creating home & swap drives manually is easy. Personally speaking it is not and there are easier and more foolproof ways imo opinion creating a dual boot PC. 

Just my pennies worth!

---

### Post by hier-kommt-luis on 2018-05-08
Yes, it's possible, but make sure you don't run Ubuntu installation in UEFI mode instead of Legacy - it will cut you a lot of headache

---

### Post by online-paystub on 2018-06-06
Yeah, I am familiar with shrinking as I formatted my old windows system and changed the allocated drive space with the help of disk management utility.


> **leunam12 said:**
> The next step is to make room on your hard drive for the Ubuntu installation; you have to shrink the partition where Windows is installed. 
The best way to do this is in Windows using the Disk management utility. After shrinking the partition you have to run CHKDSK. The next step after that is to boot from your Ubuntu USB stick to install it. Make sure you read an understand the official documentation for booting and installing in UEFI mode.


> **hier-kommt-luis said:**
> Yes, it's possible, but make sure you don't run Ubuntu installation in UEFI mode instead of Legacy - it will cut you a lot of headache

okay I will take care of it. :)

---

### Post by oldfred on 2018-06-06
Actually you really want Ubuntu installed in the same boot mode as Windows whether UEFI or BIOS/Legacy/CSM boot mode. That avoids issues and allows you to dual boot from grub.
If not in same boot mode you can only dual boot UEFI Windows and BIOS Ubuntu from UEFI boot menu.

UEFI and BIOS are not compatible. They write hardware info onto hard drive differently for operating system to use. Or once you start booting in one mode, you cannot change. And then grub can only boot other systems in the same boot mode.

---

