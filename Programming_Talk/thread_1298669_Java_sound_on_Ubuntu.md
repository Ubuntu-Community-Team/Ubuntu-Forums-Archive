---
title: "Java sound on Ubuntu"
date: 2009-10-23
forum: Programming Talk
---

### Post by m0nkeyk0ng on 2009-10-23
I am having trouble outputting sound (simple .wav or .au files) through Java on Ubuntu. I have tried following every basic approach out there short of installing the JMF API. I'm all out of ideas after spending half the day trying to get a beep or a buzz.

I am wondering if anyone else has run into a similar problem?

---

### Post by OpenGuard on 2009-10-23
Haven't used Java for such tasks, but wouldn't it be easier to use mpeg123 ( it's too small to not to give it a try ) ?

---

### Post by m0nkeyk0ng on 2009-10-23
I checked mpg123 and isn't it a C library?

Anyway, it appears the Java libraries require exclusive access to audio resources on Ubuntu in order to playback. This is not really pragmatic for the magnitude of the program.

[http://linux.dsplabs.com.au/lsof-grep-snd-how-to-free-a-linux-sound-device-p25/](http://linux.dsplabs.com.au/lsof-grep-snd-how-to-free-a-linux-sound-device-p25/)

I'm going to try to run the code on my Windows box. But if anyone knows how to get around this issue, let me know.

--------------
edit:

Actually... problem solved! Kinda.

Root access is needed to access audio device, so I run the program with root privileges and it works. This isn't the most elegant solution, though. So if you have a better solution let me know!

---

### Post by OpenGuard on 2009-10-23
> **m0nkeyk0ng said:**
> I checked mpg123 and isn't it a C library?


[http://www.mpg123.de/](http://www.mpg123.de/) - it's a lightweight CLI based music player, not a C library.

---

