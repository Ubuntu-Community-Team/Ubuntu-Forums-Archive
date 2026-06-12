---
title: "Help on installation"
date: 2009-06-22
forum: Philippine Team
---

### Post by guitar_man on 2009-06-22
mga sir alam kong medoyo out of topic to pero kailangan ko lang ng tulong sa pag-install...
Pano ko ba install ito [http://www.t3-i.com/ncdgames/eof15src.zip]("http://www.t3-i.com/ncdgames/eof15src.zip")

editor to ng kanta sa frets on fire,gumagana kasi yung sa windows pero ito hindi ko mapagana..kailangan ko kasi mag-edit ng kanta at magpa-free play kami sa isang event ng org namin...

---

### Post by guitar_man on 2009-06-22
Any Help???:(

---

### Post by loell on 2009-06-22
assuming that you have install the ubuntu development package,
you also have to install **liballegro4.2-dev**

then do a **make** command

**eof** will be located on **/bin**

---

### Post by ismoke101 on 2009-06-23
> **guitar_man said:**
> mga sir alam kong medoyo out of topic to pero kailangan ko lang ng tulong sa pag-install...
Pano ko ba install ito [http://www.t3-i.com/ncdgames/eof15src.zip]("http://www.t3-i.com/ncdgames/eof15src.zip")

editor to ng kanta sa frets on fire,gumagana kasi yung sa windows pero ito hindi ko mapagana..kailangan ko kasi mag-edit ng kanta at magpa-free play kami sa isang event ng org namin...

hindi kasi magandang idea yung pag compile ng program, baka di pa supported ng mga developers mismo, try mo gumamit ng wine kasi nakita ko dun sa site e merong windows installer :popcorn:

---

### Post by guitar_man on 2009-06-23
> **loell said:**
> assuming that you have install the ubuntu development package,
you also have to install **liballegro4.2-dev**

then do a **make** command

**eof** will be located on **/bin**

sir nainstall ko yung allegro...

tapos nag-**make** na din 
pero ito lumalabas...

---

### Post by guitar_man on 2009-06-23
> **ismoke101 said:**
> hindi kasi magandang idea yung pag compile ng program, baka di pa supported ng mga developers mismo, try mo gumamit ng wine kasi nakita ko dun sa site e merong windows installer :popcorn:

gumana nga po yun window version sa wine pero medyo mabagal.

---

### Post by loell on 2009-06-23
> **guitar_man said:**
> sir nainstall ko yung allegro...

tapos nag-**make** na din 
pero ito lumalabas...


i'm not really sure how to fix that, maybe switch to ALSA if it can't output sound through pulseaudio.

---

### Post by guitar_man on 2009-06-26
> **loell said:**
> i'm not really sure how to fix that, maybe switch to ALSA if it can't output sound through pulseaudio.

boss loell pano ko switch yun from pulseaudio to alsa??

---

