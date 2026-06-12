---
title: "New PC unfamiliar OS"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by Dougelove on 2012-06-18
Hi guys, My old PC died so i bought a new one. I asked for Ubuntu Studio Gnome as i previously had it and was familiar with it. I no longer have LMMS and several audio programs ( i know this is a case for SPM which i can manage.)
Now I'm running something completely different and i don't really like it! 
I THINK its xfce but don't know. Also i have no log in screen on startup which i would like.
I would also like to revert back to Studio if i can. Like i said this is a brand new machine with nothing but OS on HDD. and i need to reconnect my USB mouse every time i switch on, tried every usb port - still the same?!
Could someone point me in the right direction to put it right please?
Many thanks in advance

---

### Post by Paqman on 2012-06-18
Can you take a screenshot and show us?

What does the splash screen show while booting?

---

### Post by Cheesemill on 2012-06-18
The latest version of Ubuntu Studio doesn't use Gnome anymore, it uses XFCE instead.

If you want you can install regular Ubuntu instead and just install all of the Ubuntu Studio application packages afterwards.
```
sudo apt-get install ubuntustudio-generation ubuntustudio-graphics ubuntustudio-recording ubuntustudio-video
```Bear in mind that the latest versions of Ubuntu use Unity on top of Gnome 3 as a desktop interface, this may be different to what you know as Gnome (you could well be thinking of Gnome 2 which is no longer developed or supported).

For more info:
[http://www.techworld.com.au/article/386600/ubuntu_studio_says_no_unity_adopts_xfce/](http://www.techworld.com.au/article/386600/ubuntu_studio_says_no_unity_adopts_xfce/)
[http://techie-buzz.com/foss/ubuntu-studio-xfce.html](http://techie-buzz.com/foss/ubuntu-studio-xfce.html)

---

### Post by Dougelove on 2012-06-19
Cheesemill - Thanks and i am already running up to date. one question solved! thanks deal with it!!
Do you have the code for a splash log in screen? At present it logs me in as i boot up without asking for password or user. to my knowledge i have changed this in the settings but to no avail.
finally my mouse - why do i have to keep plugging it in every time so annoying? 
thanks

---

### Post by d4m1r on 2012-06-19
Who built the PC for your or where did you buy it from? If it was a recent purchase, I'd contact the hardware manufacturer.

---

### Post by Dougelove on 2012-06-19
is that for the mouse issue? USB Mouse works fine and it is recognized i just have to pull it out and put it back in every time i startup or reboot! it is so annoying

---

