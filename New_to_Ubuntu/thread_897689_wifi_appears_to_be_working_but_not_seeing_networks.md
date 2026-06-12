---
title: "wifi appears to be working but not seeing networks"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by hhare on 2008-08-22
I have two computers here.  I just installed Hardy on the second, a Presario M2000.  It did what it needed to to enable wireless and the wireless light is on, it grabbed the drivers etc.

The snag is that when I click on the connection in the panel it shows NO networks.  

I know that the networks are there and working because another machine sees mine and two others.

I believe that all is installed well on the M2000 because when I right click on the connection icon I can enable and disable the wifi and the light on the machine goes on and off.

For what it is worth I am running the broadcom BCM4306 controller, but as I say the hardware manager tells me that it is working fine

Help please!

---

### Post by tuxulin on 2008-08-22
im assuming the other machine is windows

Try installing Samba. It's a program that "shares folders over your network". Point is, that will probably help. You can install Samba by going to System/Administration/Shared Folders. There will be a popup that has Samba and a different program that works for Mac OS and lets you install them. Once the install is finished, go to System/Administration/Services and make sure the little box next to Samba is checked so it runs on startup.

Tuxulin

---

### Post by hhare on 2008-08-22
I am not inclined to install samba on this machine unless someone can explain why on earth it will help with this.  I can not imagine that samba would be able to see the networks if the network connections can't.

I appreciate the reply but am just not inclined to do it wthout some further explanation as to why it would help.  I would also point out that the other machine doe not have samba on it and works fine and was installed from the same master disk

---

### Post by LowSky on 2008-08-22
sudo apt-get install wifi-radar

---

### Post by tuxulin on 2008-08-22
can you the switch ?
can you ping any of the other machines ?

Tuxulin

---

### Post by hhare on 2008-08-22
I actually decided to b43-fwcutter and installed bcm43cc-fwcutter and all is now working.  Weird!

Posting this here in case it helps anyone else

---

