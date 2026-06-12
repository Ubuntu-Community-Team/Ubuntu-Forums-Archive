---
title: "Video Problems"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by bull205 on 2008-10-19
When I put in a DVD, boot up Totem Movie Player it tells me 

AN ERROR OCCURED
COULD NOT READ FROM RESOURCE

Also, I am unable to watch trailers from Apple's website.  It streams the buffer, but when it begins to "show" the preview, it plays the audio, but all i see is the text filename of the temp file in the video player.  I am using firefox. I am running a Sony Vaio on 8.10.  And the video resolution is 800x600 generic because I am not able to find the Intel Mobile 4/Cantiga drivers.

Um....help!  All i want to do is watch some movies:popcorn:

---

### Post by tjwoosta on 2008-10-19
i have also had many issues with totem

you could try just installing the restricted extras

```
sudo apt-get install ubuntu-restricted-extras
```

also you could install the w32 codecs  (w64 codecs if you have 64bit ubuntu)

for those codecs you would have to enable the medibuntu repository
(here is a guide)
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

after enabling medibuntu repository do this to install the codecs
(remember to substitute w64codecs if you have 64bit Ubuntu)
```
sudo apt-get update
```
then
```
sudo apt-get install w32codecs
```

but i never had any luck with totem anyway

i installed GNOME MPlayer and ever since everything has just worked

i highly recommend it   
(you would still need all of those codecs with GNOME MPlayer, but if totem still doesn't work after installing the codecs then you should definatly try it)


first you would remove the totem firefox plugin

```
sudo apt-get remove totem-mozilla
```

then install GNOME MPlayer and the firefox plugin for MPlayer

```
sudo apt-get install gnome-mplayer
```

```
sudo apt-get install mozilla-mplayer
```


now if GNOME MPlayer is giving you issues where the screen turns blue when you move the window, you can change the video output in the preferences (i use X11)

after all of this hassle, you should be able to play your dvd and watch the trailers on apples website :)

---

### Post by bull205 on 2008-10-19
did all that, when i put in the movie, it said nautilus crashed and asked me to submit a report.  Also, still can't watch apple trailers.  I still see only text in the movie box.  any other ideas?

---

### Post by Potts on 2008-10-20
> **bull205 said:**
> When I put in a DVD, boot up Totem Movie Player it tells me 

AN ERROR OCCURED
COULD NOT READ FROM RESOURCE

Also, I am unable to watch trailers from Apple's website.  It streams the buffer, but when it begins to "show" the preview, it plays the audio, but all i see is the text filename of the temp file in the video player.  I am using firefox. I am running a Sony Vaio on 8.10.  And the video resolution is 800x600 generic because I am not able to find the Intel Mobile 4/Cantiga drivers.

Um....help!  All i want to do is watch some movies:popcorn:


I have the same problem and also did what was suggested and this didn't work.

---

### Post by stephanvaningen on 2008-10-20
> **bull205 said:**
> When I put in a DVD, boot up Totem Movie Player it tells me 

AN ERROR OCCURED
COULD NOT READ FROM RESOURCE

Also, I am unable to watch trailers from Apple's website.  It streams the buffer, but when it begins to "show" the preview, it plays the audio, but all i see is the text filename of the temp file in the video player.  I am using firefox. I am running a Sony Vaio on 8.10.  And the video resolution is 800x600 generic because I am not able to find the Intel Mobile 4/Cantiga drivers.

Um....help!  All i want to do is watch some movies:popcorn:

Which distro do you have installed? 32 or 64-bit's Ubuntu?

---

### Post by bull205 on 2008-10-21
32bit

---

