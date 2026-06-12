---
title: "[SOLVED] what do you make of this dvd problem"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-01
I am trying to play a dvd. It's not copied it's just a rentel.

In vlc if I click on play from the menu it will get stuck at the FBI warning.

But if I select to play a specific chapter it will play just fine
Note: This is with all dvds that I have tested.

If I try to play a dvd in movie player I have a bad picture and will not allow me to jump to the DVD menu and I can not ff

I tried to install Mplayer but after install I cant find it.

I also don't want Mplayer to take over my full media experiance through firefox or what have you. I just want to play DVD's flawlessly.

I have all restricted driver installed and I have the medibutu repos.

Any suggestions?

I am running intrepid

---

### Post by fr.theo on 2008-12-01
I have the same problem and I some times switch between players to get a certain DVD to work but I found that xine movie player works ok most of the time.


 VLC seems to work well when selecting a certain scene on the DVD but I always have a problem playing the full DVD Flawlessly as you do. I found this to be the case also in windows xp, VLC does have problems as well, even media player has problems playing certain DVD's.


try to update your players, make sure they are the latest release. 


Sorry if I am not much help.

---

### Post by kpkeerthi on 2008-12-01
> **nakama85 said:**
> 

I tried to install Mplayer but after install I cant find it.

It should be under Applications -> Sound / Video. If you can't find it
Open a terminal and type 
```
gmplayer
```

> **nakama85 said:**
> 
I also don't want Mplayer to take over my full media experiance through firefox or what have you. I just want to play DVD's flawlessly.

mplayer will not take over your firefox. It comes in a separate package **mozilla-mplayer**.

---

### Post by kpkeerthi on 2008-12-01
Try gxine

[http://www.ubuntugeek.com/install-xine-multimedia-player-in-ubuntu.html](http://www.ubuntugeek.com/install-xine-multimedia-player-in-ubuntu.html)

---

### Post by SunnyRabbiera on 2008-12-01
do you have libdvdcss?

---

### Post by nakama85 on 2008-12-01
> **SunnyRabbiera said:**
> do you have libdvdcss?

yes i already have it installed.

I will give xine and mplayer a try.
thanks for the advice guys

---

