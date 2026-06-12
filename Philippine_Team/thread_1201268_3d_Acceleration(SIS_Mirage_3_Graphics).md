---
title: "3d Acceleration(SIS Mirage 3 Graphics)"
date: 2009-06-30
forum: Philippine Team
---

### Post by Lila_IT_CMU on 2009-06-30
Paano po ba i-enable yung 3d Acceleration sa SIS mirage 3 grphics card??? does it need any driver???

---

### Post by kiminaiseah on 2009-07-01
try the ff: in console or terminal under root login account 

$sudo su -

1st. backup xorg.conf
$cp /etc/X11/xorg.conf ~/xorg.conf.bak

then

$dpkg-reconfigure -phigh xserver-xorg

then 

$/etc/init.d/gdm stop && /etc/init.d/gdm start

then pag nag fail, 

$cp ~/xorg.conf.bak /etc/X11/xorg.conf

$/etc/init.d/gdm stop && /etc/init.d/gdm start

and kung hindi mag fail, check mo kung may kakaibang enhancement sa desktop u D:

---

### Post by guitar_man on 2009-07-01
Laptop ba to???



try mo muna punta sa system >> preference >> Hardware Drivers



pero ayon sa mga usapan sa net hindi gagana ang 3D,,hangang 2D lang

---

### Post by Script Warlock on 2009-07-01
[URL="http://forlong.blogage.de/entries/pages/Compiz-Check"]:p
[/URL]

---

### Post by Lila_IT_CMU on 2009-07-03
yes, this is a laptop, NEO basic

---

### Post by Script Warlock on 2009-07-03
desktop fx lang ang di ko na try sa laptop ng kaibigan(boss) ko buti na lang may driver na ang SIS para sa ubuntu..3daceleration is it also about compiz?.

---

### Post by loell on 2009-07-03
> **Lila_IT_CMU said:**
> does it need any driver???

3d acceleration won't work with this card, in linux :(

---

### Post by synco on 2010-10-26
so there's no 3d acceleration for this video card?

---

### Post by oobermensch on 2010-10-26
Probably not. This is actually a very old graphics chip. It doesn't even have vertex shaders. :O If you did a fresh install of Ubuntu on your computer, I think it would automatically use the best, open source drivers. And if you can't change the effects, chances are, you'll be stuck with an effect-less desktop. :(

I could be wrong though.

---

### Post by JCyberinux on 2010-10-26
kindly visit this thread > [http://newyork.ubuntuforums.org/showthread.php?t=886463&page=12](http://newyork.ubuntuforums.org/showthread.php?t=886463&page=12)

i think they having a discussion on video card in SIS. just let us know if that helps. :)

---

