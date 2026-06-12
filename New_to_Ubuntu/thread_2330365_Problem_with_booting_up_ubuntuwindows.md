---
title: "Problem with booting up ubuntu/windows"
date: 2016-07-11
forum: New to Ubuntu
---

### Post by waaaffles on 2016-07-11
Hello, sorry if this is the wrong place to post this question, but I am new to this forum. 

So  first of all, I had windows and ubuntu installed onto my hard drive so I  was able to dual boot. This worked fine, as I was able to get into  whichever one i wanted to. 
The problem now is that I wanted to have a  flash drive with ubuntu on it, in which I would be able to plug it into  any computer and I would be able to boot into the ubuntu installed on  the flash drive. So I followed a walk through and installed ubuntu onto a  flash drive. When I booted into it, that worked fine, and I was also  able to get into my windows and my other ubuntu installed on my hard  drive. However, if I remove my flash drive, when I start my computer up,  I get into the GNU grub menu, and from there, I cannot do anything. The  only way to boot into anything is to have my flash drive plugged in. So  is there any way to have my hard drive with windows/ubuntu launch  first? And is there any way for my USB with ubuntu installed on it to  also be able to launch if its plugged into a computer? 

Thanks in advance!

---

### Post by zacmartin on 2016-07-11
Go to your BIOS and change boot preference.

---

### Post by mastablasta on 2016-07-11
> **waaaffles said:**
> 
The problem now is that I wanted to have a  flash drive with ubuntu on it, in which I would be able to plug it into  any computer and I would be able to boot into the ubuntu installed on  the flash drive. So I followed a walk through and installed ubuntu onto a  flash drive. When I booted into it, that worked fine, and I was also  able to get into my windows and my other ubuntu installed on my hard  drive. However, if I remove my flash drive, when I start my computer up,  I get into the GNU grub menu, and from there, I cannot do anything. The  only way to boot into anything is to have my flash drive plugged in. So  is there any way to have my hard drive with windows/ubuntu launch  first? And is there any way for my USB with ubuntu installed on it to  also be able to launch if its plugged into a computer? 


firstly - you installed full OS on USB drive, you should know that if you added any drivers or setup anything specific to your PC it might not work on another PC.

now on to your issue - to get what you want to have you need to - 
1. install to USB
2. during install you need to tell it to install GRUB to USB
3. do not update the grub on your PC as that would add USB as option. if you have that boot form live and update grub to remove USB option from it. 

this should give you the option to boot with USB inside (if USB is first device in boot order) or without it (from disk).

so GRUB has to be on hard disk as well as on USB. and USB disk should **NOT** be an entry in GRUB on hard disk. it's the same in windows only there you have to have it's boot record on both disk to be able to boot form them.
in the old days you formatted a floppy with /s parameter to get a system disk from it.

EDIT: alternative option is to use a live USB disk and add persistence (casper file) to it. a separate partition on it can be used for data. just a thought....

---

### Post by yancek on 2016-07-11
Your post indicates that you have overwritten the Grub code in the MBR of the internal drive with code from Grub on the flash drive either by following poor instructions or not paying attention.  You did use the manual "Something Else" option during the install?  Which windows version are you using and are you using UEFI or MBR.  Methods of repair will differ.  The simplest solution if it is MBR and you can boot the Ubuntu installed to the hard drive from the flash drive boot menu is to  re-install Grub to the MBR of that drive.  Use one of the options at the Ubuntu documentation site below.  If you are using UEFI, do not follow these methods but post back for suggestions.  

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by waaaffles on 2016-07-11
How can you check whether you are UEFI? 
As for what I did in the installation, I followed the instructions in this link ([http://askubuntu.com/questions/307802/how-to-install-ubuntu-on-a-usb-stick](http://askubuntu.com/questions/307802/how-to-install-ubuntu-on-a-usb-stick)).

Edit: I believe I am using UEFI. I am not certain on this, but when I ran sudo fdisk -l from the terminal, one of the devices said EFI system.

---

### Post by yancek on 2016-07-11
Check on UEFI by reading the official Ubuntu documentation at the site below, scroll down the page a bit.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The link you posted is accurate but very cryptic.  The part about "Device for bootloader installation" is what went wrong.  As you can see in the image, the default is /dev/sda which would be your internal hard drive.  This should not have happened if you had selected the correct drive which would have been something like sdb or sdc.  Also, it would not matter if you were using UEFI or MBR on the computer hard drive if you had done the install of Grub to the MBR of the flash drive.  However, since you have installed Grub from the flash drive to the internal hard drive you will need to correct that and unless we know which version of windows you are using and more precisely whether it is UEFI or MBR, any suggestions will just be guesses.

---

### Post by waaaffles on 2016-07-11
I believe that I have fixed my issue. I installed boot repair onto my computer and set the boot flag onto my original ubuntu which is in my internal drive, and now when I boot up with and without my USB connected, I am able to get into the menu which allows me to select which OS I want to boot into. 

Hopefully I did everything right, but if I didn't, I have windows 10 and I believe I have UEFI because when I run this comand line -
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
- I get EFI boot on HDD.

edit: the boot repair output that I have is [http://paste.ubuntu.com/19110540/](http://paste.ubuntu.com/19110540/)

---

### Post by yancek on 2016-07-11
> set the boot flag onto my original ubuntu

Setting a boot flag or marking a partition as active is not needed on any Linux system, only windows so I'm not sure what fixed it.  If it's working, no problem.  You might have posted a link to the boot repair output as instructed and some of the members here more familiar with UEFI could point out potential problems, if any.  Glad you got it working.

---

