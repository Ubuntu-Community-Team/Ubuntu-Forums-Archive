---
title: "[SOLVED] Getting the microphone to work"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-09-03
I have a logitech notebook camera with a built in microphone. It works no problem with Skype. However I am having real problems getting it to record anything with gnome-sound-recorder or Lingot. Neither seem to recognise or find the microphone.

---

### Post by NESFreak on 2008-09-03
try going to the volume manager-->preferences and enable both digital and digital input. Configure them as you like.

---

### Post by billgoldberg on 2008-09-03
Try selecting "ALSA" as your capture device in "system -> preferences -> sound".

Can you record in audacity?

---

### Post by Harisz750 on 2008-09-03
> **billgoldberg said:**
> Try selecting "ALSA" as your capture device in "system -> preferences -> sound".

Can you record in audacity?

i have exactly the same problem after i upgraded from gutsy to hardy.. only in skype works...

---

### Post by Bucky Ball on 2008-09-03
As NESFreak says, right click on your speaker icon, select preferences and you will probably discover your mic is muted. Unmute and you should be right. Also, make sure you are set to the right card/driver in there.

---

### Post by Harisz750 on 2008-09-03
> **Bucky Ball said:**
> As NESFreak says, right click on your speaker icon, select preferences and you will probably discover your mic is muted. Unmute and you should be right. Also, make sure you are set to the right card/driver in there.

it is not muted...  i also tried from terminal alsamixer and nothing muted there... and believe me.. i have made other mics to work... the problem is mine!!!!!

---

### Post by dunbrokin on 2008-09-07
> **NESFreak said:**
> try going to the volume manager-->preferences and enable both digital and digital input. Configure them as you like.


Thanks for that....

---

### Post by itsjustarumour on 2008-09-07
> **Bucky Ball said:**
> As NESFreak says, right click on your speaker icon, select preferences and you will probably discover your mic is muted. Unmute and you should be right

I couldn't get my microphone to work in Skype 2.0 on Hardy 8.04, but this fixed it.  I just selected my Plantronics headset as the device in the drop-down list, turned up the volume, and all working - thanks chaps!  :-)

---

