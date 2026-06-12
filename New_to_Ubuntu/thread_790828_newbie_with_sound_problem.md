---
title: "newbie with sound problem"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by ubunu on 2008-05-11
I've installed Heron 'within' windows. When running tests using the built i facility the sounds are fine and I hear the beating drums on boot however I cannot get applications (music players, note edit etc. ) to play sounds, the programs run but don't seem to access the sound card.

Any help much appreciated.

Sound card: onboard Intel 82801BA-ICH2 (Alsa mixer)

---

### Post by pro003 on 2008-05-11
you'll have to update your codecs...through terminal:


```
sudo apt-get update
```

```
sudo apt-get install mplayer
```


or connect to internet and start totem player with some movie or mp3 and then you will be asked to search automatically for appropriate codecs...

---

### Post by ubunu on 2008-05-11
"you'll have to update your codecs..."

Would this be the case even though MIDI files don't produce sound?

cheers

---

### Post by ubunu on 2008-05-12
Audio CD's, Video files all play ok but both Totem and Note-edit are silent when 'playing' midi files!

Am I right then in assuming that this is not a codec issue but a soundcard config issue, neither program appear to have an interface for the soundcard.

any suggestions?

---

### Post by pro003 on 2008-05-12
this [post]("http://ubuntuforums.org/showthread.php?t=44753") will help you, hopefully

[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

---

### Post by ubunu on 2008-05-14
Many thanks, I think it will!

---

