---
title: "burning to a cd rom"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by saveri on 2013-11-04
im using windows vista right now on a panasonic cf-74. i downloaded the Iso file but im having trouble burning it to a disc.
i tried burning it to a 700mb cd-rom but apparently the iso i downloaded was 707mb and it wont fit, i managed to get ahold of a 4.7gb dvd-rom but i cant write to it, HELP!

---

### Post by Impavidus on 2013-11-05
Indeed it's too big for a cd. A dvd-rom cannot be written to. You need one of the other versions (dvd+r, dvd+rw, etc.). Alternatively, try installing from usb: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick). Most computers can boot from usb.

---

### Post by saveri on 2013-11-05
thanks for the help but i dont have a usb and im too poor to buy one. i think the disk i got was a dvd-rw, im not sure though i gotta check.

---

### Post by rohaniswariah on 2013-11-05
I had same problem and burned to 800 mb cd-rom e-bay also philips DVD+RW worked for cd boot and install

---

### Post by saveri on 2013-11-05
well im broke and i only have a 700mb cd-r and a 4.7 gb dvd-r but the 4.7 gig isnt letting me burn to it.

---

### Post by newb85 on 2013-11-05
It is possible to burn the Ubuntu minimal (which you can download here [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)) to a CD.  After you install Ubuntu minimal, you can get to a full-fledged Ubuntu with 
```
sudo apt-get install ubuntu-desktop
```

The snag: instead of the installation wizard, the minimal CD has a command-line installer, which can be more difficult, especially for first time users.  The risk is compounded if you're trying to install alongside another OS.

---

### Post by alphacrucis2 on 2013-11-05
Maybe your drive doesn't have capability of writing DVD's only CD's perhaps. USB thumb drives are very cheap - only a few dollars for an 8GB one. Can you borrow one? You can use the free unetbootin program to use the iso to create a bootable USB.

---

### Post by nativehound on 2013-11-05
+1 for Ubuntu Mini.
It has a very easy to use setup installer and on the Software Selection menu you can pick LAMP,KUBUNTU,UBUNTU,XUBUNTU and alot more.

---

### Post by saveri on 2013-11-05
doesnt the usb have to be empty of everything but the iso if you want to boot from it? if it is then pretty much no one i know will lend me one. right now i have about 4 bucks and if im gonna get a new usb im going for at least 16gb or 32gb corsair survivor.

---

### Post by mastablasta on 2013-11-06
no, it doesn't have to be emtpy. you just **don't **format it when creating live USB. Linuxlive usb will do this and then give the "uninstall.exe" option which will remove all folders etc from the USB once you have the os installed.

yumi for exmapel does a multiboot and it puts it all in separate folder so you can add more data to usb. 
i have a couple of USB sticks like that. (liveOS+data).

then there is always mini iso. here is how install with that looks like: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by saveri on 2013-11-06
managed to scrape together enough for an 8gig kingston. some one recommended i try a program called unetbootin to install to the kingston and it works! HUZZAH!

---

