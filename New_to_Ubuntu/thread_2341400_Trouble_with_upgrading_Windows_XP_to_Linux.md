---
title: "Trouble with upgrading Windows XP to Linux"
date: 2016-10-27
forum: New to Ubuntu
---

### Post by boochie2 on 2016-10-27
I am new to Linux. Second day trying to reboot from USB drive.  Computer keeps loading Windows XP and doesn't see files on USB. I changed the boot sequence in BIOS to Removeable.....still no luck. This is an Gateway GT5228 AMD Anthon 64x2 Dual Core 4200+ 2.21 Ghz, 1.87 of RAM. I know its pretty old, but in good condition, barely used.  I am trying to use this second computer for training to learn Linux and other computer classes. Can anyone help me start the process from scratch? First I would like to make sure I have a good download for Linux, which I will do on a separate updated ASUS computer, then I would like to use USB to install Linux on old AMD computer.  Any takers up for the challenge?

---

### Post by Koobelakahn on 2016-10-27
Are you looking to dual boot or completely be rid of Windows?

---

### Post by Bucky Ball on 2016-10-27
Welcome. How are you creating the USB drive and which release/flavour of Ubuntu are you using (standard Ubuntu 16.04 LTS or something else)?

The best and safest way to obtain the install ISO is from [the official download site]("https://www.ubuntu.com/download/desktop") (did you get the ISO from there?). Go there to '[Alternative Downloads]("https://www.ubuntu.com/download/alternative-downloads")' and down the page a bit grab the torrent file and torrent the ISO. You will get a clean copy. 

Failing that, have you checked the MD5SUM of the ISO you already have? Have you downloaded the 32bit or the 64bit version of Ubuntu?

---

### Post by kurt18947 on 2016-10-28
Something to consider re your machine's specs. Which 'flavor' of Ubuntu are you trying? I would probably one of the 'lightweight' versions such as Xubuntu or Lubuntu. Those are less graphically demanding. This shouldn't matter regarding your problem with getting a flash drive to boot but may impact your user experience.

Echoing Bucky Ball, how did you create the USB drive? Are you sure your machine will boot from a live USB? Some older machines can be kind of 'persnickity' with that. Kind of 'old school' but can you burn a DVD? I've had problems with booting live USBs on older machines but never a problem that I can recall with live DVDs.

---

### Post by mörgæs on 2016-10-28
In addition to the fine contributions above:

If you have an Nvidia 6100 graphics card or a near relative, which many of similar Gateways do, then using closed source drivers are the best option. This is an exception to the rule: Most Nvidia cards are well supported by open source drivers.

---

### Post by boochie2 on 2016-10-28
I want to completely remove and install Linux. I will be using this computer for training.

---

### Post by leunam12 on 2016-10-28
Once you have the right ISO downloaded depending on your preference, use Rufus to create your USB stick. See below:

[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by Geoffrey_Arndt on 2016-10-28
Or another tool I've used with 100% success is Etcher.   It's open source (see github) and MUCH easier to use than many other similar tools.   

The developers obviously have a HF (human factors) specialist on the team (FWIW, . . Mark Shuttleworth is a big-time HF proponent . . )

Anyway, here's the link:   [https://www.etcher.io/](https://www.etcher.io/)

---

### Post by RobGoss on 2016-10-28
Hello and welcome,** Kurt** is post **#4 **mentioned trying a **DVD** instead of a USB drive if your machine is still running** Windows XP **then I'm almost certain it may not recognize a bootable USB and cannot boot from it. Download the Ubuntu ISO and burn it to the DVD instead and try booting from that and let us know how that works

You would also probably have to use a lighter distribution also noted in the comments above it seems you don't really have much RAM for Ubuntu 16.04

Here's the link to download Lubuntu 32-bit [http://cdimage.ubuntu.com/lubuntu/releases/14.04.5/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04.5/release/)

---

### Post by him610 on 2016-10-29
Not sure if a computer as old as yours will even boot from a USB drive. 
Were you able to select 'boot from USB' as your first boot option in the BIOS?

---

### Post by verymadpip on 2016-10-30
Hi there!
Sometimes I have found the USB boot option to be "hidden" amongst the hard drive boot priorities.

---

### Post by leunam12 on 2016-10-31
You can try also plop boot manager which you can run from cd and it will give you a menu to boot from USB even if BIOS does not allow it.

[https://www.plop.at/en/bootmanagers.html](https://www.plop.at/en/bootmanagers.html)

---

