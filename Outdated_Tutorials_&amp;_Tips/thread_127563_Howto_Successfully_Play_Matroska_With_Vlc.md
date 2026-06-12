---
title: "Howto: Successfully Play Matroska With Vlc"
date: 2006-02-09
forum: Outdated Tutorials &amp; Tips
---

### Post by terry98 on 2006-02-09
i noticed that many people are complaining about not playing mkv files on ubuntu, including myself.....

so i started to compile VLC and noticed that when it's setting the matroska driver it searches for something else... 

Before you can play MKV files you need to do the following: In Konsole type...

1- sudo apt-get install libebml-dev

2- sudo apt-get install libmatroska-dev

3- sudo apt-get install libmp4v2-0 libmp4v2-dev

After Installing these 3 files you will need to compile VLC, remember to get all VLC dependencys.. try this

4- sudo apt-get install libdvdcss2 libdvdcss2-dev libdvdplay0 libdvdplay0-dev libdvdnav-dev libdvdnav4 libdvdread3-dev libdvdread3 libogg-dev libogg0 libvorbis-dev libvorbis0a liba52-0.7.4-dev liba52-0.7.4 libmad0-dev libmad0

5- Go to [http://www.videolan.org/vlc/download-sources.html]("http://www.videolan.org/vlc/download-sources.html")
and download the latest vlc source code, i have 0.8.4a and get ready to compile it...

6- Extract the file typing "tar -zxvf vlc-XXXX.tar.gz" and go in the extraxted directory,

7- Type "sudo ./configure --enable-mkv" (this might take a while)

8- Type "sudo make" (this also might take a while)

9-Type "sudo make install"

if everything went well, try "vlc --list |grep mkv" it should display a line with "mkv                   Matroska stream demuxer"

i'm assuming that you have installed the packages to compile... if not, try
"sudo apt-get install build-essential autoconf automake1.9"

enjoy...;)

---

### Post by crypticreign on 2006-02-10
You also need: libavcodec-dev, libavformat-dev, libmpeg2-4 libmpeg2-4-dev, and libwxgtk2.6-dev

Also, I have to run 

'./configure --disable-ffmpeg'

Also, I dont see any video.  I can just hear audio.   Test with .mpg files.

---

### Post by terry98 on 2006-02-11
[QUOTE=crypticreign]You also need: libavcodec-dev, libavformat-dev, libmpeg2-4 libmpeg2-4-dev, and libwxgtk2.6-dev

Also, I have to run 

'./configure --disable-ffmpeg'

Also, I dont see any video.  I can just hear audio.   Test with .mpg files.[/QUOTE]

maybe because of the "--disable-ffmpeg" option.., whu do you have to install with that option???? i dont see any need

---

### Post by dude2425 on 2006-02-11
Mine doesn't seem to work if I don't use --disable-ffmpeg. It gives me an error while compiling. I still can't play any of my mkv files. I'm trying to watch InuYasha, and once I got to episode 58, everything went from ogm format which works just fine, to mkv which crashes VLC, and the audio is seriously b0rked in totem and mplayer. I've been trying to get this to work for a good two weeks already, and nothing I've done is working.

Any suggestions?

---

### Post by crypticreign on 2006-02-11
[QUOTE=terry98]maybe because of the "--disable-ffmpeg" option.., whu do you have to install with that option???? i dont see any need[/QUOTE]


if I just run "./configure" and then run "make" I get the following error:

