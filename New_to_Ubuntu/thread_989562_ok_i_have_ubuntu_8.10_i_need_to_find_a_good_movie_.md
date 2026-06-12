---
title: "ok i have ubuntu 8.10 i need to find a good movie player that works with my dvds"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by keith071482 on 2008-11-21
I have the movie player that comes with ubuntu 8.10 but its not working very well, any ideas on a diffrent movie player? thanks

---

### Post by SuperSonic4 on 2008-11-21
vlc

```
sudo apt-get install vlc
```

smplayer:

```
sudo apt-get install smplayer
```

---

### Post by taurus on 2008-11-21
VLC seems to be real good.  In fact, it has a version for windows too.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install vlc
```
You can now find it in Applications -> Sound & Video.

---

### Post by zenarcher on 2008-11-21
I guess, first off, I would ask if you have installed Medibuntu, so you can get the proprietary software you most likely need.

Here is how...open a terminal window, then:

To enable the Medibuntu repository, please do the following:

Import the repository:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

Import the gpg-key and update your package-list:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Having done this, I would go to Applications>Add/Remove and I would search for Ubuntu Restricted Extras and install that package.  That will give you all the codecs and such you will require to play many of your movies. 

This would be the first step.  Then, players are pretty much a matter of choice.  I like MPlayer, SMPlayer and VLC, but I'm sure many others will be able to make further suggestions.  You really need the Medibuntu Repository added first, as shown above.

Welcome and best wishes with your efforts!
zenarcher

---

### Post by AndyCooll on 2008-11-21
> **keith071482 said:**
> I have the movie player that comes with ubuntu 8.10 but its not working very well, any ideas on a diffrent movie player? thanks
When you say "not working very well", can you be a little more specific?

:cool:

---

### Post by steveneddy on 2008-11-21
Vlc

---

### Post by frankleeee on 2008-11-21
As a couple of poster suggest smplayer or vlc they are both in add remove. Install the medibuntu 1st

---

### Post by eternalnewbee on 2008-11-21
Vlc has always done the job for me, before 8.10, but I find myself using Totem player nowadays. Vlc's perfomance, for me, has gone down, while Totem's gone up.

---

### Post by Therion on 2008-11-21
Has anyone mentioned SMPlayer or maybe VLC?

---

### Post by redseventyseven on 2008-11-21
Totem Movie Player does the job for me, but make sure it's using the right engine. There are two engines you can use it with - xine and gstreamer. Xine is the one which works for me.

---

### Post by LowSky on 2008-11-21
medibuntu repos, then install libdvdcss2

all the instructions are here

---

### Post by rburkartjo on 2008-11-21
keith just my preference but i still like vlc the best/cheesemaker

---

