---
title: "[SOLVED] green bar in video players"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by shadowber on 2008-09-16
I just updated to the latest [vlc player]("http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/#comment-29049") and now any time I play a video (wether in vlc or not) there is a green bar going down one side of the video (about 1/6th from the left side of the video player) and I cannot get rid of it. I am guessing it has to do with an updated codec, because it is happening with all video players, but like I said, I haven't a clue about how to get rid of it, please help!!!

*edit:* I just noticed that the video is doubled. (ie. if you see a person in the vid, there is a shadow of the person next to them...)

---

### Post by shadowber on 2008-09-17
bump

---

### Post by jemate18 on 2008-09-17
> **shadowber said:**
> bump

1. open vlc
2/ click settings
3. click preferences
4. Click video
5. click output module
6. select opengl video output

---

### Post by shadowber on 2008-09-17
Thanks for the advice, I am not at that computer now, but I will try it as soon as I can get to it... I hope that works!

---

### Post by billgoldberg on 2008-09-17
> **shadowber said:**
> Thanks for the advice, I am not at that computer now, but I will try it as soon as I can get to it... I hope that works!

No, not the opengl output.

Pick the "X11" output. Much better.

---

### Post by shadowber on 2008-09-17
Thank you both!!! that worked like a charm!!!
I will mark this thread as solved, but first if you don't mind what are the differences between x11, and open gl etc.

---

