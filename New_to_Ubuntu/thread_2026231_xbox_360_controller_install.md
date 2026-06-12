---
title: "xbox 360 controller install"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by Nekrosilisk on 2012-07-14
I just installed Znes  and am looking for a PSX emulator and i would like to use my 360 controller for playing the games.  Where would i go about looking for the drivers to use on ubuntu and then installing them?

---

### Post by vacana on 2012-07-14
for the psx emulator search for pcsx reloaded.

---

### Post by Nekrosilisk on 2012-07-14
thanks any idea where to find the controller drivers?

---

### Post by anewguy on 2012-07-15
A simple net search using

linux xbox 360 controller

in the search string returns many results, among them:

[http://www.ehow.com/how_8725674_make-linux-use-xbox-controller.html]("http://www.ehow.com/how_8725674_make-linux-use-xbox-controller.html")

It references the kernel so I don't know if it still works with the newest kernel.

---

### Post by Kain000 on 2012-07-16
there is a default xbox controler driver in the kernal already called xpad, however I find a driver called xboxdrv to be much more accurate

google it, you have to install it, then tell the kernal not to use the default one, and then run it in a terminal, where it will output all the current status of your controler

```
sudo apt-get install xboxdrv
```
```
sudo rm xpad
```
I think, but double check that one... either way if you try to run xboxdrv before disabling the default xpad it will instruct you on the proper command
```
sudo xboxdrv
```

---

### Post by Nekrosilisk on 2012-07-16
thanks for the recs.  I've got the drivers installed now and am just waiting to get back to my wireless receiver before i mark this solved.

---

### Post by hugoBOSS81 on 2012-12-12
very useful info indeed since I'm setting mine up now too. yet, I'm just curious...wouldn't it be better to blacklist the default driver instead of removing it?? I've noticed that kind of action usually leads to future problems when you literally remove drivers specially if you don't have/make a backup of the original working drivers that come with Ubuntu. I just set up a desktop with 12.04  and upgraded the stock kernel to 3.4-generic and it's worked out great so far but I did find info on this forum and ppl mentioned that certain drivers were no longer included or used in this kernel for numerous reasons so i actually had to go hunt for them online, compile and troubleshoot custom drivers or try recompiling windows version of drivers into linux compatible ones.I personally had to do that with some wireless usb drivers for my machine to work with a Netopia usb wifi adapter since the manufacturer didn't provide support for linux. It worked after some serious terminal use to figure out how to compile stuff. Later I made a custom DVD with all the needed drivers using Remastersys so I never have to go through all that setup hassle on the machine again should I need to re-install in the future or upgrade to newer Ubuntu's.

---

