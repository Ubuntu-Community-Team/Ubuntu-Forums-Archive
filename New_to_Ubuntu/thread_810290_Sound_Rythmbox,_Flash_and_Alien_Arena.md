---
title: "Sound: Rythmbox, Flash and Alien Arena"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by powerpleb on 2008-05-28
Hi everyone,

I would like to be able to simultaneously play mp3s from Rhythmbox, watch flash videos such as on YouTube with sound and play games such as Neverball and Alien Arena.

Currently, If I want to watch flash videos and have rhythmbox playing, I need to have ESD enabled. I installed libflashsupport. However, games like Neverball and Alien Arena don't have sound. 

If I want Rythmbox and game sound I need to disable ESD, restart X server and it works. But I can't play flash videos with sound and there are no sound events.

If there anyway to configure this so I can have everything at once without having to mess around with setting all the time?

---

### Post by sayakb on 2008-05-28
Open the Volume control from the panel and Change the device to ALSA from PulseAudio.

---

### Post by powerpleb on 2008-05-28
> **LinuxIsInnovation said:**
> Open the Volume control from the panel and Change the device to ALSA from PulseAudio.

Thank you :)

That worked insofar as now I can listen to mp3s and play games at the same time without disabling sound events. 

But I when I try to play a flash video when Rythmbox is playing an mp3 the flash video freezes after 2 seconds.

---

### Post by powerpleb on 2008-05-30
I found the solution here...
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

