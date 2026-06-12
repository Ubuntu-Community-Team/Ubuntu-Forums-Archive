---
title: "Installing Ubuntu on laptop with USB stick"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by Laurence WM on 2012-10-15
Any tips for installing Ubuntu as dual boot on to my [Asus X501]("http://www.pcworld.co.uk/gbuk/asus-x501u-xx049v-15-6-laptop-white-14442750-pdt.html") 64-bit laptop (currently Windows 7), using an USB stick, would be much appreiciated. 

I have tried and failed to install with the wubi.

From these instructions

[http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)

I went to these ones:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

How should I reply to the questions asked by Pendrivelinux during the download (see link above)? 

Bit confused about whether I should download Ubuntu, then Pendrivelinux, or the other way round, or what? 

Many, many thanks,
Laurence

---

### Post by Zimmer on 2012-10-15
OK,
Installing to a Flash Drive is usually a case of installing the distribution so that it behaves like a Live CD would. There are other scenarios but let's be uncomplicated for now.
In order to create a live CD or a USB install you need the .iso file of the distribution you want to try. So download the one you want.. for simplicity eg.

ubuntu-12.04.1-desktop-i386.iso

Save this file somewhere memorable...

Then download the PendriveLinux Universal USB installer (UUI).

Insert your  USB drive and discover what Drive Letter Windows allocates to it.

If the 2 downloaded files  are saved in the same directory then when running the UUI your distribution should appear on a drop down list to select, if not, browse to the location of the iso..
Ensure you select the Drive letter of the USB for the install.
For simplicity ensure the USB drive is formatted to either FAT16 or FAT32.

Creating 'Persitence' (an option) on the USB will allow you to save changes etc to the USB install. 
See the instructions you linked to earlier..

When completed...
Make sure your BIOS is set to boot from USB BEFORE the internal drive or you will only boot to Windows..
Good Luck

---

### Post by oldfred on 2012-10-15
Zimmer mentions the 32 bit ISO, if your system is 64bit & has at least 3GB of RAM I would suggest the 64 bit version.
ubuntu-12.04.1-desktop-amd64.iso

How new is system? Some very new systems have UEFI as the new way to boot. Most UEFI will also boot in BIOS mode but if dual booting you have to install Ubuntu in same mode UEFI or BIOS as Windows is installed.

When you get liveUSB working use the try Ubuntu and check that system works ok. Then from terminal post this to see how drive is partitioned:

sudo parted /dev/sda unit s print

---

### Post by jackthesamurai on 2012-10-15
is it possible to create a live bootable usb using the 64 bit server .iso?

---

### Post by oldfred on 2012-10-15
Server & alternative installer are not liveCDs, but you can install from USB flash drive. 
They have more drivers, are text based installs to save room for drivers and different software. If you install with them, you probably should still have a liveCD to make repairs.

---

### Post by Laurence WM on 2012-10-15
Thanks a lot, guys. 

It all sounds a bit complicated, to my ultra-novice mind. I'll get a good night's sleep (it's bedtime here in England) and hope to give it a go tomorrow. I'll report back, most likely with further queries about why it  didn't work.

The laptop was purchased new last month, by the way. How would i find out whether it's got UEFI?

Cheers,
Laurence

---

### Post by Cheesemill on 2012-10-15
The X501A does use UEFI, I got one myself last week and installed 12.10 on it.

---

### Post by Laurence WM on 2012-10-16
> **Cheesemill said:**
> The X501A does use UEFI, I got one myself last week and installed 12.10 on it.


Oh thanks, Cheesemill. it's good to know it can be done.

Mine is actually X501U - is that a significant difference?

Did you install a 64-bit version?

So how does having UEFI affect what I should do, practicallY?

Thanks a lot,
Laurence

---

### Post by Laurence WM on 2012-10-30
How can I tell whether my Asus X501U laptop (purchased in September) has UEFI or BIOS?

If it has UEFI, how - in absolute beginner language, please - would that affect installation?

Thank you very much indeed,
Laurence

---

### Post by oldfred on 2012-10-30
From liveCD terminal run & post this. 
If partitioned with gpt and first (or second) partition is efi then you are in UEFI mode.
 If partitioned with MBR(msdos) then you have BIOS & MBR. 

sudo parted /dev/sda unit s print

---

### Post by Laurence WM on 2012-10-30
> **oldfred said:**
> From liveCD terminal run & post this. 
If partitioned with gpt and first (or second) partition is efi then you are in UEFI mode.
 If partitioned with MBR(msdos) then you have BIOS & MBR. 

sudo parted /dev/sda unit s print

Thanks a lot, Oldfred. 

I do apologise for my extrene ignorance, but some translation into absolute absolute beginner langauage would be appreciated.

Many thanks,
Laurence

---

### Post by oldfred on 2012-10-30
If you have the 64 bit liveCD or USB can you boot that? Then run liveCD try mode and open a terminal.

---

### Post by Laurence WM on 2012-10-31
> **oldfred said:**
> If you have the 64 bit liveCD or USB can you boot that? Then run liveCD try mode and open a terminal.

The laptop does not play CDs. Is there such a thing as a 64bit liveUSB, or are we back to square one?

Many thanks,
Laurence

---

### Post by oldfred on 2012-10-31
You create a liveUSB.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Write image or burn image not copy ISO as one large ISO file to CD or USB.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

