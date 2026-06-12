---
title: "gcc &amp;&amp; g++ errros"
date: 2007-10-08
forum: Programming Talk
---

### Post by nitro_n2o on 2007-10-08
Hi all, 
I've been experiencing  weired issues with gcc and g++ the keep failing to compile giving me errors in stdlib or linux headers... does anybody have an idea of what might cause this:

from /home/nitro/alsa-driver-1.0.14rc1/acore/pcm.c:1:
/home/nitro/alsa-driver-1.0.14rc1/include/sound/pcm.h: In function ‘snd_pcm_mmap_data_open’:
/home/nitro/alsa-driver-1.0.14rc1/include/sound/pcm.h:977: error: dereferencing pointer to incomplete type
/home/nitro/alsa-driver-1.0.14rc1/include/sound/pcm.h: In function ‘snd_pcm_mmap_data_close’:
/home/nitro/alsa-driver-1.0.14rc1/include/sound/pcm.h:983: error: dereferencing pointer to incomplete type
make[3]: *** [/home/nitro/alsa-driver-1.0.14rc1/acore/pcm.o] Error 1
make[2]: *** [/home/nitro/alsa-driver-1.0.14rc1/acore] Error 2
make[1]: *** [_module_/home/nitro/alsa-driver-1.0.14rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2

when  trying to compile the alsa driver on my machine.... the errors referenced by gcc don't exist

---

### Post by maddog39 on 2007-10-08
As far as the stdlib problems, I'd make sure you have the entire build-essential package installed as that also gets you the development package for the standard C library. The errors you posted however look like they  have more to do with the source code you are trying to compile. I'd look for patches from the developer which fix compile errors, and see where that gets you.

---

### Post by j_g on 2007-10-08
Obviously, these compiler errors have to do with the ALSA (ie, sound) functions being used. I've just done a few programs that use ALSA and had no such problems. What is this /home/nitro/alsa-driver-1.0.14rc1 directory that contains a pcm.h file? That isn't one of the standard ALSA include directories. Offhand, it sounds like you may be using someone else's "sound framework" riding on top of ALSA, and the errors are in that framework. In such a case, you'd need to post the offending source code in that framework to get a definitive answer what is wrong with the code.

---

### Post by nitro_n2o on 2007-10-09
ohh this is just the src code for alsa straight from their website... I'm almost giving up on compiling ALSA (I don't have sound in my machine) but I also try to compile other things i keep getting (most of the time) unterminated #ifndef but I'm SURE that the code is fine .. in fact there is an #endif and the end of file...
this is really weired and frustrating.. 

does anybody have any idea

---

### Post by geraldm on 2007-10-10
The build setup being used is strange, I think, when I see that
the first make shows a different path than the second make.
The chance is increased that a header that you might expect to be 
included is not actually included due to a path mixup.

make[2]: *** [/home/nitro/alsa-driver-1.0.14rc1/acore] Error 2
make[1]: *** [_module_/home/nitro/alsa-driver-1.0.14rc1] Error 2

There is a chance that the "include/sound/pcm.h"  is coming from
your kernel headers, which path should be found in the Makefile.

If you do not find a correction easily, alsa is up to 1.0.15rc3.
I recommend getting the more recent source, rather than spend
time on the older version.

Gerald

---

