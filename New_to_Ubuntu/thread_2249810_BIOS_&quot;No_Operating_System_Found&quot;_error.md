---
title: "BIOS &quot;No Operating System Found&quot; error"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by mark171 on 2014-10-24
I just recently downloaded Ubuntu 14.04.1 LTS and ran Pen Drive Linux as per the instructions. When I went to boot it using BIOS on my Dell Latitude, it was able to detect my USB, but when I selected it, I got the error message "No Operating System Found" and then it loaded Windows 7. Does anyone know what I did wrong? Do I need to re-install Ubuntu or will my current setup work? (Edit: The images shown on the[ help page]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") have the "Format Drive" option checked. Will this matter, seeing as my USB was blank to begin with?)

---

### Post by oldfred on 2014-10-24
Some systems require you to turn on or allow boot from USB ports. Check your BIOS?

Is this a newer system that you installed Windows 7 over Windows 8? Then it would be UEFI which has even more settings.

---

### Post by barroncm on 2014-10-24
You dont need to reload Ubuntu, just upgrade it. The software upgrade service should show an available up date to the kernal. Or from a command prompt you can run do-release-upgrade.
This is assuming you have an older ubuntu version loaded already.

---

### Post by oldrocker99 on 2014-10-24
The program generally recommended for burning a bootable USB device is called **unetbootin**, which is in the Ubuntu repositories, and also is available for Windows and Mac machines.

One important tip: Format the USB device **first**, and format it as **FAT**. This is the usual cause of an unbootable USB.

---

### Post by mark171 on 2014-10-24
First, an update to my specs would be in order. I am currently using a Dell Latitude D820, with BIOS revision A10. the processer is an Intel(R) Core(TM)2 CPU with 2 gigs of RAM. As far as I can tell, BIOS doesn't need any changes to boot from USB, I have successfully booted ChromeOS from USB before. It doesn't use UEFI, so that can't be the problem.

---

### Post by grahammechanical on 2014-10-24
&#924;y BIOS sees a USB memory stick with Ubuntu on it as an external USB disk. So, even if I have the boot order set to boot from USB before hard disk the live session does not load. I have to go into a section of the BIOS where I can change which hard disk to boot from.

It might be something similar with your machine.

Regards.

---

### Post by oldfred on 2014-10-25
Then I would check that ISO downloaded correctly.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that is good then it can be just which tool you used to write ISO to flash drive or even some flash drives seem to work when others do not.

 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
           
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

   Usb installer from Windows - pendrive
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

    Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

 Howto make USB boot drives 
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)
pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by rahul25 on 2014-10-25
Don't do such long process just install universal USB and flash it in the USB if not understood go to YouTube and watch the video to install ubuntu through USB

---

### Post by Vladlenin5000 on 2014-10-26
Please... The links in post #7 are enough to guide you trough the process. The information there has been tested and confirmed by many people unlike certain Youtube videos that contain many errors and/or "bad practices" and/or are specific for a certain installations or certain hardware. Well intentioned, no doubt, but lead many newbies into a path they hardly can recover from.

---

### Post by mark171 on 2014-10-26
> **Vladlenin5000 said:**
> Please... The links in post #7 are enough to guide you trough the process. The information there has been tested and confirmed by many people unlike certain Youtube videos that contain many errors and/or "bad practices" and/or are specific for a certain installations or certain hardware. Well intentioned, no doubt, but lead many newbies into a path they hardly can recover from.
I agree with you, and all my hopes have been dashed. I tried one of the Youtube video methods and now my computer doesn't register my flash drive... :cry:

---

### Post by snowmobiler on 2014-10-26
Mark,
I am a windows guy who recently got into Ubuntu. I had a spare 8GB flash drive that I used Ubuntu 14.04 to make a bootable flash drive. I too was trying to load on to a Latitiude D820. What I realized was that even though I formatted the flash drive as FAT, it was labeled as gpt instead of MBR. I used EASEUS partition manager on Win7 to change the setting to MBR, then re-did the imaging to the flash drive and it worked fine.
Steve

---

### Post by oldfred on 2014-10-27
If you use the dd method to copy ISO to flash drive, that is not a standard partitioned device. It is an image of the DVD that is more like a DVD even though on flash drive. DVD are not partitioned but have their own configuration.

So then you have to erase the first sector or MBR (sector 0) and create a partition table for flash drive to work.

I think MBR should work, but I also have only used gpt partitioning with all new devices whether hard drive or flash drive.

---

### Post by Alireza_Zamani on 2014-10-27
hi
first run your system with Ubuntu Live!
then in Ubuntu , Format you Flash Drive to Ext4 File System and write you ISO file with "Disk Image Writer" program to your flash ,

---

### Post by mark171 on 2014-10-30
> **snowmobiler said:**
> Mark,
I am a windows guy who recently got into Ubuntu. I had a spare 8GB flash drive that I used Ubuntu 14.04 to make a bootable flash drive. I too was trying to load on to a Latitiude D820. What I realized was that even though I formatted the flash drive as FAT, it was labeled as gpt instead of MBR. I used EASEUS partition manager on Win7 to change the setting to MBR, then re-did the imaging to the flash drive and it worked fine.
Steve

Thanks! Your idea of using a partrion manager was good, but i used a different one, due to the fact that my disk was formatted as "Super Floppy". EASEUS doesnt allow editing of other formats. i created a main primary partion and a small unallocated partion with MBR, and it worked fine. creating it all as primary reverted to super floppy for some reason. i then re-imaged it using Unetbootion. it works fine now, just have to get all the plugins ready to run most videos!

---

