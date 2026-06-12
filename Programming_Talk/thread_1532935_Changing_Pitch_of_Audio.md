---
title: "Changing Pitch of Audio"
date: 2010-07-17
forum: Programming Talk
---

### Post by verymagicalguy on 2010-07-17
I'm looking for a library that will allow me to change the pitch of video clip while it's playing. There's little information about audio in general, but I'm willing to write this software in pretty much any language.

Optimally I'd like to see a package that can play video and manipulate the audio pitch independently.

---

### Post by lykeion on 2010-07-17
If you develop in Java you can use Java Sound API/Java Media Framework, but why invent the wheel when you can do this easily in Audacity?

Just extract the audio from the video using mplayer, and edit it in Audacity (pitch change or whatever), and finally replace the old audio with the new using mencoder.

This process is described here: [http://wiki.showmedo.com/index.php/Video_editing_Ubuntu](http://wiki.showmedo.com/index.php/Video_editing_Ubuntu)

---

### Post by splicerr on 2010-07-17
You can use the GStreamer framework for that, it has a pitch element that does exactly what you want.

---

