---
title: "Problems with Movie Player"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by hAvAAck on 2008-07-21
Somehow my Movie Player settings got screwed up (hue, contrast, etc) and "reset to defaults" gives everything a hard blue tint. I wanted to try to reinstall it, but I can't apt-get remove it or find it in synaptic. I don't know what settings it does require so I can't manually fix it either. Does anyone know how I can go about fixing it?

I'm trying hard to become a complete convert but little things keep tripping me up :lol:

---

### Post by dracayr on 2008-07-21
the package is called totem (not movieplayer) so:

sudo apt-get remove --purge totem

If nothing helps, you can still use the vlc media player

dracayr

---

### Post by hAvAAck on 2008-07-21
Thanks
so I used these two commands
```
sudo apt-get remove --purge totem
```
```
sudo apt-get install totem
```
And I still have the blue tint problem. I installed VLC when this happened so I could watch movies, but for instance, firefox still uses it for some streaming, etc. Any other ideas on how to fix it?

---

### Post by sisco311 on 2008-07-21
Also try to rename the config files and force totem
to create new config files with the default settings:
```
mv ~/.gnome2/totem_config ~/.gnome2/totem_config-old
```and/or
```
mv ~/.gnome2/totem ./.gnome2/totem-old
```
restart the movie player.

to restore the old settings:
```
mv ~/.gnome2/totem_config-old ~/.gnome2/totem_config
``````
mv ~/.gnome2/totem-old ./.gnome2/totem
```

---

### Post by hAvAAck on 2008-07-21
That seems like a great idea, however I get
```
ray@ray-ubuntu:~$ mv ~/.gnome2/totem_config ~/.gnome2/totem_config-old
**mv: cannot stat `/home/ray/.gnome2/totem_config': No such file or directory**
ray@ray-ubuntu:~$ mv ~/.gnome2/totem ./.gnome2/totem-old
**mv: cannot stat `/home/ray/.gnome2/totem': No such file or directory**
ray@ray-ubuntu:~$ 

```

---

### Post by sisco311 on 2008-07-21
> **hAvAAck said:**
> firefox still uses it for some streaming, etc. Any other ideas on how to fix it?
```
sudo aptitude install  mozilla-plugin-vlc
```
or
```
sudo aptitude install mozilla-mplayer
```

---

### Post by sisco311 on 2008-07-21
> **hAvAAck said:**
> That seems like a great idea, however I get
```
ray@ray-ubuntu:~$ mv ~/.gnome2/totem_config ~/.gnome2/totem_config-old
**mv: cannot stat `/home/ray/.gnome2/totem_config': No such file or directory**
ray@ray-ubuntu:~$ mv ~/.gnome2/totem ./.gnome2/totem-old
**mv: cannot stat `/home/ray/.gnome2/totem': No such file or directory**
ray@ray-ubuntu:~$ 

```

Open your file browser and Press Ctrl+H to list hidden files.
Search for the totem config file/folder and rename it.
(I don't use gnome)

Totem is a frontend for xine or gstreamer???
Maybe search for xine or gstreamer.

---

### Post by hAvAAck on 2008-07-21
no Luck on that front, I went through all kinds of folders and I only found one file that was promising, renamed it, and when I loaded movie player it still had the weird blue.

---

### Post by dca on 2008-07-21
You can see if this is relative to your issues...
 
[https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373)

---

### Post by sisco311 on 2008-07-21
you can try to reinstall the codecs.
search in synaptic for the installed ones.
(vlc and mplayer uses theirs own codecs)

---

### Post by hAvAAck on 2008-07-21
> **dca said:**
> You can see if this is relative to your issues...
 
[https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373)

One of those solutions fixed the problem, but made it choppy and unusable, similar to one of the other users in the thread. I have a GeForce 8600gt so it might be the whole ATI thing

> **sisco311 said:**
> you can try to reinstall the codecs.
search in synaptic for the installed ones.
(vlc and mplayer uses theirs own codecs)

Ugh, I hate being a n00b. How would I find the codecs specific to mplayer?

---

### Post by sisco311 on 2008-07-21
no.no.
just search for codecs or codec.
(the codecs are for totem)

mplayer and vlc comes with their own built-in codecs.
you don't need to install extra codecs for vlc and mplayer.

---

### Post by hAvAAck on 2008-07-21
All right, so I reinstalled all of the codecs I could find (about 16 packs) and I still have the problem lol.
I installed that VLC FF plugin a while back too, so if worse comes to worst, I should be ok with just VLCplayer

---

