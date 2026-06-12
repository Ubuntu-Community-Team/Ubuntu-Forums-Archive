---
title: "Compileing Gyachi!!"
date: 2009-07-15
forum: Packaging and Compiling Programs
---

### Post by Short__Error on 2009-07-15
I know that this is already done for us and there is a ppa but there are things that i would like to change when trying to compile i get some errors some help on how to get around that would be awesome.
  here is what i am getting.


```
checking for ALSA... configure: error: Package requirements (alsa >= 0.9.8) were not met:

No package 'alsa' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALSA_CFLAGS
and ALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

---

### Post by loell on 2009-07-16
you need alsa development package, alternatively there is a disable alsa in the configure parameter.

---

