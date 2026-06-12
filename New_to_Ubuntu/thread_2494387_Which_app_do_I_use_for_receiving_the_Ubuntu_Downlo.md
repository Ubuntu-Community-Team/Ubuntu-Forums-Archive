---
title: "Which app do I use for receiving the Ubuntu Download"
date: 2024-01-15
forum: New to Ubuntu
---

### Post by mdsmith1 on 2024-01-15
I have been attempting to download Ubuntu.

It asks me how should I open the package and I have tried to use Word which doesn't work. 

What package should I use?

I am attaching a screen capture. 

Mike

---

### Post by coffeecat on 2024-01-15
You don't open the downloaded ISO. It's an image which you write to a USB stick using special software. You then get a bootable USB which you can run as a live session to try Ubuntu without installing, or use it to install Ubuntu as a usable OS on your machine.

Please be aware that setting up a dual boot of Ubuntu with your existing Windows, if that is what you were planning to do, is not a trivial task. There are other options. Read through this Ubuntu tutorial - [https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview) - which includes instructions for writing the ISO to a USB stick - and then if you have any questions, do not hesitate to ask.

Welcome to the forum.

---

### Post by yancek on 2024-01-16
The image you posted shows you have previous downloads of Ubuntu as well as rufus which is software you can use to create a bootable usb.  Try that.I

---

### Post by grahammechanical on 2024-01-17
The Ubuntu ISO image is in fact a compressed or archived file. So, it can be opened or extracted by an app designed to do that. The Ubuntu ISO image gives us a fully functioning Ubuntu operating system but compressed to a size that can fit onto a DVD disc or USB stick. In the past Ubuntu was small enough to fit on a CD-ROM disc.

How we do it today;

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

Regards

---

### Post by ActionParsnip on 2024-01-19
Use something like Etcher to copy the ISO to a USB stick, or burn the ISO to a DVD. Its not an installer like a Windows application

---

### Post by MAFoElffen on 2024-01-19
I have to say it... I, until recently, worked doing onsite warranty computer repairs & support for HP, Dell and HP... For both Windows and Ubuntu (yes, they all had some Ubuntu pre-installed in their lineups on some models.) On calls, along with my tools, I took my Laptop, plenty of pre-made bootable USB Flash Drives, and blank ones to create as needed. I got paid by the call, so time mattered and accuracy.

I intermittently had problems booting USB's made with Etcher. Yes, it works most of the time, but I did run into problems some times. I never ran into problems with Rufus. That is just the honest truth in my experiences.

You have Rufus installed already. Here is a tutorial: [https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-with-rufus-on-windows/14020](https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-with-rufus-on-windows/14020)

---

### Post by TheFu on 2024-01-19
I've been using **cp** to create boot/install flash drives.  Anything that can copy bits from A ---> B unmolested will work.  No need for any specific tools. There must be 20 built-in programs that copy bits from A--->B on every Unix system.  I have never, ever, ever, had any issues with this method.

```
$ sudo cp /tmp/path/to/ubuntu.iso  /dev/sdZ
```

Of course, you'll need to 100% know the target device, /dev/sdZ. If the wrong device is used, a terrible day/week/month/year could happen. There's zero protection from user mistakes.

Of course, if you are on MS-Windows, I think every program molests the bits during copy.

---

### Post by mdsmith1 on 2024-01-22
I used the Belena Etcher app to create a bootable Flash Disk.
I have downloaded the Ubuntu .iso file and have it in my download folder.
I am using Windows 11.
I have rebooted my computer and held down the F12 key which is supposed to allow me to route to the bootable flash drive but that didn't work.  
So I still have not installed Ubuntu.
What should I do next?
Mike

---

### Post by aljames2 on 2024-01-22
Welcome!

It sounds like you are attempting to begin an installation, or a "Try Ubuntu" from the USB.  You mentioned you are on Windows 11.  Good to elaborate what you are up to so folks can understand you goal. Did you read through the entire resource that coffeecat linked to in #2?  Read it all and understand it, and keep asking questions..

The F12 thing is to get into your bios, boot system. Although, F12 doesn't work on my computer, instead it is F2 or DEL. On some computers it could be F10.  Anyhow, once you gain access there is an option to select your USB as your boot device.

Have you tried Ubuntu yet?  That installer you made can let you test-drive it first on your computer.  Select "Try Ubuntu" first to see if you like it and to see if everything works.

I do not do dual-boot so I will have to bail out here.

---

### Post by aljames2 on 2024-01-22
On second thought, I did buy a laptop about 6 months ago and my goal was to zap Windows 11 off the internal NVMe and install Ubuntu.  This I could handle, but I remember how crazy it was to get into the Windows 11 UEFI Bios.  The laptop had the Windows 11 Home edition, not sure if Pro requires this or not, but the usual F2/F12/DEL was not an option upon bootup.  I had to go into the Windows system recovery section and select advanced startup to tell the system which device to boot up to.  What a pain that was to learn for the first time, anyhow thats all I have.

---

### Post by lucky092 on 2024-01-25
When Ubuntu runs [GUI mode], it will automatically notify you if updates are available.

---

### Post by MAFoElffen on 2024-01-27
> **aljames2 said:**
> On second thought, I did buy a laptop about 6 months ago and my goal was to zap Windows 11 off the internal NVMe and install Ubuntu.  This I could handle, but [COLOR=#ff0000]I remember how crazy it was to get into the Windows 11 UEFI Bios.  The laptop had the Windows 11 Home edition, not sure if Pro requires this or not, but the usual F2/F12/DEL was not an option upon bootup.[/COLOR]  I had to go into the Windows system recovery section and select advanced startup to tell the system which device to boot up to.  What a pain that was to learn for the first time, anyhow thats all I have.
This is important to recognize this, as a support person helping Users... It explains the why we recommend some things.

That is because, until you turn off/disable "fastboot" in the UEFI BIOS Settings, the Post ignores USB's and keyboard input. That is why we recommend turning that setting off as a default. We want to be able to provide some kind of input if something is wrong, to be able to interrupt the boot process and do things to fix that machine. 

On another topic, I do have to note that very time I see the title of this thread, it makes me think of Download Managers. I don't know why.

---

