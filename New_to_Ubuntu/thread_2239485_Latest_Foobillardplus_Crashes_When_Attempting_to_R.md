---
title: "Latest Foobillardplus Crashes When Attempting to Run on Ubuntu 14.04.1"
date: 2014-08-14
forum: New to Ubuntu
---

### Post by KJ55 on 2014-08-14
The latest Foobillardplus (3.43-svn170+ddfsg-1) that I acquired from the Trusty (14.04 LTS) Repository Crashes When Attempting to Run on Ubuntu 14.04.1.  I'm receiving the following output when starting Foobillardplus (++) from a terminal:

```
hjones@hjones:~$ foobillardplus
Check for Dialog-Program
Dialog Program zenity found
Data dir entry
Browser initialized for history-functions
Player variables initialized
Use config-file: /home/hjones/.foobillardrc
Base-Configuration initialized
processing option 0=human
processing option 1=ai
processing option 2=Ken
processing option 3=Computer
processing option 5=Computer
processing option 10=Computer
processing option 13=off
processing option 14=7.000000
processing option 17=7.000000
processing option 19=on
processing option 20=0.000000
processing option 21=0.000000
processing option 22=v
processing option 23=off
processing option 25=m
processing option 26=192.168.1.1
processing option 27=56341
processing option 28=830x647
processing option 30=firefox
processing option 31=on
processing option 32=off
processing option 33=128
processing option 34=off
processing option 35=off
processing option 36=off
processing option 37=off
processing option 38=match
processing option 39=off
processing option 40=500.000000
processing option 41=on
processing option 42=on
processing option 43=on
processing option 44=2
processing option 45=on
processing option 46=on
processing option 47=on
processing option 48=10
processing option 49=90
processing option 50=10
processing option 51=off
processing option 52=off
processing option 53=0.000000
processing option 54=on
processing option 55=off
processing option 56=on
processing option 57=0
processing option 58=on
processing option 59=1
processing option 60=en
Configuration processed
Language initialized
History system initialized
OpenGL context initialized
extension_cubemap_ARB=1
extension_multitexture_ARB=1
extension_combine_ARB: 1
extension_dot3_ARB: 1
extension_vp_ARB: 1
extension_ts_NV=0
extension_rc_NV=0
extension_vp_NV=0
options_multisample: 1
Anisotropic Filter 1.
Load 2D Graphics start
Graphics loaded and initialized
Create balls scene
Create table object
Initialize billiard table-frame
Initialize table-texture
Initialize clothing table texture
Initialize new table GL object
Generate furrow object
Generate lower upper furrow object
Generate some middle pocket triangles object
Generate lower left, lower right, upper right, upper left pocket triangles object
Generate left, right pocket triangles object
Generate left, right pocket fans triangles object
Generate pocket objects: Not carom: Call to build a table border
lower Call to build a table border
upper left Call to build a table border
upper right Call to build a table border
lower left Call to build a table border
lower right Call to build a table border

Generate diamonds border objects
Generate gold/silver edges and cover objects
Generate bumpers for gold/silver edges and covers
Generate side holes
Generate wood frame
Return the new table object
Create room object
Graphics loaded and initialized
Status-line initialized
Player initialized
Another error code means that the font file could not e opened or read, or simply that it is broken

** (zenity:14556): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

I'm running the program on the following hardware: Athlon 2200+ (1.6 GHz) with 2 GB of RAM, and an AMD Radeon 9600 Pro video card with 128 MB of RAM.

I have visited the author's/authors' website [http://foobillardplus.sourceforge.net/needs.html]("http://foobillardplus.sourceforge.net/needs.html") to try to compile the program from the latest source code.  I was able to compile and run it successfully; however, I had to disable sound due to the program crashing due to a different error (the SDL_mixer file I downloaded from the Trusty Repository lack OGG and MP3 support).  

Here's how I compiled the program that provided the error concerning the SDL_mixer lacking OGG and MP3 support from the author's/authors' foobillardplus-3.42beta source code:

```
hjones@hjones:~/foobillardplus-3.42beta$ make clean
Making clean in src
make[1]: Entering directory `/home/hjones/foobillardplus-3.42beta/src'
test -z "foobillardplus" || rm -f foobillardplus
rm -f *.o
make[1]: Leaving directory `/home/hjones/foobillardplus-3.42beta/src'
make[1]: Entering directory `/home/hjones/foobillardplus-3.42beta'
make[1]: Nothing to be done for `clean-am'.
make[1]: Leaving directory `/home/hjones/foobillardplus-3.42beta'


hjones@hjones:~/foobillardplus-3.42beta$ ./configure --enable-sse=yes 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for png_read_image in -lpng... yes
checking for SDL_Init in -lSDL... yes
checking for SDL_LockAudio in -lSDL... yes
checking for SDLNet_Init in -lSDL_net... yes
checking for Mix_OpenAudio in -lSDL_mixer... yes
no mingw/msys Windows support
checking for pow in -lm... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for unistd.h... (cached) yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for string.h... (cached) yes
checking endian.h usability... yes
checking endian.h presence... yes
checking for endian.h... yes
checking GL/glu.h usability... yes
checking GL/glu.h presence... yes
checking for GL/glu.h... yes
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for socket... yes
checking for poll... yes
checking whether to enable aggressive optimization flags... no
checking whether to enable standard optimization flags... no
checking whether to enable special optimization flags... no
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating foobillardplus.spec
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands

General configuration ================================================

    CC:                       gcc
    CFLAGS:                   
    LDFLAGS:                  

    Install path:             /opt/foobillardplus
    Binary dir:               /opt/foobillardplus/bin
    Data rootdir:             /opt/foobillardplus/data
    Data dir:                 /opt/foobillardplus/data
    Locale dir:               /opt/foobillardplus/data/locale
    Doc dir:                  /opt/foobillardplus/data/locale

    Debug flags:              
    Optimization flags:       
    Mathsingle precision:     yes
    Sound compiling:          yes
    Generic Touchdevice:      no
    WeTab Tablet compiling:   no
    Network compiling:        yes
    use sse                   yes
    fast math routines        yes

Now run make ...

hjones@hjones:~/foobillardplus-3.42beta$ make
Making all in src
make[1]: Entering directory `/home/hjones/foobillardplus-3.42beta/src'
make  all-am
make[2]: Entering directory `/home/hjones/foobillardplus-3.42beta/src'
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT billard3d.o -MD -MP -MF .deps/billard3d.Tpo -c -o billard3d.o billard3d.c
billard3d.c: In function ‘player_copy’:
billard3d.c:2267:6: note: The ABI for passing parameters with 16-byte alignment has changed in GCC 4.6
 void player_copy(struct Player * player, struct Player src)
      ^
mv -f .deps/billard3d.Tpo .deps/billard3d.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT language.o -MD -MP -MF .deps/language.Tpo -c -o language.o language.c
mv -f .deps/language.Tpo .deps/language.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT billmove.o -MD -MP -MF .deps/billmove.Tpo -c -o billmove.o billmove.c
mv -f .deps/billmove.Tpo .deps/billmove.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT billard.o -MD -MP -MF .deps/billard.Tpo -c -o billard.o billard.c
mv -f .deps/billard.Tpo .deps/billard.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT vmath.o -MD -MP -MF .deps/vmath.Tpo -c -o vmath.o vmath.c
mv -f .deps/vmath.Tpo .deps/vmath.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT ball.o -MD -MP -MF .deps/ball.Tpo -c -o ball.o ball.c
mv -f .deps/ball.Tpo .deps/ball.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT png_loader.o -MD -MP -MF .deps/png_loader.Tpo -c -o png_loader.o png_loader.c
mv -f .deps/png_loader.Tpo .deps/png_loader.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT table.o -MD -MP -MF .deps/table.Tpo -c -o table.o table.c
mv -f .deps/table.Tpo .deps/table.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT queue.o -MD -MP -MF .deps/queue.Tpo -c -o queue.o queue.c
mv -f .deps/queue.Tpo .deps/queue.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT aiplayer.o -MD -MP -MF .deps/aiplayer.Tpo -c -o aiplayer.o aiplayer.c
mv -f .deps/aiplayer.Tpo .deps/aiplayer.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT options.o -MD -MP -MF .deps/options.Tpo -c -o options.o options.c
mv -f .deps/options.Tpo .deps/options.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT evaluate_move.o -MD -MP -MF .deps/evaluate_move.Tpo -c -o evaluate_move.o evaluate_move.c
mv -f .deps/evaluate_move.Tpo .deps/evaluate_move.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT helpscreen.o -MD -MP -MF .deps/helpscreen.Tpo -c -o helpscreen.o helpscreen.c
mv -f .deps/helpscreen.Tpo .deps/helpscreen.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT textobj.o -MD -MP -MF .deps/textobj.Tpo -c -o textobj.o textobj.c
mv -f .deps/textobj.Tpo .deps/textobj.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT font.o -MD -MP -MF .deps/font.Tpo -c -o font.o font.c
mv -f .deps/font.Tpo .deps/font.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT sys_stuff.o -MD -MP -MF .deps/sys_stuff.Tpo -c -o sys_stuff.o sys_stuff.c
mv -f .deps/sys_stuff.Tpo .deps/sys_stuff.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT net_socket.o -MD -MP -MF .deps/net_socket.Tpo -c -o net_socket.o net_socket.c
mv -f .deps/net_socket.Tpo .deps/net_socket.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT sound_stuff.o -MD -MP -MF .deps/sound_stuff.Tpo -c -o sound_stuff.o sound_stuff.c
mv -f .deps/sound_stuff.Tpo .deps/sound_stuff.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT menu.o -MD -MP -MF .deps/menu.Tpo -c -o menu.o menu.c
mv -f .deps/menu.Tpo .deps/menu.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT bumpref.o -MD -MP -MF .deps/bumpref.Tpo -c -o bumpref.o bumpref.c
mv -f .deps/bumpref.Tpo .deps/bumpref.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT room.o -MD -MP -MF .deps/room.Tpo -c -o room.o room.c
mv -f .deps/room.Tpo .deps/room.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT mesh.o -MD -MP -MF .deps/mesh.Tpo -c -o mesh.o mesh.c
mv -f .deps/mesh.Tpo .deps/mesh.Po
gcc -DHAVE_CONFIG_H -I.    -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm  -MT history.o -MD -MP -MF .deps/history.Tpo -c -o history.o history.c
mv -f .deps/history.Tpo .deps/history.Po
gcc -Wall `freetype-config --cflags` `sdl-config --cflags` -DNO_NV_BUMPREF -DNO_NV_FRESNEL -DUSE_SOUND    -DNETWORKING -DVMATH_SINGLE_PRECISION  -DUSE_SSE -msse  -DFAST_MATH -lm   `freetype-config --libs` `sdl-config --libs`  -o foobillardplus billard3d.o language.o billmove.o billard.o vmath.o ball.o png_loader.o table.o queue.o aiplayer.o options.o evaluate_move.o helpscreen.o textobj.o font.o sys_stuff.o net_socket.o sound_stuff.o menu.o bumpref.o room.o mesh.o history.o -lGL -lGLU -lpng -lfreetype -lSDL_net -lSDL_mixer -lm -lSDL_mixer -lSDL_net -lSDL -lSDL -lpng 
make[2]: Leaving directory `/home/hjones/foobillardplus-3.42beta/src'
make[1]: Leaving directory `/home/hjones/foobillardplus-3.42beta/src'
make[1]: Entering directory `/home/hjones/foobillardplus-3.42beta'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/hjones/foobillardplus-3.42beta'



