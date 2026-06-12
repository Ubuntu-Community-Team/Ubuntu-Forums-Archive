---
title: "no audio sometimes..."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-06-04
OK I've noticed with ubuntu that certain applications that use sound will effect other applications such as running audacious but then pausing it to watch a video with smplayer wont work because smplayer will just stop working :( is there anyway to make it so all applications can use sound at the same time? or maybe you can recommend a command or a GUI which can tell me what application is using sound as sometimes the only way to play a video is to log out and in again:mad:

---

### Post by fs3rp4 on 2008-06-04
> **kamitsukai said:**
> OK I've noticed with ubuntu that certain applications that use sound will effect other applications such as running audacious but then pausing it to watch a video with smplayer wont work because smplayer will just stop working :( is there anyway to make it so all applications can use sound at the same time? or maybe you can recommend a command or a GUI which can tell me what application is using sound as sometimes the only way to play a video is to log out and in again:mad:



This sometimes happens because the application uses OSS instead ALSA. OSS lock the system sound.

Try to find if the application support ALSA or PulseAudio.

---

