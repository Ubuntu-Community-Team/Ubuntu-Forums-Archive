---
title: "HOWTO: Xubuntu Intrepid Bluetooth Mouse Setup"
date: 2009-01-03
forum: Outdated Tutorials &amp; Tips
---

### Post by hlmuller on 2009-01-03
It was a simple solution found after hours of searching, and I leave it here for the next soul to find.

There have been many reported problems on bluetooth in Intrepid.  The big difference between Intrepid and previous versions being bluez version 4.X is in use.  Apparently most of the HID bugs are fixed.

I set up a Microsoft Bluetooth Notebook Mouse 5000, but I expect this will work for you.

Open a terminal and enter the following:

$ bluetooth-applet

This will create the bluetooth applet.  Left or Right click the bluetooth icon, and click "Setup new device...".   Follow the wizard's instructions and you are done.

The bluetooth-applet will not survive reboots, but the mouse itself will remain paired and working.

If you really want the bluetooth-applet to show then edit:

    /etc/xdg/autostart/bluetooth-applet.desktop

Modify:

    OnlyShowIn=GNOME;

    to

    OnlyShowIn=GNOME;XFCE;

The last ampersand is most likely not necessary.

The applet issue is a known bug:

    [https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/163518](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/163518)

Cheers.

---

