---
title: "Burning ISO image"
date: 2016-06-29
forum: New to Ubuntu
---

### Post by psam2 on 2016-06-29
Hello, I am new to Ubuntu and am wanting to instal 16.04.  I have downloaded the i386 (32 bit) image several times to try to burn the image to disc.  Each time the folders are imaged but not the instal files.  I used Infrarecorder on both 32 and 64 bit Win 7 PCs.  Would you be able to help please.  Thank you. psam

---

### Post by grahammechanical on 2016-06-29
Please allow time for people to respond. We are Ubuntu users like yourself. We are volunteers. Many people have registered on this forum but in comparison only few try to help others with their problems.

This is how to create a Ubuntu install DVD or USB memory stick from the Windows operating system

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

This is the installation guide

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

If you are looking for an install.exe file to install Ubuntu from inside Windows, then that is not the way things are done. We change a setting in the BIOS/UEFI settings utility to load an OS from a DVD drive or USB port and then reboot with the Ubuntu DVD disc in the drive or USB stick connected to the USB port. Ubuntu will then load its own installer program and run it in computer memory from the DVD or USB

If you have a machine with a 64 bit CPU then you should run 64 bit Ubuntu. It is called amd64 and it will run on CPUs made by both Intel and AMD. If you have a 32 bit CPU then the machine may not be be capable of running Ubuntu. You may need to install an edition of Ubuntu that uses a different user interface. such as Xubuntu, Lubuntu or Ubuntu Mate. A lot will depend on the specification of the hardware. What CPU? How much RAM? What video adapter? 

Regards.

---

### Post by psam2 on 2016-07-01
Thanks grahammechanical for your reply and help. I am trying to instal to a clean PC, no Windows.  I have tried on a both 32 and 64 bit pc's with the BIOS to boot from disc drive.  I have viewed this page  [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)  which shows what the disc should look like.  My image only shows the folders and two files, md5Sum and Readme.diskdefines.
What am I missing in the process?

---

### Post by sudodus on 2016-07-01
Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier for us to give relevant help.

- Check the md5sum of the iso file
- Burn the image with the slowest possible speed. Notice that you need a DVD disk (a CD disk is too 'small').
- Check the mdsums of the program packages

You can also consider flashing the iso file to a USB pendrive. Only very old computers (more than 12 years old) have problems booting from USB.

See this link: [Checking the iso file and the boot drive - detailed tips](http://ubuntuforums.org/showthread.php?t=2196858&p=13511608#post13511608)

---

### Post by Impavidus on 2016-07-01
> **psam2 said:**
> I have viewed this page  [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)  which shows what the disc should look like.  My image only shows the folders and two files, md5Sum and Readme.diskdefines.
What am I missing in the process?

That image is from an older version of Ubuntu. The contents of the live disk have changed somewhat. The important thing is that you see a bunch of folders and a few files, not a single .iso file. So I think you burned the .iso correctly.

---

### Post by sudodus on 2016-07-01
> **Impavidus said:**
> That image is from an older version of Ubuntu. The contents of the live disk have changed somewhat. The important thing is that you see a bunch of folders and a few files, not a single .iso file. So I think you burned the .iso correctly.

Good catch :-)

---

