---
title: "Audio only media players"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by nnjond on 2008-06-20
Hi, can anyone help me?

I have installed 3 media players: GNOME MPlayer, Movie Player, and MPlayer. None of them show the video aspect of my files; .avi, dvx, vob, nor can I see the DVDs I play? I can watch videos on Utube etc?

---

### Post by avtolle on 2008-06-20
Try installing ubuntu-restricted-extras from Synaptic (or from Add/Remove).

---

### Post by tjwoosta on 2008-06-20
umm... all the media players you mentioned should play videos for you

you probably have to install the right codecs

open a terminal and do this 
```
sudo apt-get install ubuntu-restriced-extras
```

then you may also need some codecs that are only availabe in the medibuntu repository

you would have to add the medibuntu repository to the sources list

here is a guide[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

after adding medibuntu do this
```
sudo apt-get update
```
then 
```
sudo apt-get install w32codecs
```
(if using 64bit ubuntu it should be w64codecs instead)

and lastly for youtube videos you will need to install flash (i think the ubuntu-restricted-extras should have taken care of that for you though)

---

### Post by anjilslaire on 2008-06-20
Also, give vlc a try...

---

### Post by Sef on 2008-06-20
> sudo apt-get install ubuntu-restriced-extras

That should be

```
sudo apt-get install ubuntu-restricted-extras
```

Also read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by abn91c on 2008-06-20
try using Kaffeine

---

### Post by tjwoosta on 2008-06-20
> 
That should be

Code:

sudo apt-get install ubuntu-restricted-extras



hah, nice,  i didnt even notice the missing t

---

### Post by nnjond on 2008-06-20
Thanks I think the prob is solved.

---

