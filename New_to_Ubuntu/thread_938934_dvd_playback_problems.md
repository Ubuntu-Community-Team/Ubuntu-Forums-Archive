---
title: "dvd playback problems"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Periswell on 2008-10-05
hello everyone

after the first episode of the 3rd season of heroes (yes its only just come out over here in britain) i wanted to catch up and watch the 1st season so i put in the dvd and it does not work as it is a fresh install of ubuntu so it has no plug-ins. after a quick google search i found and followed the instructions which go like this:
> sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3
> sudo /usr/share/doc/libdvdread3/install-css.sh
but when i open mplayer, it only plays the opening sequence of the universal name orbiting the earth and thats it and i can access the menus. only vlc uses the menus but id rather not use it. also i wanted to watch it in Elisa but it does the same as mplayer does. help please.

-joshua

---

### Post by SuperSonic4 on 2008-10-05
wibble :p

on topic: I know in VLC if you go to open -> disc you can bypass the menus by selecting a specific title (usually t=0, c=0, a=0, s=-1 or 0)

---

### Post by Periswell on 2008-10-05
brillinatly on topic but not what im looking for
-joshua

---

### Post by Periswell on 2008-10-05
sorry to be a bit hasty but i need it for about an hour as some friends of the family are coming round and this laptop is the only dvd player in the house.

---

### Post by billgoldberg on 2008-10-05
> **Periswell said:**
> sorry to be a bit hasty but i need it for about an hour as some friends of the family are coming round and this laptop is the only dvd player in the house.

I use this command to install all my codecs and it can play all dvd's I tossed at it:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

I use Totem to play it (or vlc).

---

### Post by Periswell on 2008-10-05
dvd playback still does not work in elisa
-joshua

---

