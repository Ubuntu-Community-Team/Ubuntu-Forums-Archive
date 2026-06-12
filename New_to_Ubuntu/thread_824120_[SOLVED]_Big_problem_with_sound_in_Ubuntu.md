---
title: "[SOLVED] Big problem with sound in Ubuntu"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-06-09
My computer won't play sound on Youtube (or any other sound) when I have Amarok open, and I have played any music in it. For example, if I open Amarok and play a song, even if the song ends and there's no music playing, I can't hear sound in Youtube videos (or in any files requiring sound for that matter) without closing Amarok and Firefox and then re-loading Firefox. I can also start by opening Firefox, playing a Youtube video, and then even if I finish watching the video, I can't listen to any music in Amarok without first closing Firefox. If I try to open Amarok with Firefox (with the Youtube video) already open, Amarok will simply not play the audio and then crash, and I have to use the system monitor to end the process. Note that this isn't just with Amarok and Youtube, it is with any two files that play sound. What's going on? How can I fix this?

---

### Post by iaculallad on 2008-06-09
Install the LibFlashSupport file

```
sudo apt-get install libflashsupport
```

---

### Post by Watchtow3r on 2008-06-09
Thanks!

---

