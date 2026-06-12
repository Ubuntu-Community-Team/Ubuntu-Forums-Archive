---
title: "PulseAudio"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by gharootu on 2008-07-04
Hi,
I noticed alot of problems with media players, browsers, and anything else that plays sound when the PulseAudio process is running. When I end/kill the process (using System Monitor) everything seems to work fine. I've attempted to stop it from loading up, but it continues to do so. I've tried the following methods:

sudo sysv-rc-conf 
(following this post: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491))

Boot-Up-Manager
(following this url [http://www.zolved.com/synapse/view_content/28311/Tune_Boot-Up-Manager_for_better_performance_of_Ubuntu](http://www.zolved.com/synapse/view_content/28311/Tune_Boot-Up-Manager_for_better_performance_of_Ubuntu))

I'm completely lost as to why it still continues to load up. Any help would be much appreciated. Thank you.

---

### Post by wolfen69 on 2008-07-04
did you try [this]("http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio") ? worked great for me.

---

### Post by scragar on 2008-07-04
just add:```
killall pulseaudio
```to the startup applications found under: System>Preferences>Sessions

---

### Post by gharootu on 2008-07-05
Thanks for the link wolfen69 but it didn't work for me. Scragar's suggestion worked, thank you. Much obliged to both of you.

---

