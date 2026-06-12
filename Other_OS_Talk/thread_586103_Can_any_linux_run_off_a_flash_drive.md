---
title: "Can any linux run off a flash drive?"
date: 2007-10-22
forum: Other OS Talk
---

### Post by xsabrewulf on 2007-10-22
I have a 2gb flash drive and I was wondering if there is a linux that will boot and run off a flash drive?

Im not talking about installing linux FROM the drive I mean actually take linux where ever i go

---

### Post by -grubby on 2007-10-22
Damn Small Linux. Feather Linux...tons more

---

### Post by HermanAB on 2007-10-22
Here are a couple:
[http://mandriva.com/en/product/mandriva-flash](http://mandriva.com/en/product/mandriva-flash)
[http://puppylinux.com/](http://puppylinux.com/)

---

### Post by RedPandaFox on 2007-10-22
Id be interested to find out this as well. Iwould be great if I could do this because I dont have any set network becuase all the other PC's I use are on windows and for some reason wont network, so if I could take Linux with me where I went it would make me feel more at home with at work or anywhere

---

### Post by xsabrewulf on 2007-10-22
out of those, what would you recommend is the best one?

---

### Post by LaRoza on 2007-10-22
I have used Knoppix and Slax on a flash drive to great effect, Slax in Particular is great because you can add the modules easily. [www.slax.org](www.slax.org)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by TeaSwigger on 2007-10-22
Oh yeah it's been possible with Linux for a little while now. I wasn't asked ;) but I don't think one can say there's a best for everyone's uses. But Damn Small Linux is well established and Puppy Linux is another to give serious consideration to.

Cynical prediction moment: Microsoft is fortunately behind the curve again on this aspect, but once Linux devs have done the groundwork for Microsoft, it'll be among Microsoft's next "breakthroughs" from which they'll reap untold riches. If you listen closely, you can already hear the fore echoes of the paid off plugs, er "marketing synergy," er stories, on NBC.

---

### Post by xsabrewulf on 2007-10-22
[http://mandriva.com/en/product/mandriva-flash](http://mandriva.com/en/product/mandriva-flash)


looks cool, but you have to pay for it. I dont see where you can download the flash key version... you gotta buy the actual flash drive

---

### Post by starscalling on 2007-10-22
actually any live cd can be run off a usb key - and you can make a livecd custom from some tools out there - been doing research on that myself ;)
so say you dont want allt he extras etc you COULD do a successfull install on hdd and make live out of that - tho there are also ways of adding a few packages etc

---

### Post by Antman on 2007-10-22
Puppylinux..... puppylinux.... did I say Puppylinux?!?

[http://puppylinux.com/](http://puppylinux.com/)

---

### Post by xsabrewulf on 2007-10-22
Yea i was looking at Puppy Linux

[http://puppylinux.com/flash-puppy.htm]("http://puppylinux.com/flash-puppy.htm")


but it says you need to burn the image to a disc (which i dont really wanna do) or you can ISO Bust it... im fine with that but that site said they are too lazy to write out instructions what to do when you exact the iso to install it on the flash.

---

### Post by RAV TUX on 2007-10-22
> **xsabrewulf said:**
> I have a 2gb flash drive and I was wondering if there is a linux that will boot and run off a flash drive?

Im not talking about installing linux FROM the drive I mean actually take linux where ever i goThe best and the easiest is [Wolvix]("http://wolvix.org/").

---

### Post by init1 on 2007-10-22
> **starscalling said:**
> actually any live cd can be run off a usb key - and you can make a livecd custom from some tools out there - been doing research on that myself ;)
so say you dont want allt he extras etc you COULD do a successfull install on hdd and make live out of that - tho there are also ways of adding a few packages etc
Actually, it's quite a bit harder than that. Most live distros will not run off a USB drive. They will not be able to find the device that the drive is at. One can overcome this by editing the linuxrc and adding USB kernel modules to the initrd. 

What I recommend is Live Helper. It allows one to make a Debian based live CD or USB. This tutorial is great. 
[http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/](http://www.pendrivelinux.com/2007/05/31/create-your-own-live-linux-cd-or-usb-distribution/)

Also try MCN Live. 
[http://www.mcnlive.org/](http://www.mcnlive.org/)

If you don't care about having X11, there is Finnix, GRML, and Knopperdisk to try. 
[http://www.finnix.org/](http://www.finnix.org/)
[http://knopperdisk.knopper.tk/](http://knopperdisk.knopper.tk/)
[http://grml.org/](http://grml.org/)

---

### Post by init1 on 2007-10-22
> **xsabrewulf said:**
> Yea i was looking at Puppy Linux

[http://puppylinux.com/flash-puppy.htm]("http://puppylinux.com/flash-puppy.htm")


but it says you need to burn the image to a disc (which i dont really wanna do) or you can ISO Bust it... im fine with that but that site said they are too lazy to write out instructions what to do when you exact the iso to install it on the flash.
Puppy Linux installs to a flash drive with the standard Syslinux method
```

sudo apt-get install syslinux mtools

```
Copy all files on the CD/ISO to the flash drive. 
Move all files from the "boot" and "isolinux" folders to the root of the drive, so that they are not in folders
Rename the isolinux.cfg to syslinux.cfg and edit it so that it knows that the files are not in the "boot" and/or "isolinux" folders
Unmount the flash drive
```

syslinux -sf /dev/yourdrive

```
See here:
[http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)

---

### Post by xsabrewulf on 2007-10-22
> **init1 said:**
> Puppy Linux installs to a flash drive with the standard Syslinux method
```

sudo apt-get install syslinux mtools

```
Copy all files on the CD/ISO to the flash drive. 
Move all files from the "boot" and "isolinux" folders to the root of the drive, so that they are not in folders
Rename the isolinux.cfg to syslinux.cfg and edit it so that it knows that the files are not in the "boot" and/or "isolinux" folders
Unmount the flash drive
```

syslinux -sf /dev/yourdrive

```
See here:
[http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)





I would still need to burn the image to use the live cd correct? inorder to use the sudo commands within puppylinux

---

### Post by FLCLFan on 2007-10-22
Just an FYI for people who dont know. Flash drives can only handle a certain number of write cycles before they die, and doing something that contently writes to it will severally lower the life of it.

---

### Post by xsabrewulf on 2007-10-22
> **FLCLFan said:**
> Just an FYI for people who dont know. Flash drives can only handle a certain number of write cycles before they die, and doing something that contently writes to it will severally lower the life of it.


Really? I thought that didnt matter since a flash drive is solid media


UPDATE: Wow, i just read that on wikipedia you're right... good to know they say a mid ranged flash drive can go about several hundred thousand cycles

---

### Post by SkyNet2029 on 2007-10-23
Debian can run off of a flash drive too.

[http://www.debian-administration.org/articles/179]("http://www.debian-administration.org/articles/179")

---

### Post by new2*buntu on 2007-10-25
I use Puppy Linux on my 1GB flash drive because it is very easy to install to flash drives and it only takes up 100 MB of space (3.x version).
To install Puppy Linux to a flash drive, download and burn the Live CD, boot from it, and then choose the Universal Puppy Installer (or something like that) and follow the steps.

---

### Post by SunnyRabbiera on 2007-10-25
I am personally curious on how mandriva flash will work for me, though I feel mandriva 2008 unstable.

---

### Post by igknighted on 2007-10-25
> **SunnyRabbiera said:**
> I am personally curious on how mandriva flash will work for me, though I feel mandriva 2008 unstable.

"Mandriva Flash" is not some special version.  You are paying for a pretty flash drive that says Mandriva on it and them to do the work to set it up properly.  You could take the Mandriva CD and do the same thing yourself.  They freely admit this... the whole point of buying it is because (a) its easier, and (b) it looks pretty.

---

### Post by j.miller565 on 2007-10-26
Feather Linux is a good distro for USB sticks

---

### Post by AdamWill on 2007-10-26
It's worth noting the current Flash is built off Mandriva Linux 2007, which is now a bit old (about a year), so may have a few issues with hardware compatibility with recent machines. It's worth bearing that in mind when considering it. We're currently working on a 2008-based Flash, and if we are able to make it work sufficiently well, it would replace the 2007-based one at some point in the middle future.

Aside from the official Flash product, there's another Mandriva-related distro which is tailored to run off a Flash drive. That's MCNLive - [http://www.mcnlive.org/](http://www.mcnlive.org/) . It's basically a slightly tweaked Mandriva designed to be installed to a Flash drive (there's also a CD version). As it's specifically designed for this purpose, it's very easy to do and works well. Their latest version at present is based on Mandriva Linux 2007 Spring, the second most recent stable release. I believe they're working on a 2008 version now.

---

### Post by omns on 2007-10-26
I've just ordered an 8gb stick to give Zenwalk a go on.

---

### Post by SenojLuap on 2007-10-30
What about making a custom distro? I've skimmed over topics on trimming down the kernel an whatnot. If I did that, would it be possoble to put, say, Ubuntu on a flash?
Also, once I have a working Linuxflash, is it as simple as booting the computer with the flash in the drive?

---

### Post by Dark-Ace on 2007-11-04
I also am wondering about this question cause right now i wanna get into the use of Linux but only from a flashdrive...i'm nto mega computer savvy and i'm kinda lazy, i know puppy linux can install easily from live CD but its just not for me but do any others have this function to install easily from Live Cd?

---

### Post by jfluhmann on 2007-11-04
If you're feeling adventurous - [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by Dark-Ace on 2007-11-04
Well not really....i'm actually asking for the lazy man way, i actual think that all linux should just be able to install themsleves from the LiveCE no hassle llike puppy, like for ubuntu the icon that says install when you click it i think that i should ask where you wanna download it whether it be harddrive or flashdrive.

---

### Post by init1 on 2007-11-04
> **xsabrewulf said:**
> I would still need to burn the image to use the live cd correct? inorder to use the sudo commands within puppylinux
Nope, you can simply mount the ISO
Substitute /mnt for any mount directory you wish. 
```

mount -o loop thenameofthe.iso /mnt

```

---

### Post by init1 on 2007-11-04
> **Dark-Ace said:**
> I also am wondering about this question cause right now i wanna get into the use of Linux but only from a flashdrive...i'm nto mega computer savvy and i'm kinda lazy, i know puppy linux can install easily from live CD but its just not for me but do any others have this function to install easily from Live Cd?
CPX-Mini has the easiest installer. There's an icon for it on the desktop.
[http://debian.tu-bs.de/project/cpx-mini/](http://debian.tu-bs.de/project/cpx-mini/)

---

### Post by Dark-Ace on 2007-11-04
I've tried all these Linux OS's but none of them can run the LiveCD on my comp like with CPX-mini, what happens is that it goes through everything but once it loads autoconfiguring devices it just stops at the end and nothing happens....the only real working ones on my comp are Puppy and Ubuntu LiveCd so if there is any based on Ubuntu tell me and also people pls give me more to test out.

---

### Post by SenojLuap on 2007-11-05
> **jfluhmann said:**
> If you're feeling adventurous - [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

This is perfect! It does require a bit of techno-confidence, but it answers my question perfectly. Thanks!:)

---

### Post by init1 on 2007-11-05
> **SenojLuap said:**
> This is perfect! It does require a bit of techno-confidence, but it answers my question perfectly. Thanks!:)
I've done it before, and it worked fine on my laptop, but not at all on a different computer I tried it on. Worth a try, anyway.

---

### Post by uwishurockedthishxc on 2007-11-05
i have run puppy linux, slax popcorn linux and damn small linux all off of flash drives

---

### Post by Dark-Ace on 2007-11-23
This is kinda way late but this post can help this thread.......I found a marvelous software known as mocka5....you can install it onto your desktop or a flashdrive...well i didn't find it but my friend showed it to me and it works great...you can download LivePC's from there website but it works like an actual Distro...you can save all your changes and everything...i myself love it and use Ubuntu 7.04 on it and am downloading KDE right now so you should try it if ya want.

---

### Post by geneven on 2007-12-12
Puppy Linux is incredibly easy to install on a flash drive; you only need a CD one time, to do the installation.

It's optimized to minimize excess writing to disk, thus making the amount of wear the flash drive has as low as possible.

I became a superfan when I discovered how easy it was to connect to the internet via my Dell Laptop, which has a BCM43xx wireless card, famous for being problematic.

I haven't yet found another distro so fun and easy to install, though I will keep on trying! One of the big attractions for me is the fact that it's very easy to make sub-distros with particular setups. Puppy has a number of them, and they are fascinating and there is a talented group of other fans who keep coming up with great new features.

---

