---
title: "[SOLVED] I can't listen to music"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by clipeuh on 2008-08-06
When I open Rhythmbox, and I try to listen to a song, it doesn't work, the song doesnt start... I also tried with Amarok and it doesn't work.

I have all the codec installed.

---

### Post by 0utlaw 0f Pk on 2008-08-06
Ah yes I had this problem only I had World of Warcraft open at the same time when i closed both and opened rhythmbox then Wow it worked :\ Do you have any other problems that may use your sound drives?

---

### Post by clipeuh on 2008-08-06
At the moment I only have Mercury Messenger and Firefox open...

---

### Post by Ryadt on 2008-08-06
Try ```
killall pulseaudio
```

---

### Post by clipeuh on 2008-08-06
> **Ryadt said:**
> Try ```
killall pulseaudio
```

Hey it works now ! Thank you man !

---

### Post by tech9 on 2008-08-06
> **clipeuh said:**
> When I open Rhythmbox, and I try to listen to a song, it doesn't work, the song doesnt start... I also tried with Amarok and it doesn't work.

I have all the codec installed.

install gstreamer plugins for MP3s

---

### Post by perlluver on 2008-08-06
There is a known bug, that if you were playing a flash video, or had a player open in firefox, Rythmbox, and Any other media players, will not play until a restart.

---

