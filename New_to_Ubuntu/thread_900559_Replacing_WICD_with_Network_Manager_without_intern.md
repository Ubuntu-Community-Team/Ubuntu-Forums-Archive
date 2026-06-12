---
title: "Replacing WICD with Network Manager without internet"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Tobis84 on 2008-08-25
I am a newbie to this Ubuntu and I have an obvieous question:
How do you install these files?
I have the exact same problem.
my RT2860 driver doesn't seem to work with Wicd

---

### Post by aysiu on 2008-08-25
Download the file from [your local mirror](http://packages.ubuntu.com/hardy/i386/network-manager/download) using another computer.

Transfer the file to your Ubuntu computer.

Double-click the file.

---

### Post by billgoldberg on 2008-08-25
Or just pop in your Ubuntu live cd and you'll be able to install Network Manager using synaptic.

---

### Post by ugm6hr on 2008-08-25
> **aysiu said:**
> Download the file from [your local mirror](http://packages.ubuntu.com/hardy/i386/network-manager/download) using another computer.

Transfer the file to your Ubuntu computer.

Double-click the file.

You'll want netwrork-manager-gnome too: [http://packages.ubuntu.com/hardy/i386/network-manager-gnome/download](http://packages.ubuntu.com/hardy/i386/network-manager-gnome/download)

(Links for 32-bit Ubuntu)

---

### Post by Tobis84 on 2008-08-26
now I got installed, but the tray icon isn't there.. you know, the one next to the clock in the upper right corner, where I can choose network.
How do I get it there

---

### Post by aysiu on 2008-08-26
> **Tobis84 said:**
> now I got installed, but the tray icon isn't there.. you know, the one next to the clock in the upper right corner, where I can choose network.
How do I get it there Press Alt-F2 and paste in ```
/opt/wicd/tray.py &
``` Then go to System > Preferences > Sessions

Add to the Startup Programs the command ```
/opt/wicd/tray.py &
```

---

### Post by ugm6hr on 2008-08-26
Are you trying to use Wicd or NM now?

aysiu's advice explains how to get a Wicd system tray icon.

For NM:

System-> Preferences-> Sessions
Add
Name: Network Manager
command: nm-applet --sm-disable

Then reboot.

---

