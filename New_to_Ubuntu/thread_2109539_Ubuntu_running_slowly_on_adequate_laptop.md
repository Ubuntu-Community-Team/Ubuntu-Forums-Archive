---
title: "Ubuntu running slowly on adequate laptop"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by woodensoul on 2013-01-27
I have an older laptop with the following specs that is running Ubuntu 12.10 installed through wubi.  

AMD Turion 1.8 GHz 64 bit processor
2 GB RAM

I am experiencing slowness when launching software (Chromium takes 15-20 seconds to load), installing software through the software center and loading the dash (super key).
 
Please help me determine if my laptop has the hardware needed to run Ubuntu well enough to be speedy and responsive.  Is the wubi installation the problem?  (I did install 12.04 by booting to the install disk but 12.04 was pretty sluggish as well.)

---

### Post by HiImTye on 2013-01-27
you're probably not using any accelerated graphics drivers. to check, run:
```
gksudo software-properties-gtk
```
then go to 'Additional Drivers'

---

### Post by tejpatel98 on 2013-01-27
I had 12.10 on my Core i3 processor and 4gb of ram laptop and was also experiencing sluggish response. I switched over to 12.04LTS and most of the sluggish movements went away, but I also have a Windows partition, and also used wubi to install the partition.

---

### Post by woodensoul on 2013-01-27
> **HiImTye said:**
> you're probably not using any accelerated graphics drivers. to check, run:
```
gksudo software-properties-gtk
```
then go to 'Additional Drivers'

Right. I have just 1 "additional" driver in use and it's for my wireless. Now- How to find & install the accelerated graphics driver...

Searching the forums for my issue, I've been looking into installing an accelerated graphics driver... I have ATI radeon xpress 200m 5955.

---

### Post by mastablasta on 2013-01-28
> **woodensoul said:**
> I have ATI radeon xpress 200m 5955.
 
i wanted to ask you the chip.... but i saw when i read down that you posted it.
 
anyway, it is causign you  problems as AMD dropped support for linux for this card. so you are stuck with reverse engineered opensource drivers. which are a hit and miss. they work great with some cards while others have lag and other issues.
 
since Unity is 3D i suggest you try XFCE (Xubuntu) or perhaps even KDE (Kubuntu). they and desktop environemtns and both render desktop  differently than default Gnome. you might even try Lubuntu (LXDE). XFCE and LXDE are not 3D accelerated desktops by default. so they should work a bit faster on you setup. you just won't have so many special effects.
 
if you want to stick with unity you can try 12.04 and then install and use unity 2D. it should also speed up the things.

---

