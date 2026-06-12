---
title: "[SOLVED] totem will not play avi movies"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by workshop1702 on 2008-07-09
hi can someone please tell me how to get totem to play avi have tried the totem xin but still wont play them. any help would be much appreciated . Thanks Andrew:confused:

---

### Post by sayakb on 2008-07-09
At a terminal
```
sudo apt-get install ubuntu-restricted-extras
```
Reboot and try again..

---

### Post by sujoy on 2008-07-09
> **workshop1702 said:**
> hi can someone please tell me how to get totem to play avi have tried the totem xin but still wont play them. any help would be much appreciated . Thanks Andrew:confused:

well the first time you try to play avi files, it would ask you to install the codecs, so do that.

in case it doesn't, search in synaptic for gstreamer codecs and install them.

---

### Post by Darkchef on 2008-07-09
> **workshop1702 said:**
> hi can someone please tell me how to get totem to play avi have tried the totem xin but still wont play them. any help would be much appreciated . Thanks Andrew:confused:

Download VLC, that should take care of it

```

sudo apt-get update
sudo apt-get install vlc

```

---

### Post by muteXe on 2008-07-09
How the hell will installing vlc help him play avi's in totem?

---

### Post by workshop1702 on 2008-07-09
tried all your suggestions still no luck wont play avi. andrew

---

### Post by apostate on 2008-07-09
Make sure you installed ubuntu-restricted-extras for good measure.

Then change the backend of your totem by installing totem-xine. This may ask to install a few other things, and uninstall totem-gstreamer. That is ok, you can switch it back at *any time*.

Reboot, or log out/in, and try to play an .avi. It plays 'em, I assure you. We'll figure it out...

---

### Post by tjwoosta on 2008-07-09
i know on my computer i cant use totem (dont know why)

but what i had to do to watch movies is use mplayer

---

### Post by kostkon on 2008-07-09
Also, if you want, you can install the Windows codecs package that is offered by the [*Medibuntu* repository]("http://medibuntu.org/"), called *w32codecs*.

---

### Post by tjwoosta on 2008-07-09
> Also, if you want, you can install the Windows codecs package that is offered by the Medibuntu repository, called w32codecs. 

just so theres no confusion

if you are using 64bit ubuntu you would need w64codecs not w32codecs

---

### Post by kostkon on 2008-07-09
> **tjwoosta said:**
> just so theres no confusion

if you are using 64bit ubuntu you would need w64codecs not w32codecs
Good point! I always forget to specify this.

---

### Post by workshop1702 on 2008-07-09
have installed gzine looks good have managed to play one avi movie the other downloads wont play , they have divx or xvid before the avi in there file description , dont know if this means something or not maybe it will help, any more suggestions please. Thanks Andrew

---

### Post by tjwoosta on 2008-07-09
divx and xvid require the w32codecs

first enable medibuntu (everything is here)
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

then 

```
sudo apt-get install w32codecs
``` (w64codecs for 64bit ubuntu)

that should cover about ever single codec you can think of

---

### Post by workshop1702 on 2008-07-10
thanks for the help , have done all of the suggestions have installed all the codecs suggested , affraid no change still will not play the divx avi movies.has anyone got any of these players to work with these i have gxine and vlc which seem to be nice players i dont like mplayerat allso wont use it.any more help please. Thanks Andrew

---

