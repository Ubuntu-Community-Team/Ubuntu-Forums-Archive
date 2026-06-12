---
title: "installing ubuntu on UMPC"
date: 2007-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by vanozky on 2007-05-15
here is a little tips for anyone who wants installing ubuntu in UMPC devices (800x480).

note 1. my UMPC (ECS-h70) as the others, support 800x480 screen resolution.So, installing menu will be
cut at the bottom if screen.

note 2. play live cd ubuntu 7.0.4 (or else), and choose install link on desktop.

note 3. installing menu will appear on the screen. as i mention above, it will be cutted at the bottom of 
screen. So, "will not able to see interactive button like BACK, FORWARD, OR ACCEPT.

note 4. TIPS : Here is my tips to install it : I use combination of these 2 :
1. using "tab" key to jump through the menu. use your feelings, maybe you sould try tabing more than 
one cilcle to make sure you are on the right menu. Just imagine, each page (not always) often have 2 or 3 button bellow them : BACK, ACCEPST and FORWARD. When tab in Forward potition then hit enter. :P
2. using keyboard shortcut like alt+B for BACK, alt+A for Accept and alt+f for Forward. Then you can go through or back even you are not seeing the interactive button by pressing the short cut.

:) hope that can be usefull for you.
thanks.

_vanozky_
./eksplorasi tiada henti sampai kita mati !

---

### Post by aafshar on 2007-05-25
Hi,

Another useful tip is using Alt F7, with th arrow keys or mouse thingy to move windows around that are too big.

Does anyone have the touchscreen working?

It slightly works for the live cd but seems very dead when I used the installed Ubuntu. (Feisty).

I have tried the drivers from Galax [http://www.eeti.com.tw/web20/eg/drivers.htm#ub](http://www.eeti.com.tw/web20/eg/drivers.htm#ub) as the thing reports itself (with lsusb) as a eGalax Touchscreen, but I can't seem to get anything to work.

I can provide lots more information on my failed attempt, but if anyone has pointers I would appreciate them.

Thanks,

Ali

---

### Post by aafshar on 2007-05-27
Well, eventually, I can get the touchscreen to work. You need to build the driver and follow directions here: [http://linux.chapter7.ch/touchkit/mini-howto.txt](http://linux.chapter7.ch/touchkit/mini-howto.txt)

But things aren't so straightforward, as this only sometimes works. The touchscreen sometimes appears on /dev/input/event2 and sometimes on /dev/input/event4

When it is on event4 it doesn't work at all, ie nothing ever happens on that device and it all seems dead. When its on event2 it is readable fine and you can set it up easily on X using the directions in that how-to.

I would be very grateful if anyone has anyidea why it works on one device and not on another. I suspect UDEV has somthing to do with it, but I am not sure.

Ali

---

