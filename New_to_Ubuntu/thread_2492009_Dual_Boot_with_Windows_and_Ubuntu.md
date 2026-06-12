---
title: "Dual Boot with Windows and Ubuntu"
date: 2023-10-27
forum: New to Ubuntu
---

### Post by teotjunk on 2023-10-27
My plan is to do this. Install Windows on my main hard disk. Install ubuntu on the second harddisk.

My understanding is that if I install Grub 2 win on the windows partition, it will allow me to choose which OS to use. Do I have to install the Grub boot loader on the windows partition first or would installing Grub 2 win on the windows partition would be sufficient?

---

### Post by tea for one on 2023-10-27
After you have installed and checked Windows on your first disk:-

Disconnect, de-activate, isolate via UEFI settings or physically remove existing Windows OS drive so that only the target drive is accessible
Boot Ubuntu live and check that you are in UEFI mode
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Create GPT on your target disk using gparted
Open gparted > Device > Create Partition Table > Select gpt

If you cannot isolate your Windows 10/11 drive, you can hide the existing EFI partition.
Gparted > Right click Windows EFI Partition > Manage Flags > Uncheck boot & esp and check hidden (msfdata will be checked automatically – not a problem)
Don’t forget to reset the flags to original settings after installing Ubuntu to 2nd disk

Create an EFI partition and System / partition (or double check that they will be created automagically)
Boot loader on target disk

Boot each system independently via UEFI boot screen (ideal not cumbersome)
Boot priority can be controlled by UEFI
Each OS should be installed in UEFI mode with GPT
Each drive should have an EFI partition
Each drive should have boot manager (Windows Boot Manager and Grub for Ubuntu)

De-activate, disconnect, isolate or physically remove one drive so that you can check if the other boots independently (and vice versa)

---

### Post by teotjunk on 2023-10-27
Are you saying this is preferable to using Grub 2 Win

---

### Post by tea for one on 2023-10-27
I have no experience of Grub 2 Win.
I was simply suggesting an alternative approach.

---

### Post by teotjunk on 2023-10-28
I have a question. If I install Windows First on the first hard disk and Ubuntu on the second hard disk without installing any additional software what would happen when I start the computer

---

### Post by yancek on 2023-10-28
You have not indicated which release of windows you are going to install.  Is it windows 11?  Are your drives GPT?  If so, then the default install of windows will be UEFI mode.  Are you familiar with UEFI?

If you are going to be installing windows on a separate drive from Ubuntu, you should be able to boot either by selecting the specific drive in the BIOS.  If you want to be able to boot both from the same bootloader, you will need both in UEFI mode or if windows is Legacy mode, both in Legacy mode.  The expectation would be both installed in UEFI mode and you can use Grub2 on Ubuntu to do this.  When you start to install Ubuntu, make sure if windows is UEFI on a GPT disk that you boot the Ubuntu install media in UEFI mode.  That will show in your BIOS firmware.

Never used Grub 2 win and don't know why you would want a modified version of Grub when you have the original, your choice if you're familiar with it.

---

### Post by teotjunk on 2023-10-28
> **yancek said:**
> You have not indicated which release of windows you are going to install.  Is it windows 11?  Are your drives GPT?  If so, then the default install of windows will be UEFI mode.  Are you familiar with UEFI?

If you are going to be installing windows on a separate drive from Ubuntu, you should be able to boot either by selecting the specific drive in the BIOS.  If you want to be able to boot both from the same bootloader, you will need both in UEFI mode or if windows is Legacy mode, both in Legacy mode.  The expectation would be both installed in UEFI mode and you can use Grub2 on Ubuntu to do this.  When you start to install Ubuntu, make sure if windows is UEFI on a GPT disk that you boot the Ubuntu install media in UEFI mode.  That will show in your BIOS firmware.


I am going to install Windows 11
Never used Grub 2 win and don't know why you would want a modified version of Grub when you have the original, your choice if you're familiar with it.

