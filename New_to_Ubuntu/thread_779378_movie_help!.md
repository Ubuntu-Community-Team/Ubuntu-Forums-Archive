---
title: "movie help!"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by b_d on 2008-05-02
i have tried using Mplayer,Totem, and vlc and none of these players will run my 100+ movies from the great aXXo (all hail aXXo) these movies are all in .avi format but yet have anime in .avi that works fine. any help at all would be greatly appreciated. I was hoping it would be a simple codec pack to install through terminal but none i have installed seem to be making any difference at all.  plz help! :D  ty

---

### Post by Ender305 on 2008-05-02
I think totem uses the gstreamer libraries, so just enable(if you haven't alredy) "gstreamer0.10-ffmpeg"

---

### Post by Oldsoldier2003 on 2008-05-02
> **b_d said:**
> i have tried using Mplayer,Totem, and vlc and none of these players will run my 100+ movies from the great aXXo (all hail aXXo) these movies are all in .avi format but yet have anime in .avi that works fine. any help at all would be greatly appreciated. I was hoping it would be a simple codec pack to install through terminal but none i have installed seem to be making any difference at all.  plz help! :D  ty

have you installed the restricted codecs?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Oldsoldier2003 on 2008-05-02
> **Ender305 said:**
> I think totem uses the gstreamer libraries, so just enable(if you haven't alredy) "gstreamer0.10-ffmpeg"

if this is the case he might also want the gstreamer good bad and ugly plugins from the multiverse repo

---

### Post by MattBD on 2008-05-02
Might also need to run the libdvdread3 script after installing ubuntu-restricted-extras. I still had to install this in Kubuntu Hardy:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by b_d on 2008-05-02
thanx guys .. but how do i di all this lol ... i got the restricted extras .. but have no idea on how to go about getting all that other stuff

---

### Post by Happy_Man on 2008-05-02
If you got the extras package installed, that's all you should need. Try opening one of the movies again. If memory serves, aXXo uses .avi, so gstreamer-ffmpeg (which you installed) should be all you need.

---

### Post by Bubba64 on 2008-05-02
Add remove in applications has multiple gstreamer downloads if needed personally I installed all of them, in lieu of just having anything needed at any time.

---

### Post by b_d on 2008-05-02
thanx :) could i get a total noobs guide on how to aquire these things? try to explain it like ur talkin to a complete and total idiot lol.

---

### Post by Bubba64 on 2008-05-03
> **b_d said:**
> thanx :) could i get a total noobs guide on how to aquire these things? try to explain it like ur talkin to a complete and total idiot lol.

I am not sure who your talking to but to get the gstreamer stuff easily click on application top left corner then open up add remove at the bottom of the drop down the enable all available packages in drop down on towards top left side then type gstreamer in search tick what ever ones you think are applicable, I use all of them, probably more than I need but I only know so much hit install also you can install vlc it might be in the gstreamer list if not after marking the gstreamers type vlc in search tick on that and install all at once. As tme goes on you will learn how to use the synaptic package manager in system-administration. then you will learn how to usethe terminal if you want to.

---

### Post by iSplicer on 2008-05-03
And why would a pirate like you want to use free software?

---

### Post by b_d on 2008-05-03
errrr....is that a trick question?   lol

i dont consider myself a pirate.. i just think the ultimate stupidity is paying for anything that u can get away with not paying for.

---

### Post by Bubba64 on 2008-05-03
> **iSplicer said:**
> And why would a pirate like you want to use free software?

Thus spoke the Parrot not the raven Raaack Nevermore, Nevermore. Oh Lenore oh Lenore.

---

### Post by Ender305 on 2008-05-03
hooray for pirating and if you haven't already, to install the .avi codecs just type ```
sudo apt-get install gstreamer0.10-ffmpeg
```

---

### Post by b_d on 2008-05-04
ya iv done all that :( still cant get any of my movies to play. starting to get a little frustrated. the other few problems i had after the switch over to hardy were resolved in a few days through these forums. This one is giving me hell. iv been at it for days Googling and posting here and here with no luck. not sure what could be wrong.. all my anime works great and there all in AVI. but my AVI movies will not work...i am using vlc,kaffine,Mplayer,totem,xine. i even tried vlc in wine ...

thanx to all of u who tried to help :D if anyone comes up with anything i would sure appreciate it if u let me know.

---

### Post by SunnyRabbiera on 2008-05-04
hmm, well you can try the win32 codecs.
you can get them with medibuntu:
[try it]("https://help.ubuntu.com/community/Medibuntu")

if you need to know how to install things use this guide:
[here]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Happy_Man on 2008-05-04
> **b_d said:**
> ya iv done all that :( still cant get any of my movies to play. starting to get a little frustrated. the other few problems i had after the switch over to hardy were resolved in a few days through these forums. This one is giving me hell. iv been at it for days Googling and posting here and here with no luck. not sure what could be wrong.. all my anime works great and there all in AVI. but my AVI movies will not work...i am using vlc,kaffine,Mplayer,totem,xine. i even tried vlc in wine ...

thanx to all of u who tried to help :D if anyone comes up with anything i would sure appreciate it if u let me know.
Just an FYI: VLC is available for linux, with Ubuntu you can install it using ```
sudo apt-get install vlc
```

---

