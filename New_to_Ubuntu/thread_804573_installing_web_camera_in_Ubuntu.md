---
title: "installing web camera in Ubuntu"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by gaffajoiner on 2008-05-23
How do you install a web camera in Ubuntu it is a USB

---

### Post by cool_penguin on 2008-05-23
Just plug it in and fire up something like camstream. If you do not have it, then just sudp apt-get install camstream. After it is installed, run camstream in the terminal and you should see yourself on the monitor if your camera is compatible. 

Cheers,
Harry

---

### Post by gaffajoiner on 2008-05-23
Hi been to add and remove then typed in sudp apt but it came up with a blank screen

---

### Post by benevolent on 2008-05-23
Hello..


look at this thread: [http://ubuntuforums.org/showthread.php?t=803140](http://ubuntuforums.org/showthread.php?t=803140)

and this guide [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

:)

---

### Post by Mr. Svinlesha on 2008-05-23
First, a warning: I've not tried to install a webcamera myself, but I've read some threads about doing so, it's usually a very complicated process.  For various reasons, ubuntu can't run webcams to well.

Having said that, I think what Cool penguin meant was to type in a terminal command.  Go to Applications > Accessories > Terminal, and then copy and paste the following command at the prompt: > sudo apt-get install camstream

Note there was also a typo in Cool Penguin's instructions: he meant "sudo", not "sudp".

Good luck.

---

### Post by philinux on 2008-05-23
Go to ,

System>Admin>Synaptic Package Manager

It will ask for your password.

Click on any package then type cheese

Mark it for install.

PLug in you webcam then ina termainl System>Access>Terminal type

lsusb

You should see your camera listed if it's been recognised. 

Fire up cheese or instant messenging package like amsn or kopete

Mine worked out the box with kopete.

---

