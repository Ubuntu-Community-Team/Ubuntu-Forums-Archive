---
title: "Try to compile vlc (last version from svn) with firefox support"
date: 2006-11-17
forum: Programming Talk
---

### Post by albundy83 on 2006-11-17
Hello,
I try to compile vlc to support firefox.
I use this configure options : ./configure --enable-ffmpeg --with-ffmpeg-tree=ffmpeg --with-ffmpeg-mp3lame --with-ffmpeg-config-path=ffmpeg/ffmpeg --enable-theora --enable-flac --enable-esd --enable-dvbpsi --enable-dvdread --enable-wxwidgets --enable-libmpeg2 --enable-vorbis --disable-hal --enable-sout --enable-http --enable-dvdnav --enable-smb --enable-libcdio --enable-alsa --enable-visual --enable-libcddb --enable-cdda --enable-vcd --enable-screen --enable-ogg --enable-mkv --enable-mod --enable-mad --enable-png --enable-x264 --enable-cmml --enable-x11 --enable-xvideo --enable-glx --enable-sdl --enable-freetype --enable-libxml2 --enable-oss --enable-daap --enable-faad --with-faad-tree=faad2-20040923 --enable-loader --enable-v4l --enable-dvb --enable-release --enable-mozilla --with-mozilla-sdk-path=/usr/include/firefox --enable-mpeg2dec --enable-dmo

I am on Ubuntu Edgy Eft, I have installed firefox-dev package but at the end, the configure tells me :
..............
checking mozilla-config.h usability... yes
checking mozilla-config.h presence... yes
checking for mozilla-config.h... yes
checking npapi.h usability... no
checking npapi.h presence... no
checking for npapi.h... no
checking for npruntime.h... no
configure: error: Please install the Mozilla development tools, required headers were not found.

I check in the folder /usr/include/firefox and the files npapi.h and npruntime.h and these files are present.

Is there anyone which has an idea for my problem ?](*,)

---

### Post by Houman on 2006-11-17
hi there,

 I am not sure about compiling it, but vlc actually has a .deb package of their nightly builds for ubuntu: [http://nightlies.videolan.org/]("http://nightlies.videolan.org/")

regards

Houman

---

### Post by albundy83 on 2006-11-17
I know, but it's for a personal development, and I need to compile it....:-|

---

### Post by shining on 2006-11-17
> **albundy83 said:**
> Hello,
I try to compile vlc to support firefox.
I use this configure options : ./configure --enable-ffmpeg --with-ffmpeg-tree=ffmpeg --with-ffmpeg-mp3lame --with-ffmpeg-config-path=ffmpeg/ffmpeg --enable-theora --enable-flac --enable-esd --enable-dvbpsi --enable-dvdread --enable-wxwidgets --enable-libmpeg2 --enable-vorbis --disable-hal --enable-sout --enable-http --enable-dvdnav --enable-smb --enable-libcdio --enable-alsa --enable-visual --enable-libcddb --enable-cdda --enable-vcd --enable-screen --enable-ogg --enable-mkv --enable-mod --enable-mad --enable-png --enable-x264 --enable-cmml --enable-x11 --enable-xvideo --enable-glx --enable-sdl --enable-freetype --enable-libxml2 --enable-oss --enable-daap --enable-faad --with-faad-tree=faad2-20040923 --enable-loader --enable-v4l --enable-dvb --enable-release --enable-mozilla --with-mozilla-sdk-path=/usr/include/firefox --enable-mpeg2dec --enable-dmo

I am on Ubuntu Edgy Eft, I have installed firefox-dev package but at the end, the configure tells me :
..............
checking mozilla-config.h usability... yes
checking mozilla-config.h presence... yes
checking for mozilla-config.h... yes
checking npapi.h usability... no
checking npapi.h presence... no
checking for npapi.h... no
checking for npruntime.h... no
configure: error: Please install the Mozilla development tools, required headers were not found.

I check in the folder /usr/include/firefox and the files npapi.h and npruntime.h and these files are present.

Is there anyone which has an idea for my problem ?](*,)

Maybe it's not looking in this dir then. Try running ./configure --help and see if you can specify where (mozilla) headers are (/usr/include/firefox).

---

### Post by po0f on 2006-11-17
albundy83,

Where exactly is npapi.h then?  Run `sudo updatedb && locate npapi.h` and post the result.


shining,

If you would have read the output, it's in there, it's just not finding a couple of header files for some reason.
[quote=albundy83]... --enable-mozilla --with-mozilla-sdk-path=/usr/include/firefox ...[/quote]

---

### Post by albundy83 on 2006-11-18
Hello,
I finally solve my problem, when I check in config.log, I saw, the problem comes from an include that is correctly done in npapi.h :

#include "prtypes.h"

And the prtypes.h is not in /usr/include/firefox folder but in /usr/include/fireofx/nspr.
So I add "export CPPFLAGS=-I/usr/include/firefox/nspr" before running my ./configure and it runs fine.

But now, I have another problem, the firefox plugin does not run ...
firefox crash and I have this message in my terminal :
libvlcplugin.so: undefined symbol: XtWindowToWidget

Well... thanks for your answers. ](*,)

---

