---
title: "BCM4309 wireless card"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by moose4204l on 2008-05-31
DID ANYONE GET THEIR BCM4309 WIRELESS CARD WORKING?????

i tried so many things and i cant get mine to work. i tried this [thread]("http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm4309+wireless&page=23") but nothing worked. Anyone have success with their wireless.

Bcm4309 802.11a/b/g dell inspiron 5100

---

### Post by shifty_powers on 2008-05-31
have you thought about using ndiswrapper?

---

### Post by etherspin on 2011-07-21
I realize that this is an old thread, but if I can get it working, anybody should be able to:

Open Terminal in a new Ubuntu installation (new because I don't know what anybody might have tried before trying this).

Download and install firmware-b43-installer:

```

sudo apt-get install firmware-b43-installer

```This should also download and install b43-fwcutter for you!  This package is what extracts the Broadcom 43xx firmware.

Give it a minute...and...

Presto!  Wireless internet!

:D

---

### Post by wep940 on 2011-07-21
And.....if you have no other internet connection available (i.e., you can't hardwire a connection) to do the above, remember that the firmware cutter packages are on the install media (LiveCD) in the /pool/main/b folder. ;)
 
Also - I found it necessary to download a separate firmware package that contains a lot of the firmware needed as well.  I had to do this because even after installing the firmware cutter it still said the firmware was missing.

---

