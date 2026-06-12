---
title: "recognising usb drives"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by dnaga57 on 2008-06-13
I have Dell D420 C with XP & D with ubuntu 8.04 as 'inside- within windows.
My webcam in usb is not recognised. Any suggestions

---

### Post by worldy on 2008-06-13
Did you type the command
```

lsusb

```
and didn't find anything detected

You need additional software like cheese to view your webcam,or you can test it with ekiga

I am not sure about anything under wubi

---

### Post by stchman on 2008-06-13
> **dnaga57 said:**
> I have Dell D420 C with XP & D with ubuntu 8.04 as 'inside- within windows.
My webcam in usb is not recognised. Any suggestions

A webcam is not a USB drive.  Install Cheese.

```
sudo apt-get install cheese
```

Launch Cheese and if your webcam is supported it will turn on.

---

### Post by dnaga57 on 2008-06-14
How do I launch cheese ( already installed in my computer)

---

### Post by aktiwers on 2008-06-14
Type:
```
cheese
```In terminal or create a launcher in your panel or desktop.

Edit: it's also in Applications=>Graphics=>Cheese

---

### Post by dnaga57 on 2008-06-15
I get the following & a screen with colors splashing
dnubuntu@dnubuntu-laptop:~$ cheese
** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(757): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couldn't open file 'file:///home/dnubuntu/.gnome2/cheese/media/0002.ogg'
Reason: Stream contains no data..

** (cheese:8602): WARNING **: could not load /home/dnubuntu/.gnome2/cheese/media/0002.ogg (application/ogg)

---

### Post by dnaga57 on 2008-06-15
I have a Philips Fun cam attached. See below
dnubuntu@dnubuntu-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 05b8:3038 Agiler, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0471:0321 Philips 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 007: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 006: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 005: ID 0b97:7761 O2 Micro, Inc. 
Bus 001 Device 004: ID 413c:a005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000
I have the driver for it downloaded as pwc-9.0.2 as below
/home/dnubuntu/Documents/pwc-9.0.2
I am not knowing how & where to install the driver to make the webcam work.
Is it necessary for me to have Dorgem or Fwink? If so how do I get them?
I am 70 years ols, a retired voluntary healthcare worker. I am really inmpressed with Ubuntu & the Forum community on their prompt efficient help in my learning !!!:popcorn:

---

### Post by aktiwers on 2008-06-15
Hi there!
Read through some of the instructions in the link below and try out if any of them works for you:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

I got about 4 webcams to work this way, I hope the same will happen for you.
Welcome to Ubuntu by the way! And remember to report back if you got it to work or not :)

Cheers!

---

### Post by dnaga57 on 2008-06-15
Sorry. Not able to install easy cam 1 or 2. Got camorama but do not know how to use it. I will needs a 'for Dummys tuype help.
:confused:

---

