---
title: "flash sound problems"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by panthertd175 on 2008-05-20
In Hardy, after installing the flash plugin I had the problem that sound could only be played from either the flash player (such as on youtube) or from another source like Amarok.  If I wanted to hear a youtube video, I would have to close Amarok.  I could hear sounds from both Amarok and movie player, but just not firefox.  Anyway, I found a guide called something like what to do next after installing Ubuntu.  It had five parts including how tos on improving sound and video among other things.  I did what it said, and it totally fixed my sound problem.
However, I have just installed Ubuntu on another computer and have the exact same problem.  For the life of me can't find the guide I used and can't find what worked before.  I have tried changing firefox to use aoss, and it didn't work.  I know I did not have to install PulseAudio and would prefer not to have to, as some threads have suggested.  Ideally, I would like to have a link to the guide I found before.  However, I would also appreciate any solution that will get my audio to work.

---

### Post by shadow-of-sin on 2008-05-20
Install libflashsupport by typing the following command in the terminal:
```
sudo apt-get install libflashsupport
```

---

### Post by panthertd175 on 2008-05-20
That did it, thanks.

---

