---
title: "HOWTO :install Transcode from source, with last ffmpeg and libmpeg2"
date: 2005-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by skyboy on 2005-07-16
Hi, this is my first HOWTO, so well, you know

Ok, I tried to install transcode this afternoon and couldn't get any rep (even debian-marillat) to work fine with unmet dependencies. So, I decided to take to bull by the horns and to compile everything from source. And trust me, it wasn't as simple as it sounds. (and I'm used to use source and compile)

so, lets start by downloading the sources you will need :

1 - from [http://www.transcoding.org](http://www.transcoding.org)
download latest version : [http://kraymer.de/mirroring/transcode-1.0.0.tar.gz](http://kraymer.de/mirroring/transcode-1.0.0.tar.gz)

2- from [http://ffmpeg.sourceforge.net](http://ffmpeg.sourceforge.net)
download latest version : [http://sourceforge.net/project/show...?group_id=16082](http://sourceforge.net/project/show...?group_id=16082) (when I write this version 0.4.9-pre1)

3- from [http://libmpeg2.sourceforge.net/](http://libmpeg2.sourceforge.net/)
download also latest version (mpeg2dec-0.4.0b) : [http://libmpeg2.sourceforge.net/fil...c-0.4.0b.tar.gz](http://libmpeg2.sourceforge.net/fil...c-0.4.0b.tar.gz)

4- uncompress all the files and lets start !

5- start with libmpge2
a simple ./configure && make && sudo make install
should be enough

6 - Now compile ffmpeg, but be carefull. Indeed, in order to get transcode to work, you have to enable the shared library so libavcodec can be installed and used by other application

so to configure :
./configure --enable-shared
(I also --enable-mp3lame --enable-vorbis)

then make && sudo make install

check you have libavcodec installed with :
$ dpkg -l | grep libavcodec
you should have :
ii libavcodec-dev 0.cvs20050121- development files for libavcodec
rc libavcodec2 0.4.9-pre1-0.4 Library to encode decode multimedia streams

after that you need to do something, otherwise transcode will not compile, eventhough you have everything installed :

check where your libavcodec-O.4.9-pre1.so is installed
$whereis libavcodec-0.4.9-pre1so

then make a link :
$ sudo ln -s /usr/local/lib/libavcodec-0.4.9-pre1.so /usr/lib/libavcodec.so

this is to avoid having the error "undefined reference to `dts_frame'"

then you can compile transcode :
go to transcode directory :
$./configure && make && sudo make install

if you want to enable or disable more, look here : [http://www.transcoding.org/cgi-bin/...lding_Transcode](http://www.transcoding.org/cgi-bin/...lding_Transcode)

if you have trouble with "$sudo make install" telling you you have already /usr/local/man installed, remove it (at least that was this only possibility for me)
and $sudo make install

now you should be done
NOTE : you might need to install some extra library, check your configure output. (this depend on your install)

---

### Post by ghostintheshell on 2005-07-16
He, thank you guy!
Transcode is no more in beta version :)
Great!

Another tips for you:
- you can specify [color=Indigo]./configure --prefix=/usr[/color] to install in the */usr* tree and not in the */usr/local* tree (by default)
- to uninstall when a new version will be available: go in the sources folder and type [color=Indigo]sudo make uninstall[/color] (this is why I copy/backup all my sources in */usr/local/src*)
- last but not least, after an installation you can type [color=Indigo]make clean[/color] to remove unneeded compiled files, that saves disk space.

Thank you again. I'll try it tonight.

---

### Post by skyboy on 2005-07-16
thanks,

Usually, I do a checkinstall instead of a normal make install, so then I can save the .deb file and just save the header files.
But, thanks for the tips anyway.

---

### Post by unreg on 2005-08-05
I'm trying to build transcode.....at the configure step I get: 

checking for gzopen in -lz... no
configure: error: transcode depends on libz, but cannot links against libz


But a locate of libz shows:

/usr/lib/libz.so.1.2.2
/usr/lib/libz.so.1


Any ideas?

---

### Post by ghostintheshell on 2005-08-05
try [color=Navy]*sudo apt-get install libzzip-dev*[/color]

---

