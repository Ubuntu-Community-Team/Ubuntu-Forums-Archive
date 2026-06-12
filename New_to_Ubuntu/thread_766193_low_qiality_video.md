---
title: "low qiality video"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Primefalcon on 2008-04-25
I just upgraded to 8.04 version of Ubuntu

I went to play a dvd movie in it tonight, and found appallingly all the color was messed up, i said to go to default, it seems to have fixed the color balance somewhat. though still a little messed up.

and its also running very low quality with lines and such.

I'm sure theres an easy way to fix this, but since I'm still rather new to ubuntu, any help would be appreciated, thank you

---

### Post by Saya on 2008-04-25
Try disabling the desktop effects if you haven't already. System -> Preferences -> Appearence -> Visual Effects -> None.
If that isn't it, what media player and what video output are you using?

---

### Post by Primefalcon on 2008-04-25
I already have the desktop effects disabled though I have a fast computer.

I am using the default player:

Totem Movie Player 2.22.1
Movie Player using xine-lib version 1.1.11.1 and GNOME

---

### Post by Saya on 2008-04-25
I don't use Totem, sorry. If you're willing to use a different and in my opinion better media player, do this:

- [https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

- Pick your distribution and add the Medibuntu repository along with its GPG key.

- Open a terminal and do sudo apt-get install mplayer.

Then you'll find it in Applications -> Sound & Video > MPlayer Movie Player. It is much more configurable.

---

### Post by Primefalcon on 2008-04-25
Thx it seems your right while I was waiting for a reply, I tried vlc, which works very good, just not sure how to change to my usb headphones like I can with totem, yoh well.

Thx for your help, why do they make totem the default I wonder when the quality isn't up to scratch

---

### Post by Xiong Chiamiov on 2008-04-25
> **Primefalcon said:**
> Thx it seems your right while I was waiting for a reply, I tried vlc, which works very good, just not sure how to change to my usb headphones like I can with totem, yoh well.

Thx for your help, why do they make totem the default I wonder when the quality isn't up to scratch
You got USB headphones working?  Lucky dog.

---

### Post by SunnyRabbiera on 2008-04-25
> **Primefalcon said:**
> Thx it seems your right while I was waiting for a reply, I tried vlc, which works very good, just not sure how to change to my usb headphones like I can with totem, yoh well.

Thx for your help, why do they make totem the default I wonder when the quality isn't up to scratch

actually the quality can be adjusted easily in totem, but xine beats both mplayer and totem for DVD playing in my opinion :D

---

