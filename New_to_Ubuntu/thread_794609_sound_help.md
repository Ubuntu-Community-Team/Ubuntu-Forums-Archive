---
title: "sound help"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by ddoong91 on 2008-05-14
i typed in alsamixer and i got
Card HDA ATI SB
Chip SigmaTel CXD9872RD/K
VIEW [PLAYBACK] CAPTURE ALL
ITEM MASTER [dB gain=0.00, 0.00]

and then in the bottom left it has a thing called <MASTER> in red
with 100<>100 and 00green in the box just below the bar

then theres another column PCM 100<>100

MY computer is a Vaio VGC VA11G and the sound will not work that is my info I do not know what more I can do if there is any other information I need to give please let me know

---

### Post by spiderbatdad on 2008-05-14
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

>  For example: If cat /proc/asound/card0/codec#* | grep Codec or : aplay -l  return "Realtek ALC260" , Look under "ALC260" in the list and add the following line in your /etc/modprobe.d/alsa-base or (if that one does not exist or is empty) /etc/modprobe.conf

options snd-hda-intel model=hp 

---

