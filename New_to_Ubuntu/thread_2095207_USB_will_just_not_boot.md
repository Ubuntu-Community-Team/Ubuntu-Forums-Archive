---
title: "USB will just not boot"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by ziomeks on 2012-12-16
Another noob question.  I have taken the latest distribution and burned it to a DVD and it works fine.  No issues.  From inside the Ubuntu system I choose the option to setup a bootable USB and went through the steps as indicated and no error was forthcomming so I thought all was OK.  Not so.  The USB stick will not boot.
 
The BIOS is set to boot in this order:  USB then CD/DVD then HDD.  My burned DVD work just fine under this condition but the USB does not.  I can see during the boot of my system that the USB device IS being ping'd (a KINGSTON 4.0Gb stick with the lights flashing) but no success in booting.
 
Looking at the device after a _windows _startup, the device is visible.  The BIOS also 'see's' the device prior to boot up when I check the settings before it tries to boot.  This is driving me crazy.  The system stats are (custom machine built by me):
A8n32 ASUS mother board with the latest BIOS updates
AMD Athlon 64 x2
2.0 Gb RAM
 
What's going on?

---

### Post by Terry of Astoria on 2012-12-16
I have a Vaio that will boot from the USB port on one side of the computer, but will not boot from the USB ports on the other side!

---

### Post by squakie on 2012-12-16
Try unetbootin and see if the usb image it creates boots or not.

---

### Post by westcoast01 on 2012-12-16
[SIZE=2]Hello ziomeks, I have two machines running Ubuntu that [SIZE=2]have[/SIZE] [SIZE=2]Asus MB's and both of them require me to not only change the boot order but also to disable the hdd (usb flash drive only not dvd). [SIZE=2]A[SIZE=2]lso sometimes I need to format the flash drive and then erase it with the start up disk creator before [SIZE=2]I have a successful/bootable load. Hope this helps and please keep us informed of how it goes.[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by U-Ren on 2012-12-16
Did you try to select the boot device from the device tab menu thingy (it comes out if you type F8/Tab/ESC depends on your bios)? If it doesn't boot even from there it means your usb cannot boot. Try another usb port or format it like users said before me.

---

### Post by Cheesemill on 2012-12-16
It could also be your USB stick. I've had sticks that refuse to boot but work OK in every other situation. Try using a different one.

---

### Post by Mark Phelps on 2012-12-16
I've found that I have better success making bootable USB sticks using the tools from PendriveLinux.com.

---

### Post by Cheesemill on 2012-12-16
> **Mark Phelps said:**
> I've found that I have better success making bootable USB sticks using the tools from PendriveLinux.com.
I've always had issues using Ubuntus 'Startup Disk Creator' as well.
I find that UNetbootin gives the best results.

---

### Post by coldraven on 2012-12-16
My laptop won't boot from USB if there is any other USB devices plugged in. I usually have a SD card in the slot so I have to remember to remove it first.

---

### Post by kurt18947 on 2012-12-16
If you have a Windows install available, try formatting the USB stick to fat32 using Windows.  I have one machine AMD processor/chipset that will not boot a liveUSB if the stick was formatted with Gparted.  I get a 'boot error' message and that's that.  I checked to make sure the 'boot' flag was set.  If I format with Windows first,  the live USB is created using Unetbootin and boots just fine.  The same boot error  is not present on an older AMD/Gigabyte board or on a couple different notebooks so it appears to be the modular BIOS of this one board with an AMD785 chipset.

---

### Post by verymadpip on 2012-12-16
I often find flash drives in the HDD boot order thingummy.
Perhaps it's hiding in there.  Worth a look IMO.

---

### Post by Eugene King on 2012-12-16
depending on where and how you select the USB drive, how you partition it. (the swap space) it may have installed the iso in the second partition which will make it unbootable. 

I ran into this problem. 

whats weird is I installed 11.10 to my usb stick on works computer running XP and when I take the stick home to run off my VAIO laptop it won't boot.................but works fine at work.

---

### Post by C.S.Cameron on 2012-12-16
You might also check the MD5SUM of your downloaded iso to make sure it is not a little corrupt.

You could also try Plop boot manager, that should work if you can boot CD.

---

### Post by ziomeks on 2012-12-17
Thank you for  your responses.  Here's what I've already tried prior to my request to this forum:
1.  Tried three different USB ports as supported by my mother board.  All three yield the same 'no boot.'
2.  USB is formatted using the HP formatting tool and it's in the FAT32 mode.
3.  I changed the boot disk drive order to force the boot from the USB stick, not simply just go find it.  No help as it's stuck in a no-boot loop.
 
What I will try:
1. build the USB stick using the unet..... (can't rememeber hte name) and see what happens.
2. also try the linuxpendrive web site and thier recommendations for the building the stick.
3. Depopulating the USB ports for 'other' devices plugged in.  (I do have a USB signal line for the UPS and a bluetooth transciever plugged in)((printer uses ethernet)
 
What I'm confused about:
1. The request for shutting down the HDD.  As I have five HDD's in my system is this request to shut down all of them?  Just the boot HDD?
2. What exactly should the USB stick contain to be bootable?  Can I look to see if the proper setup happened?  What should be on the stick to boot?

---

### Post by Eugene King on 2012-12-17
Download the .iso file from Ubuntu and save it......depending on what operating system you have it may think its a ZIP file, just ignore that part.

Find your down load and burn the image to a DVD, Ubuntu has a great step by step for this and even breaks it down by operating system.

after image is burned to DVD install it in your drive and reboot the computer and do what is necessary to boot up off the DVD.

That should have you running Ubuntu off of the disk you just created.

Now pop the USB stick you want to install Ubuntu in a USB slot and select the install app on the Ubuntu desktop. 

The Pendrive doesn't always work for some reason. Yes it will install a usable version on the stick thats bootable.....however when you try and make a perminant install off the pendrive it fails sometimes. The DVD method always worked for me. And on top of that you only need 1 USB stick instead of 2 of them (one running the temp Ubunto and one that gets it permanently installed.

Follow the instructions. and make sure you know which drive your USB stick in. You should be able to recognize it by the size and name. select the drive and then "change" make it EXT4 and for boot you want to select "/". and select the format box and hit continue...............

I'm sure I missed a step or two but that is how to do a perminant install of Ubuntu onto a USB drive and use it as a PC / Linux box. 

PS this is how I'm replying to your question. Its a 32G ScanDisk USB stick from RadioShack, and I'm tethering with my iPhone 5.......

---

### Post by ziomeks on 2012-12-17
STOP!  Problem found (solved).
 
It turns out that the mother board is to blame.  From an obscure forums reference, there are three settings in the mother board BIOS that needs to take place.  These changes are NOT intuitive.  The USB legacy option is to be 'Enabled.'  The USB mass storage stttings are to be changed to 'HDD.' And finally, the USB stick has to be placed in the first position of the HDD list of boot devices.  YUK!!!!
 
After completing these changes, WA-LA! Works fine and boots OK.

---

