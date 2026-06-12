---
title: "Streaming videos jump"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by Gabcat on 2012-09-09
Hi all
I have installed xubuntu 12.04 and seems to work great apart from one problem with streaming videos: they jump (audio works ok, it's only the image that jumps). All works fine with Win XP. Can you help?
thanks

---

### Post by pqwoerituytrueiwoq on 2012-09-09
define jump
really slow fps
frames shift up and down 

which video player
what gpu

---

### Post by Gabcat on 2012-09-09
really slow fps

Also, with firefox it seems to work fine, but i prefer chrome and there it is really slow, even at low definition.

I have flash installed, and i guess the video player is gstreamer, but am not sure (i didn't change any setting so i imagine it is the default one).

My graphic card is 
VGA compatible controller: Advanced Micro Devices [AMD] nee ATI M24 1P [Radeon Mobility X600]

---

### Post by pqwoerituytrueiwoq on 2012-09-09
if the source is not using any drm crap if you pause it in firefox you can run this long command
```
cd /tmp;d="`date`";ln -s `f="$(ls -l /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"` /tmp/"movie-$d";smplayer -fullscreen /tmp/"movie-$d"
```
flash uses your cpu for everything, i'm guessing you have a really old amd based laptop

---

### Post by Gabcat on 2012-09-10
it is in fact my very old laptop. I understand it might be the slow cpu,althou i can not see why it would work well on wixp (and firefox on xubuntu) and not in chrome.

---

### Post by pqwoerituytrueiwoq on 2012-09-10
chrome uses a thing called pepper not flash

---

