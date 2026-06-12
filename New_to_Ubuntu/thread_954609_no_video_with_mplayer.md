---
title: "no video with mplayer"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-10-21
I only get audio and no video with mplayer plug in for firefox.

Any suggestions on how to get video?

---

### Post by tjwoosta on 2008-10-21
do you have all the right codecs?

first do

```
sudo apt-get install ubuntu-restricted-extras
```

that should give you some of the codecs


if it still doesnt work, then you will probably need to install the w32 codecs (w64codecs for 64bit ubuntu)

for that you will need to enable the medibuntu repository

theres a guide here
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

after enabling the reopository do this

```
sudo apt-get update
```
```
sudo apt-get install w32codecs
``` (substitute w64codecs if you have 64bit Ubuntu)

now with all of those codecs you whould be able to play almost anyting that comes your way without issues

---

### Post by saskatchewan on 2008-10-21
I still get no video

It keeps saying that I have two upgrades but when I go to install them it will not let me.

---

### Post by tjwoosta on 2008-10-21
> It keeps saying that I have two upgrades but when I go to install them it will not let me. 
what is the error it gives you?

> I still get no video

run mplayer in a terminal and see what the output is when it is playing

(the more info you post the better your chances of finding an answer)

one other thing the problem could be, is the video output of mplayer

i know i had to set my default video output to x11 before i could get a picture

the easiest way to change the video output with mplayer is just to install GNOME-MPlayer

(its just a simple GNOME frontend for MPlayer)

but after installing it, you just start gnome-mplayer and in the preferences you can change the default video output to x11

---

