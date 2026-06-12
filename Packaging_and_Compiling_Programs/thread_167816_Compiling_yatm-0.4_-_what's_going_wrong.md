---
title: "Compiling yatm-0.4 - what's going wrong?"
date: 2006-04-29
forum: Packaging and Compiling Programs
---

### Post by grayhorse on 2006-04-29
Hi all

I'm getting that sinking feeling: I tried to compile this neat little utility to speed up or slow down an MP3 or OGG file a while ago, got it running, and hosed my network connection at the same time, possibly with a rogue kernel up-/down-/sideways-grade which I still don't understand.

Since re-installing, I'm getting compile errors (see below)

"./configure" seems to work fine, but there's some subtlety here I don't have the background to work out.](*,) 

advthanksance

Grayhorse 

> 

ross@dragonhome:~/yatm-0.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for ao... yes
checking for Ogg... yes
checking for Vorbis... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DSP... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for unistd.h... (cached) yes
checking for string.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
ross@dragonhome:~/yatm-0.4$




> 
ross@dragonhome:~/yatm-0.4$ make
make  all-am
make[1]: Entering directory `/home/ross/yatm-0.4'
if g++ -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT yatm.o -MD -MP -MF ".deps/yatm.Tpo" -c -o yatm.o yatm.cc; \
then mv -f ".deps/yatm.Tpo" ".deps/yatm.Po"; else rm -f ".deps/yatm.Tpo"; exit 1; fi
yatm.cc:59: error: ‘SoundTouch’ in namespace ‘soundtouch’ does not name a type
yatm.cc:60: error: ‘SoundTouch’ in namespace ‘soundtouch’ does not name a type
yatm.cc:61: error: ‘SoundTouch’ in namespace ‘soundtouch’ does not name a type
yatm.cc:62: error: ‘SoundTouch’ in namespace ‘soundtouch’ does not name a type
yatm.cc: In function ‘int main(int, char**)’:
yatm.cc:104: error: ‘SoundTouch’ is not a member of ‘soundtouch’
yatm.cc:104: error: expected `;' before ‘SoundTouch’
yatm.cc:160: error: expected primary-expression before ‘,’ token
yatm.cc:161: error: expected primary-expression before ‘,’ token
yatm.cc:162: error: expected primary-expression before ‘,’ token
yatm.cc:163: error: expected primary-expression before ‘,’ token
yatm.cc: At global scope:
yatm.cc:184: error: ‘SoundTouch’ in namespace ‘soundtouch’ does not name a type
yatm.cc: In function ‘mad_flow decode_filter(void*, const mad_stream*, mad_frame*)’:
yatm.cc:246: error: request for member ‘setTempo’ in ‘* player->player::touch’, which is of non-class type ‘int’
yatm.cc:250: error: request for member ‘setTempo’ in ‘* player->player::touch’, which is of non-class type ‘int’
yatm.cc:254: error: request for member ‘setTempo’ in ‘* player->player::touch’, which is of non-class type ‘int’
yatm.cc:258: error: request for member ‘setTempo’ in ‘* player->player::touch’, which is of non-class type ‘int’
yatm.cc: In function ‘mad_flow process_output(void*, const mad_header*, mad_pcm*)’:
yatm.cc:342: error: request for member ‘setSampleRate’ in ‘* player->player::touch’, which is of non-class type ‘int’
yatm.cc:343: error: request for member ‘setChannels’ in ‘* player->player::touch’, which is of non-class type ‘int’
yatm.cc:344: error: request for member ‘putSamples’ in ‘* player->player::touch’, which is of non-class type ‘int’
yatm.cc:347: error: request for member ‘receiveSamples’ in ‘* player->player::touch’, which is of non-class type ‘int’
yatm.cc: At global scope:
yatm.cc:475: error: ‘SoundTouch’ in namespace ‘soundtouch’ does not name a type
yatm.cc: In function ‘int play_mpeg(int, int*, float, char*, char*)’:
yatm.cc:497: error: request for member ‘setTempo’ in ‘* player.player::touch’, which is of non-class type ‘int’
yatm.cc: At global scope:
yatm.cc:613: error: ‘SoundTouch’ in namespace ‘soundtouch’ does not name a type
yatm.cc: In function ‘int play_ao(int*, int, int)’:
yatm.cc:623: error: request for member ‘receiveSamples’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc: At global scope:
yatm.cc:638: error: ‘SoundTouch’ in namespace ‘soundtouch’ does not name a type
yatm.cc: In function ‘int play_vorbis(int, int*, float, const char*)’:
yatm.cc:697: error: request for member ‘setTempo’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:698: error: request for member ‘setSampleRate’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:699: error: request for member ‘setChannels’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:707: error: request for member ‘setTempo’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:711: error: request for member ‘setTempo’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:740: error: request for member ‘putSamples’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc: At global scope:
yatm.cc:752: error: ‘SoundTouch’ in namespace ‘soundtouch’ does not name a type
yatm.cc: In function ‘int play_speex(int, int*, float, char*)’:
yatm.cc:883: error: request for member ‘setTempo’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:884: error: request for member ‘setSampleRate’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:885: error: request for member ‘setChannels’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:897: error: request for member ‘setTempo’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:901: error: request for member ‘setTempo’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:939: error: request for member ‘putSamples’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc: At global scope:
yatm.cc:967: error: ‘SoundTouch’ in namespace ‘soundtouch’ does not name a type
yatm.cc: In function ‘int play_sndfile(int, int*, float, char*)’:
yatm.cc:998: error: request for member ‘setTempo’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:999: error: request for member ‘setSampleRate’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:1000: error: request for member ‘setChannels’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:1011: error: request for member ‘setTempo’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:1015: error: request for member ‘setTempo’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:1019: error: request for member ‘setTempo’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:1023: error: request for member ‘setTempo’ in ‘* touch’, which is of non-class type ‘int’
yatm.cc:1038: error: request for member ‘putSamples’ in ‘* touch’, which is of non-class type ‘int’
make[1]: *** [yatm.o] Error 1
make[1]: Leaving directory `/home/ross/yatm-0.4'
make: *** [all] Error 2

---

