---
title: "Rythmbox(and Amarok) aren't playing well with internet videos"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by DeadEagle on 2008-06-13
When I open Rythmbox, and any media player I've tried so far, and play music, then go to YouTube or something, the videos have no audio. If I close Rythmbox and then watch the video, the audio works just fine, but Rythmbox won't play as long as the video is open. What can I do about this?
Hardy Heron by the way.

---

### Post by ataraxia on 2008-06-13
sudo apt-get install libflashsupport

worked for me!

---

### Post by billgoldberg on 2008-06-13
libflashsupport will work but can make firefox/flash a tad unstable.

You could just switch to ALSA, that way you won't have stability issues.

[http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/](http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/)

---

### Post by DeadEagle on 2008-06-18
> **billgoldberg said:**
> libflashsupport will work but can make firefox/flash a tad unstable.

You could just switch to ALSA, that way you won't have stability issues.

[http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/](http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/)
Roger that, sir. Works like a charm. Thanks very much. :-D

By the way, nice avatar 8)

---

