---
title: "Ubuntu Live Usb Creator"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by inoxllor on 2008-05-20
Recently Fedora 9 brought the Live Usb Creator which allow us to easy create usb febora live pens.

Is there any easy way to do the same in Ubuntu?

---

### Post by avtolle on 2008-05-20
> **inoxllor said:**
> Recently Fedora 9 brought the Live Usb Creator which allow us to easy create usb febora live pens.

Is there any easy way to do the same in Ubuntu?
[https://wiki.ubuntu.com/LiveUsbPendr...t=LiveUsbStick]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent?action=show&redirect=LiveUsbStick") isn't terribly complex or difficult.

---

### Post by zorkerz on 2008-10-20
There is also a new gui tool in intrepid beta at the moment. In system->administration->Create a USB startup disk
As intrepid is still beta for another 10 days I would not recommend giving it a shot unless you an extra machine and are not worried about running in to show stopping problems. Though those are pretty rare this late in the development stage of intrepid.

Also I have not successfully created a usb startup disk yet. The app appears to work fine but when I boot from the usb I end up at and (intramfs) prompt.

---

### Post by Hexagoon on 2008-10-20
UNetbootin (search@google) is another easy way to create usb pendrives with various distributions or OSs on. Worth a try, it also have an option where you just choose the dist you want, and it will download and install it on the usb drive in a jiffy.

---

### Post by Duck2006 on 2008-10-20
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by mgmiller on 2008-10-20
I have found an amazing utility that creates these drives for many popular distros and tools.  It will actually download and install the iso to the thumb drive for you or you can point it at an iso you have.  It works great.  It's called unetbootin.  It has 2 dependencies that need to be installed before you try to run it.

Get it here:  [http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-linux-293&use_mirror=superb-east](http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-linux-293&use_mirror=superb-east)
After downloading the unetbootin, make it executable by right clicking it and selecting Properties and then permissions and checking off the Execute box.

You also need to install it's dependancies:
```
sudo apt-get install mtools p7zip-full
```That's it.  

The thumb drive you are going to use must be formatted in fat32, so use gparted to do that.

When you run unetbootin, it will ask for your password.

I really enjoy using this utility.  Running an Ubuntu live disk off it is way faster then from CD.

As an alternative:
There are also some .deb installers that may take care of the dependencies for you, but I didn't try them. They have a 32 bit and a 64 bit .deb. Get them here:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by C.S.Cameron on 2008-10-20
Unetbootin is quick and simple but not persistent.
Usb-creator is quick, simple and persistent but not quite ready.
Liveusb is slow, simple and can be made persistent following instructions on Pendrivelinux for fixing casper.

---

### Post by inoxllor on 2008-10-20
I shall way for 8.10 then. Thks for the reply. :D

---

### Post by bodhi.zazen on 2008-11-21
More a FYI of others that stumble on this thread :

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_usb_creator&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_usb_creator&num=1)

---

