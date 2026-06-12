---
title: "HOWTO: Fix UT2004 Sound"
date: 2007-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by fiendskull9 on 2007-01-12
After installing Kubunt 6.10, i attempted to install UT2004

when starting i had no sound, and looking at the terminal, i saw this message

```
open /dev/[sound/]dsp: Device or resource busy
```

The default OpenAL Installation isnt compiled with Artsd support (the sound daemon for KDE)

Heres how to fix the error

download [The Latest Source Code]("http://www.openal.org/openal_webstf/downloads/openal-0.0.8.tar.gz") from OpenAL's Website

Extract the tar
```
tar xvf openal-0.0.8.tar.gz
```

Go into the directory
```
cd openal-0.0.8
```

Configure with our needed flags, then compile
```
./configure --enable-arts --enable-alsa
```
```
make
```
```
sudo make install
```

After compiling, we need to edit our openalrc

User your favorite text editor (vim in my case)
```
vim ~/.openalrc
```

Now paste this into the file
```
(define devices '(native arts))
```

Save the file. and your good to go!

you should now have sound working in UT2004!

-clay

---

### Post by Tryke on 2007-01-21
I gave it a shot.... no dice. :(

---

### Post by stiankarlsen on 2007-03-03
no dice here either

---

### Post by nalmeth on 2007-03-20
To anyone without sound in UT2004, in edgy all I had to do was install this package:
```
libopenalpp-cvs1
```
It's available in the repo's

---

