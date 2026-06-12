---
title: "skype problem"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by willy james on 2008-11-13
Until recently, skype worked OK, I am running ubuntu 8.04 (hardy).   

Now, no.  the program does not call at all (skype test call returns "test call failed" no more), or even search out other users successfully.

I have done all the lame newbie tricks with apt-get (clean, update, and purge then reinstall).  Nothing seems to work.  Very frustrating.

Any tips out there from people having similar issues??
Will

---

### Post by Mark_in_Hollywood on 2008-11-15
> **willy james said:**
> Until recently, skype worked OK, I am running ubuntu 8.04 (hardy).   

Now, no.  the program does not call at all (skype test call returns "test call failed" no more), or even search out other users successfully.

I have done all the lame newbie tricks with apt-get (clean, update, and purge then reinstall).  Nothing seems to work.  Very frustrating.

Any tips out there from people having similar issues??
Will

1. Have you checked skype options/audio devices (maybe hardware devices).
2. Open a terminal, type alsamixer   move the volume up (or down), close terminal. Load skype. try again.

---

