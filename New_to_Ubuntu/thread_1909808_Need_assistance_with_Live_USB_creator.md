---
title: "Need assistance with Live USB creator"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by SteveMHaupt on 2012-01-16
I have finally done away with windows and went Ubuntu all the way, but I was interested in seeing what other flavors of Linux GUI were like. I wanted to use the fedora live usb creator. I have downloaded the tar.gz file and extracted it but have no idea what to do next. I thought somebody would be able to help me out.
file:///home/steve/Downloads/liveusb-creator-3.11.6.tar.bz2
is what I downloaded and when extracted the are several different directories but if it isn't a deb file or I havn't done an apt-get command Im not sure how to set it up or configure it. Please help because this is really bugging me. I'm in no way swaying away from Ubuntu, I've because quit comfortable with it, but I'm just curious as to how another version is layed out and such. thanks.

Steve

---

### Post by Fernhill Linux Project on 2012-01-16
Using a tar.bz or such will require extracting, configuring & compiling prior to installing. Have a look at this article for an example [https://answers.launchpad.net/ubuntu/+question/6001](https://answers.launchpad.net/ubuntu/+question/6001)
If you can find .deb files for the program you want they should install automatically through software centre.
Unetbootin is also a good tool for creating live USB drives, available from software centre.

---

### Post by mastablasta on 2012-01-16
you don't need Fedora usb creator. you can use tools available in Ubuntu software center and then use them with Fedora image.

---

### Post by Anuovis on 2012-01-16
> **mastablasta said:**
> you don't need Fedora usb creator. you can use tools available in Ubuntu software center and then use them with Fedora image.

Yes, *Startup Disk Creator* is installed by default in 11.10 and probably prior Ubuntus as well. You could easily use that.

---

### Post by C.S.Cameron on 2012-01-16
If you wish to give a few different flavours of Linux a try check out MultiBootUSB.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by imagecko on 2012-01-16
UNetbootin  [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by N2G(bn#7+ on 2012-06-03
Hi, there is a comprehensive solution detailed here:
[http://ifireball.wordpress.com/2011/10/14/running-fedoras-liveusb-creator-on-ubuntu/](http://ifireball.wordpress.com/2011/10/14/running-fedoras-liveusb-creator-on-ubuntu/)

Essentially, you need to install some other software first (dependencies); download the latest version of liveusb-creator; extract it and from the terminal run:
```
sudo /path/to/liveusb-creator
```
Eg. ```
sudo /home/john/Downloads/liveusb-creator-3.11.6/liveusb-creator
```

To the other folks who replied: nice to chip in, but not very helpful. Fedora recommends against UNetBootin; the "Startup Disk Creator" that comes with Ubuntu by default is set up to only install Ubuntu iso's to USB and in this case a configure make install is not possible.

---

