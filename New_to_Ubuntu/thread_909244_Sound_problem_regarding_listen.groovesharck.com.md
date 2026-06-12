---
title: "Sound problem regarding listen.groovesharck.com"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by SG3 on 2008-09-03
Hey, 
I'm kinnda new to the whole OS, so a friend of mine set it up.I have no sound problems with different apps, but I can't start the sound from this online playlist.I'm not quite sure what needs to be installed.Can anyone help.

---

### Post by NESFreak on 2008-09-03
hi and welcome,

for some reason [http://listen.groovesharck.com/](http://listen.groovesharck.com/) doesn't exists. Are you sure it's the right url?

---

### Post by SG3 on 2008-09-03
[http://listen.grooveshark.com/](http://listen.grooveshark.com/)

My bad.That is the correct url.

---

### Post by NESFreak on 2008-09-03
this website apparently uses flash. Do you have any other audio related problems with flash? If yes you might try installing libflashsupport

---

### Post by SG3 on 2008-09-03
thank you, it seems that there several problems with the flash, trying to reinstall it now, hope it works :)

---

### Post by lompa on 2008-09-22
no way... I tried to install libflashsupport but still it does not work. The flash interface stops on the "buffering" phase, before any songs is actually played

Any guess?

---

### Post by billgoldberg on 2008-09-22
> **lompa said:**
> no way... I tried to install libflashsupport but still it does not work. The flash interface stops on the "buffering" phase, before any songs is actually played

Any guess?

Remove libflashsupport.

It will make flash unstable which will result in lots of firefox crashes.

Switch to ALSA instead.

---

I am using Flash Player 10 RC 2 and the website doesn't do nothing. It's just a white screen I'm looking at.

Must be a badly coded site.

---

### Post by markbuntu on 2008-09-22
That site works for me. I am listening to the weepies from it right now. I have a fully updated firefox from proposed and am using flash10b.

---

### Post by lompa on 2008-11-12
Ok... I removed libflashsupport, but that was not the problem. I installed the new flash plugin 10 (I had to use the 32 plugin wrapper, as I'm running ubuntu 64): still nothing. My guess is that for some reason firefox can't connect to the buffering source: this could be a socket or permission problem, rather than a sound one... (by the way: I also tried to run firefox with root privileges: got nothing)

---

