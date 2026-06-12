---
title: "[SOLVED] rhythmbox music player"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by meirizal on 2008-05-25
i use ubuntu feisty on my pc, now i can't play mp3 on my rhythmbox music player. it said "couldn't read playlist -
the playlist file may be in an unknown format or corrupted". is there anything i can do? thank you for all your support.

---

### Post by jpeddicord on 2008-05-26
Rhythmbox is probably missing the GStreamer "ugly" codec set, which includes MP3. Visit Applications > Add/Remove and search for **mp3**. Install the **GStreamer extra plugins** package and try to play the songs again.

Also - the playlist, if copied over from Windows, might not be pointing to the right music paths. You'll want to create a new playlist in Rhythmbox and find your music manually.

---

### Post by arizonagt on 2008-08-12
I tried the solution and it worked until i restarted my computer and i can no longer play mp3s. I tried to remove GStreamer so i could add it again and see if that helped but i get the message:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

any advice?

---

