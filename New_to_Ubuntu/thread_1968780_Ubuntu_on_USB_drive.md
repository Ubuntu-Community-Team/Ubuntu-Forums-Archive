---
title: "Ubuntu on USB drive"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by RufusSwan on 2012-04-29
I used the pendrive downloader and got the .ISO file downloaded  then finished the directions to get Ubuntu 11.10 my 16gb Sandisk USB drive.  All OK so I rebooted my ASUS eeePC 1015PE from the USB drive and up comes Ubuntu.

Fabulous, everything works ok, and I will look forward to a more permanent install.  I did download some web cam software and it tested well.  So I then did a shutdown.   When I rebooted this morning the new webcam software is gone, as is the short test video I created.  That's weird!  So I downloaded a different program, created some files which I can see in the file system, but after a shutdown and reboot ,software and new fileswere gone!!!

Doesn't seem normal to me.  Did I get a wanky 'install'?  I did not format the USB since it did have a MBR (master boot record).  

Also I see an "Install Ubuntu" program on the home page of Ubuntu.  What is it's purpose?

---

### Post by cheatos on 2012-04-29
Hi,

you probably tried the liveUSB but without enabling persistent mode.
In this case you can use the OS just as you did, but all changes to the system get discarded on shutdown.
If you want to keep your files make sure to activate the persistent mode when making the startup stick.
There you can also choose what size that files system should have.

---

### Post by jockyburns on 2012-04-29
The "Install Ubuntu" option (on the USB) does just that. It will install Ubuntu to your computer. I don't think there's an install tab on the Ubuntu website though. You'd still have to download it , or purchase the Live CD.

---

### Post by souravc83 on 2012-04-29
Alternatively, you can try and install it in the 16GB USB.
But then you need to format the USB.

---

### Post by RufusSwan on 2012-04-29
Yep, I did ignore the persistent settings when installing.  I'l reinstall and all should be well.

Thanks to you all:)

---

### Post by rgreener25 on 2012-04-29
you could also try burning it too a cd and installing it directly on to the usb for a permanent install however you will have to format the usb

---

### Post by tmaranets on 2012-04-29
You can set it to persistent mode so you don't lose your stuff after a shutdown and a reboot.

---

### Post by oldfred on 2012-04-29
With 16GB flash drive you can do a full install. I have a full install of Ubuntu 12.04 on my 16GB flash drive in a 8GB partition to test with my laptop. It is then just like any install to another drive.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Installs to 4GB flash, newer versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

