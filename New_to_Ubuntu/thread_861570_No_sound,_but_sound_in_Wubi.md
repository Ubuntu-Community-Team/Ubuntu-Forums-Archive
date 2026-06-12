---
title: "No sound, but sound in Wubi"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Me887799 on 2008-07-16
I was using Wubi for a little while and my sound worked with a little tweaking (Right clicking the volume control, going to preferances, and selecting my headset) but after I partitioned my hard-drive and installed ubuntu, the same method does not produce sound. 

I am using AC883 drivers with a logitech USB headset.... any help?  Please?

---

### Post by Me887799 on 2008-07-16
I also have sound at start up

---

### Post by saitoh on 2008-07-16
If you have sound at startup but not afterwards I would check to make sure that alsa has the right volume settings.
Open up a terminal and type "alsamixer" you should get a screen where you can adjust the max volume for various devices(even your headphone jack).

---

### Post by Me887799 on 2008-07-16
Never mind.  I think I'm bleeding after going to system>preferences>sound and making everything feed through USB sound.

---

