---
title: "cant find usb on virtual box (xp)"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-11-08
i have ubuntu 12.04 on my system,,, i installed virtual box oracle on it,,, and then installed windows xp on it...now xp is running fine,,but i cant detect/find any usb stick in it,, there is no indication when i conect usb on system... 
how to resolve issue??what to check for it???

---

### Post by shinasha on 2012-11-08
Did you check the Devices menu? Have you added that USB drive in the VB settings options?

---

### Post by cwsnyder on 2012-11-08
You need to be running the VirtualBox non-free version from Oracle (either from the ppa or .deb file) with the host extensions as well as the client VirtualBox extensions for USB to work at all.

---

### Post by squakie on 2012-11-08
Used to be 2 versions of VB - the one in the repositories didn't have USB support (it was true open source), but you had to download the puel version from Sun (now Oracle).  There is also an "extras" package there as well - it might enable USB now - I haven't checked it.  If you installed VB from the repositories I would delete it and get the version on Oracle's site as well as the extras and install those instead.

---

### Post by Mr_JMM on 2012-11-08
According to VirtualBox website - [https://www.virtualbox.org/wiki/Editions](https://www.virtualbox.org/wiki/Editions) there is, since v4.0, only one version now. Instead of having the OSE and non-free there is just the one and you add the extension pack to "upgrade" this to what was the non-free version. I gather the repo version should be good to go once you add this extension pack, did you do that? Make sure it is for the correct version as I believe the repo is a few version numbers behind.

Please correct me if I'm wrong.

---

### Post by syednasirraza on 2012-11-08
> **shinasha said:**
> Did you check the Devices menu? Have you added that USB drive in the VB settings options?

hi shinasha
when i click the devices menu,,, i  see usb devices option there in , which further shows no usb devices connected....although my usb is connected...  i dont know wht more to do with it to make it enable???
when i go in the settings,, there i click on usb, enable usb controller is already checked,,but its un editable, i cant try unchecking or checking it myself... 
i m new to virtualization,,i dont know what to do with it???

---

### Post by syednasirraza on 2012-11-08
> **Mr_JMM said:**
> According to VirtualBox website - [https://www.virtualbox.org/wiki/Editions](https://www.virtualbox.org/wiki/Editions) there is, since v4.0, only one version now. Instead of having the OSE and non-free there is just the one and you add the extension pack to "upgrade" this to what was the non-free version. I gather the repo version should be good to go once you add this extension pack, did you do that? Make sure it is for the correct version as I believe the repo is a few version numbers behind.

Please correct me if I'm wrong.

i dont know much:( ,, but when i see details of virtual box from about menu , it shows version 4.1.12,,, i downloaded and installed it from ubuntu software centre just a couple of weeks ago,, so that must be latest available version...(as i m attaching its screen shot aswell to make it clear what i m saying)
but dont know what to do now to make usb work...:confused:

---

### Post by Mr_JMM on 2012-11-08
Did you remember to add your username to the vbox group?

use a terminal and type ```
cat /etc/group
```

Near the bottom you'll see an entry clearly for virtualbox like vboxusers, is your username on the list (displayed to the right of this) - ```
vboxusers:x:126:jimmy
```

If not, type ```
sudo usermod -a -G vboxusers [yourusername]
```
e.g.
```
sudo usermod -a -G vboxusers jimmy
```

enter your password, close terminal, logoff Ubuntu and log back in again. Now, when you click the icon in VB to add a USB device you'll see a list of devices. You might have to unmount the USB stick first (but don't remove it).

do NOT add the keyboard or mouse to the VB!!

---

### Post by syednasirraza on 2012-11-09
> **Mr_JMM said:**
> Did you remember to add your username to the vbox group?

use a terminal and type ```
cat /etc/group
```Near the bottom you'll see an entry clearly for virtualbox like vboxusers, is your username on the list (displayed to the right of this) - ```
vboxusers:x:126:jimmy
```If not, type ```
sudo usermod -a -G vboxusers [yourusername]
```e.g.
```
sudo usermod -a -G vboxusers jimmy
```enter your password, close terminal, logoff Ubuntu and log back in again. Now, when you click the icon in VB to add a USB device you'll see a list of devices. You might have to unmount the USB stick first (but don't remove it).

do NOT add the keyboard or mouse to the VB!!


THANKS ALOT :PDEAR
I GOT IT DONE THE WAY U TOLD ME by adding my username in the vbox users....(was not this supposed to be done by defualt once i installed virtual box and xp in it)
now i can access my usb there after adding it (although i have to add it everytime once it plug it out,, i dont know if it should work this way)...
thanks alot for helping me out

---

### Post by Mr_JMM on 2012-11-09
You're welcome, glad it worked for you.

Unfortunately, for what ever reason, it is not supposed to happen automatically, that I am aware of. I'm sure there's a good reason for it.

Good luck, feel free to ask any more questions.

---

