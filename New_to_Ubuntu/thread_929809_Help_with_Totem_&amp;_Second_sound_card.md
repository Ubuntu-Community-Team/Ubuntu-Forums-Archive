---
title: "Help with Totem &amp; Second sound card"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by realunreal on 2008-09-25
I have two sound cards in my system,  one for the operating system and general use and the other for dedicated music playback.

How do I go about setting Totem to use the second sound card ? ? ?

---

### Post by Teamgeist on 2008-09-25
In a Terminal type ```
gstreamer-properties
```

This will pop up the multimedia preferences where you can select the soundcards etc.

---

### Post by northern lights on 2008-09-25
The totem preferences unfortunately don't have an "output module" option.

If you'd prefer to set the sound device for an application only, rather than making a global change, VLC and Amarok, for instance, allow you to do that, by setting```
plughw:0,X
```as the ALSA stereo output module where X is the device number given in the left column of the output of```
cat /proc/asound/cards
```

---

### Post by markbuntu on 2008-09-25
I have written a guide to setting up and using multiple sound cards here:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

