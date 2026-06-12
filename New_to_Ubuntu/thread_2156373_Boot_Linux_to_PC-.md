---
title: "Boot Linux to PC-"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by jcg2u on 2013-06-21
Hey,

I am completely new to Linux and have practically no knowledge in computer science; however, I would like to learn.

I would like to use Linux with a Dell PC that is currently not working.

1st Question: Is this computer redeemable or does it need a new hard drive?

Here is what I have:

- Dell Desktop that goes to blue screen upon start: "A problem has been detected and windows has been shut down to prevent damage to your computer".

- Hard Drive Diagnostics tells me:
   
Drive 0:     ST3500320AS - Fail. Return Code: 7
Drive 1:     ST3160023AS - Pass

- Boot to Utility Partition - Utility partition not available

I have downloaded the unetbootin.exe file as well as an ubuntu plugin and try to boot from a usb, but i receive the message: "Missing Operating system".

Obviously I am missing a bunch of steps, but if someone could point me in the direction of a tutorial it would be very much appreciated!

Thank you!

---

### Post by oldfred on 2013-06-21
You have to install the ISO not copy it to the flash drive or DVD. You can use unetbootin to do that. New versions are oversize so CDs do not work anymore. 

       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Uly55es on 2013-06-21
Do you mean you can boot from the usb, but ubuntu exits with an error (Missing OS)? If not, are you sure you did all right with the usb (I mean: you downloaded an .iso image of ubuntu, put it into the usb using some program to create a bootable drive (e.g. pendrive, see pendrive.com), then changed your BIOS boot disks sequence...)

---

### Post by grahammechanical on 2013-06-21
If you manage to boot to a Ubuntu live session open the Dash - press the windows key or click on the Ubuntu icon at the top of the Launcher (panel at the left side) and search for Disks.

You can launch the Disks utility and it can check out the welfare of your hard disk. If the hard disk is a smart hard disk then the utility will read then information regarding serviceability on the disk.

Regards.

---

### Post by jcg2u on 2013-06-24
Thanks Old Fred!

Got the computer working great!  Excited to start messing with other versions!

---