hjones@hjones:~/foobillardplus-3.42beta$ sudo checkinstall -D make install
[sudo] password for hjones: 

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@hjones ]
1 -  Summary: [ foobillardplus ]
2 -  Name:    [ foobillardplus ]
3 -  Version: [ 3.42beta ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ foobillardplus-3.42beta ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ foobillardplus ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/hjones/foobillardplus-3.42beta/src'
make[2]: Entering directory `/home/hjones/foobillardplus-3.42beta/src'
 /bin/mkdir -p '/opt/foobillardplus/bin'
  /usr/bin/install -c foobillardplus '/opt/foobillardplus/bin'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/hjones/foobillardplus-3.42beta/src'
make[1]: Leaving directory `/home/hjones/foobillardplus-3.42beta/src'
make[1]: Entering directory `/home/hjones/foobillardplus-3.42beta'
make[2]: Entering directory `/home/hjones/foobillardplus-3.42beta'
make[2]: Nothing to be done for `install-exec-am'.
make  install-data-hook
make[3]: Entering directory `/home/hjones/foobillardplus-3.42beta'
mkdir -p /opt/foobillardplus/data
cp -p ./data/* /opt/foobillardplus/data -R
cp -p ./AUTHORS /opt/foobillardplus
cp -p ./COPYING /opt/foobillardplus
cp -p ./INSTALL /opt/foobillardplus
cp -p ./README /opt/foobillardplus
cp -p ./ChangeLog /opt/foobillardplus
cp -p ./TODO /opt/foobillardplus
cp -p ./foobillardplus.desktop /opt/foobillardplus
cp -p ./foobillardplus.png /opt/foobillardplus
cp -p ./foobillardplus.xbm /opt/foobillardplus
make[3]: Leaving directory `/home/hjones/foobillardplus-3.42beta'
make[2]: Leaving directory `/home/hjones/foobillardplus-3.42beta'
make[1]: Leaving directory `/home/hjones/foobillardplus-3.42beta'

======================== Installation successful ==========================

Copying documentation directory...
./
./ChangeLog
./README
./TODO
./INSTALL
./COPYING
./AUTHORS
./NEWS

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/hjones/foobillardplus-3.42beta/foobillardplus_3.42beta-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r foobillardplus

**********************************************************************

hjones@hjones:~/foobillardplus-3.42beta$ cd /opt/foobillardplus/bin
hjones@hjones:/opt/foobillardplus/bin$ ./foobillardplus
Usage: foobillardplus [--option [<arg>]]\n  Options:\n--player1 <arg>
     arg=ai|human set player1 ai/human
--player2 <arg>
     arg=ai|human set player2 ai/human
--p1 <arg>
     arg=ai|human set player1 ai/human
--p2 <arg>
     arg=ai|human set player2 ai/human
--name1 <arg>
     Set name of player1
--name2 <arg>
     Set name of player2
--8ball 
     8ball pool game
--9ball 
     9ball pool game
--carambol 
     Carambol billard game
--snooker 
     Snooker billard game
--chromeblue 
     Blue table with chrome edges
--goldgreen 
     Green table with gold edges
--goldred 
     Red table with gold edges
--blackbeige 
     Beige table with black metal
--tronmode <arg>
     Toggle Tron Mode
--tablesize <arg>
     Table size (length) in foot (default=7.0)
--lensflare 
     Turn on lens flare
--nolensflare 
     Turn off lens flare
--poslight 
     Use positional light
--dirlight 
     Use directional light
--vsync <arg>
     arg=on|off
--ai1err <arg>
     To err is artificial (player1 error 0..1)
--ai2err <arg>
     To err is artificial (player2 error 0..1)
--balldetail <arg>
     Set ball detail l[ow] m[edium] h[igh] or v[eryhigh]
--glassball <arg>
     arg=on|off Glassballs on or off
--rgstereo 
     Start in stereo mode (red-green(cyan))
--rgaim <arg>
     arg=left|right|middle for aiming eye position
--hostaddr <arg>
     arg=IP-address for TCP/IP connection
--portnum <arg>
     arg=port# for TCP/IP connection
--geometry <arg>
     <width>x<height> window geometry
--fullscreen 
     Play in fullscreen mode
--browser <arg>
     arg= browsername in path (default: firefox)
--freemove <arg>
     arg=on|off free move in external view mode
--cuberef <arg>
     arg=on|off rendered cubemap reflections
--cuberes <arg>
     arg=<texture size for cuberef> (must be power of 2)
--ballsphere <arg>
     arg=on|off
--bumpref <arg>
     arg=on|off bumpmap reflections of edges
--bumpwood <arg>
     arg=on|off bumpmap of wood covers
--balltraces <arg>
     arg=on|off trace lines of balls
--gamemode <arg>
     arg=match|training|tournament
--avatar <arg>
     arg=on|off enable/disable avatar
--tourfast <arg>
     arg=1.0..10.0 AI fast motion ratio for tournament
--showbuttons <arg>
     arg=on|off
--jumpshots <arg>
     arg=on|off
--aliasing <arg>
     arg=on|off
--aliasmax <arg>
     fsaa value 1,2,4,8
--statustext <arg>
     arg=on|off
--usesound <arg>
     arg=on|off
--usemusic <arg>
     arg=on|off
--musicvol <arg>
     Volume 0-128
--soundvol <arg>
     Volume 0-128
--pcarambol <arg>
     arg=5-100
--controlkind <arg>
     arg=on|off
--aibirdview <arg>
     arg=on|off
--anisotrop <arg>
     arg=on|off
--mouseshoot <arg>
     arg=on|off
--auto_freemove <arg>
     arg=on|off
--fsaa <arg>
     arg=on|off
--roomtexture <arg>
     arg=on|off
--furnituretex <arg>
     arg=on|off
--netspeed <arg>
     arg=1-5 Network-Speed slow to high
--netcompatible <arg>
     arg=on|off
--help 
     This help
/home/hjones/.foobillardrc
./foobillardplus: unrecognized option '--oldmoving=off'
./foobillardplus: unrecognized option '--language=en'
extension_cubemap_ARB=1
extension_multitexture_ARB=1
extension_combine_ARB: 1
extension_dot3_ARB: 1
extension_vp_ARB: 1
extension_ts_NV=0
extension_rc_NV=0
extension_vp_NV=0
options_multisample: 1
Anisotropic Filter 1.
Mix_Init: Failed to init both ogg and mp3 support!
Check only for ogg.
Mix_Init: Mixer not built with MP3 support
*** stack smashing detected ***: ./foobillardplus terminated
Aborted (core dumped)
hjones@hjones:/opt/foobillardplus/bin$ 

```

I have reviewed all the necessary files required for compiling this program in Synaptic Package Manager, and I have everything (both binaries and devel files) installed.

I believe that SimpleDirectMedia Layer (SDL) may be messed up in the Repository for Ubuntu 14.04 (without OGG and MP3 support), but I don't know that for sure.  I can't acquire a binary from the SDL site at [http://www.libsdl.org/download-1.2.php]("http://www.libsdl.org/download-1.2.php"), and compiling this program may be beyond my capabilities.

Help, please.  I really like the looks of the new Foobillardplus.  But, I would really like to hear the music they added to program.  :)

---

### Post by westie457 on 2014-08-14
Hi, not sure how much help I can give with this.

Installed from the repo's, first run output was this.```
graham@Noname:~$ foobillardplusCheck for Dialog-Program
Dialog Program zenity found
Data dir entry
Browser initialized for history-functions
Player variables initialized
Use config-file: /home/graham/.foobillardrc
Base-Configuration initialized
Configuration processed
Language initialized
History system initialized
OpenGL context initialized
extension_cubemap_ARB=1
extension_multitexture_ARB=1
extension_combine_ARB: 1
extension_dot3_ARB: 1
extension_vp_ARB: 1
extension_ts_NV=1
extension_rc_NV=1
extension_vp_NV=1
options_multisample: 1
Anisotropic Filter 1.
Load 2D Graphics start
Graphics loaded and initialized
Create balls scene
Create table object
Initialize billiard table-frame
Initialize table-texture
Initialize clothing table texture
Initialize new table GL object
Generate furrow object
Generate lower upper furrow object
Generate some middle pocket triangles object
Generate lower left, lower right, upper right, upper left pocket triangles object
Generate left, right pocket triangles object
Generate left, right pocket fans triangles object
Generate pocket objects: Not carom: Call to build a table border
lower Call to build a table border
upper left Call to build a table border
upper right Call to build a table border
lower left Call to build a table border
lower right Call to build a table border


Generate diamonds border objects
Generate gold/silver edges and cover objects
Generate bumpers for gold/silver edges and covers
Generate side holes
Generate wood frame
Return the new table object
Create room object
Graphics loaded and initialized
Status-line initialized
Player initialized
Players text initialized
Game restart for the selected start-game
Mix_Init: Failed to init both ogg and mp3 support!
Check only for ogg.
Mix_Init: Mixer not built with MP3 support
Sound-system initialized
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Play sound-intro
Initialize default mesh-graphics
Initialize default Sofa object
Initialize default Chair object
Initialize default Table object
Initialize default Fireplace object
Initialize default ceiling-lamp object
Initialize fire object
load fireplace fire graphics
Create fire no: 0 of 14
Create fire no: 1 of 14
Create fire no: 2 of 14
Create fire no: 3 of 14
Create fire no: 4 of 14
Create fire no: 5 of 14
Create fire no: 6 of 14
Create fire no: 7 of 14
Create fire no: 8 of 14
Create fire no: 9 of 14
Create fire no: 10 of 14
Create fire no: 11 of 14
Create fire no: 12 of 14
Create fire no: 13 of 14
Initialize fire lists completed
Graphic meshes initialized
Run into game loop
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()

```

Here is the output after installing 'vorbis-tools and K/L/X/Ubuntu-restricted-extras'
```
graham@Noname:~$ foobillardplus
Check for Dialog-Program
Dialog Program zenity found
Data dir entry
Browser initialized for history-functions
Player variables initialized
Use config-file: /home/graham/.foobillardrc
Base-Configuration initialized
processing option 0=human
processing option 1=ai
processing option 2=graham
processing option 3=Computer_1
processing option 5=Computer_1
processing option 10=Computer_1
processing option 13=off
processing option 14=7.000000
processing option 17=7.000000
processing option 19=on
processing option 20=0.000000
processing option 21=0.300000
processing option 22=v
processing option 23=off
processing option 25=m
processing option 26=192.168.1.1
processing option 27=56341
processing option 28=1317x750
processing option 30=firefox
processing option 31=off
processing option 32=on
processing option 33=128
processing option 34=off
processing option 35=off
processing option 36=off
processing option 37=off
processing option 38=match
processing option 39=off
processing option 40=30.000000
processing option 41=on
processing option 42=on
processing option 43=on
processing option 44=2
processing option 45=on
processing option 46=on
processing option 47=on
processing option 48=10
processing option 49=90
processing option 50=10
processing option 51=off
processing option 52=off
processing option 53=0.000000
processing option 54=on
processing option 55=off
processing option 56=on
processing option 57=0
processing option 58=on
processing option 59=1
processing option 60=en
Configuration processed
Language initialized
History system initialized
OpenGL context initialized
extension_cubemap_ARB=1
extension_multitexture_ARB=1
extension_combine_ARB: 1
extension_dot3_ARB: 1
extension_vp_ARB: 1
extension_ts_NV=1
extension_rc_NV=1
extension_vp_NV=1
options_multisample: 1
Anisotropic Filter 1.
Load 2D Graphics start
Graphics loaded and initialized
Create balls scene
Create table object
Initialize billiard table-frame
Initialize table-texture
Initialize clothing table texture
Initialize new table GL object
Generate furrow object
Generate lower upper furrow object
Generate some middle pocket triangles object
Generate lower left, lower right, upper right, upper left pocket triangles object
Generate left, right pocket triangles object
Generate left, right pocket fans triangles object
Generate pocket objects: Not carom: Call to build a table border
lower Call to build a table border
upper left Call to build a table border
upper right Call to build a table border
lower left Call to build a table border
lower right Call to build a table border


Generate diamonds border objects
Generate gold/silver edges and cover objects
Generate bumpers for gold/silver edges and covers
Generate side holes
Generate wood frame
Return the new table object
Create room object
Graphics loaded and initialized
Status-line initialized
Player initialized
Players text initialized
Game restart for the selected start-game
Mix_Init: Failed to init both ogg and mp3 support!
Check only for ogg.
Mix_Init: Mixer not built with MP3 support
Sound-system initialized
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Tessellation Error: gluTessBeginContour() must precede a gluTessEndContour()
Tessellation Error: gluTessEndContour() must follow a gluTessBeginContour()
Play sound-intro
Initialize default mesh-graphics
Initialize default Sofa object
Initialize default Chair object
Initialize default Table object
Initialize default Fireplace object
Initialize default ceiling-lamp object
Initialize fire object
load fireplace fire graphics
Create fire no: 0 of 14
Create fire no: 1 of 14
Create fire no: 2 of 14
Create fire no: 3 of 14
Create fire no: 4 of 14
Create fire no: 5 of 14
Create fire no: 6 of 14
Create fire no: 7 of 14
Create fire no: 8 of 14
Create fire no: 9 of 14
Create fire no: 10 of 14
Create fire no: 11 of 14
Create fire no: 12 of 14
Create fire no: 13 of 14
Initialize fire lists completed
Graphic meshes initialized
Run into game loop
Initialize billiard table-frame
Initialize table-texture
Initialize clothing table texture
Initialize new table GL object
Generate furrow object
Generate lower upper furrow object
Generate some middle pocket triangles object
Generate lower left, lower right, upper right, upper left pocket triangles object
Generate left, right pocket triangles object
Generate left, right pocket fans triangles object
Generate pocket objects: Not carom: Call to build a table border
lower Call to build a table border
upper left Call to build a table border
upper right Call to build a table border
lower left Call to build a table border
lower right Call to build a table border


Generate diamonds border objects
Generate gold/silver edges and cover objects
Generate bumpers for gold/silver edges and covers
Generate side holes
Generate wood frame
Return the new table object
Initialize billiard table-frame
Initialize table-texture
Initialize clothing table texture
Initialize new table GL object
Generate furrow object
Generate lower upper furrow object
Generate some middle pocket triangles object
Generate lower left, lower right, upper right, upper left pocket triangles object
Generate left, right pocket triangles object
Generate left, right pocket fans triangles object
Generate pocket objects: Not carom: Call to build a table border
lower Call to build a table border
upper left Call to build a table border
upper right Call to build a table border
lower left Call to build a table border
lower right Call to build a table border


Generate diamonds border objects
Generate gold/silver edges and cover objects
Generate bumpers for gold/silver edges and covers
Generate side holes
Generate wood frame
Return the new table object

```

The first had no sound and the second one had sound.

Hope this helps.

---

### Post by KJ55 on 2014-08-14
I had the Ubuntu-restricted-extras installed, but not the restricted-extras for Kubuntu/Lubuntu/Xubuntu.  

Nor did I have vorbis-tools package installed.  I went to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"), and search and found it; since I was unfamiliar with this package.  It sounded promising; therefore, I installed it through Synaptic Package manager.  i tried running it from a terminal, and here's my unchanged output from foobillardplus:

```
hjones@hjones:~$ foobillardplus
Check for Dialog-Program
Dialog Program zenity found
Data dir entry
Browser initialized for history-functions
Player variables initialized
Use config-file: /home/hjones/.foobillardrc
Base-Configuration initialized
processing option 0=human
processing option 1=ai
processing option 2=Ken
processing option 3=Computer
processing option 5=Computer
processing option 10=Computer
processing option 13=off
processing option 14=7.000000
processing option 17=7.000000
processing option 19=on
processing option 20=0.000000
processing option 21=0.000000
processing option 22=v
processing option 23=off
processing option 25=m
processing option 26=192.168.1.1
processing option 27=56341
processing option 28=830x647
processing option 30=firefox
processing option 31=on
processing option 32=off
processing option 33=128
processing option 34=off
processing option 35=off
processing option 36=off
processing option 37=off
processing option 38=match
processing option 39=off
processing option 40=500.000000
processing option 41=on
processing option 42=on
processing option 43=on
processing option 44=2
processing option 45=on
processing option 46=on
processing option 47=on
processing option 48=10
processing option 49=90
processing option 50=10
processing option 51=off
processing option 52=off
processing option 53=0.000000
processing option 54=on
processing option 55=off
processing option 56=on
processing option 57=0
processing option 58=on
processing option 59=1
processing option 60=en
Configuration processed
Language initialized
History system initialized
OpenGL context initialized
extension_cubemap_ARB=1
extension_multitexture_ARB=1
extension_combine_ARB: 1
extension_dot3_ARB: 1
extension_vp_ARB: 1
extension_ts_NV=0
extension_rc_NV=0
extension_vp_NV=0
options_multisample: 1
Anisotropic Filter 1.
Load 2D Graphics start
Graphics loaded and initialized
Create balls scene
Create table object
Initialize billiard table-frame
Initialize table-texture
Initialize clothing table texture
Initialize new table GL object
Generate furrow object
Generate lower upper furrow object
Generate some middle pocket triangles object
Generate lower left, lower right, upper right, upper left pocket triangles object
Generate left, right pocket triangles object
Generate left, right pocket fans triangles object
Generate pocket objects: Not carom: Call to build a table border
lower Call to build a table border
upper left Call to build a table border
upper right Call to build a table border
lower left Call to build a table border
lower right Call to build a table border

Generate diamonds border objects
Generate gold/silver edges and cover objects
Generate bumpers for gold/silver edges and covers
Generate side holes
Generate wood frame
Return the new table object
Create room object
Graphics loaded and initialized
Status-line initialized
Player initialized
Another error code means that the font file could not e opened or read, or simply that it is broken

** (zenity:21128): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
hjones@hjones:~$ 

```

On my monitor, I see attached.

There may be a problem with the freetype2 font?

I don't believe I should have the restricted-extras for Kubuntu/Lubuntu/Xubuntu installed on my Ubuntu 14.04.1 LTS "ONLY" installation.  I know I can install them, and in my desperate attempt to get this "very cool and updated" FooBillardplus game installed I may try installing them.  I don't believe they would damage my Ubuntu installtion.  I will install them later.  I still only have a 28.8 Kbps dial-up connection here in the sticks of Kentucky, and these are 10 or so megabytes each.  :(

---

### Post by grahammechanical on 2014-08-14
The web sites says we need freetype2 installed and it is not be installed default. Well, not on my system.

[COLOR=#000000][FONT=Ubuntu Mono]Another error code means that the font file could not e opened or read, or simply that it is broken[/FONT][/COLOR][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif].[/FONT]

---

### Post by sotiris2 on 2014-08-14
[libfreetype6](https://launchpad.net/ubuntu/+source/freetype) is supposed to be the freetype2 libraries for ubuntu but installing them does not solve the problem.

Further
```
strace foobilardplus
```includes```
open("DejaVuSans.ttf", O_RDONLY)        = -1 ENOENT (No such file or directory)write(2, "Another error code means that th"..., 100Another error code means that the font file could not e opened or read, or simply that it is broken
) = 100
```Despite having [fonts-dejavu](https://launchpad.net/ubuntu/+source/fonts-dejavu) installed.

---

### Post by CantankRus on 2014-08-14
FYI, out of curiosity I just installed this through synaptic and played a game with sound no problems.
```
System:    Host: Trusty Kernel: 3.13.0-34-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 1400.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.38
Memory:    1534.3/3935.1MB
```

---

### Post by KJ55 on 2014-08-14
> **sotiris2 said:**
> [libfreetype6](https://launchpad.net/ubuntu/+source/freetype) is supposed to be the freetype2 libraries for ubuntu but installing them does not solve the problem.


Further
```
strace foobilardplus
```includes```
open("DejaVuSans.ttf", O_RDONLY)        = -1 ENOENT (No such file or directory)write(2, "Another error code means that th"..., 100Another error code means that the font file could not e opened or read, or simply that it is broken
) = 100
```Despite having [fonts-dejavu](https://launchpad.net/ubuntu/+source/fonts-dejavu) installed.

And, yes I have libfreetype6 package installed.

I received the following output (it looks like it's the same as you received):

```
open("DejaVuSans.ttf", O_RDONLY)        = -1 ENOENT (No such file or directory)
write(2, "Another error code means that th"..., 100Another error code means that the font file could not e opened or read, or simply that it is broken
) = 100
rt_sigaction(SIGINT, {SIG_IGN, [], 0}, {0xb7425170, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_IGN, [], 0}, {0xb741d8f0, [], 0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
clone(child_stack=0, flags=CLONE_PARENT_SETTID|SIGCHLD, parent_tidptr=0xbfb4d2d0) = 4406
waitpid(4406, 
** (zenity:4407): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

And, yes I have fonts-dejavu installed.

I don't know if you're running Foobillardplus on a 32-bit version or 64-bit version of Ubuntu.  Since I have an Athlon 2200+ processor; I'm running the 32-bit version of Ubuntu.

---

### Post by sotiris2 on 2014-08-14
I am running a 64bit version. I think those packages are arch indipendent or only 32bit since installing with :i386 got me just an already latest version message.

---

### Post by KJ55 on 2014-08-14
It was a thought, and wishful thinking on my part.  But, you're right.  

I really would like to get this cool enhanced (plus) version of Foobillard (with music now) up and running.  

BTW: My Ubuntu 14.04.1 installtion is a fresh install of Ubuntu 14.04.1 LTS, after deleting my partition containing 12.04.4 LTS, formatting it, then installing 14.04.1 from DVD.  And, yes I do have a separate partition on my hard drive for /home (I mentioned this because I still have my old configuration file ".foobillardrc" for the previous version of FooBillard,  that I ran in Ubuntu 12.04.4).

---

### Post by KJ55 on 2014-08-14
Since I downloaded the author's or authors' source code for the latest FooBillardPlus; I shall get to reading the source code.  Maybe I'll get lucky, and find a solution.  NOT...I'm an old dude (60 years old), and programming in C - a lost cause...lol.  My B.S. (********) degree was in Computer IS (we're not trained to be programmers).  :)

---

### Post by KJ55 on 2014-08-17
I have reviewed the source code from the author and no help.  But; I don't claim to be a C programmer, either.                                                                                                                                                     

In order to play the game; I could not compile sound into the game, or foobillardplus terminated (an abort and core dump).  Also; I noted that even with the sound not compiled in, you still had an unstable program without the fonts-dejavu package installed from the Trusty (14.04 LTS) Repository.  And, you had to have the libfreetype6 packages installed from the Trusty (14.04 LTS) Repository for the binaries/development installs of freetype2.

I summary, I did the following to get Foobillardplus working (without sound) after installing all the necessary dependencies packages:

(Please refer to the author's website at [http://foobillardplus.sourceforge.net/needs.html](http://foobillardplus.sourceforge.net/needs.html))

After I downloaded the source; I extracted it to my home folder in the foobillardplus-3.42beta folder.

```
cd ~/foobillardplus-3.42beta

sudo aclocal --force

sudo autoconf -f

sudo autoheader -f

sudo automake -a -c -f

./configure --enable-sound=no    <===  Disabled sound in this compile

make

sudo checkinstall -D make install
```



then, to run the program:

```
/opt/foobillardplus/bin/foobillardplus
```



When I get a chance, I will attempt to submit a bug report in the next couple of days on Foobillardplus.  If anybody has any suggestions, please advise.  Thanks!

---

