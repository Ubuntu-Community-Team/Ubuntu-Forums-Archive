---
title: "usb in virtual box"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Kedster on 2008-04-23
OK i would really like to get my usb to work on my virtual box so i can use my ipod and other stuff

---

### Post by talikarng on 2008-04-27
From memory you need to go into the settings tab (on the top) when you have your virtual machine selected. From there go down to the USB options and turn it on.

---

### Post by mlentink on 2008-04-27
Which version of Virtualbox are you running? Afaik the Open Source Edition (OSE, which is the one in the ubuntu repo's) does not support USB. You would need to install the closed source edition for that, which you can find [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI").

---

### Post by frup on 2008-04-27
My brother got it working (with the free version AFAIK) I will quickly call him and get him to post how he did it.

---

### Post by master5o1 on 2008-04-27
> **frup said:**
> My brother got it working (with the free version AFAIK) I will quickly call him and get him to post how he did it.



Using the proprietary version for gutsy because there is no hardy non-free yet (because the usb compatibility is proprietary), you can follow these commands that I did:

Bare in mind that I believe (from quick over view) there are a few different methods
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)
and
[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)
(I followed the second one).

If you haven't added yourself to the virtualbox group then do this: (i assume you have though)
> Step 2: Setup User groups & USB support
Add yourself as a virtual box user
In a terminal type:
```
sudo adduser username vboxusers
```
You must replace userame with your user name!


USB starts here:
> 
Add USB support to you fstab file
In a terminal type:
```
sudo gedit /etc/fstab
```

And paste this line to the end of your fstab
```
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
```

Enable USB
In a terminal type:
```
sudo gedit /etc/init.d/mountdevsubfs.sh
```

You need to look for this section:
```
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

```
And delete all the # shown, it should look exactly like this.

```
#Magic to make /proc/bus/usb work

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

```

Find your vboxusers number
[QUOTE=master5o1]Mine was 123
In a terminal type:
```
sudo gedit /etc/group
```

Look for this, the number following it is your vboxusers number
vboxusers:x:NUMBER
[QUOTE=master5o1]eg. vboxusers:jason:123[/QUOTE]

Next you have to add a line to your /etc/fstab to allow usb mounting
In a terminal type:
```
sudo gedit /etc/fstab
```

Add this line:
```
none /proc/bus/usb usbfs devgid=virtualbox-users-number-here,devmode=664 0 0
```

[QUOTE=master5o1]eg.
```
none /proc/bus/usb usbfs devgid=123,devmode=664 0 0
```
[/QUOTE]

Allow access to /proc/bus/usb/
in a teminal type:
```
sudo chown -R root:vboxusers /proc/bus/usb
```

Once you Log out or reboot, you can start VirtualBox (Applications>System Tools>Innotek VirtualBox)[/QUOTE]

The reboot/logout is to restart the kernel module for Virtualbox :)

Hope I could be of some help...This worked for me as I now have a USB menu in my virtual machine's settings.

---

### Post by SuperSon!c on 2008-04-27
> **frup said:**
> My brother got it working (with the free version AFAIK) I will quickly call him and get him to post how he did it.

well, both versions are free, but you'll need the closed-source vrsion.  [here is the page]("http://www.virtualbox.org/wiki/Editions") with the differences between the two.

---

