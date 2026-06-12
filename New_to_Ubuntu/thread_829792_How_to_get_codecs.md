---
title: "How to get codecs"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Tharakanuwanpro on 2008-06-15
How to get audio and video codecs without internet on ubuntu . I have windows and ubuntu 8.04 on the same computer . But my modem is a usb one and i can't connect to the internet through it . Tell me how to get codecs from windows and install it on ubuntu .

---

### Post by hyper_ch on 2008-06-15
that's going to be painfull. You'll have to download each individual package...

however a simple solution would be

(1) install vmware or virtualbox in your windows

(2) setup an ubuntu virtual machine

(3) download and install then the codecs in the virtual machine (it will have an ethernet connection to your windows host and so be able to use that internet acces - I hope)

(4) then copy the downloaded .deb files into your actual installation and install codecs there then :)

---

### Post by atomkarinca on 2008-06-15
[This]("http://ubuntuforums.org/showpost.php?p=4519538&postcount=4") should help.

---

### Post by bumanie on 2008-06-15
> **Tharakanuwanpro said:**
> How to get audio and video codecs without internet on ubuntu . I have windows and ubuntu 8.04 on the same computer . But my modem is a usb one and i can't connect to the internet through it . Tell me how to get codecs from windows and install it on ubuntu .

I have a friend with a usb modem that connects to the internet via ubuntu. xp won't recognise the usb modem, but ubuntu does. Have you tried to configure the modemand internet settings under ubuntu?
Also is your connection adsl or cable? My friend's is cable, although I can't see how that will make much difference if the signal is strong.

---

### Post by steveneddy on 2008-06-15
**[COLOR="Blue"]Codecs[/COLOR]** are designed to get sound and video output from your PC. 

**[COLOR="Blue"]Drivers[/COLOR]** are designed to make hardware work.

Which one are you looking for? Drivers or codecs?

The A/V codecs are something like

**w32codecs**

and you can find them in Synaptic or apt-get.

Unless you are a 64 bit OS, then it is

**w64codecs**

---

