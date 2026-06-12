---
title: "Switching from lubuntu to ubuntu"
date: 2019-01-24
forum: New to Ubuntu
---

### Post by raagcity94+ on 2019-01-24
Hello! I recently downloaded lubuntu on my surface pro 1 (yes, it still hasn't melted itself) but I wanted to uninstall it and install a fresh copy of ubuntu instead. How do I go about doing this? I have found various places that say to install it using the "sudo apt-get install ubuntu-desktop" command but that doesn't install a fresh copy of ubuntu it just adds features to the lubuntu. Please help! :) Thank you in advance!

---

### Post by Autodave on 2019-01-24
You could just download Ubuntu and do a clean install by overwriting Lubuntu.  Make sure that you back up anything that you need first!

---

### Post by raagcity94+ on 2019-01-24
Thank you autodave! I downloaded the .iso file on a flashdrive but I am  having trouble to boot the surface pro from the flashdrive to start the  fresh install. I am sorry I am a noob :/

---

### Post by sisco311 on 2019-01-25
Hi, raagcity94+,

and welcome to the forums!

You have to create a bootable USB flash drive. You can use the inbuilt Startup Disk Creator to do it. If you can't find it in the menu, the command to run it is:```
usb-creator-gtk
```

If it's not installed install it:```
sudo apt install usb-creator-gtk
```

Instructions to boot the Surface from the USB can be found here: [https://support.microsoft.com/en-us/help/4023511/surface-boot-surface-from-a-usb-device](https://support.microsoft.com/en-us/help/4023511/surface-boot-surface-from-a-usb-device)

In short: Turn it off, hold down the Volume Down key, turn it on and wait for instructions.

---

### Post by raagcity94+ on 2019-01-25
Ahh this worked thank you sisco311 and Autodave!

---

