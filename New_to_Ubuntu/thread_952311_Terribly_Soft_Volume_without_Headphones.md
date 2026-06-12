---
title: "Terribly Soft Volume without Headphones??"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by ChaosMuffins on 2008-10-19
Okay, this is another silly question from my side of things...but the volume on my computer seems to be AWFUL. No matter what speakers I'm using, no matter how high I turn everything...it's very soft, and I strain to hear music. It's fine over Headphones, but I do occasionally enjoy *not* wearing headphones.

Is this a driver thing? Are there files I'm missing? Is my soundcard failing? Rocks fall and everyone dies?

Thanks in advance. :confused:

---

### Post by anjilslaire on 2008-10-19
Open the sound mixer settings, and check that all channels are up high. On my Kubuntu system, the PCM volume was way down, and raising it fixed everything.

---

### Post by Christmas on 2008-10-19
You can also try to run in a terminal emulator:
```
sudo alsamixer
```
And then modify volume to maximum from there. Make sure no channels are muted (press M to mute/unmute) and when you're done, hit ESC.

---

### Post by CharonM72 on 2008-10-19
Speakers tend to amplify their input quite a lot by using an external electricity source. This may sound silly, but... are your speakers plugged-in and on (presuming they are supposed to be)? Having them not so will often cause exactly that problem, especially for lower-end speakers (which won't completely mute sound if not turned on).

---

### Post by paulchinnz on 2009-01-28
I've got the same problem on my Dell e1405.  I've got everything turned up including the MediaDirect buttons and alsamixer.

By the way, are the sound options in Sound Preferences/Sound so limited, as in I can't leave empty trash sound on but turn login/logoff off?

---

### Post by paulchinnz on 2009-01-31
Anyone have any ideas about this?

---

### Post by paulchinnz on 2009-01-31
Hmm was playing around with 'main menu' and found that I wasn't seeing 'volume'.  PCM was way down: put it up and, for me at least, it's solved.

---

