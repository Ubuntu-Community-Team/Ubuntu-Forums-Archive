---
title: "How to compile Wired sound studio"
date: 2006-07-21
forum: Outdated Tutorials &amp; Tips
---

### Post by lzap on 2006-07-21
Download sources from [http://wired.is.free.fr](http://wired.is.free.fr). Then:

```
apt-get install libwxgtk2.6-dev libsamplerate0-dev libportaudio-dev
libsoundtouch1-dev libsndfile1-dev
./configure --prefix=/opt/wired
make && make install
```

You`re done. Enjoy.

---

### Post by lapsey on 2006-07-22
extracting, installing wired-libs ?

```
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
configure: error: Couldn't find libasound

```

```
~/Desktop/wired-libs-0.2$ sudo sh install-wired-libs.sh
Password:
Before install these specifics libs, you need to install some:
- alsa-libs, alsa-headers
- GTK 2

```

---

### Post by Boomy on 2006-07-22
I get the same errors.

---

