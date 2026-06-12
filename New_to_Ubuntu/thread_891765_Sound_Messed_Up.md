---
title: "Sound Messed Up"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by lilxlaoxboi on 2008-08-16
When i play music i downloaded, the sound on firefox doesn't work.
and when i play sound on firefox. my music i downloaded doesnt work.
how do i fix this?

---

### Post by leepesjee on 2008-08-16
The problem is pulseaudio, which is used by Firefox/flash. Pulseaudio needs exclusive use of the sound driver (alsa) and captures it, so to speak, so that other applications cannot longer use it.
There are no easy fixes. One way is to configure all your sound-applications to use pulseaudio as well. Another is to use jack and route the pulseaudio output to jack. The easyest way is probably is to remove pulseaudio.
There are some threads about these things. See i.e.:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
Leo

---

### Post by Nepherte on 2008-08-16
In my opinion, the best way is to fix it instead of removing: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by kansasnoob on 2008-08-16
I've used the instructions pointed to in the beginning of Nepherte's link in both Hardy and Mint Elyssa successfully!

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

