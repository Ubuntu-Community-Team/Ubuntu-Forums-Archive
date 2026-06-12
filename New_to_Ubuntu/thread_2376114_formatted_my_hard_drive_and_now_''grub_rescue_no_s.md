---
title: "formatted my hard drive and now ''grub rescue: no such partition'' error comes up"
date: 2017-10-30
forum: New to Ubuntu
---

### Post by pyroxd on 2017-10-30
so i dual booted Windows 10 and Ubuntu [FONT=arial]16.04.1 then i formatted my whole hard drive because it was full of junk and viruses at least on the windows 10 side, ive tried booting off a live USB but it never wants to go to the install screen rather it goes to grub rescue[/FONT]

---

### Post by Autodave on 2017-10-30
Are you / did you put Win 10 back on?

---

### Post by Autodave on 2017-10-30
You are going to need to remove any and all partitons on the HD. You should be able to do that with your live USB.

---

### Post by pyroxd on 2017-10-30
no i cant boot from anything it always takes me to grub rescue

---

### Post by pyroxd on 2017-10-30
i did remove all partitions its just 1 big partition and i cant remove that

---

### Post by QIII on 2017-10-30
Hello!

Have you adjusted your BIOS to allow for booting from a USB device and placing that as the first in the boot order?

For some motherboards the device has to be inserted prior to entering the BIOS menu for you to be able to do that.

---

### Post by pyroxd on 2017-10-30
already did and i tried using a CD too

---

### Post by oldfred on 2017-10-30
Then it may be an error in ISO, try redownloading it & check it md5sum.
Or the install to flash drive/DVD was not correct.
If it cannot boot from flash drive, it reverts to booting from internal drive which still had boot loader and nothing else, so grub error.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[URL="http://www.ubuntu.com/download/desktop"]http://www.ubuntu.com/download/desktop
[/URL]
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

If UEFI system and you want UEFI installer:
      
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media) 
    [URL="http://www.ubuntu.com/download/desktop"]
[/URL]        
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]https://wiki.ubuntu.com/Win32DiskImager/iso2usb
[/URL]
 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) 

[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]
[/URL]

---

### Post by QIII on 2017-10-30
OK.  

Please work on oldfred's suggestions -- especially the md5sum suggestion.  If you still have trouble, we can try something else.

For whatever reason, when the motherboard is done with its thing it is looking for bootable media.  It is finding your original OS drive and turning control over to GRUB.  GRUB, not finding the partition is was told to look for, is dropping to GRUB rescue.

I have an experiment to check to see if we can get around that for a moment.  However, before I suggest that:

1.  Is this a laptop or a desktop?

2.  What is the manufacturer and model number?

3.  Would opening the machine void your warranty?

---

### Post by pyroxd on 2017-10-30
replying to oldfred's answers: ive downloaded multiple ISO's and none of them would go to the install screen it would always go back to grub rescue so now as you suggested im using Rufus to make a another live USB thats FAT32 and UEFI.
replying to QIII: it is a desktop that is custom built so i dont really have a model number but i can provide my motherboard model numberer if needed and no i open the computer to switch hard drives (the one whit the grub rescue and a working secondary one)


ok so a little bit of progress now my computer thinks the USB is a hard drive but it still wont boot from it it goes to grub rescue again


ok i adjusted the boot order and now nothing shows up other then that small blinking ''_''

---

### Post by oldfred on 2017-10-30
Need to know Motherboard brand & model number.
Some require a few settings and others multiple settings to work.

It is normal that USB drive is seen as a hard drive. Back in 2006 with my custom build it took me quite a while to figure that out. I had tried every USB boot options and none worked, but  then under hard drive was my USB flash drive.

---

### Post by pyroxd on 2017-10-30
Asus M5A78L-M

---

### Post by pyroxd on 2017-10-30
ok so an update my hard drive fell out of its cage then the screen went black then it showed me the ubuntu install screen
so i guess my problem is resolved?

---

