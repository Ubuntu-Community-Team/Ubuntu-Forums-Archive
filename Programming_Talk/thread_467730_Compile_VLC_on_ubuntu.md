---
title: "Compile VLC on ubuntu"
date: 2007-06-08
forum: Programming Talk
---

### Post by yinglcs2 on 2007-06-08
Hi,

I am trying to compile VLC trunk and ffmpeg trunk on ubuntu 7.0.4.

I get both to compile, but when I use vlc to open a mov file, I can hear the audio, but I can't see the video.
I see the following error:

VLC probably does not support the 'h263' audio or video format.
Unfortunately there is no way for you to fix this.

Can you please tell me how to fix my problem? how can i make vlc to see ffmpeg?

I think I have ffmpeg installed properly. I have these files in my /usr/local/lib:
$ ls -la libav*
-rw-r--r-- 1 root root 15123666 2007-06-07 23:28 libavcodec.a
-rw-r--r-- 1 root root  4010450 2007-06-07 23:28 libavformat.a
-rw-r--r-- 1 root root   133462 2007-06-07 23:28 libavutil.a
$ pwd
/usr/local/lib

here is my configure for vlc:

$ ./configure --enable-x11 --enable-xvideo --disable-gtk --enable-sdl --enable-ffmpeg-faac --enable-mad --enable-libdvbpsi --enable-libmpeg2 --enable-dvdnav  --enable-vorbis --enable-ogg --enable-theora --enable-faac --enable-mkv --enable-freetype --enable-fribidi --enable-speex --enable-flac --enable-caca --enable-skins --enable-skins2 --enable-alsa --disable-kde --enable-qt --enable-wxwindows --enable-ncurses --enable-release --disable-a52 --enable-libmpeg2 --disable-dbus --disable-hal

Here is my configure for ffmpeg:

$ ./configure


Thank you for any pointers.

---

