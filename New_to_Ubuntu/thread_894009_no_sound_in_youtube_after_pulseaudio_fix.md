---
title: "no sound in youtube *after* pulseaudio fix"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Jengajam2 on 2008-08-18
Youtube kept crashing my Firefox browser, so I followed the guide here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578), but now it doesn't have any sound output (though i have output on everything else). On the pulse audio manager, whenever I play a flash video, the Devices and Clients tabs get really shaky (something on the list flicks on and off really fast).

---

### Post by tuxxy on 2008-08-18
Have you tried running ALSA as the ouput at system > prefs > sound

---

### Post by markbuntu on 2008-08-18
That flashing in the pulse manager is flash opening and closing audio streams. It is a problem with flash 9 and is fixed with 

libflashsupport 

which you can get from the repos with Synaptic.

---

