---
title: "How can I execute a command line in Ubuntu?"
date: 2014-08-10
forum: New to Ubuntu
---

### Post by commercial2 on 2014-08-10
Hi guys, I have a Ubuntu OS initially installed on my laptop but I also want to dual boot it with Windows 7.

I managed to install a windows 7 installer on my USB using "Windows 7 USB DVD Download Tool". However, I am getting a ntldr is missing as I boot my usb on my laptop.

As I search from the internet, I found a quick fix on the following link
[http://chwang.blogspot.com/2012/07/fix-ntldr-is-missing-for-windows-78-usb.html](http://chwang.blogspot.com/2012/07/fix-ntldr-is-missing-for-windows-78-usb.html)


However, I don't know how to execute steps 3 & 4 because my os is Ubuntu.

Here is the excerpt of the steps from the link provided: 
> 
 
[LIST=1]
[*]Boot the existing windows (my one is XP, but windows 7 should also works)
[*]Insert the created windows 7/8 installer USB drive
[*]Open a command window, go to the USB drive (my one is G:) 
[*]Change directory to: USBDRIVE:\boot (for example, [FONT=Courier New]cd G:\boot[/FONT]) This directory contains the executable file "bootsect.exe". Under this directory, run the following command: 
[/LIST]
 
 [FONT=arial] [/FONT][FONT=Courier New]bootsect /nt60 **USBDRIVE**:  



can someone please help me?

Thanks!
[/FONT]

---

### Post by grahammechanical on 2014-08-10
Your thread title asks a question and I will answer it. Open the terminal. Now it all depends upon which version of Ubuntu you are using. In Ubuntu 12.04 or 14.04 open the Dash and type terminal.

But I doubt that this will work. I do not think that the command line interpreter used by the terminal (BASH) will understand the command [I]bootsec /nt60 USBDRIVE:
[/I]
Regards.

---

### Post by gbauer156 on 2014-08-10
First of all I think you should change your title it is misleading. Secondly dual booting Windows. Open up a terminal window and type this command '$ sudo apt-get install unetbootin' (you will need to know your password). To install UNetbootin which allows you to make Linux Live CDs (you will need it). You don't have to use the terminal. I just prefer it because it is faster. By the way if you ever see a  '$' or a '#' when someone is telling you to type a command don't type those signs. They are meant to tell you what user mode to be in '$' is the default. Now once it is installed download the GParted Live CD ISO from this link 'http://downloads.sourceforge.net/gparted/gparted-live-0.19.1-1-i486.iso' burn it to the USB using UNetbootin (you will need to know your password). The restart you computer and boot to the USB. Use the tool that shows up on the screen at boot to resize your partition. Once you have done that use the free space to add a new partition make sure this one is NTFS and not ext4. That will be the partition you will install Windows on. Restart your computer and boot to your hard drive. You will to type this command to install WinUSB (Assuming you have 14.04 installed) '$ sudo apt-get install winusbgui' (you will need to know your password) if it doesn't install it look up how to install it in your Ubuntu version. Once install open it up and choose the source from which you have Windows 7 on. Then, select you USB stick and hit install (you will need to know your password/ WARNING: WILL WIPE ALL DATA ON USB STICK). Restart your computer and boot to the USB stick. I am assuming you know how to install Windows  7. So install it on the last partition on the drive (the one you made earlier). Then if you restart your computer and boot to the hard drive it should start Windows 7. But at this point you can't access your Ubuntu installation. So in Windows install a program called Lili from here 'http://www.linuxliveusb.com/' Which will allow you to make a Linux Live USB stick. Select Ubuntu from the downloads menu. And select the format option. Then, start it. In about 10-15 minutes you will have a bootable Ubuntu USB (time may vary depending on download and computing speed). Now you can either re-install Ubuntu if you like or you can keep your install and just re-install the boot loader. If you want to re-install Ubuntu just boot to the USB and go through the install if not. Boot to the USB with the Default option. Open up a file manager and go to your Ubuntu partition. Once in there hit Ctrl+C to copy the path. After that, open up a terminal and type 'sudo chroot ' then paste the directory you copied and hit enter. Once in there, type this command 'sudo grub-install /dev/sda'. That will install the boot loader. When that is finished restart and boot to your hard drive and you should see an option to be able to boot to Ubuntu or Windows 7. Congratulations you are officially done with one of the more advanced tasks in Linux. And you have now successfully dual-booted.

---

### Post by Andy_Crowd on 2014-08-10
The *ntldr* can be found in windows with (dir /s /a *ntldr*)  you can use dir /s /a /h *ntldr*. You must have same windows version and copy *ntldr *to the* **C:\** *directory*.*

---

