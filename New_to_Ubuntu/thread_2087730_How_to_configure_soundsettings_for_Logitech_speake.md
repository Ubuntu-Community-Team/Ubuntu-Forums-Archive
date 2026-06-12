---
title: "How to configure soundsettings for Logitech speakers"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by enetic on 2012-11-24
I have a set of speakers, like the ones here: ( [http://tinyurl.com/c3fcqbe](http://tinyurl.com/c3fcqbe) ) 

My problem is that I cant make them work. They dont play any sound. A few months back, they worked, and I think they stopped working when Ubuntu went over to pulseaudio, but im not sure. is there a "new" way of making them work again, under pulseaudio?

---

### Post by newb85 on 2012-11-24
What Ubuntu release are you using?  Did you upgrade using the upgrade button in the Update Manager?

---

### Post by enetic on 2012-11-24
Im using ubuntu 12.10 now, but like I said before the problem has been around for some time. Ive always upgraded through the update manager, because i dont want to delete and reinstall things for every release..

---

### Post by newb85 on 2012-11-24
I doubt a "switch to Pulse" caused you problem.  Pulse has been around since 8.10, and current systems use both Pulse and ALSA.  (They act as different "layers".)

First thing I would check is the ALSA settings.  From a terminal, run
```
alsamixer
```
and make sure none of the channels other than microphone channels are muted (marked with MM).

---

