---
title: "Question about Graphics driver"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by pgar23 on 2008-10-12
SO I have been trying to get ubuntu to work with no success because I guess i need the graphics driver or something.. I am having the same prob as this thread 

[http://ubuntuforums.org/showthread.php?t=923817](http://ubuntuforums.org/showthread.php?t=923817)

I was wondering:
1.  if the following link is the correct driver for my chipset(Intel® Graphics Media Accelerator 4500MHD)
[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2991&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2991&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

2. If i download the driver, how would i go about installing it??

Thanks in advance.

---

### Post by phidia on 2008-10-12
Reading through some of that thread it looks like the driver you want is [here]("http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/") and you can just choose to open that download with Gdebi which should install it for you.
Be sure to select the correct driver for your architecture.

---

### Post by pgar23 on 2008-10-12
> **phidia said:**
> Reading through some of that thread it looks like the driver you want is [here]("http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/") and you can just choose to open that download with Gdebi which should install it for you.
Be sure to select the correct driver for your architecture.
Thanks for the reply phidia..how do i install the driver then??
it is a .deb file but i cannot get into ubuntu. I can use the command line from the recovery mode..

---

### Post by phidia on 2008-10-12
> **pgar23 said:**
> Thanks for the reply phidia..how do i install the driver then??
it is a .deb file but i cannot get into ubuntu. I can use the command line from the recovery mode..

I forgot you didn't have a gui desktop environment-sorry.

The command to install that package is > sudo dpkg -i packagename Be sure you are in the directory that contains the deb package and you only need to type part of the package name and press the tab key-there is command completion in the CLI.

To clarify that you type "sudo dpkg -i xserver-" and press the tab key and the commandline (bash) will complete the filename provided you are issuing the command in the correct directory. I believe the downloaded deb package begins with "xserver-xorg-video-intel..." Good luck and report back if it works. There have been several threads on that GPU.

---

### Post by pgar23 on 2008-10-12
ok..thanks phidia..but right now im using windoze..how would i install in ubuntu?? I downloaded package to desktop in windows..i have a usb flash drive if necessary.

---

### Post by phidia on 2008-10-12
Maybe putting it on your usb drive is the easiest way unless you have experience mounting your windows partition or it auto mounts. After you insert the usb drive look in media "cd /media" then "ls" 

If you see your files then just start the install from there.

---

### Post by DoubleMcLovin on 2008-10-12
im no expert by any means, but try the alternate install cd [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download") As per my understanding you should have a chance to do something involving that command posted above.

---

### Post by pgar23 on 2008-10-12
@phidia: did u have to do all this also?? wut a hassle..i have ubuntu on my desktop but just bought this laptop and it is a pain trying to install..lol

---

### Post by phidia on 2008-10-12
Double, Using the live cd to do this would involve a chroot and I think that's too much work for this situation plus the flash drive or partition with the deb package still needs to be mounted.

pgar23, I've done similar things to this over the years. Getting use to working in commandline/CLI is IMO essential or at least recommended for dealing with many of the problems that occur.

BTW most posters here don't think the GMA 4500 is working in linux so if that package works that will be a good deal-I don't have that card so I can't test it.

---

### Post by pgar23 on 2008-10-12
AHHH.well in either case..im going to try it. If it works great if it doesnt I will just wait a few weeks and install intrepid..

---

