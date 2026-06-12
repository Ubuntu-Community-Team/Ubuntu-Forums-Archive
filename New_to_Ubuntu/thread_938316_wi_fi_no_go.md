---
title: "wi fi no go"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by inmanc on 2008-10-04
I have up and running Ubuntu 8.04 but can't figure out how to connect the box to my wifi connection.  I know the wifi works because I use it on my XP computer.

If I unplug my Linksys Wireless-G USB adapter from my XP and plug it into my Ubuntu, Mozilla finds no connection.

How do I show it the way to my wifi?    :confused:

---

### Post by Crafty Kisses on 2008-10-04
I'm pretty sure the rt2x00 driver works with this, which you can get right [**here**]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page"). Once you've got that install these packages:
```
sudo apt-get install ndisgtk ndiswrapper build-essential
```
Once you've done that, extract the drivers, and run the following command:
```
sudo ndiswrapper -i drivername.inf
```
Replace "drivername.inf" to the actual driver. Once you've done that use "ndisgtk" to install the .inf file. Try that, and see if that springs your card to life.

---

### Post by inmanc on 2008-10-05
Thank you for replying to my post.  I went "here" and downloaded the USB file named 'rt2570-cvs-daily.tar.gz' because I could, not because it seemed like it might be the right file.  So I thought it might be a good idea to check back with you before proceeding with the rest of your instructions.  Am I on track?

Inmanc

---

### Post by caljohnsmith on 2008-10-05
Do you know what chipset your wireless USB device uses? Please post the output of:
```
sudo lshw -C usb
```
And where was the link of that driver you downloaded? :)

---

