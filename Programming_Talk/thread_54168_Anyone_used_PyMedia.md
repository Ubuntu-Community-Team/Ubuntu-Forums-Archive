---
title: "Anyone used PyMedia?"
date: 2005-08-03
forum: Programming Talk
---

### Post by darthsabbath on 2005-08-03
Hi,

I was wondering if anyone's used the PyMedia ([www.pymedia.org](www.pymedia.org)) module.  I'm looking into playing around with the media processing capabilities of it, but I've had trouble compiling and installing.  Before I invest a significant amount of time into using this, I was wondering if it would be easier to just use command line utilities for my backend.

Thanks,
Phil

---

### Post by -DarkMind- on 2005-12-14
[QUOTE=darthsabbath]Hi,

I was wondering if anyone's used the PyMedia ([www.pymedia.org](www.pymedia.org)) module.  I'm looking into playing around with the media processing capabilities of it, but I've had trouble compiling and installing.  Before I invest a significant amount of time into using this, I was wondering if it would be easier to just use command line utilities for my backend.

Thanks,
Phil[/QUOTE]

a tried to compile and says:

Using UNIX configuration...

OGG          : found
VORBIS       : found
FAAD         : found
MP3LAME      : not found
VORBISENC    : found
Continue building pymedia ? [Y,n]:n


i have installed lame :(

---

### Post by Se7h on 2006-03-27
Pymedia has already a deb package for easier install. Anyone interest in the latest version (1.3.7) pm me.

---

### Post by wicho_anaya on 2008-06-03
Hi, i been trying to build pymedia 1.3.7.3 in python 2,5, but when i made 
python setup.py build i get this:

luis@luis-laptop:~/Documentos/Programas_python/pymedia-1.3.7.3$ python setup.py build
Using UNIX configuration...

OGG          : found
VORBIS       : found
FAAD         : found
MP3LAME      : found
VORBISENC    : found
ALSA         : found
Continue building pymedia ? [Y,n]:y
running build
running build_py
running build_ext
building 'pymedia.audio.acodec' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -DBUILD_NUM=1870 -DPATH_DEV_DSP="/dev/dsp" -DPATH_DEV_MIXER="/dev/mixer" -D_FILE_OFFSET_BITS=64 -DACCEL_DETECT=1 -DHAVE_MMX=1 -DHAVE_LINUX_DVD_STRUCT=1 -DDVD_STRUCT_IN_LINUX_CDROM_H=1 -DCONFIG_VORBIS -DCONFIG_VORBIS -DCONFIG_FAAD -DCONFIG_MP3LAME -DCONFIG_VORBIS -DCONFIG_ALSA -DHAVE_AV_CONFIG_H -DUDF_CACHE=1 -INone -INone -INone -I/usr/include/lame -INone -INone -I/home/luis/Documentos/Programas_python/pymedia-1.3.7.3 -Iaudio/ -I/usr/include/python2.5 -c audio/acodec/acodec.c -o build/temp.linux-i686-2.5/audio/acodec/acodec.o
In file included from audio/acodec/acodec.c:31:
audio/libavcodec/dsputil.h:485: error: declaración static de ‘lrintf’ después de una declaración que no es static
audio/acodec/acodec.c:249: aviso: inicialización desde un tipo de puntero incompatible
audio/acodec/acodec.c: En la función ‘ACodec_Encode’:
audio/acodec/acodec.c:668: aviso: el puntero que apunta en el paso del argumento 2 de ‘avcodec_encode_audio’ difiere en signo
error: command 'gcc' failed with exit status 1

I dont know how to fix it, anyone can help me?? Im using ubuntu 8.04

---

### Post by wicho_anaya on 2008-06-08
Hi, i'm interested about your deb package of pymedia 1.3.7, 'cause i installed a deb package of pymedia 1.3.5 but i doesn't work, my mail is wicho AT adep.dialetheia.net, if you can write me to tell me how can i get those file.... thanks

---

### Post by johnpaulett on 2008-06-18
I just wrote a simple guide to install PyMedia on Ubuntu 8.04:
[http://jhcore.com/2008/06/18/pymedia-on-ubuntu-hardy-heron/](http://jhcore.com/2008/06/18/pymedia-on-ubuntu-hardy-heron/)

-John

---

### Post by wicho_anaya on 2008-09-07
Hi, when i try to play an avi file using vplayer.py from the examples, i get this line:
*** glibc detected *** python: realloc(): invalid old size: 0x08253c00 ***

and then i get all the memory map, if somebody can tell me whats going on please?????


I'm using ubunbu hardy heron...

---

### Post by kknd on 2008-09-07
Theres a reason to don't use gstreamer?

---

### Post by Endolith on 2008-09-07
> **johnpaulett said:**
> I just wrote a simple guide to install PyMedia on Ubuntu 8.04:
[http://jhcore.com/2008/06/18/pymedia-on-ubuntu-hardy-heron/](http://jhcore.com/2008/06/18/pymedia-on-ubuntu-hardy-heron/)


Should we request that this be packaged for the repositories?

---

### Post by life_s_good on 2008-09-11
> **wicho_anaya said:**
> Hi, i been trying to build pymedia 1.3.7.3 in python 2,5, but when i made 
python setup.py build i get this:

luis@luis-laptop:~/Documentos/Programas_python/pymedia-1.3.7.3$ python setup.py build
Using UNIX configuration...

OGG          : found
VORBIS       : found
FAAD         : found
MP3LAME      : found
VORBISENC    : found
ALSA         : found
Continue building pymedia ? [Y,n]:y
running build
running build_py
running build_ext
building 'pymedia.audio.acodec' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -DBUILD_NUM=1870 -DPATH_DEV_DSP="/dev/dsp" -DPATH_DEV_MIXER="/dev/mixer" -D_FILE_OFFSET_BITS=64 -DACCEL_DETECT=1 -DHAVE_MMX=1 -DHAVE_LINUX_DVD_STRUCT=1 -DDVD_STRUCT_IN_LINUX_CDROM_H=1 -DCONFIG_VORBIS -DCONFIG_VORBIS -DCONFIG_FAAD -DCONFIG_MP3LAME -DCONFIG_VORBIS -DCONFIG_ALSA -DHAVE_AV_CONFIG_H -DUDF_CACHE=1 -INone -INone -INone -I/usr/include/lame -INone -INone -I/home/luis/Documentos/Programas_python/pymedia-1.3.7.3 -Iaudio/ -I/usr/include/python2.5 -c audio/acodec/acodec.c -o build/temp.linux-i686-2.5/audio/acodec/acodec.o
In file included from audio/acodec/acodec.c:31:
audio/libavcodec/dsputil.h:485: error: declaración static de ‘lrintf’ después de una declaración que no es static
audio/acodec/acodec.c:249: aviso: inicialización desde un tipo de puntero incompatible
audio/acodec/acodec.c: En la función ‘ACodec_Encode’:
audio/acodec/acodec.c:668: aviso: el puntero que apunta en el paso del argumento 2 de ‘avcodec_encode_audio’ difiere en signo
error: command 'gcc' failed with exit status 1

I dont know how to fix it, anyone can help me?? Im using ubuntu 8.04
In audio/acodec/acodec.c you may need to add


#define HAVE_LRINTF

So that you get:

#include <libavcodec/avcodec.h>
#define HAVE_LRINTF
#include "libavcodec/dsputil.h"
#include "version.h"

---

### Post by vinces1979 on 2009-06-18
Thanks life_s_good, your suggestion worked great

---

