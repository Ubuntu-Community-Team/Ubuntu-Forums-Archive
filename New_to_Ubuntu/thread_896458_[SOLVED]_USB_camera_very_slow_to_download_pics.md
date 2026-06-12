---
title: "[SOLVED] USB camera very slow to download pics"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2008-08-21
I hooked up my Kodak camera and it takes ages to download the pics from it. On my Dell laptop it is quick. both using 2.6.24-19 kernal

I installed usbview and when I run it it gives the following

[COLOR="Blue"]Cannot open the file /proc/bus/usb/devices

Verify that u have USB compiled into your kernel, have the USB core modules loaded, and have the usbdevfs file system mounted[/COLOR]

My Brother USB colour printer prints fine, nice and quick...

So what could be the problem

---

### Post by unutbu on 2008-08-21
Sorry, I don't know the answer to your problem. However, I do know that usbview is broken. It reads /pro/bus/usb/devices. But:

[https://bugs.launchpad.net/ubuntu/+source/usbview/+bug/156085](https://bugs.launchpad.net/ubuntu/+source/usbview/+bug/156085)
> Scott James Remnant wrote on 2007-10-29: (permalink)

    Support for /proc/bus/usb has been dropped because it is racey, and permissions are
    difficult to set -- compared with /dev/bus/usb which is maintained by udev and doesn't
    have these issues.

    Ubuntu is not the only distribution to have dropped it.

    If your software is using /proc/bus/usb, it is broken -- you've had over a year to
    change it, and you've failed to do so. Please change your software to use /dev/bus/usb
    now.


---

### Post by unutbu on 2008-08-21
Does the problem remain if you unplug the Brother printer and plug the camera into the USB port the printer was using?

---

### Post by forger on 2008-08-21
Do both computers have usb2.0 support? Is your camera usb2.0?
Do you use any kind of special software on your laptop?

---

### Post by Ducatiboy Stu on 2008-08-21
USB view works fine on my laptop..


Shall try the printer port..

---

### Post by merlin051 on 2008-08-21
I also use a dell laptop and was having problems with transfer speeds on usb. Once I implemented the fix in the thread below and it helped me out a great deal.


[http://ubuntuforums.org/showpost.php?p=5447719&postcount=10](http://ubuntuforums.org/showpost.php?p=5447719&postcount=10)

---

### Post by Ducatiboy Stu on 2008-08-21
> **forger said:**
> Do both computers have usb2.0 support? Is your camera usb2.0?
Do you use any kind of special software on your laptop?

Nothing special on the Laptop...I pretty much run both with the same Ubuntu setup.

PC and Camera are USB 2.0

Was sort of wondering why USBview worked on the lappy, but not the PC, cause it shows every USB device connected on the lappy..but i can accept that it may be broken.

---

### Post by philinux on 2008-08-21
I would think using

lsusb

from the terminal would give similar info as usbview.

I raised this bug about usb cameras.
[https://bugs.launchpad.net/ubuntu/+bug/242644](https://bugs.launchpad.net/ubuntu/+bug/242644)

If they mounted correctly then you could use cp to copy the pics. This is lightning fast. 

I've now bought a cheap card reader which mounts correctly and does the job miles faster then having the card in the cam.

---

### Post by Ducatiboy Stu on 2008-08-23
well I did this and it works much better downloading

```

To re-enable it edit the file '/etc/init.d/mountdevsubfs.sh' and uncomment the code after line 40 so it reads:

 # Magic to make /proc/bus/usb work
 #
 mkdir -p /dev/bus/usb/.usbfs
 domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
 ln -s .usbfs/devices /dev/bus/usb/devices
 mount --rbind /dev/bus/usb /proc/bus/usb

Execute the script manually to enable the change before a system reboot:

$ sudo /etc/init.d/mountdevsubfs.sh start
```

---

### Post by unutbu on 2008-08-23
Thanks very much for posting the solution, Ducatiboy Stu. What is "domount"?

---

### Post by Ducatiboy Stu on 2008-08-24
> **unutbu said:**
> Thanks very much for posting the solution, Ducatiboy Stu. What is "domount"?


I dont know what "domount"

But the above changes where what I needed to help make USB in VirtualBox and VMware...


But I found wine...more stressfull, but better in the long run...

---

