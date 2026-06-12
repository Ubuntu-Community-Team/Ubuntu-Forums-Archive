---
title: "hack tweak regionset (DVD region)"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by aktiwers on 2008-06-27
Hey all,

Just installed Ubuntu on my sisters laptop. I hoped there was a way to hack/tweak the region code of the dvd drive firmware. She has both DVDs from USA and EUROPE and we want to be able to play them all.

It seams like most hardware vendors put at 5 times limit if you change the region code with apps like regionset.

Anyway to get around this?

---

### Post by bred on 2008-06-27
> **aktiwers said:**
> Hey all,

Just installed Ubuntu on my sisters laptop. I hoped there was a way to hack/tweak the region code of the dvd drive firmware. She has both DVDs from USA and EUROPE and we want to be able to play them all.

It seams like most hardware vendors put at 5 times limit if you change the region code with apps like regionset.

Anyway to get around this?


[COLOR="Navy"]I would recommend vlc for that. It's in the repos.

**sudo apt-get vlc**

cheers

A.[/COLOR]

---

### Post by aktiwers on 2008-06-27
I am already using VLC...  how would I do that with VLC?

---

### Post by bred on 2008-06-27
[COLOR="Navy"]sorry my mistake with VLC,

In oder to play my dvd's UE or US I use Totem Movie Player

this thread helped me with dvds

[https://help.ubuntu.com/8.04/musicvideophotos/C/video.html#video-dvd]("https://help.ubuntu.com/8.04/musicvideophotos/C/video.html#video-dvd")

hope it will help u

 [/COLOR]

---

### Post by forger on 2008-06-27
Grab some popcorn :popcorn:

Since you have already played with region setting on your dvd drive, you can't use totem or any media player to play the dvd directly.
I'm not really sure, but you probably can rip the dvd in order to play it (**thoggen** from the Applications > Add/Remove is really easy to rip/encode a movie; Or you could try **k9copy**) - read more about ripping here:
[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

Ok, that being said, close all of your media players.

You probably need some extra software packages, you need to install the [www.medibuntu.org](www.medibuntu.org) repository:
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)
(Don't forget to do the step to **add the GPG key** for the repository!!)

After that, do the following in gnome-terminal:
```
sudo apt-get update
sudo apt-get install libdvdcss2 libdvdread3 mplayer
```

If it's 32-bit Ubuntu you are using, you could also install some extra codecs:
```
sudo apt-get install w32codecs
```
..or if it's 64-bit Ubuntu:
```
sudo apt-get install w64codecs
```

Now try to play the dvd from totem (default gnome "movie player"), or from mplayer (Applications > sound&video > mplayer > right-click > open > play dvd

If it doesn't work, try to rip it to your hard disk and then play it.

---

### Post by aktiwers on 2008-06-27
Thanks guys!

I had already installed the stuff from medibuntu, but I think I was missing some libs.

Now it works great! Thanks!

---

### Post by forger on 2008-06-28
You could play it after all?  Didn't rip it? Cool! :)

---

### Post by aktiwers on 2008-06-28
Yeah..  I think maybe the :
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

From the link did the trick, and that I installed some libs I didn't have. 

heh..  this seamed to be impossible on Vista, and she was only allowed to change the region 3 times there.

---

### Post by forger on 2008-06-28
ah on windows you have another solution, [anydvd]("http://www.anydvd.com")

---

### Post by aktiwers on 2008-06-28
> **forger said:**
> ah on windows you have another solution, [anydvd]("http://www.anydvd.com")

EUR 49.00 :^o
hehe..  she is pretty happy with Ubuntu so fare :)

---

