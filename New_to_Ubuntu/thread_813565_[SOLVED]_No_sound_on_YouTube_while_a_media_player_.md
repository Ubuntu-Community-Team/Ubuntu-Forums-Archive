---
title: "[SOLVED] No sound on YouTube while a media player is playing?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-05-30
For some strange reason, whenever I listen to music on a media player there is no sound on YouTube videos (or probably any other online videos).

Any ideas as to why this is occurring? Thanks in advance :|

---

### Post by iaculallad on 2008-05-30
Try disabling ESD.
Navigate through System->Preferences->Sound and click on the "Sounds" tab. Uncheck the "Enable Software Sound Mixing (ESD)"

---

### Post by tdrusk on 2008-05-30
You need a libflashsupport

I think the package is
```
sudo apt-get install libflashsupport
```

You may have to restart x
ctrl+alt+backspace

---

### Post by JimmyJim on 2008-05-30
> **tdrusk said:**
> You need a libflashsupport

I think the package is
```
sudo apt-get install libflashsupport
```

You may have to restart x
ctrl+alt+backspace

That worked, thanks

---

