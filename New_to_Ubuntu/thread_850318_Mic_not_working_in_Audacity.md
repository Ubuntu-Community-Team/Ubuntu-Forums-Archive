---
title: "Mic not working in Audacity"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by penguinbreath on 2008-07-05
After working with kmix, I was able to get sound from my mic to come out of my speakers, however I cannot seem to get Audacity. I try setting mic input to ALSA through Audacity, but that does not work either. 

Any ideas?

---

### Post by icheyne on 2008-07-05
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

alsamixer is a good way to check that the mic is not muted.

---

### Post by penguinbreath on 2008-07-05
> **icheyne said:**
> [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

alsamixer is a good way to check that the mic is not muted.

I went to alsa mixer and played with the mic settings. I can hear my mic through my speaks much better after playing with the mic settings. However I still cannot get my mic to work with audacity. When I try to set audacity to use ALSA for the mic, I get this error.
```


Error while opening sound device. Please check the input device settings and the project sample rate.
```

Any ideas?

---

