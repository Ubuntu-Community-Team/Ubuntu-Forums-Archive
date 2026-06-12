---
title: "[SOLVED]USB to serial port doesnt work in Virtualbox"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by ubume2 on 2012-09-21
Ubuntu 12.04 is host. Windows XP guest. Installed latest deb package and extension pack from Oracle Website.

I finally got the serial port working. I cannot get usb to serial port cable to work. lsusb shows the device as recognized, and I have modprobed the device. I have set up usermod so I am a member of vboxusers.

USB flash drives work properly in XP guest.

I am trying to get a Windows Program (MixW) to work in the XP guest in Virtualbox.  I've tried it in Wine.  Since WINE does not recognize usb devices, I thought I would try vbox.

Under system in vbox the usb device is recognized and I have checked the appropriate boxes. Still no luck.

Just to check it out I installed FLDIGI in Windows guest and the usb to serial does not work in it either. FLDIGI (linux version) does work on the Ubuntu host. 
 
How do I get this device to work in Virtualbox?

Any ideas or suggestions would be welcome! Thanks

---

### Post by lkraemer on 2012-09-22
You haven't mentioned that you executed VirtualBox and then click on USB and enabled a couple of Filters.  Do you have a couple of Filters available
for your USB Devices?

Also, when your GUEST OS is running, hover your Mouse over the USB Icon in the Lower portion of the Window and see if your USB Device shows up when it is Inserted.  You may have to click on this Icon and Enable the device by checking it.  Same for REMOVAL of the USB Device.

Be sure to Install Guest Additions too!

LK

---

### Post by ubume2 on 2012-09-22
@LK

Edit: Virtualbox guest additions installed within XP guest, but I still didnt get USB support.  I tried a different USB to serial (Prolific), and it works. Now I can get my Windows only Program to work within my favorite distro, Ubuntu. Thanks for your help! :)

Edit: 9/26 I installed the generic usb driver within XP guest. I now have both USB devices working.

I wish WINE would be more reliable and would give USB support.

---

