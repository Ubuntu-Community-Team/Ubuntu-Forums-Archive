---
title: "Cinelerra under Dapper Drake 6.06  [ HowTO / Tutorial ]"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by lprofil on 2006-06-03
Hello guys,

please click on [this link here]("http://ubuntuforums.org/showthread.php?p=1091483"). 
By accident i posted this thread twice and left this half translated one over.

My apologies!

/lprofil

---

### Post by benobi on 2006-06-04
Man, I would love to follow your "How-to", but I just don't speak German (I mean, it looks like German). 
So, is there someone willing to translate that stuff ?
I hate just copying and pasting commands without knowing why !

Thanks !

---

### Post by yage on 2006-06-04
Well i didn't do so well with this one... The howto is missing some parts! I had to install libasound2 and libasound2-dev. Even then it didnt work. Doing configure gives me this output: 
```
Summary of mandatory components:
  libogg                  found
  libvorbis               found
  libvorbisenc            found
  libvorbisfile           found
  libtheora               found
  OpenEXR                 found
  libdv                   found
  libpng                  found
  libjpeg libraries       found
  libjpeg headers         found
  FreeType 2              found
  libx264 libraries       missing
  libx264 headers         missing
  libuuid libraries       found
  libuuid headers         found
  mjpegtools              found
  libfftw3 libraries      found
  libfftw3 headers        found
  liba52 libraries        found
  liba52 headers          found
  libmp3lame libraries    found
  libmp3lame headers      found
  libsndfile libraries    missing
  libsndfile headers      missing
  libfaac libraries       missing
  libfaac headers         missing
  libfaad libraries       found
  libfaad headers         found

Summary of optional components:
  ESD subsystem           found
ESD (Enlightenment Sound Daemon) is enabled
  ALSA subsystem          found
ALSA is enabled
  libraw1394              missing
  libiec61883             missing
  libavc1394 libraries    found
  libavc1394 headers      found
  librom1394 libraries    found
  librom1394 headers      found
Firewire is disabled

WARNING: Mandatory components are missing; compilation may fail!
```
And so i does... 
```
ar: .libs/reconmmx.o: No such file or directory
make[3]: *** [libmpeg3_video.la] Error 1
make[3]: Leaving directory `/opt/cinerella_cvs/hvirtual/libmpeg3/video'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/cinerella_cvs/hvirtual/libmpeg3'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/cinerella_cvs/hvirtual'
make: *** [all] Error 2
```
libraw1394.so is under /usr/lib/ so i think there is nothing missing?
This howto should be in english yes... This is German. Sorry to say but thats just waisted time...

Du kan jo prøve å lese en HOWTO hvis jeg skriver den på mitt språk? :-k 
In english this is: You can try to read a HOWTO if i write it in my language?

---

