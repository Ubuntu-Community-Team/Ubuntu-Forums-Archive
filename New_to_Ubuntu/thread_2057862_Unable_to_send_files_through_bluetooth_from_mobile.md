---
title: "Unable to send files through bluetooth from mobile phone to the laptop"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by linuxandunix on 2012-09-14
Hi! I'm using Ubuntu 12.04 64bit on a Dell Latitude E6410. I noticed that I'm not able to send files through bluetooth from mobile phone to the laptop. Any remedy for this?

---

### Post by black veils on 2012-09-14
you need to make sure that the laptop bluetooth settings, or file sharing settings or something, are allowing files to be received.

also did you do the obvious and pair the devices first?

is your phone an android? if yes, then you could connect it to the computer as a usb mass storage device, if it has an sd card in it. when you plug the phone in, you will need to tell it to connect to the computer as mass storage. remember when you disconnect, to unmount from the computer file manager first, then on your phone turn off the mass storage connection.

---

### Post by BrianBlaze on 2012-09-14
or if it's an iphone you can ssh into it :) assuming it is jailbroken (WHICH IT SHOULD BE)

---

### Post by Mark Phelps on 2012-09-14
> **black veils said:**
> ... is your phone an android? if yes, then you could connect it to the computer as a usb mass storage device ... 

NOT, if it's one of the newer phones (e.g., Samsung Galaxy S3) or one of those updated to Android 4.x (ICS).  ICS removed the capability to mount the phone as USB Mass Storage.

---

### Post by black veils on 2012-09-14
> **Mark Phelps said:**
> NOT, if it's one of the newer phones (e.g., Samsung Galaxy S3) or one of those updated to Android 4.x (ICS).  ICS removed the capability to mount the phone as USB Mass Storage.

thats inconvenient! glad i didnt want to waste money on an overly fancy phone :P

---

### Post by linuxandunix on 2012-09-15
Thank you all for your responses. I found out that typing "gnome-file-share-properties" in a terminal opens up the relevant window to enable file sharing over bluetooth.

---

