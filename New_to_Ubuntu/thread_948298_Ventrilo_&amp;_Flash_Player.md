---
title: "Ventrilo &amp; Flash Player"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Dessx on 2008-10-15
Hi guys i just installed ubuntu yesterday and i cant get flash player to work with firefox at all ive installed all the addons multiple times and even downloaded a few ones off the wineapps or whatever and i still cant figure out how to get it to work so much help would be very appreciated.

And also with ventrilo ive got the sound and voice working in it but when i dont have the ventrilo window opened i cant talk and ive downloaded the ventrilo-ctrl5.0 but i cant seem to figure out how to compile it again help would be much appreciated.

Thanks guys,

Dessx

---

### Post by eternalnewbee on 2008-10-15
> **Dessx said:**
> Hi guys i just installed ubuntu yesterday and i cant get flash player to work with firefox at all ive installed all the addons multiple times and even downloaded a few ones off the wineapps or whatever and i still cant figure out how to get it to work so much help would be very appreciated.

And also with ventrilo ive got the sound and voice working in it but when i dont have the ventrilo window opened i cant talk and ive downloaded the ventrilo-ctrl5.0 but i cant seem to figure out how to compile it again help would be much appreciated.

Thanks guys,

Dessx

Try this:
sudo apt-get install libflashsupport

---

### Post by Dacker on 2008-10-15
After you download flashplayer, to get rid of sound problem you install alsa within this command :

```
sudo aptitude install alsa-oss

sudo gedit /etc/firefox/firefoxrc
```



then you edit this line here:

```
FIREFOX_DSP=&#8221;aoss&#8221;
```

if the sound doesn't work yet let us know.....

---

### Post by SunnyRabbiera on 2008-10-15
also try the new .deb installer for flash too as provided on adobes website.

---

