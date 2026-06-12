---
title: "How to fix MBR using Ubuntu 8.04"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by shailendra on 2008-05-14
Hi,

I have Windows XP installed on my Dell laptop. Few days back I installed Ubuntu 8.04 in my USB external hard disk. 

Now when I startup my laptop, I get GRUB Error 21 if the external hard disk is not connected. So, I have to first connect the external hard disk and then power up the laptop. I then get the option to log on to Ubuntu or Windows operating system.

I want to get rid of the dependency on external hard disk. I tried using the help provided in one of the Ubuntu forum thread.

So, as per the help if I try to execute "sudo apt-get install ms-sys" command, I get the error "Couldn't find package ms-sys".

Here is the snap shot:
ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys

I don't know what to do next. Can anyone help me out through this? Also, is there any other way to fix the MBR?

---

### Post by tamoneya on 2008-05-14
if my MBR ever breaks I fix it with super grub: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by mkoehler on 2008-05-14
Check out this thread: [http://ubuntuforums.org/showthread.php?t=672328](http://ubuntuforums.org/showthread.php?t=672328)

---

### Post by meierfra. on 2008-05-14
ms-sys is not Hardy repos. But you can install it via a debian package:

[http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys")

---

### Post by forrestcupp on 2008-05-14
If you do what you are asking about, it will overwrite grub and you won't be able to boot to Ubuntu at all.  Is that what you're wanting?

The reason the external has to be plugged in is because all of the grub settings files are located on whatever drive you installed Ubuntu on.

---

### Post by shailendra on 2008-05-15
Hi,

I want to keep Ubuntu on my external hard drive. So, I just want that when I power up my laptop and the external hard rive is not connected, I should be able to use Windows. 

Then if I want to use Ubuntu, I just have to connect the external hard drive, reboot the laptop and select Ubuntu.

Thanks in advance.

---

### Post by adrian15 on 2008-05-15
> **shailendra said:**
> 
I want to get rid of the dependency on external hard disk.


Please check:
[Grub on Removable External Hard Disk (Super Grub Disk Wiki)](http://www.supergrubdisk.org/wiki/GrubOnRemovableExternalHardDisk)
and if you are millionaire do not hesitate to donate some thousand dollars to the Super Grub Disk project. ;).

adrian15

---

### Post by stchman on 2008-05-15
> **shailendra said:**
> Hi,

I have Windows XP installed on my Dell laptop. Few days back I installed Ubuntu 8.04 in my USB external hard disk. 

Now when I startup my laptop, I get GRUB Error 21 if the external hard disk is not connected. So, I have to first connect the external hard disk and then power up the laptop. I then get the option to log on to Ubuntu or Windows operating system.

I want to get rid of the dependency on external hard disk. I tried using the help provided in one of the Ubuntu forum thread.

So, as per the help if I try to execute "sudo apt-get install ms-sys" command, I get the error "Couldn't find package ms-sys".

Here is the snap shot:
ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys

I don't know what to do next. Can anyone help me out through this? Also, is there any other way to fix the MBR?

That is the reason not to install an OS on an external drive.

The GRUB configuration files are on the external drive in the /boot/grub/menu.lst file and GRUB is written to the MBR of the main hdd in your laptop.

I recommend dual booting on your internal hdd and using the external hdd as storage unless your laptop hdd is really small.

---

### Post by meierfra. on 2008-05-15
I wrote a HowTo for your situation. Click on DualTwo in my signature.

---

### Post by adrian15 on 2008-05-15
> **meierfra. said:**
> I wrote a HowTo for your situation. Click on DualTwo in my signature.

If someone uses your howto needs, just after connecting the external hard disk needs to press F8 or another key in order to activate its boot.

Isn't it?

With my howto you do not need to press that F8 key.
And I also think that with my howto you do not have to type any commands.

But why don't we ask shailendra to test both howtos and tell us which one is the best one for her (or him?).

adrian15

---

### Post by meierfra. on 2008-05-15
> If someone uses your howto needs, just after connecting the external hard disk needs to press F8 or another key in order to activate its boot. Isn't it 

No. Just one and for all set the bios to boot from the external drive first.

---

### Post by adrian15 on 2008-05-16
> **meierfra. said:**
> No. Just one and for all set the bios to boot from the external drive first.

You are very lucky then. My BIOS needs to re set up the usb hard disk to be booted as the first time each time that I power down it. It might depend on the BIOSes I suppose.

adrian15

---

### Post by shailendra on 2008-05-18
Hi Everyone,

Thanks a lot for your help. I was able to fix the MBR by usiing ms-sys. I had to install ms-sys package by using debian.

---

### Post by shailendra on 2008-06-08
Hi,

Finally the issue was resolved. Follow the below link to know the procedure;
[http://ubuntuforums.org/showthread.php?t=822789](http://ubuntuforums.org/showthread.php?t=822789)

---

