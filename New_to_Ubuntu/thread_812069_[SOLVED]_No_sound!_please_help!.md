---
title: "[SOLVED] No sound! please help!"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by iwannalearn on 2008-05-29
Hi recently got hold of this mobo only thing is i have no sound!

Any tips please. tried searching drivers but all seem to be for m$?

Thanks

---

### Post by xfceuser on 2008-05-29
hi try these commands:

sudo /etc/init.d/alsa-utils restart

and

gnome-alsamixer

---

### Post by iwannalearn on 2008-05-29
Dummy forgot this is the mobo
[http://www.giga-byte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1601](http://www.giga-byte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1601)

---

### Post by sayakb on 2008-05-29
Install the backport modules:
```
sudo apt-get install linux-backports-modules
```

---

### Post by iwannalearn on 2008-05-29
xxxxx@xxxxx-desktop:~$ gnome-alsamixer

** (gnome-alsamixer:6639): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Surround Jack Mode"!

** (gnome-alsamixer:6639): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mic Select"!

** (gnome-alsamixer:6639): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mono Output Select"!

** (gnome-alsamixer:6639): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Channel Mode"!

What you make of this please?

---

### Post by xfceuser on 2008-05-29
these errors are not so important, see if you get the sound controls on the mixer, then see if there is anything muted etc. ...

---

### Post by sayakb on 2008-05-29
Try the backports modules. It has a couple of the drivers included..

---

### Post by xfceuser on 2008-05-29
i dont think you need any driver, your mobo has Realtek ALC650 sound chipset, which should already work with alsa ...

---

### Post by iwannalearn on 2008-05-29
there was some muted but i unticked them but still no sound

got this ina pop up

Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash '/'
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash '/'


also tried 


xxxxx@xxxxx-desktop:~$ sudo apt-get install linux-backports-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules
gsimpson@gsimpson-desktop:~$ 

:(

---

### Post by xfceuser on 2008-05-29
firtsly:
$: asoundconf list
then see what is the sound card name (SCN) listed
then
sudo asoundconf set-default-card SCN
restart the sound applications (all, better logout then login), then try sound again. this that you see the controls on the mixer shows that you have already the driver, there is something wrong with the settings.
also try:
sudo /etc/init.d/alsa-utils reset

---

### Post by iwannalearn on 2008-05-29
xxxxx@xxxxx-desktop:~$ asoundconf list
Names of available sound cards:
I82801DBICH4
UART


xxxxx@xxxxx-desktop:~$ sudo asoundconf set-default-card SCN
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

xxxxx@xxxxx-desktop:~$ sudo /etc/init.d/alsa-utils reset 
 * Resetting ALSA...                                                     [ OK ] 

Just going to restart now!

---

### Post by xfceuser on 2008-05-29
type:
sudo asoundconf set-default-card I82801DBICH4
replace SCN with the name.

---

### Post by iwannalearn on 2008-05-29
xxxxx@xxxxx-desktop:~$ sudo asoundconf set-default-card I82801DBICH4
[sudo] password for x: 
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

When i do gnome-alsamixer i get this in a window

An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly.

Googled it and found this
[https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768](https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768)

Many thanks for now mate, another thing i can try is getting hold of spare speakers just to confirm, since mine is sound direct from the monitor.

Thanks again will post again tomorrow:lolflag:

---

### Post by xfceuser on 2008-05-29
you can also try alsa-mixer-gui instead of gnome-mixer ....

---

### Post by iwannalearn on 2008-05-30
**xfceuser** many thanks for the help tips sure learn't a lot from you mate:)

Going back to my problem, i installed a second hdd installed m$, and guess what still no sound!

This was a second pc build for me so downloaded mobo manual, found out it was a jumper setting!

rebooted and viola SOUND:lolflag:

Cheers for the help just the same

---

