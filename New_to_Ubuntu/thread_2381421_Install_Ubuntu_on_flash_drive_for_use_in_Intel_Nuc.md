---
title: "Install Ubuntu on flash drive for use in Intel Nuc"
date: 2017-12-31
forum: New to Ubuntu
---

### Post by kevinbrogers on 2017-12-31
[FONT=Helvetica]I apologize if I use any wrong terminology here, but I’ll try my best.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]My purpose in all of this is to set up on always-on device that can run Plex so I don’t have to worry about keeping my personal laptop (MacBook Pro, 2011) running all the time (I’d rather just have my primary laptop run the client version).  So I bought an Intel NUC (NUC5CPYH), 4 GB of memory, two 32 GB SanDisk flash drives, and a 4 TB hard drive to use to actually store all of the video files.  I figured for the operating system, I could just use Ubuntu and everything would be fine.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Essentially, my problem is that after installing Ubuntu on a flash drive, that drive is not bootable on either the nuc setup or on my Mac.  On the Mac, it doesn’t appear bootable at all.  On the nuc, it *looks* bootable but upon selection I’m given the message “Insert boot media in selected boot device and press a key”.  To me that implies that it found the flash drive but not the operating system.  I’m fairly confident the OS in on there - when I go back to reinstall, it shows there is a copy of Ubuntu running on the flash drive, but more on that in a moment...[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]These are the steps I used to install.  First, I downloaded a copy of the latest ISO file for Ubuntu desktop (ubuntu.com/desktop).  I used their tutorial ([https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)) to create a Ubuntu Live usb stick.  I can boot from this with no problems on my Mac.  Next, I followed the instructions from a different tutorial ([http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/](http://ubuntuhandbook.org/index.php/2014/11/install-real-ubuntu-os-usb-drive/)) skipping step 1 (creating the live USB).  I did not deviate from the tutorial steps in any way, and was even able to find some other online tutorials that followed essentially the same steps.  This I believe should have created a bootable copy of Ubuntu on my second USB that could be used in the same way as a typical Windows system, that I could use to download software, store files, etc.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]At this point, I believe I should have had a working USB that I could use to boot to Ubuntu and use as I pleased.  However, the device does not appear on the boot menu on my Mac and only sort of appears on the boot menu on my nuc (see above).[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]And that’s where I’m stuck.  Is there a fatal flaw in an assumption I made, or in my understanding of Linux?  Or does it sound like I did something wrong during the setup of the second USB?[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Any help would be greatly appreciated.  Thank you.[/FONT]

---

### Post by C.S.Cameron on 2017-12-31
Why do you want to run Ubuntu off a flash drive if there is a hard drive? Suggest you use the flash drive to do a Full install to the hard drive instead.

---

### Post by oldfred on 2017-12-31
Both of your systems are UEFI.
But the instructions you are following are older and for BIOS/MBR, you need UEFI/gpt.

But I agree, why not install to SSD?

 Full install
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)
[https://askubuntu.com/questions/906857/installing-ubuntu-on-usb-and-booting-from-destop-with-uefi](https://askubuntu.com/questions/906857/installing-ubuntu-on-usb-and-booting-from-destop-with-uefi)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)
[URL="https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks"]https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks
[/URL]
 Two drive or any second, external or other drive than sda.
Note that full install to any drive other than sda in UEFI mode has some issues. Grub only installs to the ESP - efi system partition on sda. And you then have to copy files to your install.
Good advice on UEFI and two drive installs
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration) 
   Mac full install UEFI boot to flash drive
[http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528](http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528) 
   Full install to external drive.
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312) 
   Manually copy efi files to efi partition on flash drive for booting. Toshiba Satellite S855-5378  by ubfan1
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515) 

[URL="https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks"]
[/URL]

---

### Post by HermanAB on 2018-01-01
We use a few NUCs as embedded controllers with flash disks.  The install process is exactly the same as when installing on a hard disk:

On a Linux machine:
Download Ubuntu ISO file.
Note the size of the USB stick that you want to use (eg 16 GB) to install from.
Copy ISO file to an old small memory stick with dd if=filename.iso of=/dev/sdb (or whatever the 16 GB stick is called).

On the NUC:
Change the BIOS so it will boot off USB.
Put two memory sticks in it - a blank one (64 GB) and the one prepared above (16 GB).
Power up and let it boot off the 16 GB stick.
On the Ubuntu desktop, select install to hard disk and install the system to the other memory stick (64 GB).
When done, remove the 16 GB stick and reboot.

That is all there is to it.

---

### Post by sudodus on 2018-01-01
I have an Intel NUC (but another model). I have no problems with the current versions of Ubuntu (I would recommend that you start with the version Ubuntu 16.04 LTS.) The following link may help you make it work with an installed system,

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

Please notice, that during the installation, the installer selects suitable drivers for the computer hardware, when it is being installed. So you are more likely to get a system, that works in the NUC, if you do the installation in the NUC (and more likely to get a system, that works in the Mac, if you do the installation in the Mac). If the computers are similar enough, the installed system will probably work in both computers.

[hr][/hr]
If you want a system, that is portable between computers that are rather different, you should try a persistent live system. Such a system cannot be fully upgraded, and it is sensitive to corruption (so you should take frequent backups), but it might be a good option in this case. See the following links

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

