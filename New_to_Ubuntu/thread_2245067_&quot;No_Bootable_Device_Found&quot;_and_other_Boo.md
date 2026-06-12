---
title: "&quot;No Bootable Device Found&quot; and other Bootable USB Trouble"
date: 2014-09-20
forum: New to Ubuntu
---

### Post by yusuke2 on 2014-09-20
Note: Although I mention multiple types of Linux, only one OS (or partition) is every loaded on the usb at a given time. 

Goal: I am trying to boot ubuntu from a usb flash drive (32gbs). I'd like to store all ubuntu content on the USB. I would rather not partition my main hard drive to boot it. 

The SetUp:

   The Computer:
       I am running OS X 10.9.4 (Mavericks) on a 2.6 GHz Intel Core i5 Macbook Pro.

   The USB:
      I have a 32.46 GB UFD 2.0 Silicon Power32G Media USB.

Process:

   Configuring the USB:
       What should I configure the USB as?
           Options
            - GUID Partition Table - Apple Partition Map - Master Boot Record
           Format
           - Mac OS Extended (journaled) - MS-DOS(FAT) - ExFat - Free Space

   Configuring Ubuntu:
       The iso file I've downloaded has worked in a VM.
       I've been trying to use this step-by-step process to configure the ubuntu file and usb: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
      However, I had to tweak the [COLOR=#333333][FONT=Ubuntu Mono]hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso[/FONT][/COLOR] by eliminating the ~/ in each of file-paths in order to not receive a No file or directory found error. I don't think this is a big deal though. (I was able to use this system to sort of boot antergos)

    Booting:
      After completing the 10 steps, I eject the usb, unplug it, restart the comp in boot by holding alt/option. I plug in the usb. If I've done the 10 steps correctly, an orange disk image with the word "Windows" appears next to the silver Macintosh HD image. (When I was able to boot Antergos, it actually said "Antergos" but says Windows when I try to boot Ubuntu or Tails).
      I double click the Windows Image. The screen goes black. At the top a cursor blinks and then outputs:
 
"No Bootable Device -- insert boot disk and press any key"

This has happened every time I've been able to successfully bring up a Ubuntu option on the Boot. 

Please help/advise me. I will gladly answer any questions. Thanks
______________________
I've also tried using unetbootin which told me that I should insert the usb into a PC not a mac in order for it to work.

I tried using DiskMaker X. Which does not work.

I also tried creating a startup disk of the usb through Ubuntu through a VM. This did not work.

---

### Post by sudodus on 2014-09-21
Welcome to the Ubuntu Forums :-)

There is a thread in the Ubuntu Forums, that might help you solve your problem. See [this Ubuntu Forum thread by Quackers]("http://ubuntuforums.org/showthread.php?t=2174630")

There is a lot of related information about booting from USB at the following link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by snowmobiler on 2014-09-23
I just went through the same issue. My USB stick (8GB) was configured as GPT, I had to initialize it as MBR, then format as Fat 32. Then it worked.

---

