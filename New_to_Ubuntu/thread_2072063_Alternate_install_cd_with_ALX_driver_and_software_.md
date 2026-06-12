---
title: "Alternate install cd with ALX driver and software raid"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by savagetwinky on 2012-10-17
hi,

So i've run into some issues. I just bought myself a brandy new mobo along with 2 solid state drivers. I want to set the ssd's up as a raid 0. I found out how to do that pretty simple, but the problem is I can't continue the install because I don't have a network adapter.

The mobo I have is a z77-ds3h from gigabyte, its got an atheros r8161 or something.  Somewhere buried on the internet i found a small guide on how to download and build the alx driver... but I can't install it, don't really know how.

So the task i have at hand is to figure out how to make this magic combo work, alt cd + raid0 + network..

although I might try and take the easy way out and borrow a usb to ethernet adapter from work tomorrow...

---

### Post by shreepads on 2012-10-17
Can you post output from 
$ sudo lspci -vvnn

Filter out the things other than the networking interface(s) pls...

Hmmm, since ethernet is not working on the machine I guess you would need to redirect output to file, edit, copy using USB and then post..

---

### Post by savagetwinky on 2012-10-17
ok stupid question, how would i do that with the alternate cd... or should i get a live cd as well. 

I already know I need to install the alx driver from.. i think the copact wireless

[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

[http://askubuntu.com/questions/6499/provide-driver-on-removable-media-during-installation](http://askubuntu.com/questions/6499/provide-driver-on-removable-media-during-installation)

I don't have a debian package though :(

---

### Post by savagetwinky on 2012-10-17
Ok i used a usb to ethernet to get ubuntu installed, and post this message

i had to zip the output of lspci -vvnn

---

### Post by shreepads on 2012-10-18
OK so it's a Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091]

And there are no drivers attached to it by default...

Only option is to download and shuffle files over USB and then install as outlined in this post:

[http://ubuntuforums.org/showpost.php?p=12206899&postcount=6](http://ubuntuforums.org/showpost.php?p=12206899&postcount=6)

---

