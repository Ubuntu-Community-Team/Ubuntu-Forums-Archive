---
title: "Boot from USB on OSX problem"
date: 2014-03-17
forum: New to Ubuntu
---

### Post by Matthew_Garsteck on 2014-03-17
Hey everyone, Im trying to install 13.10 on my 27" iMac from the USB.  I have gone through the instructions several times and still no dice.

Ive gone through the terminal instructions, converted the iso to an img after unmounting the usb drive.  After this is done, the computer will not mount the drive.  After rebooting, there is no option for booting from the USB. I have no idea what to do here.  Can anyone help?

---

### Post by rollingthunderb on 2014-03-17
Take a look.

[http://www.macyourself.com/2011/04/24/boot-your-mac-from-cd-dvd-external-drive-or-usb-flash-drive/](http://www.macyourself.com/2011/04/24/boot-your-mac-from-cd-dvd-external-drive-or-usb-flash-drive/)

Hope that helps.

---

### Post by Matthew_Garsteck on 2014-03-17
Sorry, it does not.  

I got the image onto my thumbdrive by using unebootin
I then copied the image in terminal to a partitioned drive on my hard disk.

I restarted and went to boot into the linux partition but a message says that the operating system is missing.

---

### Post by rollingthunderb on 2014-03-17
> **Matthew_Garsteck said:**
> Sorry, it does not.  

I got the image onto my thumbdrive by using unebootin
I then copied the image in terminal to a partitioned drive on my hard disk.

I restarted and went to boot into the linux partition but a message says that the operating system is missing.

I'm sorry, but that doesn't actually install the linux operating system or create a boot loader to point to the system once properly installed.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

under faq's
"[h=2]FAQs[/h][COLOR=#000000][FONT=verdana]**How does UNetbootin work, and what does it do?**[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]For the Live USB creation mode, UNetbootin downloads and extracts an ISO file to your USB drive, generates an appropriate syslinux config file, and makes your USB drive bootable using syslinux.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]For the Hard Disk / "frugal install" mode, UNetbootin uses a Windows or Linux-based installer to install a small modification to the bootloader (bootmgr and bcdedit on Vista, grldr and boot.ini for NT-based systems, grub.exe and config.sys for Win9x, or GRUB on Linux, uses the bootloader to boot the desired distribution's installer or to load the system utility, no CD required. After the distribution has been installed, or once done using the system utility, the modification to the bootloader is then undone."

Also right below that is;

"See [USB Drive and Hard Disk Install Modes]("http://sourceforge.net/apps/trac/unetbootin/wiki/installmodes")."

under "hard disk install mode"
"[/FONT][/COLOR]
[h=2]Hard Disk Install Mode[/h][COLOR=#000000][FONT=Verdana]If you provide a LiveCD iso file, such as the Ubuntu desktop iso, to UNetbootin and use the hard disk install mode, the resulting install will NOT be a full, standard hard drive installation. Rather, you are simply booting into the live environment, the same way as if you had booted from a live CD or a live USB, except it's being loaded from your hard disk instead. This is often referred to as a "frugal install", as it doesn't install a dedicated bootloader and doesn't make a separate partition, but rather piggybacks off the existing OS's bootloader and installs the files for the live environment inside the existing partition."[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]
[FONT=Verdana]I've never done this on any of my macs since I just run virtual machines, so I can't say for sure how to do this. I was expecting that you had a live USB install and you couldn't get the mac to see it. Hence the quick suggestion for the option command. Yet some of this text says macs don't support live USBs. I'm not sure why. 

I do know that simply copying an image to a partition without a bootloader to know it is there and what to do with it isn't going to work.[/FONT][/FONT][/COLOR]

---

### Post by Matthew_Garsteck on 2014-03-17
Ive searched through some forums and I have not been able to find a way to hard install, not a way that works on my computer.  Im stopped dead in my tracks.  I do have a VM running ubuntu but I want to have it as my main system without running osx.  I have gone through the tutorial word for word that is provided by Ubuntu and still nothing.  I have tried to install through a dvd, but I am not even able to burn a dvd on this Mac.  Im sick of running OSX and I just want an os that works.

---

### Post by rollingthunderb on 2014-03-17
Hi,

read these. 

then read them again. 

often when I'm frustrated I tend to launch into "do mode". I then fail to read or catch one important step, and that leads me to all sorts of $%^@$@$ ...stuff. ;-)

 I hope you're not anything like me, but just in case, please read some more.

[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

If nothing else, this will provoke thought and help you achieve linux goodness. I hope you get to what you want soon.

---

### Post by Matthew_Garsteck on 2014-03-18
Thank you for responding.  I have read over these several times.  However, the problem I am having is that the USB is not showing up when I boot the computer.  I have the USB containing the iso image, but there is no option to boot into linux.

---

### Post by Vladlenin5000 on 2014-03-18
[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) -> *[UNetbootin for Mac OS X]("http://unetbootin.sourceforge.net/")  can be used to automate the process of extracting the Ubuntu ISO file  to USB, and making the USB drive bootable. _The resulting USB drive,  however, can be booted on PCs only_.*

---

### Post by Matthew_Garsteck on 2014-03-18
Ive used it, I use a mac so it is useless.  I found something else that works just great.  Linux to mac usb.  Worked great.

---

