---
title: "change graphics card"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by expatCM on 2012-12-29
Very strange situation ...   I just had an MSI graphics card fail and so had to drop in a spare which is an nVidia card.  Problem is with selecting the driver ...  it is impossible.

If you click on the Restricted Drivers since the machine is presently in 640 x 480 mode whilst you can see the top part of the page you cannot see that there is an Activate button to enable the driver.  There is no apparent way to change out of the 640 x 480 mode.

I think the nVidia drivers are installed but I cannot figure out how to select them.

How do you get round this?

I was going to try the Recovery Mode but that does nothing other than hang after selecting network support.

---

### Post by TheFu on 2012-12-29
Backup your /etc/X11/xorg.conf file, then delete it.  You need to be root (or use sudo) for this.

$ sudo mv  /etc/X11/xorg.conf  /etc/X11/xorg.conf-backup

Reboot. All should be back to normal with defaults and Ubuntu should tell you that it found an nvidia card.

---

### Post by Frogs Hair on 2012-12-29
Not quite sure understand , but if the Nvidia driver is installed then the Nvidia Xserver Settings settings is where the resolution setting is located. MSI is one of many companies that manufacture Nvidia cards but that doesn't mean the driver you might have installed is interchangeable with the replacement card. 

The desktop effects on or off option on earlier versions on Ubuntu disappeared with Gnome 2. What is the output of the following command ? lspci -v

---

### Post by audiomick on 2012-12-29
Have a look here

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Installation_without_X_.2BAC8_from_the_console]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Installation_without_X_.2BAC8_from_the_console")

Read the whole thing, but I think the spot that the link brings you to is what you might need.

---

### Post by expatCM on 2012-12-29
Fixed ...

The Jockey command confirmed that the driver was installed but it was disabled and not in use.  The final line selected the driver and on reboot all was back to normal.

Many thanks for all the assistance.

---

