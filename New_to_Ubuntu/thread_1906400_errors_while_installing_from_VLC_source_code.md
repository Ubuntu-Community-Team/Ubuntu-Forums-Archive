---
title: "errors while installing from VLC source code"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by sagar_aarya on 2012-01-09
hi frnds

I am trying to install VLC from source code.
First i used the command
./configure

but i got some error like this...

[I]configure: error: Could not find lua. Lua is needed for some interfaces (rc, telnet, http) as well as many other custom scripts. Use --disable-lua to ignore this error.
[/I]

so i tried command 
./conigure --disable-lua

again i got similar errors....
finally with this command...i am able to configure(NO ERRORS CAME)

[I] ./configure --disable-lua --disable-avcodec --disable-postproc --disable-glx --disable-qt4 --disable-skins2
[/I]


then i used command 
[B]
make
[/B]


but it gave errors like this ....

[I]
sagar@MRFRODO:~/sagar source code/vlc-1.1.13$ make

make  all-recursive
make[1]: Entering directory `/home/sagar/sagar source code/vlc-1.1.13'
Making all in po
make[2]: Entering directory `/home/sagar/sagar source code/vlc-1.1.13/po'
make[2]: Leaving directory `/home/sagar/sagar source code/vlc-1.1.13/po'
Making all in compat
make[2]: Entering directory `/home/sagar/sagar source code/vlc-1.1.13/compat'
make  all-am
make[3]: Entering directory `/home/sagar/sagar source code/vlc-1.1.13/compat'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/sagar/sagar source code/vlc-1.1.13/compat'
make[2]: Leaving directory `/home/sagar/sagar source code/vlc-1.1.13/compat'
Making all in src
make[2]: Entering directory `/home/sagar/sagar source code/vlc-1.1.13/src'
  GEN    ../include/vlc/libvlc_version.h
config.status: creating src/../include/vlc/libvlc_version.h
  GEN    stamp-revision
/bin/bash: git: command not found
make  all-recursive
make[3]: Entering directory `/home/sagar/sagar source code/vlc-1.1.13/src'
Making all in .
make[4]: Entering directory `/home/sagar/sagar source code/vlc-1.1.13/src'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/sagar/sagar source code/vlc-1.1.13/src'
Making all in test
make[4]: Entering directory `/home/sagar/sagar source code/vlc-1.1.13/src/test'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/sagar/sagar source code/vlc-1.1.13/src/test'
make[3]: Leaving directory `/home/sagar/sagar source code/vlc-1.1.13/src'
make[2]: Leaving directory `/home/sagar/sagar source code/vlc-1.1.13/src'
Making all in libs/srtp
make[2]: Entering directory `/home/sagar/sagar source code/vlc-1.1.13/libs/srtp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sagar/sagar source code/vlc-1.1.13/libs/srtp'
Making all in libs/unzip
make[2]: Entering directory `/home/sagar/sagar source code/vlc-1.1.13/libs/unzip'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sagar/sagar source code/vlc-1.1.13/libs/unzip'
Making all in bin
make[2]: Entering directory `/home/sagar/sagar source code/vlc-1.1.13/bin'
  CC     vlc_static-vlc.o
gcc: source: No such file or directory
gcc: code/vlc-1.1.13": No such file or directory
gcc: source: No such file or directory
gcc: code/vlc-1.1.13": No such file or directory
<command-line>: warning: missing terminating " character
<command-line>: warning: missing terminating " character
[B]
vlc.c: In function ‘main’:
vlc.c:158: error: missing terminating " character
vlc.c:158: error: expected ‘)’ before string constant
vlc.c:161: error: missing terminating " character
vlc.c:161: error: expected ‘)’ before string constant
vlc.c:194: warning: ‘libvlc_playlist_play’ is deprecated (declared at ../include/vlc/deprecated.h:59)
[/B]
make[2]: *** [vlc_static-vlc.o] Error 1
make[2]: Leaving directory `/home/sagar/sagar source code/vlc-1.1.13/bin'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sagar/sagar source code/vlc-1.1.13'
make: *** [all] Error 2
sagar@MRFRODO:~/sagar source code/vlc-1.1.13$ 

[/I]
 



PLEASE HELP ....

using UBUNTU 9.10


P.S:
I didnt modified any part of source code
downloaded from VLC main website....


Regards
sagar

---

### Post by Double.J on 2012-01-09
Hi there and welcome to the forums!.. or not, well welcome to beans!

Was there a version specific reason for building vlc from source? Vlc is a metapackage, so your more likely to encounter difficulties - not my recommendation for learning building from source - that's be something like htop system monitor, but I digress. 

I'd be inclined to get it from the sofrtware centre or downloading a .deb file from pkgs.org

---

### Post by Double.J on 2012-01-09
Sorry just notice you said your using karmic. Was there a reason you didn't want to upgrade to the 10.o4 lts?

---

### Post by anewguy on 2012-01-09
Not to mention - if you're downloading current source I wouldn't count on it being able to compile in 9.x anyway.

---

