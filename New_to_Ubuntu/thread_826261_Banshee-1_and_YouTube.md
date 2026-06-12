---
title: "Banshee-1 and YouTube"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by teamkiller87 on 2008-06-11
Just installed Banshee RC1 and loving every moment of it... However, I've encountered a slight problem. Whenever I have Banshee running, sound is blocked from every flash site I've tried. It goes both ways as well, Banshee doesn't play any sound if there's a flash site in my browser. I was unable to find any solution on Google so I'm hoping someone else had or has this problem! HELP!

---

### Post by teamkiller87 on 2008-06-11
Anyone? I'm really enjoying the Banshee experience... Wouldn't want it to end so abruptly, but this bug will force me into it if it won't be fixed! A six-pack of e-beers to the one who lends a helping hand! :D

---

### Post by st33med on 2008-06-11
This is 'Functioning properly' according to pulseaudio. Pulseaudio only allows one program using audio at once.

I know, I don't like this either....

---

### Post by gr4nf on 2008-06-11
This may be fixed in the next version of either banshee or alsa.

---

### Post by st33med on 2008-06-11
Ok, supposed fix:
Go to System -> preferences -> Sound and change every dropdown box from 'Auto' to 'ALSA'. 

(ALSA FTW!)

---

### Post by teamkiller87 on 2008-06-12
Thanks, I'll give that a try when I get home from work! The six pack is on its way... but I wouldn't hold my breath waiting for it! :)

---

### Post by iaculallad on 2008-06-12
Try installing the libflashsupport file:

```
sudo apt-get install libflashsupport
```

---

### Post by teamkiller87 on 2008-06-12
> **st33med said:**
> Ok, supposed fix:
Go to System -> preferences -> Sound and change every dropdown box from 'Auto' to 'ALSA'. 

(ALSA FTW!)

That did the trick!! *bows in awe at st33med's greatness* Thanks a lot!

---

### Post by Izym on 2008-07-23
Was having this problem as well, thanks a lot! :D

---

