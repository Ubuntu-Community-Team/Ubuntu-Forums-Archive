---
title: "formating external drive with ubuntu so I can boot from external drive"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by bill_bokstein on 2013-12-27
Hi Guys,
Thanks in advance for the help.
[LIST=1]
[*]Do I need to reformat drive and backup data before installing Linux on drive?
[*]Where can I get the software and how do I load Linux as opposed to Windows 7?
[/LIST]
That's it thanks so very very much for your help!
Bill Bokstein

---

### Post by de Bacon on 2013-12-27
Hey, 
If you want to keep the data on the drive, you had best back it up or copy it onto a different partition than the one you intend to use for your install.  It is never a requirement to back up anything, ever!  

The source for getting software is through the various distributions of Linux, there are many.  What is best is something that each individual must determine for themselves.  You are on Ubuntu forums here so that might insinuate that you are planning to use one of its variant distributions. After you make your choice you have to download a copy of it to your existing system and make a "live" disc of it, dependent on its size, it will fit on either a CD-R or a DVD-R.  You must burn this .ISO file onto the media before you can install it on your system.   

The remaining software, of your choosing, comes from centers of distribution that are set up all over the world, through what are known as repositories.  It might sound difficult, but it is made very simple, though it is likely you will find a bit of learning curve dependent on your abilities with computing.

Best of luck

---

### Post by bill_bokstein on 2013-12-27
thanks a lot de bacon

---

### Post by bill_bokstein on 2013-12-27
so is this the way it works? I download a distribution of umbunto and than burn it onto a DVD which will make it a live version than install it on my external drive?
thanks again

---

### Post by oldfred on 2013-12-27
I prefer flash drives now. But you can use DVD.  You do not copy ISO file to drive, but have to install it to make it bootable.

Instructions also on this download site.
       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If an external drive best to use manual install or Something Else. Default install is / (root) and swap but it also defaults to installing the grub2 boot loader to sda, which usually is your internal drive. You should just keep Windows boot loader on internal drive.

---

### Post by monkeybrain20122 on 2013-12-27
> **bill_bokstein said:**
> so is this the way it works? I download a distribution of umbunto and than burn it onto a DVD which will make it a live version than install it on my external drive?
thanks again

Umbunto??

Anyway, use the 'advanced' or 'manual' option to install and  make sure you install the bootloader in the external drive (like /dev/sdb, e.g) default is the internal drive of your computer. If you install bootloader in the internal harddrive your computer would become unbootable without the external drive plugged in (fix would be easy if you are also running Linux in your internal drive, if it is Windows you are going to have a lot of pain :))

---