I checked my Disk Mangement and it says my system is EFI system partition which I presume is UEFI. Nope I am not familar with UEFI. How do I check if my Drive is GPT and UEFI.

My understanding is that if I install Windows First and then Ubuntu. Then whenever I boot, it I will get a basic screen to chose either windows or ubuntu

---

### Post by yancek on 2023-10-29
You can determine if your computer has a GPT drive and is EFI with the command below from a terminal when booting the Ubuntu install USB:

```
sudo parted -l
```

The output should show 'Partition Table: gpt' as well as showing a partition marked as EFI.  Example output from my system, yours will probably be different but it should show a partiition marked as EFI as shown below.  The parted command has a lower case letter L and not a a number 1. 

```
 1      1049kB  274MB   273MB   fat32        EFI system partition          boot, esp
```

If you want windows and Ubuntu separate, you need to create an EFI partition on the drive on which you are installing Ubuntu.  It will simplify things for you if you can disconnect the windows drive before installing Ubuntu.

If windows and Ubuntu are installed on separate drives, you can select the windows drive in the BIOS on boot to boot it and the Ubuntu drive to boot it.  When installing Ubuntu, it will install Grub and it should/might detect windows on the other drive and create an entry for windows which you will see when you boot.   You may need to enable os-prober on Ubuntu to get windows and you may also need to go into the BIOS firmware after installing Ubuntu to set Ubuntu as first in boot priority.

---

### Post by teotjunk on 2023-10-29
Suppose I already have windows on my main hard drive. then I start the computer, interrupt the bios to start from a usb drive which I already have unbuntu installation on it, then direct it to install on the second hard drive. is there anything else I need to do?

---

### Post by jeremy31 on 2023-10-29
I would remove the drive with Windows and install Ubuntu on the new drive, reboot and see if it works.  Then put the Windows drive back in and see if Ubuntu boots.  If Ubuntu boots, in terminal
```
gedit admin:///etc/default/grub
```
You will likely have to enter your password twice, add this line to the file
```
GRUB_DISABLE_OS_PROBER=false
```
Save and exit the text editor, then in terminal
```
sudo update-grub
```
Reboot and test the Windows option in the grub menu

---

### Post by teotjunk on 2023-11-03
My computer shop is installing the ubuntu for  me. If I don't remember wrongly when one installs ubuntu, they ask you for an admin password and create a user account. I think I can give them a temporary admin password which I can change later. Can the the creation of the user account be delayed to a later stage?

---

### Post by oldfred on 2023-11-03
I have seen a lot of users post computer shop installs, install in the old BIOS/MBR configuration as they do not really understand UEFI/gpt.

Normal install.
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

There is the OEM install which they should use. It install and first then you then have to do is create a user & password.
[https://devicetests.com/pre-install-ubuntu-oem-installation-guide](https://devicetests.com/pre-install-ubuntu-oem-installation-guide)

OEM mode so user can add name & password later:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install](http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install)
Perform end-user configuration after initial OEM installation 
 sudo apt-get install oem-config-gtk

If not installing to same drive and 22.04 or before or some flavors, make sure you understand this bug.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by teotjunk on 2023-11-04
> **oldfred said:**
> I have seen a lot of users post computer shop installs, install in the old BIOS/MBR configuration as they do not really understand UEFI/gpt.

Normal install.
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

There is the OEM install which they should use. It install and first then you then have to do is create a user & password.
[https://devicetests.com/pre-install-ubuntu-oem-installation-guide](https://devicetests.com/pre-install-ubuntu-oem-installation-guide)

OEM mode so user can add name & password later:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install](http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install)
Perform end-user configuration after initial OEM installation 
 sudo apt-get install oem-config-gtk

If not installing to same drive and 22.04 or before or some flavors, make sure you understand this bug.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

What would happen if they do the normal install of the OEM install?

