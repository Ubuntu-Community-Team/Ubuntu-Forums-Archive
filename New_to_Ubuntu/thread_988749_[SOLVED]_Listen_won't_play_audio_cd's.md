---
title: "[SOLVED] Listen won't play audio cd's"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by mesmith on 2008-11-20
I popped an audio cd into my combo dvd/cd/cdr drive today and although "Listen" opened, it did not actually respond to anything and produces no playback.  Is Listen dependent on Totem, or will MPlayer be enough if it needs stuff.

---

### Post by shifty_powers on 2008-11-20
do you have ubuntu restricted extras installed?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mesmith on 2008-11-20
I downloaded the pkg you suggested, and a ton of stuff came down.  What exactly did I get?

Bad news is that when the CD is inserted, Listen opens but no activity takes place.  Not even an error msg.  Took a look at Thunar advanced configuration and the program listed for audio CD is listen.  Is listen dependent on Totem?  Reason I ask is that I removed Totem the other day and loaded mplayer.  Having said that, I never tried to play an audio CD while Totem was installed so I don't know if that made any difference.

---

### Post by mesmith on 2008-11-20
The Thunar command for audio cd's that is in the advanced/configure section is:

mplayer cdda://

Is that correct?  Why do no controls appear?

Thanks.

---

### Post by mesmith on 2008-11-20
Can you recommend a good audio cd player that will work with the mplayer kit?

Thanks.

---

### Post by mesmith on 2008-11-21
Threw away Totem, MPlayer and the like.  Loaded VLC and works well.  No Real Audio support for the beeb, but someday...

---

