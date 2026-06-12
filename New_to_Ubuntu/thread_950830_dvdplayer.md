---
title: "dvdplayer"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by rbee on 2008-10-17
I have a problen installing dvd player.  Can soneone steer me to a good dvd player (coprwrite) and installation?

---

### Post by Ryadt on 2008-10-17
You can try installing vlc```
sudo apt-get install vlc
```
Make sure that you get the medibuntu repos
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Dr Small on 2008-10-17
+1 for VLC

---

### Post by H.Callahan on 2008-10-17
> **Dr Small said:**
> +1 for VLC

+1 to that +1! :):)

---

### Post by ww711 on 2008-10-17
> **h.callahan said:**
> +1 to that +1! :):)
 +3

---

### Post by rbee on 2008-10-17
I added vlc using sud apt-get install vlc, tried medibuntu repos libdvdcss2 but get imprpoper command. HELP can someone direct me to the proper codecs/ command(s)

---

### Post by saj0577 on 2008-10-17
I tried this not long ago and looking at my temrinal history it seems this is the one for you.

```
sudo apt-get install vlc vlc-plugin-esd
```

Saj

---

### Post by oldos2er on 2008-10-17
> **rbee said:**
> I added vlc using sud apt-get install vlc, tried medibuntu repos libdvdcss2 but get imprpoper command. HELP can someone direct me to the proper codecs/ command(s)

 Assuming you've enabled Medibuntu properly, copy and paste this in a terminal:

sudo aptitude update && sudo aptitude install libdvdcss2

---

### Post by Aero-Z on 2008-10-17
I'm using Totem (xine). Works fine.

---

### Post by swoody on 2008-10-17
Ok, I got mine working from this little how-to here:
[http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html](http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html)

Thanks for the help guys! :D

---

