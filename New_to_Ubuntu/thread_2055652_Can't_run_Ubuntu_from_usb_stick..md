---
title: "Can't run Ubuntu from usb stick."
date: 2012-09-09
forum: New to Ubuntu
---

### Post by Sorapak on 2012-09-09
Tried 2 guides,same result.

guide 1) [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
guide 2) [http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)

from the 3 boot sequences I selected:

[LIST]
[*]USB-FDD ignores usb,enters windows normally
[*]USB-ZIP boot error
[*]USB-CD rom ignores usb,enters windows normally
[/LIST]
Used Windows XP SP3 for the creation of the USB boot stick.

Main reason I'm doin this it's because a friend told me that linux may be able to start reading my failed hard drive,and I might save some of my files. (used to semi-work in windows untill few days ago,but now it rarely gets working even semi properly for me to view my files. But I know that's a different issue :P)

Any help is appreciated :)

---

### Post by Bashing-om on 2012-09-09
Sorapak; Hi ! welcome to the forum.

Firstly, in bios have you set the boot priority to boot from usb first ?
 a. Bad usb device ?
 b. Bad connectivity ?
 c. Errors on the medium ?

secondly, if above is good, do you have a cd device capable of reading/writing ? So that you can make up a boot cd disk for ubuntu ?

[INDENT]kindest regards <==BDQ

[/INDENT]

---

### Post by jerrrys on 2012-09-09
Another possibility

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by NikTh on 2012-09-09
> **Sorapak said:**
> Used Windows XP SP3 for the creation of the USB boot stick.

Hi , 
did you use unetbootin ? [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Download the Ubuntu iso from here : [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)
"cook" them together and make a bootable usb stick.

> **Sorapak said:**
> 
from the 3 boot sequences I selected:

[LIST]
[*]USB-FDD ignores usb,enters windows normally
[*]USB-ZIP boot error
[*]USB-CD rom ignores usb,enters windows normally
[/LIST]
See if a "One boot key" exits. Usually is a similar to F12 or F2. It allows you to select the boot-device without needed to go in Bios configuration page.



> **Sorapak said:**
> Main reason I'm doin this it's because a friend told me that linux may be able to start reading my failed hard drive,and I might save some of my files. (used to semi-work in windows untill few days ago,but now it rarely gets working even semi properly for me to view my files. But I know that's a different issue :P)

Yes , you can test your disk with smartmontools or already installed disk-utility.  You can do it even from live-Usb , without needed to install Ubuntu. 

Thanks

---

### Post by DeezyFaReal on 2012-09-09
This method of installing Ubuntu on at least a 4 GB flash drive always works for me.
1. Download Ubuntu 10.04.4 (it's small enough to fit on 4 GB)
2. Burn it to a CD
3. Boot from the CD with the flash drive plugged in
4. When the installer asks you where to install Ubuntu, select "Erase disk and install Ubuntu" but then change the drive in question from your hard drive (sda) to the Flash drive (sdc1)
5. Watch it install Ubuntu on the usb stick. 
The difference between having as a live CD and a live Usb is: with the Usb you can save your work.
Hope this helps! If the flash drive won't boot, I don't know what to tell you.

---

### Post by anewguy on 2012-09-10
> **DeezyFaReal said:**
> This method of installing Ubuntu on at least a 4 GB flash drive always works for me.
1. Download Ubuntu 10.04.4 (it's small enough to fit on 4 GB)
2. Burn it to a CD
3. Boot from the CD with the flash drive plugged in
4. When the installer asks you where to install Ubuntu, select "Erase disk and install Ubuntu" but then change the drive in question from your hard drive (sda) to the Flash drive (sdc1)
5. Watch it install Ubuntu on the usb stick. 
The difference between having as a live CD and a live Usb is: with the Usb you can save your work.
Hope this helps! If the flash drive won't boot, I don't know what to tell you.

I thought you were allowed to save a on USB flash device if you just created persistence using unetbootin.

---

### Post by DeezyFaReal on 2012-09-10
You're right you will have persistence with a live usb made with UNetBootin. 

I just prefer the method I suggested, because I have a personal bias against UNetBootin == installing Debian 6.04 on a 4 gig usb didn't work for me (my noob mistake).

---

### Post by Cheesemill on 2012-09-10
It looks like your motherboard doesn't support booting from a USB flash drive.

If it did then as well as the USB-FDD, USB-ZIP and USB-CD options you would also have one called USB-HD.

If you know the make and model of your motherboard you can look this information up.
If this turns out to be the case then you will have to boot from a CD instead.

---

### Post by Sorapak on 2012-09-10
> **jerrrys said:**
> Another possibility

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Thanks for the replies guys! I used jerrys tool and it's workign fine untill now so I guess I won't use ubuntu after all.

Sorry for wasting your time,have a great day!

---