---

### Post by oldfred on 2023-11-04
You can change id & password.
But I think if you are capable of changing id & password, you are capable of doing an install.
Its just follow the directions in links.

Also info in link in my signature, but some is more for major issues which you can skip.

---

### Post by teotjunk on 2023-11-04
> **oldfred said:**
> You can change id & password.
But I think if you are capable of changing id & password, you are capable of doing an install.
Its just follow the directions in links.

Also info in link in my signature, but some is more for major issues which you can skip.

Oh I have done installation of ubuntu before. Just never done it for dual boot. What id are we talking about? The user account?

---

### Post by yancek on 2023-11-05
When you install Ubuntu, you are required to create a user before the  installation completes.  If you are having someone do the install for  you, you can let them select a user name and a password and they can  inform you of what it is so you can boot and change it later.  You can  also give them a user name to create and a password and change the  password later.  You should verify that they are familiar with  installing Ubuntu in EFI mode in a dual boot situation before doling anything.

You have not indicated  which release of Ubuntu you are using.   If you want them separate, you  need to create an EFI partition on the second disk where you will install Ubuntu and install Grub EFI files there.  You must also verify that you are booting in EFI mode so that it is installed properly.  Some releases will install the  Ubuntu EFI files to the first partition on the first disk which will be  the disk you have with windows on it.   In this case, you will then need to create an EFI partition on the 2nd drive with Ubuntu and copy the EFI files for Ubuntu from the windows disk to the Ubuntu disk.

I'd suggest reviewing the links posted above by oldfred and reviewing some links on dual booting Ubuntu and windows EFI.  Newer computers will only install and boot EFI but if you have an older computer, you will have an option to boot the install USB in Legacy or EFI mode, so make sure you select EFI in the BIOS firmware.  

