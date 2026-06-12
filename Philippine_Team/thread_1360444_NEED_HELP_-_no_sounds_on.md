---
title: "NEED HELP - no sounds on"
date: 2009-12-20
forum: Philippine Team
---

### Post by ncvaldez on 2009-12-20
Codec: Realtek ALC883
Codec: Motorola Si3054

i upgraded from 9.04 to 9.10

i recently fixed my screen resolution problem but i just found out that the the sound card(?) had a problem too? i dont really know the real problem but i looked on threads similar to my problem and if im not mistaken its an issue of having the kernel from 9.04 instead of a newer version?

i dont know what to do. there were a lot of said solutions on some threads but it is not working. im planning to download and imply a stable kernel but im not sure if this is the right thing to do(maybe ill mess it up somemore if i actually try to do this)

can anyone help me on this please please please?

---

### Post by loell on 2009-12-20
what solutions have you tried so far?

---

### Post by ncvaldez on 2009-12-21
i tried adding a line "options snd-hda-intel model=auto" to the /etc/modprobe.d/alsa-base.conf

i tried changing "DISALLOW_MODULE_LOADING=1" to "DISALLOW_MODULE_LOADING=0" in the /etc/default/pulseaudio

i tried removing pulseaudio(some said that will fix the problem)

i tried installing grub2(someone said it will fix it)

(i dont know if these are all the things ive tried)

and the most recent, i tried ugrading may ALSA but i found out that the driver, library and the utilities version are not equal and they said this may be caused by the kernel problem so i tried to fix that one first

and now im stuck :(

---

### Post by ncvaldez on 2009-12-21
i dont know if this would help but when i checked the pulseaudio volume control, there were no hardware output detected, only a virtual output.

---

### Post by ncvaldez on 2009-12-21
ei i found the solution!

apparently the first one shouldve worked if i had the right model name

:)

here's the link i followed if ever someone needs it

[http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634)

:)

---

### Post by loell on 2009-12-21
heheh, great! it usually just takes a little more searching and if doesn't work, even initially asking will clear the mind in searching for the right question. 

It almost always, works everytime. :KS

---

