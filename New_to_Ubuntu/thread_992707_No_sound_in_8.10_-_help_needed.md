---
title: "No sound in 8.10 - help needed"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by Dragonseer on 2008-11-25
My troubles started when I upgraded WINE to 1.1.9 and the sound stopped working.  After doing some searching I saw that perhaps Pulseaudio was at fault and I tried removing it, as detailed here- [http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637).

At this point sound stopped working altogether, including the system start up sounds.  I tried reinstalling pulseaudio but now I don't know how to restore pulse audio in the System>Preferences>Sessions dialogue.  So I could use some help in getting sound restored before tackling the WINE issue again.

---

### Post by magli on 2008-11-25
If you are having trouble with pulseaudio, you can try bringing up alsa instead, with the following commands:

```
sudo killall pulseaudio
sudo alsa force-reload
```

---