Making all in ffmpeg
make[5]: Entering directory `/home/crypticreign/vlc-0.8.4a/modules/codec/ffmpeg'
make[6]: Entering directory `/home/crypticreign/vlc-0.8.4a/modules/codec/ffmpeg'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../..   -DSYS_LINUX -I../../../include `top_builddir="../../.." ../../../vlc-config --cflags plugin ffmpeg` -Wsign-compare -Wall  -pipe -MT libffmpeg_plugin_a-ffmpeg.o -MD -MP -MF ".deps/libffmpeg_plugin_a-ffmpeg.Tpo" -c -o libffmpeg_plugin_a-ffmpeg.o `test -f 'ffmpeg.c' || echo './'`ffmpeg.c; \
then mv -f ".deps/libffmpeg_plugin_a-ffmpeg.Tpo" ".deps/libffmpeg_plugin_a-ffmpeg.Po"; else rm -f ".deps/libffmpeg_plugin_a-ffmpeg.Tpo"; exit 1; fi
ffmpeg.c:49:44: error: libpostproc/postprocess.h: No such file or directory
make[6]: *** [libffmpeg_plugin_a-ffmpeg.o] Error 1
make[6]: Leaving directory `/home/crypticreign/vlc-0.8.4a/modules/codec/ffmpeg'
make[5]: *** [all-modules] Error 1
make[5]: Leaving directory `/home/crypticreign/vlc-0.8.4a/modules/codec/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/crypticreign/vlc-0.8.4a/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/crypticreign/vlc-0.8.4a/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/crypticreign/vlc-0.8.4a/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/crypticreign/vlc-0.8.4a'
make: *** [all] Error 2

---

### Post by terry98 on 2006-02-11
> **crypticreign]if I just run "./configure" and then run "make" I get the following error:

Making all in ffmpeg
make[5]: Entering directory `/home/crypticreign/vlc-0.8.4a/modules/codec/ffmpeg'
make[6]: Entering directory `/home/crypticreign/vlc-0.8.4a/modules/codec/ffmpeg'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../..   -DSYS_LINUX -I../../../include `top_builddir="../../.." ../../../vlc-config --cflags plugin ffmpeg` -Wsign-compare -Wall  -pipe -MT libffmpeg_plugin_a-ffmpeg.o -MD -MP -MF ".deps/libffmpeg_plugin_a-ffmpeg.Tpo" -c -o libffmpeg_plugin_a-ffmpeg.o `test -f 'ffmpeg.c' || echo './'`ffmpeg.c said:**
> : *** [libffmpeg_plugin_a-ffmpeg.o] Error 1
make[6]: Leaving directory `/home/crypticreign/vlc-0.8.4a/modules/codec/ffmpeg'
make[5]: *** [all-modules] Error 1
make[5]: Leaving directory `/home/crypticreign/vlc-0.8.4a/modules/codec/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/crypticreign/vlc-0.8.4a/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/crypticreign/vlc-0.8.4a/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/crypticreign/vlc-0.8.4a/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/crypticreign/vlc-0.8.4a'
make: *** [all] Error 2

you need to install the postprocess development package try

sudo apt-get install libpostproc-dev

after try again without the --disable-ffmpeg

---

### Post by crypticreign on 2006-02-11
[QUOTE=terry98]you need to install the postprocess development package try

sudo apt-get install libpostproc-dev[/QUOTE]

I'm guessing that's in the Marillat repositories?

---

### Post by terry98 on 2006-02-11
mmm.... try to add this lines to your /etc/apt/sources.list

