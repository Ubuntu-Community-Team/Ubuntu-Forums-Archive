---
title: "Adding some more sample rate for snd_aloop"
date: 2015-04-29
forum: Packaging and Compiling Programs
---

### Post by peter190 on 2015-04-29
Hello!

I need to increase default max value of sample rate in aloop.c from 192000 to 1536000 for my internal needs.
How I can re-compile snd_aloop in Ubuntu 14.04? It was pretty easy before when ALSA had separate src package, but now getting alsa-source from apt-get just giving out outdated version, which wont compile and gives errors from both manual compiling and through module-assistant.

(ex. error: static declaration of &#8216;jiffies_to_msecs&#8217; follows non-static declaration etc.)

Any suggestions?

---

### Post by peter190 on 2015-05-02
Ok, this was my misunderstanding.
aloop.c is now included into kernel. So, apt-get install linux-source will bring the kernel source in tar.bz2 into /usr/src. After that I just unpacked it, went to ./sound/drivers/aloop.c and made my changes. After that make menuconfig to check that config is ok, make -j5, make modules install and make install. and it is there.

---

