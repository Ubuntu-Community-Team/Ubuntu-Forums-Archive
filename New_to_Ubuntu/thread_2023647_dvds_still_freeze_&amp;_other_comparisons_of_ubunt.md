---
title: "dvds still freeze &amp; other comparisons of ubuntu and windows"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by Oldcanoe on 2012-07-12
Greetings,

New here to ubuntu with 12.04 fully installed (no partition) on former amd athlon 64, 2 gb xp machine four days ago. So far so good with home network (wireless and cat 5 cxn), radio and youtube streaming and figuring out how to get it to play commercial dvds. Found and dowloaded the "forbidden" files and likewise applied the correct (I think) sudo string (usr/share/doc/libdvdread4/) and presto-chango it worked. Started to feel a bit smug, I did. :razz:

Then, one minor problem with color youtube at full 480 resolution and commerical dvds. :sad: The image freezes after say 3 to 15 minutes. BW youtube Charlie Chaplin movie worked fine. Last lockup was dvd with frozen image, with sound continuing to play. Restarted ok each time after hard reboot.

The machine can run internet radio for several hours ok. Sounds nice when fed through the old stereo.

I am thinking video card; either drivers, or something more serious and hardware related. Grateful for any thoughts or feedback.

Keep up the good work and thanks in advance.

Best, Oldcanoe

p.s. Ubuntu vs. windows so far; boots <1/2 x faster than xp on the old box, and ~1.5 x slower than W7 on the new Dell i3 with 6gb. Visually, W7 is nicest with xp and ubuntu about the same. Software downloads (VLC, Audacity) faster than windows and firefox seemingly responds a bit quicker than Explorer on the W7 machine. I have managed to solve most ubuntu issues so far by looking on line for answers and trying things to see what works. Have read and done my best to heed the warnings about being careful with the sudo commands. Major hurdle was dvds.

pps. folks gripe about the unecessary software that often comes with windows machines, but I noted a lot of stuff carried in with ubuntu that seemed to fit in the same category.

---

### Post by jmfal on 2012-07-12
Welcome to Ubuntu

 You should install ubuntu-restricted-extras, it should clear up the dvd/video problems

You can find it in the software center or
```
 sudo apt-get install ubuntu-restricted-extras   
```

Might have to restart to finish install.

---

