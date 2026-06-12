---
title: "Ubuntu and External Drive"
date: 2016-11-18
forum: New to Ubuntu
---

### Post by GiuHei3u on 2016-11-18
Running Windows 7. Is it possible to plug into the computer an external hard drive and run Ubuntu with it? I really do not want to repartition my computer's hard drive and run Ubuntu from it.

---

### Post by yancek on 2016-11-18
Yes.  You need to be familiar with Linux drive/partition naming conventions so you don't overwrite your OS on the internal drive.  You would then select to install Ubuntu to the external drive and make sure that you install the Grub boot code to the master boot record of the external drive.  The link below gives a detailed explanation of installing Ubuntu 14.04 which should be very similar to 16.06, if that's what you are using.

The tutorial is for installing using MBR so if you are using EFI with windows 7, don't use the tutorial.  

  [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by RobGoss on 2016-11-18
Hello and welcome, Yes it's possible if you're going to install Ubuntu on the external drive just create your bootable USB or DVD, make sure the bootable USB is pluged in then plug the external drive 

Boot your machine and choose the external drive for your installation the rest should be straight forward

I'm not sure the level of experience you have using Linux but it's always good to read up on what it is you want to accomplish

---

### Post by ajgreeny on 2016-11-18
To do what you want **YOU MUST CHOOSE "Something Else"** at the partitioning stage of the installation and make sure you put grub, the Ubuntu bootloader files, on the root of the external disk, which will probably be /dev/sdb (note there is no number after the sdb).

If you don't do that the installer will install grub to your internal disk and you will then be unable to boot either OS without the external disk attached.

Once you have Ubuntu installed to the external disk, with grub on it, set your BIOS/UEFI to boot to the external disk first and the internal disk second.
Now when you boot with the external disk attached you will get the grub menu and should be able to choose either OS; with the external disk missing the system should boot to Windows as if nothing had happened.

---

### Post by GiuHei3u on 2016-11-18
Downloaded Ubuntu 16.04.1 Desktop AMD64 to a usb but I have a 32 bit system Windows 7. Will this work?

---

### Post by howefield on 2016-11-18
As long as the computer can support 64 bit you'll be fine, you should be made aware fairly soon as the USB won't boot if the computer is not 64 bit capable.

---

### Post by ajgreeny on 2016-11-18
Tell us more about your hardware; computer model, CPU, amount of RAM, etc etc, otherwise we have no idea if it will run or not, nor how sensible it is to even try.

For your information, you can run a 32 bit OS on 64 bit hardware but not vice-versa; you [B]must[B] have 64 bit hardware to run a 64 bit OS.

---

### Post by GiuHei3u on 2016-11-18
ACPI x86-based PC
AMD A4-5300 APU with Radeon (tm) HD Graphics
ASUS F2A55-M LK Series Motherboard
4 GB RAM (2.72 GB usable)

Would like to include the above with every post or reply in otherwords a signature. How can I do that?

I downloaded the Ubuntu 16 to a usb drive and went into my BIOS to change the drive upon boot but it is not recognizing the drive and continues to open Windows.

---

### Post by GiuHei3u on 2016-11-18
What is the latest 32 bit OS in Ubuntu available for me?

---

### Post by GiuHei3u on 2016-11-18
Your info much appreciated. Please provide a link or two for a start.
Thank You.

---

### Post by HermanAB on 2016-11-18
Howdy, if you ensure that each disk is a wildly different size, then you can use their sizes as an indication that you working with the correct one.  For example the internal disk is 500 GB, the boot disk is an GB memory stick and the target disk is 2 TB, then you can easily tell which is which.

---

### Post by GiuHei3u on 2016-11-18
Since 16.04 is a 64 bit os I downloaded 12.04.5 Desktop-i386 to my usb drive. This will not work correct? 12.04 must be burnt to a cd or a dvd right?

---

### Post by RobGoss on 2016-11-18
You have to burn it to a DVD or USB drive this is the only way to install any distribution of Ubuntu

Following the instructions given and you should be ok

---

### Post by GiuHei3u on 2016-11-18
Thanks

---

### Post by RobGoss on 2016-11-18
You can use this tool to burn the ISO file to a USB drive [https://rufus.akeo.ie/](https://rufus.akeo.ie/) I'm assuming you're using Windows to create it correct?

---

### Post by GiuHei3u on 2016-11-18
Thanks. I am going to update my system next week. Quad processor, solid state hard drive etc. Then come back and install 16.04 64 bit.

Thanks to all for the suggestions.

---

### Post by RobGoss on 2016-11-18
Sounds good well be here if you need assistance good luck

---

### Post by GiuHei3u on 2016-11-18
All worked very well with Rufus.

---

### Post by GiuHei3u on 2016-11-18
Great tool. Now running 12.04 on usb drive. Thanks RobGoss!

---

### Post by GiuHei3u on 2016-11-18
Good day!

---

### Post by gordintoronto on 2016-11-19
Ubuntu 16.04 is available in 64-bit and 32-bit versions. Your computer can almost certainly run the 64-bit version, which is a better choice.

Any current version of Ubuntu can be installed from DVD or USB. If you are installing to an external drive, there is a much better chance of success if you install from DVD. (If you install from USB, you will have SDA, SDB and SDC, and you really want to install onto SDB.)

> **gumshoegrant said:**
> Since 16.04 is a 64 bit os I downloaded 12.04.5 Desktop-i386 to my usb drive. This will not work correct? 12.04 must be burnt to a cd or a dvd right?

---

### Post by RobGoss on 2016-11-19
> **gumshoegrant said:**
> Great tool. Now running 12.04 on usb drive. Thanks RobGoss!

Great but were you able to install Ubuntu on the external drive?

---

### Post by Geoffrey_Arndt on 2016-11-20
Just a couple bits of info re this thread.   12.04 reaches EOL (end of life/. . end of support) in April 2017.    So, not a long term solution.    Second, an "outstanding" way to run any Linux distro is on an external usbv3 SSD such as the SanDisk 500 Extreme.

   Virtually the same speed and update-ability as a full internal disk install.   Not to be confused with a Live OS (read only) or Live OS (with persistence).

---

