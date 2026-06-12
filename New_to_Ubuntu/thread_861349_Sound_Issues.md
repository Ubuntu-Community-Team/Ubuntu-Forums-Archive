---
title: "Sound Issues"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by BiohazardSteven on 2008-07-16
I just installed xubuntu and then ubuntu on top i'm using ubuntu And i'm having problems with my sound... it works in some programs like totem media player and I tired it on both ... Please help Thanks.

---

### Post by AOZ on 2008-07-16
So when does sound not work? RythmBox? firefox?

---

### Post by BiohazardSteven on 2008-07-16
Everything else perrty much doesn't work in skype firefox it works in pidgin internet messenger have not tired much else

---

### Post by AOZ on 2008-07-16
try going system>preferences>sound and runnig the tests. if the tests don't make any sound then make sure the devices are set to ALSA. WHat is your sound card by the way?

---

### Post by BiohazardSteven on 2008-07-16
The tests work its a USB headset

---

### Post by BiohazardSteven on 2008-07-16
C-Media USB headphone set (ALSA mixer)

---

### Post by BiohazardSteven on 2008-07-16
Also when looking at this in terminal it doesn't show


```
alsamixer
```




```
steven@steven-desktop:~$ alsamixer
ALSA lib confmisc.c:256:(snd_func_getenv) error getting field default
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_getenv returned error: Invalid argument
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: Invalid argument
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default

alsamixer: function snd_ctl_open failed for default: Invalid argument
steven@steven-desktop:~$ 

```

---

### Post by BiohazardSteven on 2008-07-16
Bump?

---

### Post by BiohazardSteven on 2008-07-16
HELP!@#@!#:confused::confused::confused::confused::confused::confused:

---

### Post by BiohazardSteven on 2008-07-21
..... wow no help ...

Pretty helpful community we have here don't we?

---

### Post by Raistlin82 on 2008-07-21
you could try to re-install alsa mixer, its in synaptic if you have a look for it, check that nothing is muted


EDIT: just a thought but do you have anything else usb and if so do they all work correctly?

---

### Post by kansasnoob on 2008-07-21
Try installing

> libflashsupport

from synaptic.

---

### Post by kansasnoob on 2008-07-21
Otherwise I pretty much shared everything I know about sound in various posts in this thread:

[http://ubuntuforums.org/showthread.php?t=855544](http://ubuntuforums.org/showthread.php?t=855544)

Read all the posts though, not just mine! I'm still a nOOb at this.

---

