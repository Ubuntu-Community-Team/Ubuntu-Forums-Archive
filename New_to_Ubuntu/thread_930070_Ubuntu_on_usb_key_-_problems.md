---
title: "Ubuntu on usb key - problems"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Boozeman on 2008-09-25
Hi,

I am absolutely new at linux although I have used pc's since ms-dos so I am not scared of command prompts ;-)

I have managed to follow instructions and put ubuntu on a 2GB usb key. 

I would like to use this as a sort of private kingdom I can run on my pc at home, work etc. 

It boots fine, I can surf the web etc. My only gripe is that I cannot make a permanent user to save settings eg. of email account or browser favourites. I cannot move files to the "casper" partition, but I can't figure out how to login as root to change privilege ratings.

I have tried creating a new user and selected all priviliges, but when I reboot I am logged in as Live Session user and trying to switch user to the one I created does not work. How can I save the settings?

Thank you for your time,

Fred

---

### Post by _sAm_ on 2008-09-25
It sounds to me that you only have installed it on the USB key as a "live medium"(meaning just as an normal live-cd). That means you cant save changes. 

Take a look here for a guide to install it as a "normal install" on the usb key:  [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Boozeman on 2008-09-25
Actually I followed the guide for the "persistent install", and at boot up it says that's what I'm loading up.

FYI: if it helps at boot I do not get a login prompt but I am automatically logged in as Live session user.

---

### Post by C.S.Cameron on 2008-09-25
I install thus:

Unplug your HDD power cables or disable your HDD's in bios. (optional).
Boot the Live CD..
Plug in the USB device.
Run Install.

When you get to partitioning you can use:
Guided, use entire disk
This seems to work best on low quality devices.
or if you want to be able to plug into a computer running windows and upload files, use:
Guided, resize ...and use remaining space.
Then drag the bar right to show how much FAT you want to keep
Complete the setup, when it is done you will have Ubuntu on USB.
It runs the same as it does from hard disk, all changes are there on reboot.

---

