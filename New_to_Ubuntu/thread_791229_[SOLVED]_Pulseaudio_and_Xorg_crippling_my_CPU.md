---
title: "[SOLVED] Pulseaudio and Xorg crippling my CPU"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by lobo-tuerto on 2008-05-12
Hello guys,


I'm experiencing exactly the same as the guy in the last post in this thread:
[http://ubuntuforums.org/showpost.php?p=4529889&postcount=10](http://ubuntuforums.org/showpost.php?p=4529889&postcount=10)

> Hardy is good for a while but sometimes it goes into some kind of problem-mode where "Xorg" will sit at 75 to 100% cpu, while doing nothing useful...

I think it's got something to do with either GVFS or Pulseaudio interaction with xorg, because it doesn't happen on Gutsy...


And it happens periodically. Any ideas where to look for a fix?

---

### Post by sdennie on 2008-05-12
Does it help at all if you go to System->Preferences->Sounds and manually switch all those settings from "Autodetect" to "ALSA"?

---

### Post by lobo-tuerto on 2008-05-12
Thanks a lot!

It seems like it helped, if any problems arise I will report back.
It even helped with the problem I had with the flash player and rhythmbox. They could coexist together, one wouldn't let the other play sounds.

---