deb [http://www.bunkus.org/ubuntu/breezy/](http://www.bunkus.org/ubuntu/breezy/) ./
deb-src [http://www.bunkus.org/ubuntu/breezy/](http://www.bunkus.org/ubuntu/breezy/) ./

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-f$
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free n$

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free


also remove the "#" on the 

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

try sudo apt-get update, wait for it to finish and try to install the libpostproc-dev again

---

### Post by crypticreign on 2006-02-11
ok, that built... but I still don't get any video.  When I run VLC from an xterm, and try to play a video, I get the following output in the term:

[00000298] fb video output error: cannot get terminal mode (Invalid argument)

---

### Post by terry98 on 2006-02-11
try going to preferences -> video -> video output, and change the output module, i use X11... remebmber to do "vlc --list|grep mkv" to see if you really have matroska support

---

### Post by crypticreign on 2006-02-11
[QUOTE=terry98]try going to preferences -> video -> video output, and change the output module, i use X11... remebmber to do "vlc --list|grep mkv" to see if you really have matroska support[/QUOTE]

I dont have "X11" listed.  Yes, I followed all your steps.

---

### Post by terry98 on 2006-02-11
how come you dont have x11??, well.... mmm... anyway try diferent output modules, or is it that you only have fb??

---

### Post by crypticreign on 2006-02-11
[QUOTE=terry98]how come you dont have x11??, well.... mmm... anyway try diferent output modules, or is it that you only have fb??[/QUOTE]

I only have fb :\

---

### Post by terry98 on 2006-02-11
ok, try this

sudo apt-get install libx11-dev

the configure vlc again and recompile, with

./configure --enable-mkv --enable-x11

hope that helps...

---

### Post by crypticreign on 2006-02-11
[QUOTE=terry98]ok, try this

sudo apt-get install libx11-dev

the configure vlc again and recompile, with

./configure --enable-mkv --enable-x11

[/QUOTE]


I get this error:

rm -f libscreen_plugin.a
ar cru libscreen_plugin.a libscreen_plugin_a-screen.o libscreen_plugin_a-x11.o  
ranlib libscreen_plugin.a
gcc -Wsign-compare -Wall -pipe -o libscreen_plugin.so libscreen_plugin.a -L/usr/local/lib -shared -lpthread -fpic -fPIC -L/usr/X11R6/lib -lX11 -lXext -u vlc_entry__0_8_4
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
make[6]: *** [libscreen_plugin.so] Error 1

---

### Post by kaamos on 2006-02-11
try installing xlibs-dev

---

### Post by crypticreign on 2006-02-11
[QUOTE=kaamos]try installing xlibs-dev[/QUOTE]

Excellent!

Thanks!

---

### Post by LordMelkor on 2006-02-28
Before I found this thread I had tried to compile vlc with mkv support, but i was missing libmatroska dev so the configure file gave me a warning, and told me that if i wanted it to work right i would need to do configure --disable-mkv, so i installed libmatroska and did configure and got no error. During the configure process i got a few other warnings but I installed all the libs that i was missing until I could run ./configure with no errors/warnings. Therefore i know that i have all the libraries that are needed for full functionality of VLC. so i did ./configure --enable-mkv (even tho its enabled by default according to --help) and then i did make and make install. but after this was all done i did vlc --list |grep mkv but no demuxer showed up. What is going on??

note: i got an error with ffmpeg postprocessing during the install, so i went to the vlc forums and looked it up and accordingly created a file called /etc/ld.so.config (or something like that) and added the line /usr/local/lib and then i ran ldconfig in the terminal (the error was corrected by doing this). I just want to be complete in whatever i did in regaurds to the compilation of vlc.

---

### Post by LordMelkor on 2006-03-01
the failsafe way to do all this without having to waste the disk space for sources, and wait for the compilation to occur you can just add:

deb [http://nightlies.videolan.org/build/breezy-i386](http://nightlies.videolan.org/build/breezy-i386) / 

to your sources.list and use synaptic. :D

---

### Post by Bachstelze on 2006-03-01
Haha, I'll remember that one :D Anyway I did the ompilation and it worked like a charm :)

---

### Post by danhm on 2006-03-01
[QUOTE=LordMelkor]the failsafe way to do all this without having to waste the disk space for sources, and wait for the compilation to occur you can just add:

deb [http://nightlies.videolan.org/build/breezy-i386](http://nightlies.videolan.org/build/breezy-i386) / 

to your sources.list and use synaptic. :D[/QUOTE]


Whats the rest of that? It's malformed.

---

### Post by LordMelkor on 2006-03-02
make sure you include the space before the last back space and also, it does not include verification. however by adding it to sources.list will still give you access to the packages available on that site, it will complain when you type apt-get update, but you will still be able to install vlc.

---

### Post by danhm on 2006-03-02
Hmm...

My MKVs are all blocky. Is there a setting that controls the smoothness or something like that? Is it the video output?

---

### Post by danhm on 2006-03-04
Anyone? I've been looking all over the internet and haven't found a thing.

---

### Post by mads-b on 2006-03-25
I've compiled it without errors, but both video and audio is missing in mkv files, and video is missing in other files. What do I do? I'm completely new to ubuntu.

---

### Post by minitiss on 2006-10-01
I get an error when I try to configure vlc:
```

checking id3tag.h usability... no
checking id3tag.h presence... no
checking for id3tag.h... no
checking for ffmpeg-config... no
checking for FFMPEG_CFLAGS...
checking for FFMPEG_LIBS...
checking ffmpeg/avcodec.h usability... no
checking ffmpeg/avcodec.h presence... no
checking for ffmpeg/avcodec.h... no
configure: error: Missing header file ffmpeg/avcodec.h.

```

tried to locate the libavcodec.pc but I could not find it, do anyone know how to solve the problem?

---

### Post by balance07 on 2006-10-12
danhm: i have the same situation. matroska's play, but look like shit. they also look like that as thumbnails in nautilus. i suspect the two are related.

---

### Post by terry98 on 2006-10-12
well that can solved installing the ffmpeg, remember guys that when u are compiling u need the -devel packages the normal packages only wont do the job....

---

### Post by balance07 on 2006-10-13
terry98: is your message in response to my issue? i have installed all the packages mentioned in this thread (including the -dev packages) and got vlc 0.8.5 to compile ok, but still garbled video (matroska files only). is ffmpeg u speak of a separate package, will i need to re-compile vlc?

---

### Post by nickless on 2006-12-19
Do I really have to compile it all over again? :confused: 
Isn't it possible to use vlc from the recources and activate the mkv codecs somehow? This is so typically Linux](*,)

---

### Post by terry98 on 2006-12-19
well the truth is that its been a while since i used vlc, im using mplayer now, why dont u give it a try.... i use 1.0-pre8, if you're going to compile make sure you use the --disable-x264, dont know why but it gives me problems compiling if i dont disable it, also try the option --cc=/usr/bin/gcc-3.4 'cause thats the gcc dependency it uses.....

---

### Post by nickless on 2006-12-19
Well it doesn't take make a big difference what I have to compile :D
I was wondering if a simple apt-get install something could help me as well ;)

---

### Post by terry98 on 2006-12-19
well you can install both of them, mplayer and vlc, from apt (or its gui, synaptic) but i personally dont like to do that cause sometimes some features are missing in those builds, thats why i like to compile... but the decision is up to you...

---

### Post by kd7swh on 2007-01-14
A lot of dependencies are missing from this how to but I found all of them in synaptic except libdvdcss2-dev which took awhile to find. But I am know "making" so I hope all ends well.

---

### Post by terry98 on 2007-01-14
well.... it's just that this howto its getting old, now there is dapper i wrote this for breezy while using it and its repositories...

---

### Post by kd7swh on 2007-01-14
I know. The vlc I compiled was 0.8.6a. I compiled fine but no video output :( I installed those xlibs and play around with the output modules still no luck.

---

### Post by terry98 on 2007-01-15
> **kd7swh said:**
> I know. The vlc I compiled was 0.8.6a. I compiled fine but no video output :( I installed those xlibs and play around with the output modules still no luck.

well maybe it did compile ok and u just need to play with the output plugins... for example i use XV in mplayer but you could try others as sdl and opengl...

---

### Post by kd7swh on 2007-01-15
what is funny about that is that the latest build I did (from svn) doesn't have a drop down menu in the output prefs.
No video or audio either except flac

it says it is v0.9.0svn

---

### Post by terry98 on 2007-01-16
what video card do u use?? do you have instaled the dev libs for it??, if you're using mesa like me you must install the mesa-dev package that should give the opengl video output try getting the xvlib dev also, maybe you're missing all these...

---

### Post by kd7swh on 2007-01-18
if it helps, vlc says this in the terminal:

> failed: could not create access: no suitable access2 module
signal 2 received, terminating vlc - do it again in case it gets stuck


when I try and open a video file.

what is with that?

---

### Post by terry98 on 2007-01-18
im not sure, maybe u're missing that package, everytime u get an error concerning to a module or something like that try looking for it in synaptic first....

---

