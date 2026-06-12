---
title: "Virtualbox and usb"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Roen hayden on 2008-05-04
Virtualbox and usb


i have a virtual machine running windows xp and i can not get windows to mount or should i say recognize? the usb drive.  But also keep in mind that i plan on connecting my windows moble 6 device to the OS any ideas that can shed some light on this?

thanks

---

### Post by robalcorn on 2008-05-04
Did you install virtualbox ose? Becuase it doesnt support usb you need to get the personal use and evaluation version to have support.

---

### Post by bodhi.zazen on 2008-05-04
Esing any editor, gksu gedit /etc/fstab , add this line to /etc/fstab

```
# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

The reboot.

If you are using the open source edition is is quite easy to set up network file sharing, such as samba or nfs.

---

### Post by Roen hayden on 2008-05-04
> **bodhi.zazen said:**
> Esing any editor, gksu gedit /etc/fstab , add this line to /etc/fstab

```
# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```

The reboot.

If you are using the open source edition is is quite easy to set up network file sharing, such as samba or nfs.

yes i am using the OSE so in that version does the above edit still work? and would this work for all usb devices?

---

### Post by bodhi.zazen on 2008-05-04
> **Roen hayden said:**
> yes i am using the OSE so in that version does the above edit still work? and would this work for all usb devices?

No. USB sharing does not work on the OSE. See the VirtualBox pages for information.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by Roen hayden on 2008-05-09
Well what about this would this work in ubuntu 8.04? but keep in mind that its the VB ose that i have installed..

USB not working with Virtualbox in Ubuntu 7.10 Gutsy Gibbon

> I first installed Virtualbox OSE (Open Source Edition) from Ubuntu repo. I didn't see any option to load USB devices in the settings. The OSE version was 1.5 whereas the current Virtualbox version is 1.5.2. I thought, may be the OSE edition doesn't support USB devices, so I removed the OSE edition and installed Virtualbox from Virtualbox.org. Even that didn't show any option to load USB devices. I then found out from Virtualbox site that Ubuntu 7.10 Gutsy Gibbon removed support for /proc/bus/usb. If you have the same issue, this is what you have to do to fix it (Thanks to Virtualbox for the tip).

Open a terminal and type

sudo gedit /etc/init.d/mountdevsubfs.sh

Go to the lines as shown below:

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs «» /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

Uncomment the last 4 lines and make it look like below:

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs «» /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Close and restart virtualbox. You should see the USB options in the settings. You can add the devices you want. I have edited and added this information to the Virtualbox installation tips I wrote few months back.

If you are wondering what is the difference between Virtualbox and Virtualbox OSE, they are both same except the closed source one carries some enterprise features. Here is the list of features that are there in the closed source version, but absent in open source one:

    * Remote Display Protocol (RDP) Server

    This component implements a complete RDP server on top of the virtual hardware and allows users to connect to a virtual machine remotely using any RDP compatible client.

    * USB support

    VirtualBox implements a virtual USB controller and supports passing through USB 1.1 and USB 2.0 devices to virtual machines.

    * USB over RDP

    This is a combination of the RDP server and USB support allowing users to make USB devices available to virtual machines running remotely.

    * iSCSI initiator

    VirtualBox contains a builtin iSCSI initiator making it possible to use iSCSI targets as virtual disks without the guest requiring support for iSCSI.

What I initially suspected (USB not supported in OSE edition) seems to be true and may not work even after you follow the steps given above.



---

