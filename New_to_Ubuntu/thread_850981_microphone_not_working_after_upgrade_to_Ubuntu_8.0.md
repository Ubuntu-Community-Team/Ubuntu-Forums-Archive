---
title: "microphone not working after upgrade to Ubuntu 8.04"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by deepblue80 on 2008-07-06
hi
i just upgraded to Ubuntu 8.04 and my microphone is not working inskype. i tried to play around with sound preferences but nothing seems to work? i have a asus p5ne  sli motherboard with onboard 5.1. i can listen to music but no luck with mic! any ideas?

---

### Post by Aurora@FleetBuzz on 2008-07-06
Did you try to adjust the settings in alsamixer?  Open a terminal and type "alsamixer".

---

### Post by deepblue80 on 2008-07-06
> **Aurora@FleetBuzz said:**
> Did you try to adjust the settings in alsamixer?  Open a terminal and type "alsamixer".

i am using Gnome alsa mixer and sound preferences in System/preferences but i am missing something. something as simple as this should not be complicated!

---

### Post by Aurora@FleetBuzz on 2008-07-06
I had the same problem.  What fixed it for me was to enable all the settings in alsamixer and max them out.  If you are unsure how to do this, there is a "Help" feature in alsamixer, or we can show you.

---

### Post by mukhan85 on 2008-07-06
Hi, I am also having problems with microphone. I did increased all Items in "alsamixer" to maximum, but it didn't help...

---

### Post by sayakb on 2008-07-06
In Gnome Volume control (double click on Volume Control), goto **File->Change Device** and choose **Capture devices** from there and unmute them/set volume to max and try again.

---

