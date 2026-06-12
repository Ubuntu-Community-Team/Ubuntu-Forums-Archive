---
title: "linux installer"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by constantgamer247 on 2008-05-14
hi, i have an ibm think pad that exceeds the system requirements for ubuntu 8.08
but it doesn't have a CD drive, i tried the Wubi installer but it said it would take 100 hours :(
any other way? it is running windows XP (yucky)

---

### Post by TeoBigusGeekus on 2008-05-14
From usb?
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by HotShotDJ on 2008-05-14
Can your laptop boot from a USB drive?  If so, consider purchasing an external USB cdr/rw unit.  They are not terribly expensive.  [HERE]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=420&name=External-CD-DVD-Drives") are some from NewEgg.com

---

### Post by penguinbreath on 2008-05-14
Do you have USB on your laptop? If so perhaps this will be helpful?
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Edit: TeoBigusGeekus beat me to it.

---

### Post by constantgamer247 on 2008-05-14
is there any thing i can check in system bios? like if it can boot from USB and if it has USB 2.0 (i know for sure its got USB but idk if its 2.0, maybe 1.0 but more then likely 2.0)
just tell me how to get there and what to do
thx

---

### Post by billgoldberg on 2008-05-14
> **constantgamer247 said:**
> is there any thing i can check in system bios? like if it can boot from USB and if it has USB 2.0 (i know for sure its got USB but idk if its 2.0, maybe 1.0 but more then likely 2.0)
just tell me how to get there and what to do
thx

you should change the boot order, and set usb first, then the hdd.

I can't help you since every bios is different (well, per computer/make)

---

### Post by constantgamer247 on 2008-05-14
okay, i found out if i hold F12 on start up it takes me to a boot menu
the options are (and yes the first two have + signs)

1+removable devices
2+Hard Drive
3 Cd-Rom Drive
4 Network boot
5 Intel (R) Boot agent Version 4.0.17

 <Enter Setup>

Now right now all I have is a 500 GB USB external Hard Drive.  There is over 250GB of all my saved stuff on it.  Does any one know who I can use that and this boot menu to boot ubuntu 8.08 and then install it on to the thinkpads hard drive, thank you

---

### Post by az on 2008-05-14
> **constantgamer247 said:**
> okay, i found out if i hold F12 on start up it takes me to a boot menu
the options are (and yes the first two have + signs)

1+removable devices
2+Hard Drive
3 Cd-Rom Drive
4 Network boot
5 Intel (R) Boot agent Version 4.0.17

 <Enter Setup>

Now right now all I have is a 500 GB USB external Hard Drive.  There is over 250GB of all my saved stuff on it.  Does any one know who I can use that and this boot menu to boot ubuntu 8.08 and then install it on to the thinkpads hard drive, thank you

Your boot menu is set to boot from removable drive such as your usb drive.

You can follow the instruction here:
[http://ubuntu-rescue-remix.org/node/21](http://ubuntu-rescue-remix.org/node/21)

In windows, you can open up the iso image using an archive manager.  Copy the files onto your usb drive.  Download and install syslinux on windows and make your usb drive bootable.

You may need to install an mbr onto your usb drive, but the windows version of syslinux can do that for you, too.

---

