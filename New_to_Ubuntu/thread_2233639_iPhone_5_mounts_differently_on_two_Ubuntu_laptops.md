---
title: "iPhone 5 mounts differently on two Ubuntu laptops"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2014-07-09
Hi Guys,

I have a Dell Inspiron 1520 and a ZaReason Strata 7440.
I copied the home directory from the Dell to the ZaReason.
My iPhone 5 is automatically mounted on both computers.
On the Dell when the phone is mounted two windows open up.
One is called my phone and contains the DCIM directory.
The other is called Documents on my phone and has among other things the mp3 player I use on my iPhone.
This is the directory I can drag music files into and from which the mp3 app reads them.

On the ZaReason machine, the phone mounts and the window called my phone opens up.  The Documents on my phone does not open up.
The first time I plugged the phone in to the ZaReason machine after doing an iOS update, the Documents directory on my phone **did** in fact open up, however thereafter the Documents directory on the phone is not accessable.
The my phone directory that contains the DCIM directory is accessable however.

Does anyone have an idea as to why the Documents directory on the iPhone will not open on the ZaReason machine, but will open on the Dell?

---

### Post by slooksterpsv on 2014-07-10
Are they both using the same Ubuntu version? Do each of them have python-imobiledevice installed?

---

### Post by GrouchyGaijin on 2014-07-10
Thank you for the reply.
It turns out that the ZaReason machine did not have python-imobiledevice installed.
I was able to install it by running sudo apt-get install python-imobiledevice.

Unfortunately even after rebooting the machine and then connecting the phone the Documents directory on the phone is not accessible.
The My Phone window which contains the DCIM directory with any photos and videos I have taken **is** accessible.  (So it's not a total disaster if I can't get to the Documents directory.)

---

### Post by GrouchyGaijin on 2014-07-23
bump

---

### Post by slooksterpsv on 2014-07-24
We never got into this but are they both running the same OS, same version, same arch? E.g. Ubuntu 14.04 64-bit.
Also, if you open Nautilus or Thunar or Dolphin or whatever you're using, on the left does it show the iPhone with 2 different mounts?
What is in the fstab of the dell?
cat /etc/fstab

---

### Post by GrouchyGaijin on 2014-07-24
The Dell is 32 bit and the ZaReason is 64 bit - otherwise the same.
On the ZaReason only one mount shows up on the Dell two show up.
I can't check the fstab of the Dell now - I am not at home and won't be home for a couple of weeks.

---

### Post by Rob Sayer on 2014-07-24
Which version of ubuntu (eg 12.04/14.04).  It's not possible to support people who don't provide enough information.

---

### Post by GrouchyGaijin on 2014-07-24
14.04 - you know I just noticed that next to every post I have made it says:
**Distro**:
Ubuntu 14.04 Trusty Tahr  
I guess I could make a snarky reply about providing duplicate information....but what I would really like is to know why a Documents directory opens up on one machine and not on the other.
The only difference I can see is the Dell is running 32 bit and the ZaReason is running 64 bit.

---

### Post by slooksterpsv on 2014-07-25
Unfortunately even though it says Distro 14.04, we don't know for what machine or if it is for both. We just know you may just love TT, not even having it installed but your distro of choice is TT. Mine I believe still says Xubuntu 13.10, I don't remember updating mine (maybe I did 2 weeks ago...) so we can't use that information.

Hmm... 32-bit and 64-bit would make a difference on the side for what drivers load to make it mount. Maybe a 64-bit implementation of what the iPhone 5 mounts isn't available? I don't know. If you check your file manager you may see it listed there (possibly) or you may find a guide on how to manually mount it.

---

### Post by GrouchyGaijin on 2014-08-01
[COLOR=#ff0000]UPDATE[/COLOR]

A weird thing happened today.  My iPhone 5 totally ran out of battery before I could plug it in to the computer to charge it and when I did plug it in BOTH the iPhone directory _*along with the Documents directory *_opened up.

---