[https://linuxconfig.org/how-to-install-ubuntu-22-04-alongside-windows-10](https://linuxconfig.org/how-to-install-ubuntu-22-04-alongside-windows-10)

---

### Post by damidu on 2023-11-05
Hi,

I think you will have nothing to do, you are correct. First install Windows on the first drive. Then install ubuntu on the second. It's important to install windows first, and ubuntu second. grub will be setup correctly.

---

### Post by teotjunk on 2023-11-05
> **yancek said:**
> When you install Ubuntu, you are required to create a user before the  installation completes.  If you are having someone do the install for  you, you can let them select a user name and a password and they can  inform you of what it is so you can boot and change it later.  You can  also give them a user name to create and a password and change the  password later.  You should verify that they are familiar with  installing Ubuntu in EFI mode in a dual boot situation before doling anything.

You have not indicated  which release of Ubuntu you are using.   If you want them separate, you  need to create an EFI partition on the second disk where you will install Ubuntu and install Grub EFI files there.  You must also verify that you are booting in EFI mode so that it is installed properly.  Some releases will install the  Ubuntu EFI files to the first partition on the first disk which will be  the disk you have with windows on it.   In this case, you will then need to create an EFI partition on the 2nd drive with Ubuntu and copy the EFI files for Ubuntu from the windows disk to the Ubuntu disk.

I'd suggest reviewing the links posted above by oldfred and reviewing some links on dual booting Ubuntu and windows EFI.  Newer computers will only install and boot EFI but if you have an older computer, you will have an option to boot the install USB in Legacy or EFI mode, so make sure you select EFI in the BIOS firmware.  

[https://linuxconfig.org/how-to-install-ubuntu-22-04-alongside-windows-10](https://linuxconfig.org/how-to-install-ubuntu-22-04-alongside-windows-10)

I don't understand what do you mean by I want them separate ? You mean separate Windows and ubuntu on separate hard disks?

---

### Post by yancek on 2023-11-06
>  I don't understand what do you mean by I want them separate ? You mean separate Windows and ubuntu on separate hard disks?                 

Yes.  This setup will allow you to select the drive with windows from the BIOS option and boot it.  It will allow you to select the drive with Ubuntu and boot it.

I think the primary concern would be which version release of Ubuntu you are using.  I believe the most recent release allows you to select the drive on which to install the EFI boot files.  Earlier releases gave you that option but did not do it, the files were put on the first EFI partition despite the selection of the user installing.  In your case, that would mean Ubuntu EFI boot files would be on the same EFI partition on the windows hard drive.  The windows files would not be overwritten but Ubuntu would probably set itself to first boot priority but it should also include windows in the boot menu.  If you did not have the drive with Ubuntu attached while booting, it would not boot unless you went to the BIOS to select the windows option.

An EFI install of windows will not boot an EFI Linux although there may be third party software you can use.

---

### Post by teotjunk on 2023-11-06
> **yancek said:**
> Yes.  This setup will allow you to select the drive with windows from the BIOS option and boot it.  It will allow you to select the drive with Ubuntu and boot it.

I think the primary concern would be which version release of Ubuntu you are using.  I believe the most recent release allows you to select the drive on which to install the EFI boot files.  Earlier releases gave you that option but did not do it, the files were put on the first EFI partition despite the selection of the user installing.  In your case, that would mean Ubuntu EFI boot files would be on the same EFI partition on the windows hard drive.  The windows files would not be overwritten but Ubuntu would probably set itself to first boot priority but it should also include windows in the boot menu.  If you did not have the drive with Ubuntu attached while booting, it would not boot unless you went to the BIOS to select the windows option.

An EFI install of windows will not boot an EFI Linux although there may be third party software you can use.

I am not sure I understand completely. First I  install Windows on the first hard disk. Then it is not sufficient I go straight and just install ubuntu on the second hard disk. I first have create a EFI partition on the second hard disk and then install the EFI boot files there? and only after that install the ubuntu

I am pretty sure my Windows boots is UEFI mode. How do I check if the legacy option still exists?

---

### Post by yancek on 2023-11-06
The command below run from a terminal in Ubuntu will tell you.  The output will be either EFI or Legacy.  

```
 **[ -d /sys/firmware/efi ] && echo EFI || echo Legacy**  
```

You could also open a terminal in Ubuntu and do:   ```
sudo ls /boot/efi 
```  

The output should show:  EFI  'System Volume Information'
so if you see EFI from that command, it means you have an EFI install.  If you navigate to /boot/efi/EFI, you should see both a Microsoft direcxtory and an ubuntu directory and if the appropriate files are there, they will both boot in EFI mode.

>  I first have create a EFI partition on the second hard disk and then  install the EFI boot files there? and only after that install the ubuntu

No, you don't need an EFI partition on the 2nd device.  If you use the EFI partition on the first (windows) device when you install Ubuntu, the Ubuntu Grub files will point to Grub files on the 2nd drive.  If you always have both drives attached, this is not a problem.  Creating a 2nd EFI partition on the 2nd drive is something people who are paranoid about installing and want to keep one drive totally windows and one drive totally Linux.  Since your system is likely EFI, even if you install Grub boot files for Ubuntu to the EFI partition on the first (windows) drive, you will still be able to select either windows or Ubuntu from the BIOS.  This can add as much as 5 seconds to the boot time??

---

### Post by teotjunk on 2023-11-08
> **yancek said:**
> The command below run from a terminal in Ubuntu will tell you.  The output will be either EFI or Legacy.  

```
 **[ -d /sys/firmware/efi ] && echo EFI || echo Legacy**  
```

You could also open a terminal in Ubuntu and do:   ```
sudo ls /boot/efi 
```  

The output should show:  EFI  'System Volume Information'
so if you see EFI from that command, it means you have an EFI install.  If you navigate to /boot/efi/EFI, you should see both a Microsoft direcxtory and an ubuntu directory and if the appropriate files are there, they will both boot in EFI mode.



No, you don't need an EFI partition on the 2nd device.  If you use the EFI partition on the first (windows) device when you install Ubuntu, the Ubuntu Grub files will point to Grub files on the 2nd drive.  If you always have both drives attached, this is not a problem.  Creating a 2nd EFI partition on the 2nd drive is something people who are paranoid about installing and want to keep one drive totally windows and one drive totally Linux.  Since your system is likely EFI, even if you install Grub boot files for Ubuntu to the EFI partition on the first (windows) drive, you will still be able to select either windows or Ubuntu from the BIOS.  This can add as much as 5 seconds to the boot time??

I think I will just let them do the installation. How can I tell if they did the installation the original way or the OEM way?

---

### Post by yancek on 2023-11-08
They should not do an OEM install, just tell them not to.  The page at the link below has an explanation with links to other sites with more detailed explanations of the difference.  Doing a standard install will require the creation of a user to be able to use root/sudo privileges so you need to find out from them what they used or tell them in advance what to use for a user and password.  Change the password after you get the machine back.

[https://www.linuxquestions.org/questions/linux-newbie-8/the-difference-between-a-standard-install-and-an-oem-install-4175555251/](https://www.linuxquestions.org/questions/linux-newbie-8/the-difference-between-a-standard-install-and-an-oem-install-4175555251/)

---

### Post by teotjunk on 2023-11-08
> **oldfred said:**
> I have seen a lot of users post computer shop installs, install in the old BIOS/MBR configuration as they do not really understand UEFI/gpt.

Normal install.
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

There is the OEM install which they should use. It install and first then you then have to do is create a user & password.
[https://devicetests.com/pre-install-ubuntu-oem-installation-guide](https://devicetests.com/pre-install-ubuntu-oem-installation-guide)

OEM mode so user can add name & password later:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install](http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install)
Perform end-user configuration after initial OEM installation 
 sudo apt-get install oem-config-gtk

If not installing to same drive and 22.04 or before or some flavors, make sure you understand this bug.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

I am confused

This is the one they should do on my computer - usual install

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)


This is the one they should not install. OEM

[https://devicetests.com/pre-install-ubuntu-oem-installation-guide](https://devicetests.com/pre-install-ubuntu-oem-installation-guide)

---

### Post by yancek on 2023-11-09
The first link explains what should be used.  Did you read the first paragraph at the site for the 2nd link?    It is primarily used for system administrators and manufacturers to customize and do multiple installs.

If you are going to have some computer shop do the install for you, I would suggest that you verify with them before having them do anything that they are familiar with using and installing Linux, specifically Ubuntu.  You need to either give them a user name you want and a simple password you can change later.  If you don't do that, make sure you get that information from them or you will not be able to use the system.  If they have experience, it should not be a problem.

Since you plan to use 2 disks, one for windows and one for Ubuntu explain that to them.  If you leave windows in the default hibernated state, you will have problems recognizing windows from Ubuntu and Grub which will not detect windows and will not create an entry for it in the boot menu.  Having windows on a separate drive should allow you to still boot it from the BIOS so that should not be a problem.

---

### Post by teotjunk on 2023-11-21
> **yancek said:**
> The first link explains what should be used.  Did you read the first paragraph at the site for the 2nd link?    It is primarily used for system administrators and manufacturers to customize and do multiple installs.

If you are going to have some computer shop do the install for you, I would suggest that you verify with them before having them do anything that they are familiar with using and installing Linux, specifically Ubuntu.  You need to either give them a user name you want and a simple password you can change later.  If you don't do that, make sure you get that information from them or you will not be able to use the system.  If they have experience, it should not be a problem.

Since you plan to use 2 disks, one for windows and one for Ubuntu explain that to them.  If you leave windows in the default hibernated state, you will have problems recognizing windows from Ubuntu and Grub which will not detect windows and will not create an entry for it in the boot menu.  Having windows on a separate drive should allow you to still boot it from the BIOS so that should not be a problem.


I just got it installed by the computer shop but when I boot, it goes straight into windows. When I look at the bios, there is no grub. Any idea why?

---

### Post by yancek on 2023-11-22
>  When I look at the bios, there is no grub. Any idea why? 		

Grub does not show in the BIOS.  If your computer shop correctly installed Ubuntu, there should be an entry in the BIOS firmware for Ubuntu.  The install should (may have) have set Ubuntu to first boot but apparently  didn't  Your computer shop should also have done that.  That's what you paid them to do, right?  Did you check for Boot Options in the BIOS?  Does Ubuntu show there?  If so, move it to first boot priority.  You stated earlier that you thought you had an EFI system.  Have you since verified that?   Do you have fast boot  disabled in the BIOS?

Did you ask the people at the computer shop if they knew how to do this?  It doesn't appear they are familiar with the process.  Did you tell them you wanted to boot Ubuntu?  Did you resolve the user/password issue?

---

### Post by teotjunk on 2023-11-23
> **yancek said:**
> Grub does not show in the BIOS.  If your computer shop correctly installed Ubuntu, there should be an entry in the BIOS firmware for Ubuntu.  The install should (may have) have set Ubuntu to first boot but apparently  didn't  Your computer shop should also have done that.  That's what you paid them to do, right?  Did you check for Boot Options in the BIOS?  Does Ubuntu show there?  If so, move it to first boot priority.  You stated earlier that you thought you had an EFI system.  Have you since verified that?   Do you have fast boot  disabled in the BIOS?

Did you ask the people at the computer shop if they knew how to do this?  It doesn't appear they are familiar with the process.  Did you tell them you wanted to boot Ubuntu?  Did you resolve the user/password issue?

I didn't pay them. They did it for free as a favour. Yes there is an entry in Bio firmware for Ubuntu. Yes Ubuntu is in Boot options. That is the thing I cannot find the option to change the boot order. When I did the installation myself of ubuntu, I knew how to change the bios boot order to boot from a USB not sure why I cannot find the option anymore

---

### Post by teotjunk on 2023-11-23
> **yancek said:**
> Grub does not show in the BIOS.  If your computer shop correctly installed Ubuntu, there should be an entry in the BIOS firmware for Ubuntu.  The install should (may have) have set Ubuntu to first boot but apparently  didn't  Your computer shop should also have done that.  That's what you paid them to do, right?  Did you check for Boot Options in the BIOS?  Does Ubuntu show there?  If so, move it to first boot priority.  You stated earlier that you thought you had an EFI system.  Have you since verified that?   Do you have fast boot  disabled in the BIOS?

Did you ask the people at the computer shop if they knew how to do this?  It doesn't appear they are familiar with the process.  Did you tell them you wanted to boot Ubuntu?  Did you resolve the user/password issue?

User/Password no issue. 

I managed to enable something in the bios. Now it goes to grub. My question now is from Grub how do I tell it to go to Windows or Ubuntu?

---

### Post by yancek on 2023-11-24
> My question now is from Grub how do I tell it to go to Windows or Ubuntu? 		 

Does that mean you are now able to boot into Ubuntu?  If so, open a terminal and run the following command and post the output here.  It is informational and will not change anything.

```
 sudo ls /boot/efi/EFI
```

You should see several folders including a Microsoft and ubuntu.  If you don't see them, run the below command and post the information from the output here:

```
sudo fdisk -l
```

If you see both directories, running:  sudo update-grub from Ubuntu should create an entry for windows.

---

### Post by teotjunk on 2023-11-24
> **yancek said:**
> Does that mean you are now able to boot into Ubuntu?  If so, open a terminal and run the following command and post the output here.  It is informational and will not change anything.

```
 sudo ls /boot/efi/EFI
```

You should see several folders including a Microsoft and ubuntu.  If you don't see them, run the below command and post the information from the output here:

```
sudo fdisk -l
```

If you see both directories, running:  sudo update-grub from Ubuntu should create an entry for windows.

For the first command I see ubuntu and Boot folders and nothing else

For the second command this is the output

```
Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 63,45 MiB, 66531328 bytes, 129944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 63,46 MiB, 66547712 bytes, 129976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 73,88 MiB, 77463552 bytes, 151296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 73,9 MiB, 77492224 bytes, 151352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 237,21 MiB, 248729600 bytes, 485800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 349,7 MiB, 366682112 bytes, 716176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 485,52 MiB, 509100032 bytes, 994336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 1,82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Samsung SSD 970 EVO Plus 2TB            
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 4C96AD8F-1BEF-44C6-A6E3-08A02C56BF1E

Device              Start        End    Sectors  Size Type
/dev/nvme0n1p1       2048     206847     204800  100M EFI System
/dev/nvme0n1p2     206848     239615      32768   16M Microsoft reserved
/dev/nvme0n1p3     239616 3905516622 3905277007  1,8T Microsoft basic data
/dev/nvme0n1p4 3905517568 3907024895    1507328  736M Windows recovery environment


Disk /dev/nvme1n1: 953,87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: SAMSUNG MZVLB1T0HBLR-00000              
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A3C43807-B3A5-4B85-84BC-3F683A48E9F8

Device           Start        End    Sectors   Size Type
/dev/nvme1n1p1    2048    1050623    1048576   512M EFI System
/dev/nvme1n1p2 1050624 2000408575 1999357952 953,4G Linux filesystem


Disk /dev/loop8: 496,98 MiB, 521121792 bytes, 1017816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 91,69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 12,32 MiB, 12922880 bytes, 25240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 53,26 MiB, 55844864 bytes, 109072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 40,86 MiB, 42840064 bytes, 83672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 452 KiB, 462848 bytes, 904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

---

### Post by yancek on 2023-11-25
In the future, if you post the output of fdisk, remove all the loop entries as they are not needed.  What you posted shows a proper install of windows on one disk and a proper install of Ubuntu on another disk.  You indicate that when you ran the command:  ls /boot/efi/EFI you saw only ubuntu and not Microsoft.  You should be set but just to verify that Ubuntu is using the EFI on the second disk run the command below and if you see just the Boot and ubuntu directories, all you need do is run:  sudo update-grub from the installed Ubuntu.

```
sudo mount /dev/nvme1n1p1 /mnt
```

Best to copy/paste the above code

Your fdisk output shows Disk /dev/nvme0n1: 1,82 TiB and it shows only windows partitions with a separate EFI partition.
The fdisk output also shows Disk /dev/nvme1n1: 953,87 GiB with only Linux partitions and an EFI partition.  

If you are paranoid about all this, you can verify this additionally after running the command above by mounting the EFI partition on the windows drive to verify there are EFI files there which should include a Microsoft directory and should NOT include an ubuntu directory.  To do this, run the commands below consecutively, hitting Enter key after each command: 

 ```
sudo umount /mnt
sudo mount /dev/nvme0n1p1 /mnt
sudo ls /mnt
```

If you just see EFI when you enter the ls command, do ls /mnt/EFI and look for a Microsoft directory.  I don't use windows so don't have any method to verify how the EFI partition shows on a windows only drive.

Running sudo update-grub from Ubuntu should detect windows, watch the output when you run the command to verify.  This will add it to the Grub menu so you can select it from there when booting.  This would require the Ubuntu drive to be set permanently as first boot priority in the BIOS firmware.  You should also be able to select either drive from the 'one time' boot options in the BIOs if not wanting to use Grub to boot both.

---

### Post by teotjunk on 2023-11-27
> **yancek said:**
> In the future, if you post the output of fdisk, remove all the loop entries as they are not needed.  What you posted shows a proper install of windows on one disk and a proper install of Ubuntu on another disk.  You indicate that when you ran the command:  ls /boot/efi/EFI you saw only ubuntu and not Microsoft.  You should be set but just to verify that Ubuntu is using the EFI on the second disk run the command below and if you see just the Boot and ubuntu directories, all you need do is run:  sudo update-grub from the installed Ubuntu.

```
sudo mount /dev/nvme1n1p1 /mnt
```

Best to copy/paste the above code

Your fdisk output shows Disk /dev/nvme0n1: 1,82 TiB and it shows only windows partitions with a separate EFI partition.
The fdisk output also shows Disk /dev/nvme1n1: 953,87 GiB with only Linux partitions and an EFI partition.  

If you are paranoid about all this, you can verify this additionally after running the command above by mounting the EFI partition on the windows drive to verify there are EFI files there which should include a Microsoft directory and should NOT include an ubuntu directory.  To do this, run the commands below consecutively, hitting Enter key after each command: 

 ```
sudo umount /mnt
sudo mount /dev/nvme0n1p1 /mnt
sudo ls /mnt
```

If you just see EFI when you enter the ls command, do ls /mnt/EFI and look for a Microsoft directory.  I don't use windows so don't have any method to verify how the EFI partition shows on a windows only drive.

Running sudo update-grub from Ubuntu should detect windows, watch the output when you run the command to verify.  This will add it to the Grub menu so you can select it from there when booting.  This would require the Ubuntu drive to be set permanently as first boot priority in the BIOS firmware.  You should also be able to select either drive from the 'one time' boot options in the BIOs if not wanting to use Grub to boot both.


When I make ubuntu the first boot?. It goes into grub. How do I make it go into Windows or ubuntu from there?

---

### Post by yancek on 2023-11-27
>  When I make ubuntu the first boot?. It goes into grub. How do I make it go into Windows or ubuntu from there? 				

If you have the drive on which you installed Ubuntu set to first boot priority in the BIOS, you should see the Grub menu on screen with options to select Ubuntu as well as Advanced options for Ubuntu.  If you can boot into Ubuntu, just open a terminal and update grub with the command:  sudo update-grub
Watch the screen for output that shows windows.  If you don't see it, go to the /etc/default/grub file and look for a line that shows os-prober and make sure it is ENABLED.  Run suod update-grub again.  

You should also be able to select the drive which has windows on it from the BIOS to boot it.

---

### Post by teotjunk on 2023-11-27
> **yancek said:**
> If you have the drive on which you installed Ubuntu set to first boot priority in the BIOS, you should see the Grub menu on screen with options to select Ubuntu as well as Advanced options for Ubuntu.  If you can boot into Ubuntu, just open a terminal and update grub with the command:  sudo update-grub
Watch the screen for output that shows windows.  If you don't see it, go to the /etc/default/grub file and look for a line that shows os-prober and make sure it is ENABLED.  Run suod update-grub again.  

You should also be able to select the drive which has windows on it from the BIOS to boot it.

I cannot seem to find the line os-prober

---

### Post by tea for one on 2023-11-27
Boot into Ubuntu
Open a terminal and enter:-
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false [COLOR="#0000FF"]add this line[/COLOR]

```
Save and exit
```
sudo update-grub
```
Please post the output of the last command within code tags

---

### Post by teotjunk on 2023-11-27
> **tea for one said:**
> Boot into Ubuntu
Open a terminal and enter:-
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false [COLOR=#0000FF]add this line[/COLOR]

```
Save and exit
```
sudo update-grub
```
Please post the output of the last command within code tags

What do you mean within code tags?

---

### Post by #&amp;thj^% on 2023-11-27
Like this
[noparse]```
your input here
```[/noparse]

---

### Post by oldfred on 2023-11-27
While you can hand type code tags in Quick Reply, you can use Forum's Go Advanced Editor and highlight code and click on the # icon.

How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

