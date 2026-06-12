---
title: "Intrepid-Can't get bluetooth mouse &amp; keyboard to reconnect after reboot"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by TalioGladius on 2008-11-10
I searched but couldn't find anything relevant to Intrepid.  Logitech MX1000 mouse and MX5000 keyboard.  Every time I reboot I have to connect a usb keyboard/mouse and delete both from the bluetooth manager preferences and completely reconnect them.

Ideas?

---

### Post by TalioGladius on 2008-11-10
bump

---

### Post by TalioGladius on 2008-11-10
anyone?

---

### Post by waspbr on 2008-11-10
this probably won't help, but i have the same keyboars and mouse and they work fine on my ibex most of the time, every now and then I may need to reconnect them but not often tho(1x or 2x a week)

---

### Post by Bloemetjesgordijn on 2008-11-11
Hi I have the same issue. Somehow 8.10 has issues in reconnecting Bluetooth. 


A bug is made: [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/79394](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/79394)

A possible fix is in the bug report and : [http://ubuntuforums.org/showthread.php?t=958048](http://ubuntuforums.org/showthread.php?t=958048)


I havent tried them both....


Cheerz

Bloemetjesgordijn

---

### Post by Mickey G on 2008-11-11
Yes, I have the same problem with my logitech keyboard. Fresh install of 8.10.  It works after re-seating the USB dongle.  I'm currently using a wired keyboard until I can fix the problem.

I guess the problem is with USB but I don't know.

I will have a go at the bugfix tonight.

---

### Post by philinux on 2008-11-11
[http://ubuntuforums.org/showthread.php?t=966436](http://ubuntuforums.org/showthread.php?t=966436)

Second in the list.

---

### Post by BzuCo on 2008-12-05
I fixed reconnecting the mouse by douwngrading the packages to these versions:

$ dpkg -l | grep -i blue
ii bluetooth 3.19-0ubuntu3 Bluetooth stack utilities
ii bluez-cups 4.12-0ubuntu5 Bluetooth printer driver for CUPS
ii bluez-gnome 1.8-0ubuntu1 Bluetooth utilities for GNOME
ii bluez-utils 3.19-0ubuntu3 Bluetooth tools and daemons
ii libbluetooth2 3.19-0ubuntu1 Library to use the BlueZ Linux Bluetooth sta
ii libbluetooth3 4.12-0ubuntu5 Library to use the BlueZ Linux Bluetooth sta

and than i followed this tutorial
[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)
and it worked.

---

### Post by chrisinspace on 2008-12-20
> **BzuCo said:**
> I fixed reconnecting the mouse by douwngrading the packages to these versions:

$ dpkg -l | grep -i blue
ii bluetooth 3.19-0ubuntu3 Bluetooth stack utilities
ii bluez-cups 4.12-0ubuntu5 Bluetooth printer driver for CUPS
ii bluez-gnome 1.8-0ubuntu1 Bluetooth utilities for GNOME
ii bluez-utils 3.19-0ubuntu3 Bluetooth tools and daemons
ii libbluetooth2 3.19-0ubuntu1 Library to use the BlueZ Linux Bluetooth sta
ii libbluetooth3 4.12-0ubuntu5 Library to use the BlueZ Linux Bluetooth sta



I have never downgraded packages before.  How do you go about this?  Do you do this with apt-get and the repos or do you have to download the older packages and manually install them?

Thanks

---

### Post by HyRax on 2008-12-26
Woah - you shouldn't have to do all that. Try [this workaround](http://ubuntuforums.org/showpost.php?p=6438656&postcount=6) and see if that resolves your issue. It's working well for me and my Microsoft Bluetooth Notebook Mouse 5000.

---

### Post by chrisinspace on 2008-12-29
I'd give that a try, but now I can't get my keyboard/trackball combo to connect at all.  I was hoping that downgrading the packages would correct the issue until the devs get this issue sorted out.

---

### Post by HyRax on 2008-12-29
But unless you've got the Proposed repository enabled, there's nothing to downgrade to. My 64-bit desktop is up to date and is using the following versions of the Bluetooth packages:

```

$ sudo dpkg -l | grep blue
ii  bluetooth                                 4.12-0ubuntu5                           Bluetooth support
ii  bluez                                     4.12-0ubuntu5                           Bluetooth tools and daemons
ii  bluez-alsa                                4.12-0ubuntu5                           Bluetooth audio support
ii  bluez-cups                                4.12-0ubuntu5                           Bluetooth printer driver for CUPS
ii  bluez-gnome                               1.8-0ubuntu1                            Bluetooth utilities for GNOME
ii  bluez-gstreamer                           4.12-0ubuntu5                           Bluetooth gstreamer support
ii  bluez-utils                               4.12-0ubuntu5                           Transitional package
ii  libbluetooth3                             4.12-0ubuntu5                           Library to use the BlueZ Linux Bluetooth sta
$

```

I would suggest you grab a LiveCD and boot up on it so that you have a clea, default environment to play with. Connect a wired keyboard and just test things with your Bluetooth mouse first. Pair it and issue the *sudo hciconfig hci0 pscan* command I described earlier and see how you go. You should not have to make drastic changes to your setup just to get Bluetooth working under Intrepid.

I've now setup a number of machines with Bluetooth mice (with wired keyboards, though) and have had no issues with this workaround.

---

### Post by rooster_fruit on 2009-02-17
this may be a bit late, but i had the same problem (fresh install of 8.10), and simply ticking a visibility setting (by default none are set) in the bluetooth preferences window fixed it

---

