---
title: "Windows or Linux? (on 512ram, 3.2GHz)"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by randomtty on 2012-01-03
My old computer (with the above specs) is running fine on Windows XP, but it lags terribly after booting up, and when AVG runs in the background. I'm thinking of switching over to Linux if the performance is good. However, on the webpage, it says that Ubuntu requires at least 1Gb of ram to operate so it's recommended to try out Xubuntu as an alternative. But, I really like the visuals from Ubuntu. So, should I stick with XP, or switch to Ubuntu (provided that it's not lagging) ?

---

### Post by chipbuster on 2012-01-03
If you really want to try out Ubuntu. you can burn a LiveCD and boot into it. The read rate (time to boot up, access programs, etc) will be horrendous, but you can play around with some of the features and get a feel for how it performs. If you like it more than XP, then go for it.

---

### Post by sadaruwan12 on 2012-01-03
For your PC it's better to use lubuntu or bodhi which users very light weight desktop managers and will treat your hardware very nicely.

---

### Post by mastablasta on 2012-01-03
if you have a dedicated graphics card with good support you might be able to run it well. even if not, you can use Unity2D to reduce the system resources that are used.
 
Xubuntu is really a better alternative. it should use about 100-120 MB on idle.
 
Also AVG is a known resource hog. use Avira antivirus or Avast instead. they are both free of charge for home use and should be more friendly to your computer resoruces.
 
Lubuntu or Bodhi are not needed for 512mb RAM, however they will use even less resources for the OS, so you might give them a try and make the computer even faster.
 
 
as it was mentioned you can use liveCD or even LiveUSB key. USB has the advantage that it's read speeds are faster than from the CD. In a live session the whole OS loads into ram so when you turn it off all changes are lost. It also won't touch your winXP install.

---

### Post by sanderd17 on 2012-01-03
Ubuntu will run on 512MB RAM, but it will be lagging and you will do a lot of swapping (writing temporal data to the HDD and fetching it back).

Xubuntu (with the XFCE desktop environment) should run smoothly when you have more than 400MB, and Lubuntu (with the LXDE DE) runs smoothly if you have more than 200MB.

So the choice is up to you.

Btw, there is a new light DE coming: Razor-QT. Although it is already usable, it's still in development, and there isn't yet a distro made with that as default.

---

### Post by techvish81 on 2012-01-03
> **sadaruwan12 said:**
> For your PC it's better to use lubuntu or bodhi which users very light weight desktop managers and will treat your hardware very nicely.

+1 for this comment especially lubuntu is snappy and would be a better alternative to windows..

---

### Post by randomtty on 2012-01-03
I'm trying to look for one with a nice interface and wouldn't lag on my PC. I like Ubuntu best though but I might try out Xubuntu or Lubuntu. What about Kubuntu? Does it require the same system specs as Ubuntu? And should I give up XP?

---

### Post by whatthefunk on 2012-01-03
> **randomtty said:**
> I'm trying to look for one with a nice interface and wouldn't lag on my PC. I like Ubuntu best though but I might try out Xubuntu or Lubuntu. What about Kubuntu? Does it require the same system specs as Ubuntu? And should I give up XP?

Kubuntu isnt very light...Id go for either Lubuntu or Xubuntu.  

Personally, I would give up XP, but thats just me.  If this is your first time with Linux, remember that many Windows applications wont run on a Linux computer.  There are ways to get them to run, but performance isnt guaranteed.  So, if there are some Windows programs that you cant live without, you should probably keep your XP.  How big is your hard drive?  You could dual boot, that is have both XP and a Linux install on your machine.  A lot of people do that.  Whatever you do, I would do a full system backup and make sure that you have Windows XP discs laying around for if you want to go back. You should also try running a Linux Live CD before you install so you can check it out.

---

### Post by DS McGuire on 2012-01-03
I suggest using Lubuntu for a super light operating system. Just try out some distros on Live CDs and see what you think.
As long as you keep you windows partition you can always go back to it if you don't like it or find it too slow.

---

### Post by randomtty on 2012-01-03
> **whatthefunk said:**
> Kubuntu isnt very light...Id go for either Lubuntu or Xubuntu.  

Personally, I would give up XP, but thats just me.  If this is your first time with Linux, remember that many Windows applications wont run on a Linux computer.  There are ways to get them to run, but performance isnt guaranteed.  So, if there are some Windows programs that you cant live without, you should probably keep your XP.  How big is your hard drive?  You could dual boot, that is have both XP and a Linux install on your machine.  A lot of people do that.  Whatever you do, I would do a full system backup and make sure that you have Windows XP discs laying around for if you want to go back. You should also try running a Linux Live CD before you install so you can check it out.

Hard drive's around 140Gb, but only 40 is free. I saw on other threads that Bunt runs fine on 512mb RAM though, so should I try that out first? I'm not worried about Windows programs not being able to run on it, cause I've got 3 other computers.

---

### Post by mastablasta on 2012-01-03
> **randomtty said:**
> I'm trying to look for one with a nice interface and wouldn't lag on my PC. I like Ubuntu best though but I might try out Xubuntu or Lubuntu. What about Kubuntu? Does it require the same system specs as Ubuntu?
Nowadays about the same. To have it run smoothly you need about 1GB ram. There is an option in latest version to reduce system resoruces usage. it's called "kde low-fat package".  Iam not sure hwo low it reduces them. 
 
However Xubuntu and Lubuntu are sitll a better option.
 
> 
 And should I give up XP?
 
Depends on your needs. If you have big enough hard disk (at leats 20-25GB free space) you can install linux next to it. just in case there is a program you need but has no linux alternative and you can't run it via WINE. I guess Virtual box is out of the qestuion here isnce you have low ram.
 
If this is a desktop you could just add more ram. 1GB stick should do. I am using winXP on the main mashcine and will continue to use it until it is supported. I will probably upgrade it to Windows 8 when it comes out.

---

### Post by whatthefunk on 2012-01-03
> **randomtty said:**
> Hard drive's around 140Gb, but only 40 is free. I saw on other threads that Bunt runs fine on 512mb RAM though, so should I try that out first? I'm not worried about Windows programs not being able to run on it, cause I've got 3 other computers.

Ubuntu will really struggle on that machine.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

> Ubuntu Desktop Edition
1 GHz CPU (x86 processor (Pentium 4 or better)) 
1 GiB RAM (system memory) 
15 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach) 
800 by 600 screen resolution 
Either a CD/DVD drive or a USB port for the installer media

