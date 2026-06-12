---
title: "Rhythmbox freeze on Oneiric"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by aykoola on 2011-10-25
After playing a song or so,  Rhythmbox freezes and won't play. I have to force quit it. 

Help?

I'm using 64bit Ubuntu Oneiric.

---

### Post by KL_72_TR on 2011-10-25
Take a look at these links, if you can find something:
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/148241](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/148241)
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/487932](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/487932)

---

### Post by thatguruguy on 2011-10-25
> **aykoola said:**
> After playing a song or so,  Rhythmbox freezes and won't play. I have to force quit it. 

Help?

I'm using 64bit Ubuntu Oneiric.

Run Rhythmbox from a terminal and see if you can re-create the problem.  Then post the terminal output here.

---

### Post by rents1977 on 2011-10-25
Same thing for me. Crashes on segfault after say 10 minutes of playing.

v2.90.1

(rhythmbox-metadata:5697): GStreamer-CRITICAL **: gst_value_init_and_copy: assertion `G_IS_VALUE (src)' failed
Segmentation fault

---

### Post by rents1977 on 2011-10-25
Disabling all plugins cured it. Will go through them one by one and find the cause.

[edit] The Cover Art plugin. Disabling this stops the crash.

---

### Post by aykoola on 2011-10-25
thank you!

Will mark as solved if it works for me also!

---

### Post by aykoola on 2011-11-06
OK, so the problem repeated, will run in terminal and try to recreate the problem!

---

### Post by LinuxFan999 on 2011-11-06
Try a different media player, like VLC.

---

### Post by Dustout on 2011-11-16
This has been happening to me as well lately, might have to buckle and start using banshee

---

