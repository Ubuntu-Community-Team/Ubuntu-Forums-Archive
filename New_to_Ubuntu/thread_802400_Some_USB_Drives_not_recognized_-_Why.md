---
title: "Some USB Drives not recognized - Why?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by egruber on 2008-05-21
I am running Hardy on an IBM T40.  I have a number of USB drives.  Some of them work perfectly.  Others don't work at all. I plug them in, but the little light on the drive stays out and the laptop behaves as if nothing was plugged in.  All of them work perfectly on my XP machine.  

Other than the brand names and file capacities, the drives are pretty much the same.  Any idea as to why some of them don't work?  BTW, my wife had a similar problem on her MAC. She bought 5 drives..all the same.  Some worked, some appeared dead.  But all worked on my XP machine.

---

### Post by EXCiD3 on 2008-05-22
Interesting. Try pluging them in and running "lsusb" to see what is connected to usb, make sure the drives are listed here so that we know it is not a detection issue and that it is a mounting issue. Next you should install GParted and with the drive plugged in see if it appears in GParted with a valid partition.

---

### Post by egruber on 2008-05-22
> **EXCiD3 said:**
> Interesting. Try pluging them in and running "lsusb" to see what is connected to usb, make sure the drives are listed here so that we know it is not a detection issue and that it is a mounting issue. Next you should install GParted and with the drive plugged in see if it appears in GParted with a valid partition.

I am thinking it is a detection issue because many of my drives detect and mount automatically.  Just some are stubborn.

I'm really a Linux newbie, so I need some simple instructions to try your suggestions.  Thanks!

---

### Post by tgyorgyi on 2008-06-08
I might have a similar problem. Looked through a lot of posts re. USB external drives, all are about mounting problems, but in my case, the external usb HD and pendrive don't do a thing. They do get juice, the led lights up, but nothing moves. I did *lsusb* (which was so far the first useful advice as far as my problem is concerned) and indeed, only the printer is listed:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:7204 Hewlett-Packard DeskJet 36xx
Bus 001 Device 001: ID 0000:0000  

So far so good, it is a detection issue then. But what now? I'm in this forum because I'm new as well, looking for a viable alternative to Windows, so very basic instructions are very welcome! Thanx in advance!

---

### Post by Rhapsody on 2008-06-08
I have the same problem. I've got an 8GB USB flash drive plugged in here, and lsusb says:

Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 003: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

It can see my keyboard and mouse, but it's not listing anything else. How do I make Kubuntu see this thing?

---

### Post by kansasnoob on 2008-06-08
I've used two different methods for hot-plugging usb drives. Both simply amount to adding something from synaptic.

Try adding either usbmount .............

or pmount and hal.

I have a bit of preference to usbmount due to simplicity, but the latter (pmount + hal) will automatically create a desktop icon whereas usbmount does not.

---

### Post by EXCiD3 on 2008-06-08
I just noticed one of my mom's usb drives won't automatically detect in my laptop, pretty sure its just running fat32, its a 4gb OCZ drive, but won't mount automatically like every other drive...Not sure why it doesnt automount like the ones of yours. I'd rather not have to manually mount it and id like to solve the problem. Once i get some highspeed for a while ill experienment with it and see what i can figure out.

---

### Post by tgyorgyi on 2008-06-09
> **kansasnoob said:**
> I've used two different methods for hot-plugging usb drives. Both simply amount to adding something from synaptic.

Try adding either usbmount .............

or pmount and hal.

I have a bit of preference to usbmount due to simplicity, but the latter (pmount + hal) will automatically create a desktop icon whereas usbmount does not.
No change by me... I guess in order to mount, drives have to be visible for the system in the first place. In my case they are not, as if nothing was plugged in. :-(

---

### Post by Sceiron on 2008-06-09
> **tgyorgyi said:**
> No change by me... I guess in order to mount, drives have to be visible for the system in the first place. In my case they are not, as if nothing was plugged in. :-(

By reading some earlier post about these disk are working with win-xp i came to think about one disk that didnt work for me some time ago.
If you dont close or proper safely remove hardware when unplugging the disk from xp there is some processes running on it, and you wont be able to "discover" it because it seems "busy" for the OS.

Assuming you just unplugged it, you should try connect to xp and do a "safely remove hardware", then try connect it to your linux comp.

---

### Post by EXCiD3 on 2008-06-09
Thats usually a problem only for NTFS though, but def worth a shot still.

---

### Post by tgyorgyi on 2008-06-12
hi, safe remove from Windows does not help. I had that once with the ntfs partition of the NTFS drive (Windows froze and I had to hard reset, and next time Ubuntu started it could not mount the ntfs partition). But then it actually displayed a large box with a message saying that it cannot mount because it was not safely removed from Windows, whereas the external hdd and the pendrive just do not show up in any way.

---

### Post by ex-wirecutter on 2008-06-12
I have had the same problem , a hard drive which worked perfectly as a hardwired slave , will not work when externally connected to a USB port in Ubuntu but works fine in Windows. Is it because Ubuntu cannot handle more than a couple of USB items ?

---

### Post by tgyorgyi on 2008-06-13
Additional information is, that if I type dmesg in the terminal window, I can see that Linux tries to communicate with the external HDD, and get this:

Unlink after no-IRQ?  Controller is probably using the wrong IRQ.

I searched for this error message and just found [this]("http://ubuntuforums.org/showthread.php?t=81153&highlight=noapic+usb") in the archives. AND IT WORKED!!! So simple. If you have similar symptoms than me, that some USB thingies work fine, others don't, maybe try this one.

For experiment I tried the more careful method of pressing 'e' during booting, adding 

acpi=off irqpoll

to the end of the kernel line (as I just found out on another thread, this way only the current booting would be altered, and if it does not work, I have not ruined it for good).

Since it does work, now I change it for good by using

sudo gedit /boot/grub/menu.lst

---

### Post by seren6ipity on 2008-12-07
Thanks, I was able to fix usb issue on my T40 with the pointers you provided.

> **tgyorgyi said:**
> Additional information is, that if I type dmesg in the terminal window, I can see that Linux tries to communicate with the external HDD, and get this:

Unlink after no-IRQ?  Controller is probably using the wrong IRQ.

I searched for this error message and just found [this]("http://ubuntuforums.org/showthread.php?t=81153&highlight=noapic+usb") in the archives. AND IT WORKED!!! So simple. If you have similar symptoms than me, that some USB thingies work fine, others don't, maybe try this one.

For experiment I tried the more careful method of pressing 'e' during booting, adding 

acpi=off irqpoll

to the end of the kernel line (as I just found out on another thread, this way only the current booting would be altered, and if it does not work, I have not ruined it for good).

Since it does work, now I change it for good by using

sudo gedit /boot/grub/menu.lst

---

