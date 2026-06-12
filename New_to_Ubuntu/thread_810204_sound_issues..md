---
title: "sound issues."
date: 2008-05-28
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-28
If i have banshee media player open, and try to watch videos on, say, youtube, i can't hear the video on youtube. is there a way to fix this?

---

### Post by powerpleb on 2008-05-28
> **adobrakic said:**
> If i have banshee media player open, and try to watch videos on, say, youtube, i can't hear the video on youtube. is there a way to fix this?

You need to install pulse audio flash support as I think most media players use pulse in hardy
> sudo aptitude install libflashsupport
That should work.


I wanted to play games and listen to mp3s at the same time...
So I went into System>>Preferences>>Sound click on the Sounds tab and de-selected ESD.

I think it made the system use the hardware mixer. But you need to have a sound card capable of mixing. A downside is that I no longer get system event sounds or flash video sounds. So I wish I knew a way to get both.

---