The lack of RAM will slow it down more than youd want.  RAM is pretty cheap these days...might want to find out if you can add more to your motherboard.

Honestly, if you have 3 other computers running windows, Id ditch the XP and experiment with some Linux distros.  Just move all your files to one of the other machines first.  Your decision though...

---

### Post by sadaruwan12 on 2012-01-03
I think you like lots of effects then best one will be bodhi which uses a E17 desktop environment which is very nice and also when you learn about the DE you can customize it to suite your taste.

---

### Post by crazy bird on 2012-01-03
> **randomtty said:**
> My old computer (with the above specs) is running fine on Windows XP, but it lags terribly after booting up, and when AVG runs in the background. I'm thinking of switching over to Linux if the performance is good. However, on the webpage, it says that Ubuntu requires at least 1Gb of ram to operate so it's recommended to try out Xubuntu as an alternative. But, I really like the visuals from Ubuntu. So, should I stick with XP, or switch to Ubuntu (provided that it's not lagging) ?
 
I've tried using Windows XP on an P4 system with 512mb RAM. Besides the fact that XP uses a lot of system resources you must not forget that other program's installed under XP also uses system resources. The lesser RAM, the more programs' using system resources, the slower it get's (more lag). 
 
If you must choose: pick a low resource operating system like Xubuntu or Lubuntu and if it is possible for you, add more RAM. You will notice the difference between 512 mb RAM and 1 gig RAM. 
 
This is what the webiste of Xubuntu provides about minimum RAM:
> *You need 256 MB RAM to run the Live CD or 256 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.*

Keep in mind, this is just the minimum amount of RAM required just to let Xubuntu run. If you want it to have it run smoothly, then you need at least 512 mb RAM. But like i already said, better is to get minimum 1 gig RAM in your system. This will improve the speed of your system a lot.
 
And also, Linux is much more stable and safer than Windows. It's virus-proof, no malware/spyware, no problems with left-over's after removing a program, no dll files which interferes, no unexplainable crashes, it's open source so 99,9% of all programs is free, you have an active comunity here, lot of support, better rights management system so that unauthorized persons can not change or install anything. Linux has many more advantages than Windows. This doesn't mean that Windows is a good operating system, it would be much better when Microsoft took a better look at Linux and learn from Linux on safety and stability.
 
But then again, it's yur system, your choice ;)

---

### Post by 3rdalbum on 2012-01-03
My system, with Chromium (web browser) running, uses just under 300 MiB of RAM.

Regular Ubuntu will be able to run on 512MiB of RAM. You can try that first.

I imagine it will still be faster than Windows XP+Antivirus. You don't need antivirus on Ubuntu of course, so don't bother running it. (at least, not to protect Ubuntu).

If the speed is a little slow for you, you can easily install XFCE or LDE on top of Ubuntu, to effectively get Xubuntu or Lubuntu without having to reinstall your operating system.

---

