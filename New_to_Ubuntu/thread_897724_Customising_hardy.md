---
title: "Customising hardy"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Beezgetz on 2008-08-22
Hello,

I have been on linux for two weeks now. I searched a lot, but I still have several questions to get me and hardy good friends.

 How do I get my webcam (Trust) to work?
How do I attach camera (Sony)?
(thanx god, the usb key is working, heheh...)

Are there lists of repositories?

Why is there no sound in FF videos when already listening to music via amarok?  And vice versa, why amarok freezes if already watching video in FF?

Where ara desktop pictures stored? I like 'elephant/dirt', and like to have it for panels background picture.

Why some window turn grey and unresponsive?

All help welcomed, since I need to fix this in order to stay on it


Kind regards, Beezgetz

---

### Post by aloshbennett on 2008-08-22
okay!
Your camera should work as soon as you plug in the usb. If not, are you getting any error?
Is there any particular application that turns unresponsive (in a predictable manner)
How much RAM do you have?

The wallpapers are under /usr/share/backgrounds

---

### Post by LowSky on 2008-08-22
> Are there lists of repositories?

System>Admin> Synaptic
It has every application that is availible to download and auto install

```
Why is there no sound in FF videos when already listening to music via amarok?  And vice versa, why amarok freezes if already watching video in FF?
```
This is a flash glitch, it has been talked about alot in the past few weeks. in google type: **firfox flash no sound**


> Where ara desktop pictures stored? I like 'elephant/dirt', and like to have it for panels background picture.
if they are your pictures  then= /home/*yourname*/pictures
if install by system = /usr/share/backgrounds

> Why some window turn grey and unresponsive?
IDK? FF3 seems to have some issues concerning this lately for me as well, I think its because FF3 wasn't designed as well as FF1 & FF2. But it mostly occurs because the program is taking up too much system resources and is lagging behind. I blame my FF3 issue on Adobe's Flash and Sun's Java. Both companies really need to pick up t slack in Linux developement.

---

### Post by cariboo on 2008-08-22
We need to know the make/model of your web cam to help you get it working.

To repair your sound problems, have a look athis page:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

> Why some window turn grey and unresponsive?


Usually when I window turns grey and unresponsive it is processing something in the background, give it some time and it will come back.

Jim

---

### Post by Beezgetz on 2008-08-22
Oh, hello so quickly, thanx,


*/I have 2GB RAM, 2.2 GHz pentium dual core processor (HP 6280 Compaq).

*/The 'gray' app is FF. It stood gray hole night...

*/Camera: Megapixel USB2 Wide Angle Webcam Live WB-6200p
[http://www.trust.com/products/product_detail.aspx?item=14881](http://www.trust.com/products/product_detail.aspx?item=14881)

when I plug it in nothing happens. 

i got webcam2, and it says it is Microdia USB2.0 Webcam29. it , like, installed drivers, but here is the picture of test ride:
[img]http://shrani.si/f/42/77/2DWpPdHZ/screenshot-cheese.png[/img]
[[img]http://shrani.si/t/42/77/2DWpPdHZ/screenshot-cheese.jpg[/img]](http://shrani.si/?42/77/2DWpPdHZ/screenshot-cheese.png)


if I do: system->administration->Hardware drivers I get this:
[img]http://shrani.si/f/3z/9L/W8JlWR4/screenshot-hardware-driv.png[/img]
[[img]http://shrani.si/t/3z/9L/W8JlWR4/screenshot-hardware-driv.jpg[/img]](http://shrani.si/?3z/9L/W8JlWR4/screenshot-hardware-driv.png)


as I type lsusb in terminal, I get:

Bus 007 Device 007: ID 046d:c045 Logitech, Inc. 
Bus 007 Device 006: ID 046d:c312 Logitech, Inc. 
Bus 007 Device 005: ID 0c45:62b3 Microdia 
Bus 007 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 007 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 007 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

I guess Bus 007 Device 005: ID 0c45:62b3 Microdia  is one I need.

*/Thanks for background pictures!!!

*/System>Admin> Synaptic It has every application that is availible to download and auto install" - jes but don't I need some internet links for other two, universe and the other one...


Kind regards, Beezgetz

---

### Post by aloshbennett on 2008-08-22
Can you see your sony camera listed under lsusb when you plug it in?

---

### Post by t0p on 2008-08-22
> **cariboo907 said:**
> 
To repair your sound problems, have a look athis page:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)



There's a better fix for audio [at this link]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") - better because it allows you to use **Flash 10**!!

---

### Post by Beezgetz on 2008-08-22
Hello,

this is without pluged camera:
Bus 007 Device 007: ID 046d:c045 Logitech, Inc. 
Bus 007 Device 006: ID 046d:c312 Logitech, Inc. 
Bus 007 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 007 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 007 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  


This is with camera pluged in:
Bus 007 Device 008: ID 0c45:62b3 Microdia 
Bus 007 Device 007: ID 046d:c045 Logitech, Inc. 
Bus 007 Device 006: ID 046d:c312 Logitech, Inc. 
Bus 007 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 007 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 007 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000


thanx for links, ckekking them now



update:
ok, FF and amorak are working
monkotronic on this forum said: "install the package "libflashsupport" and it will fix the problem. it was available in the default repositories." 

also, the 'grey' problem is gone.

---

