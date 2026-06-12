---
title: "Best tool to create Ubuntu ISO to USB?"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by geminiforex on 2013-12-29
I saw that one being talked about:

[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

Is this a reliable tool to create an Ubuntu USB? Will the created ISO be totally clean? Can I trust it - or is there any advisable ISO to USB tool which Linux community sees more reliable?

---

### Post by hoopia on 2013-12-29
I've always used UNetbootin, seems to work pretty well for me:

 [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by sudodus on 2013-12-29
There are many tools, and different people have different favourites. It depends on the situation, which tools is the best. For example, do you need a tool to migrate from Windows or Mac, or do you need a tool, that works well in Linux?

-o-

There is a rather general overview in this link: [URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]https://help.ubuntu.com/community/Installation/FromUSBStick
[/URL]
Many people like ***Unetbootin***, that works from Windows as well as from Linux. Ubuntu's own ***Startup Disk Creator*** alias *usb-creator-gtk* and *usb-creator-kde* also works well, particularly now that a nasty bug has been squashed so usb-creator-*gtk* is much more reliable. And some people like tools by ***Pendrivelinux*** (described in the opening post).

I have good experience cloning iso files and compressed image files with the script ***mkusb***, which is described in the [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

It is also possible to use a simpler method, and install systems from tarballs with the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971")

---

### Post by 3grciii on 2013-12-29
I have to agree with rushi4687..

 			 				[INDENT] 					I've always used UNetbootin, seems to work pretty well for me:

 [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) 				[/INDENT]

---

### Post by monkeybrain20122 on 2013-12-29
Unetbootin is ok if you just want one os and don't need persistence (it only supports persistence for Ubuntu last I checked, don't know how reliable it works)
I find it inefficient to put just one live os in a 8 gb flash drive. Therefore:

I use multi-system in Ubuntu to create multiboot usbs with optional presistence.
[http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install)

If I were on Windows I would checkout LILI
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by geminiforex on 2013-12-29
Thx - 

I will check all of them.

In addition, is there any way to make the bootable USB stick only readable? I exactly want this non-writable.

I was unable to do that with an USB stick. As a solution, I purchased an SD Card, and made it read only, and put it on an USB Sd adapter.

The lock button on the SD card works well on normal SD card slot, so there is no problem with the button on the SD Card, it works - but when I put it in the USB SD adapter, the lock button does not work and it can be written.

I guess this "lock" button on the SD card is only useable when placed in the SD slot and the card sends a hardware signal from the slot to the PC not to write anything. I thought that button had something to do with the SD card itself internally preventing anything to be written. But that seems not to be the case as the lock button does not work on an USB SDadapter.

So I do have a few options, whichever works:

1. I have to make the SD card read-only on the USB SD adapter - possible?
2. I have to make the Laptop boot from the SDCard slot - But that does not seem to work, and bios does not seem to allow in both Laptops.
3. Most viable solution seems to be making the SD card image transferred to a DVD as a bootable media. I guess, simply copying and pasting the contents from the card to the DVD will not allow that? Is there any other solution or software to make exactly the same image on the SD card to boot on DVD?  

This is a customized Ubuntu - software added etc. so simply burning the official Ubuntu ISO on a DVD won't work for me - and I am unable to customize a live CD with some terminal commands. I am a novice regular Windows user and a GUI type of guy as most of the people. So - I would need to transfer the bootable card to a bootable CD ---- possible?

I looked at the stores over here for USB sticks with "read only" buttons - they are not available.

---

### Post by 3grciii on 2013-12-29
Valid points. As I don't use persistance and have a stack of old 4GB USB sticks I didn't consider that.  My experiance with multi-system was less than stellar as some systems I use prefer grub, some syslinux and others grub4dos. I find it cleaner and easier to keep these seperate and felt that keeping it simple in an Absolute Beginners section was preferable. :p

---

### Post by sudodus on 2013-12-29
> **3grciii said:**
> Valid points. As I don't use persistance and have a stack of old 4GB USB sticks I didn't consider that.  My experiance with multi-system was less than stellar as some systems I use prefer grub, some syslinux and others grub4dos. I find it cleaner and easier to keep these seperate and felt that keeping it simple in an Absolute Beginners section was preferable. :p

+1

---

### Post by sudodus on 2013-12-29
> **geminiforex said:**
> Thx - 

I will check all of them.

In addition, is there any way to make the bootable USB stick only readable? I exactly want this non-writable.

I was unable to do that with an USB stick. As a solution, I purchased an SD Card, and made it read only, and put it on an USB Sd adapter.

The lock button on the SD card works well on normal SD card slot, so there is no problem with the button on the SD Card, it works - but when I put it in the USB SD adapter, the lock button does not work and it can be written.

I guess this "lock" button on the SD card is only useable when placed in the SD slot and the card sends a hardware signal from the slot to the PC not to write anything. I thought that button had something to do with the SD card itself internally preventing anything to be written. But that seems not to be the case as the lock button does not work on an USB SDadapter.

So I do have a few options, whichever works:

1. I have to make the SD card read-only on the USB SD adapter - possible?
2. I have to make the Laptop boot from the SDCard slot - But that does not seem to work, and bios does not seem to allow in both Laptops.
3. Most viable solution seems to be making the SD card image transferred to a DVD as a bootable media. I guess, simply copying and pasting the contents from the card to the DVD will not allow that? Is there any other solution or software to make exactly the same image on the SD card to boot on DVD?  

This is a customized Ubuntu - software added etc. so simply burning the official Ubuntu ISO on a DVD won't work for me - and I am unable to customize a live CD with some terminal commands. I am a novice regular Windows user and a GUI type of guy as most of the people. So - I would need to transfer the bootable card to a bootable CD ---- possible?

I looked at the stores over here for USB sticks with "read only" buttons - they are not available.

If you run your pendrive as a live CD (made from the iso file without any effort to make it persistent), all files and tweaks and temporary files will be gone after you shutdown the computer. It will be similar to running from a CD or DVD. The root file system will be created from a compressed file and set up in RAM. If there is a disk with a swap partition, some content might be possible to extract from there, otherwise all traces will be wiped a few minutes after shutdown (when the energy has dissipated from the RAM memory cells).

In this case the One Button Installer is not an option, since it will create 'installed systems', which store data in the pendrive.

---

### Post by tea for one on 2013-12-29
> **geminiforex said:**
> Thx - 

In addition, is there any way to make the bootable USB stick only readable? I exactly want this non-writable.



This looks like an additional thread to your project of running a "sensitive financial task"

I assume that your task will need internet connection yet you do not want to receive any data via the internet?

You may wish to consider a modified distro which will load and run in RAM.

i.e. once you have removed your internal HDD, created your distro on your USB stick, booted from the USB stick, you can then run your program in RAM after removing the USB stick.
therefore, no writing to the USB stick.

---

### Post by geminiforex on 2013-12-29
> **sudodus said:**
> If you run your pendrive as a live CD (made from the iso file without any effort to make it persistent), all files and tweaks and temporary files will be gone after you shutdown the computer. It will be similar to running from a CD or DVD. The root file system will be created from a compressed file and set up in RAM. If there is a disk with a swap partition, some content might be possible to extract from there, otherwise all traces will be wiped a few minutes after shutdown (when the energy has dissipated from the RAM memory cells).

In this case the One Button Installer is not an option, since it will create 'installed systems', which store data in the pendrive.

Thanks. I did not know this. I thought that only live CD was capable of that. So I will test and see if USB will not be modified. USB stick is more convenient for me compared to CD. I just thought it was modifed. That helped a lot - thanks!...

---

