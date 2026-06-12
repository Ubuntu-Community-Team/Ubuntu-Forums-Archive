---
title: "Desktop not running smoothly"
date: 2009-09-08
forum: Philippine Team
---

### Post by Lila_IT_CMU on 2009-09-08
good day. paano po ba para maalis ang mga lines? pag nag minimize ako ng window may naiiwan na mga lines eh...parang nadedelay ang mga lines pag iminimize ko ung mga window pero...pangit kasi tingnan...

---

### Post by pendletone on 2009-09-08
naka-disable ba ang visual effects mo? if yes, meron talagang black lines na magdi-display briefly pag nag-minimize ka ng windows. don't worry, it's perfectly normal.

---

### Post by Lila_IT_CMU on 2009-09-09
> **pendletone said:**
> naka-disable ba ang visual effects mo? if yes, meron talagang black lines na magdi-display briefly pag nag-minimize ka ng windows. don't worry, it's perfectly normal.


 my video card is SIS Mirage 3. yes nakadisable na ung visual effects...sinubukan ko sa ubuntu 8.10 at 8.04 wala naman black lines a naiiwan pag nag minimize ako...only in ubuntu 9.04...

---

### Post by guitar_man on 2009-09-09
Alam ko din nromal lang yan...kahit sa fedora ganyan din..

---

### Post by Script Warlock on 2009-09-09
not the normal thing kung ang specs ng video mo is higher... f5 mo lang muna desktop

check mo cguro kung sino ang pinakamaliking kumain ng resources at kung yun ba ang dahilan or there might be something else ang problema.. sabi mo kc not on 8.04 and 8.10

---

### Post by badrra on 2009-09-09
gamitan mo kaya ng compiz

---

### Post by Lila_IT_CMU on 2009-09-09
> **badrra said:**
> gamitan mo kaya ng compiz

paano ba gamitin yan? idodownload pa ba yan?

---

### Post by wersdaluv on 2009-09-09
May ganon talaga. Effect 'yon ng metacity. 'Di ko lang alam kung gaano kabagal yung effect sa'yo. Baka naman mabagal siya mag-appear at mawala kaya mukhang hindi smooth. 

According to aysiu:
Alt-F2
Code:

gconf-editor

Apps > Metacity > General > Reduced Resources

enable Assistive Technology Support in System > Preferences.

---

### Post by Lila_IT_CMU on 2009-09-09
> **wersdaluv said:**
> May ganon talaga. Effect 'yon ng metacity. 'Di ko lang alam kung gaano kabagal yung effect sa'yo. Baka naman mabagal siya mag-appear at mawala kaya mukhang hindi smooth. 

According to aysiu:
Alt-F2
Code:

gconf-editor

Apps > Metacity > General > Reduced Resources

enable Assistive Technology Support in System > Preferences.

mabagal nga sya mag appear..
nagawa ko na yan reduced resources...nagtataka lng ako kung bakit sa jaunty lng xa ganun. sa 8.10 at 8.04 hindi naman....kung pwede lng sana ilipat ung desktop ng 8.10 sa 9.04 ginawa ko na hehehe

---

### Post by wersdaluv on 2009-09-09
Intel video card?

---

### Post by perbiu on 2009-09-09
If you have the same neo laptop with SiS 771/671 Mirage 3 video card, then you can use this driver [http://www.zshare.net/download/63891757263e27ec/](http://www.zshare.net/download/63891757263e27ec/)
But this will only give you resolution and 2D acceleration to avoid scrolling from chopping. No 3D acceleration yet so no desktop effects. We are still knocking on SiS doors to release a driver which they said they will but as of now they haven't.

---

### Post by Lila_IT_CMU on 2009-09-09
> **perbiu said:**
> If you have the same neo laptop with SiS 771/671 Mirage 3 video card, then you can use this driver [http://www.zshare.net/download/63891757263e27ec/](http://www.zshare.net/download/63891757263e27ec/)
But this will only give you resolution and 2D acceleration to avoid scrolling from chopping. No 3D acceleration yet so no desktop effects. We are still knocking on SiS doors to release a driver which they said they will but as of now they haven't.

yes my laptop is NEO with SIS 671 v-card
thanks...

---

