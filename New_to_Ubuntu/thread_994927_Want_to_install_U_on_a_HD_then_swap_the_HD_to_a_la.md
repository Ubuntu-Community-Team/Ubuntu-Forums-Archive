---
title: "Want to install U on a HD then swap the HD to a laptop"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by gefalu2008 on 2008-11-27
Hello,

I have an old laptop on which I have installed Ubuntu 8.04. 
However, the hard disk of the machine is only 10 GB so I 
would like to replace it with a bigger one.

The problem is, I can only access the machine by using a 
Wi-Fi card (the USB connections do not work any more 
and there is no Ethernet connection). Well, the phone 
line works, but it is of course very slow.

Please tell me if the following strategy would work:

- first I get a 60 GB HD and a USB frame & connection to support it
- second I install Ubuntu on this drive by using a separate desktop computer
- third I put the new hard disk into my laptop

The question is, will the HD boot with Ubuntu? 

If this does not directly, what kinds of modifications are required?

Thank you for your advice!

Gef

---

### Post by gefalu2008 on 2008-11-27
Just to add very quickly, there is no cd-rom in my laptop either...

Gef

---

### Post by Peter09 on 2008-11-27
I have done something similar (although with a desktop). The system booted OK, although I had a struggle to get the Video right as there were different cards in the machines.

Guess the problems you may face are

1. Grub might not work if the different BIOS change the hard drive name
2. Video may not work straight away
3. Wifi may not work straight away.

Also, if you do not get wifi working how would you obtain the right drivers?
However not sure what other options you have.

---

### Post by hyper_ch on 2008-11-27
could you attach the 10gb and 60gb drives somehow to your computer?

If so, you could just dd the 10gb drive to your 60gb drive, then alter the partitions (make it bigger) with cfdisk and finally grow the filesystem (I assume ext3) to the new partition size. That would probably be the fastest "installation"

---

### Post by Bucky Ball on 2008-11-27
Not a good idea as the 60Gb install will set up for the hardware it detects on the desktop, when you put it into the laptop it will get awful confused. You could try 'boot from LAN' on the laptop and try booting from a disk in the desktop. You may have 'boot from LAN' selectable in the BIOS.

What about 'partimage' and copy the partition over to the desktop, whack in the 60gb, then copy it back again? That could work. hyper_ch?

---

### Post by gefalu2008 on 2009-08-05
Thanks very much, everybody, for considering my problem.

My laptop is an ancient IBM X20 2262 11G with no cdrom, LAN or other thrills. However, it is light to carry and pleasure to use.

Especially now that I have succeeded in replacing its original Windows 98 with the brand new Ubuntu 9.04!

Until yesterday I used Ubuntu installed with the Wubi installer program in conjunction with Windows 98. But yesterday I managed to do what I intended to do orinally: I installed Ubuntu 9.04 on a hard disk and then inserted the HD into the laptop.

And it worked! This is what I did:

[LIST]
[*]I acquired an Inline USB adapter box for laptop IDE disks and placed my new HD into it
[*]I connected the device to a desktop computer
[*]I booted the desktop with a Live Ubuntu 9.04 USB stick (Ubuntu cdrom should be OK too)
[*]Running Live Ubuntu I selected the option to install and then carefully selected the USB drive as the target drive
[*]I did not succeed in selecting manual formatting options so I decided to allow the installer program to format the whole USB disk into the format Ubuntu prefers
[*]I placed the fully formatted HD into my laptop and it works beautifully!
[/LIST]

I am amazed at the speed and reliability of my reovated laptop having just a tiny internal memory. (Have [look]("http://www-307.ibm.com/pc/support/site.wss/MIGR-4L3J5T.html").)

So thanks again, everybody. Also IBM/Lenovo for producing an excellent device and maintaining their support pages for so long. Also I could not have managed without Edimax Wireless PC card. And people working to develop Ubuntu, Thank You.

- Gef

---

### Post by LewRockwell on 2009-08-05
again, we will repeat...

the installation process detects the hardware it is being installed with

when the hard drive is "transplanted" it may or may not work

OP has found that in this specific application the transplanted operating system appears to be functioning to full capacity

notice we state **"appears to be functioning to full capacity"**

as always, your mileage may vary...buyer be aware...and beware...

we now return you to your regularily scheduled programming...

.

---

### Post by ugm6hr on 2009-08-05
> **LewRockwell said:**
> when the hard drive is "transplanted" it may or may not work

Of course, it is possible to get Ubuntu to redetect graphics card and driver manually, which is generally the major obstacle, given that networking drivers etc are detected and loaded at boot.

```
sudo dpkg-reconfigure xserver-xorg
```

---

