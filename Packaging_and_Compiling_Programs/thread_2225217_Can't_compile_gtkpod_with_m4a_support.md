---
title: "Can't compile gtkpod with m4a support"
date: 2014-05-20
forum: Packaging and Compiling Programs
---

### Post by flapane on 2014-05-20
Hi there, I've just upgraded to Ubuntu 14.04 from 13.10. 
Now I can't compile gtkpod with mp4 support. For the life of me I can't get rid of "**Cannot find faad. Conversion from m4a to mp3 not possible**", even if libfaad and libmp4v2 dev packages are installed.
Any hints?
Thanks in advance

---

### Post by ron998 on 2014-06-16
> **flapane said:**
> Any hints?
Hi
```
sudo apt-get build-dep gtkpod
```

Then ./configure shows...
```
Plugin Configuration :
---------------------------------
 CoverWeb Browser           .....: yes
 Media Player               .....: yes
 MP4 File Type              .....: yes
 M4A File Type              .....: yes
 Flac File Type             .....: yes
 Ogg File Type              .....: yes
 Clarity Display Widget     .....: yes
 Sound Juicer Widget        .....: no
 Support for cover download .....: yes -- will build with coverart download support

 Now type 'make' to build gtkpod 2.1.4,
 and then 'make install' for installation.
```

---

### Post by monkeybrain20122 on 2014-06-16
```
sudo apt-get install libfaad-dev
```

---

### Post by flapane on 2014-06-16
Apparently, there was somethng wrong with **faad** binary package.
I reinstalled it and it finally compiled flawlessy. :)

---

