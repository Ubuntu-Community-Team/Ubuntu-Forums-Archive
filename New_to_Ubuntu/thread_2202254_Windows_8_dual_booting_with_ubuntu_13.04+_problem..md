---
title: "Windows 8 dual booting with ubuntu 13.04+ problem."
date: 2014-01-28
forum: New to Ubuntu
---

### Post by Sidak on 2014-01-28
OKAY I HAVE WINDOWS 8 64 BIT INSTALLED IN EFI MODE AND I HAVE BEEN FOR THE LAST MONTH TRYING TO BOOT OR DUAL BOOT UBUNTU 13.04 DEVELOPER'S FLAVOR ON IT. WELL THE PROBLEM IS THAT WHENEVER I SELECT MY USB FROM THE BOOT MENU, IT LEADS BACK TO BOOTING WINDOWS 8 WITHOUT A ERROR CODE OR A MESSAGE. PLUS I THINK I MAY NEED TO INSTALL UBUNTU IN UEFI MODE AS MY WINDOWS IS IN EFI MODE AND NOT LEGACY MODE BUT I CAN NOT FIND A WAY TO DO IT SAFELY ON A WINDOWS MACHINE. ANYONE WHO CAN HELP ME BOOT WITHOUT HAVING TO CONVERT MY MBR HARD DRIVE TO GPT OR HELPING ME CONVERT MY CURRENTLY INSTALLED UBUNTU IN A EFI MODE ON MY USB WOULD BE VERY VERY VERY HELPFUL. 
I have treid booting with unibootin. If someone can teach me how to install ubuntu on my usb in EFI mode that will be very useful. Please note all the instructions or actions you suggest i will perform on windows 8 OS.

Thanks a lot.

---

### Post by mörgæs on 2014-01-28
13.04 is unsupported. How does it work with 13.10? 

I have removed your statement of strong feelings. Ubuntu is not to blame - direct them against Windows in stead.

---

### Post by oldfred on 2014-01-28
To UEFI boot you must have gpt partitioning. 

Use Windows for Windows changes or shrinking the Windows NTFS partition if dual booting. Otherwise only use Linux tools from Live flash drive or DVD for everything Linux related and creating new partitions. Windows does not work with Linux, but Linux works with Windows (mostly). 

If you have a drive with MBR(msdos) you may be able to convert. But full backups required and it just may be safer to reformat.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

If installing to an external hard drive or flash drive, use gpt partitioning so you can boot in UEFI mode and use Something Else or manual install. You have to use Live installer flash drive to install to another larger flash drive or USB external hard drive. And you have to boot installer in UEFI boot mode.

      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
Better to use the newest Ubuntu or 13.10 or in the next couple of weeks 12.04.4. Many UEFI updates to support the newer hardware. 


 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

Often easier to partition in advance with gparted. 

  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

