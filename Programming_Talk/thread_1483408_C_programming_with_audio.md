---
title: "C programming with audio"
date: 2010-05-14
forum: Programming Talk
---

### Post by vksingh on 2010-05-14
Hi Friends,

Please post to me some reference of C programming with taking input from microphone and processing the audio file.


How can I get the source code of Ubuntu sound recorder?


Thanks,


Vivek

---

### Post by km0r3 on 2010-05-14
I hear some good stuff about [Fmod]("http://www.fmod.org/index.php/download"). I'm not sure if it's the right C audio library for your purpose.

Otherwise there is [PortAudio]("http://www.portaudio.com/"), also a portable C Sound library.

Also browsing over at stackoverflow.com might shovel up some useful results. *C Audio Library* might be a good search term.
I hope that helped.

---

### Post by soltanis on 2010-05-14
SoX (Sound Exchange) is a full-featured command line tool for recording, processing, and converting audio using various audio APIs (including ALSA, OSS). The source code for that program is likely very long.

If you want a specific interface to look at I suggest you download the source code for arecord (which is the same program as aplay) which does recording of audio using ALSA. Since it's much more simplistic, it should be easier to find relevant portions of code.

---

### Post by tgalati4 on 2010-05-14
apt-cache search sound recorder

It looks like sound recorder is part of gnome-media.  You can activate the source (src) repositories in synaptic then search for sound recorder and mark the sources for it.

---

