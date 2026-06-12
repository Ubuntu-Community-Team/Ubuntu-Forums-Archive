---
title: "HOWTO: Compiling mplayer with multi-core decoding support"
date: 2009-01-24
forum: Outdated Tutorials &amp; Tips
---

### Post by runesvend on 2009-01-24
I'm posting this HowTo since I think it is a great advancement in HD playback on Linux and people should be able to take advantage of it. I found out how to do this from the following post on doom9.org: [http://forum.doom9.org/showthread.php?p=1221445#post1221445](http://forum.doom9.org/showthread.php?p=1221445#post1221445)


Overview: To use mplayer with multithreaded decoding abilities all you have to do is compile mplayer as per usual, but having replaced the normal ffmpeg source code (within the mplayer source code directory) with the ffmpeg-mt source code ([http://gitorious.org/projects/ffmpeg/repos/ffmpeg-mt](http://gitorious.org/projects/ffmpeg/repos/ffmpeg-mt)).

I'm going to use the following guide written by andrew.46 entitled **_[[Howto] Successfully install the svn mplayer + gmplayer + all the codecs]("http://ubuntuforums.org/showthread.php?t=558538")_**  as the basis for my tutorial as it's very thorough and I feel there's no need to reinvent the spoon.


How to install:

1. Follow **_[andrew.46's guide]("http://ubuntuforums.org/showthread.php?t=558538")_** until you reach the point "**Download and Compile the svn mplayer**" (you can skip the step "**Installing the amr libraries**" if you don't need these, I skipped it)

2. When you reach the step "**Download and Compile the svn mplayer**" proceed as andrew.46 says with downloading the mplayer source code from SVN:

```
$ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
```

When this is done it's time to download the ffmpeg-mt source code. First you need *git*, install it with the following command:

```
sudo apt-get install git-core
```

Then download the source code for ffmpeg-mt using git:

```
git clone http://git.gitorious.org/ffmpeg/ffmpeg-mt.git
```

In order to make use of the now downloaded ffmpeg-mt source code you need to replace the three following folders from the mplayer source directory with the folders from the ffmpeg-mt directory: "libavcodec", "libavformat" and "libavutil".

```
cd mplayer #enter the directory where the mplayer source code is
rm -rf libavcodec libavformat libavutil #delete the three aforementioned folders
cp -a ../ffmpeg-mt/libavcodec . #copy the three folders from the ffmpeg-mt source dir to mplayers source dir
cp -a ../ffmpeg-mt/libavformat .
cp -a ../ffmpeg-mt/libavutil .
```

Now you have the mplayer source code in which the ffmpeg source has been replaced with the ffmpeg-mt source. You should be ready to go.

Now just follow the rest of **_[andrew.46's guide]("http://ubuntuforums.org/showthread.php?t=558538")_** starting from:

```
$ cd $HOME/mplayer
$ ./configure --enable-gui
$ make
$ sudo make install
$ make clean
```

and mplayer should compile with no problems.



Here are some benchmarks of mplayer with the normal single-threaded ffmpeg decoder compared to the multi-threaded ffmpeg decoder playing various 1080p H.264 video samples (using my Core2 Quad 2.83GHz CPU):

```
			SINGLE-THREADED FPS	MULTI-THREADED FPS	PERCENT INCREASE IN FPS

The Dark Knight		37			121			329%

In Bruges		45			134			296%
(no *-ss 120*)

The Bank Job		46			141			305%

The Terminator		37			126			341%
(no *-ss 120*)



(MPLAYER ARGUMENTS: -vc ffh264 -lavdopts threads=4 -vo null -benchmark -frames 1000 -ss 120 -nosound)

```

I hope you've enjoyed this guide, I basically just snatched the guides from the two aforementioned users and joined them, thanks goes out to them.

Happy HD viewing :)

---

### Post by taisao on 2009-02-23
thank you, I gonna try this when I upgrade my system, very soon.

for now, can you tell me what this mean?
```
Starting playback...
[h264 @ 0x8902510]Cannot parallelize deblocking type 1, decoding such frames in sequential order
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [null] 1280x720 => 1280x720 Planar YV12
V: 162.5   0/  0 70%  0%  0.0% 0 0

```

that's when using ```
-vc ffh264 -lavdopts threads=4 -vo null -benchmark -frames 1000 -ss 120 -nosound
```

(pentium 4, 2.6ghz)

---

### Post by andrew.46 on 2009-02-24
Hi,

You might be better to use a newer version of my MPlayer guide:

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

which is a little more polished than the older one that you have linked to. Better still why not copy and paste the relevant sections of my guide into your own? I have absolutely no objection and it would make it a bit easier for people to follow your guide from beginning to end.

All the best,

Andrew

---

### Post by pokipoki08 on 2009-02-24
Where do I download the svn tarball for ffmpeg-mt? Using git is too slow for my current bandwidth?

Thanks

---

### Post by Jeroen Vernooij on 2009-02-24
Has anyone experienced glitches / crashes during h.264 playback (encoded with x264)??

---

### Post by runesvend on 2009-03-10
> **andrew.46 said:**
> Hi,

You might be better to use a newer version of my MPlayer guide:

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

which is a little more polished than the older one that you have linked to. Better still why not copy and paste the relevant sections of my guide into your own? I have absolutely no objection and it would make it a bit easier for people to follow your guide from beginning to end.

All the best,

Andrew
Hi Andrew

Thank you for letting me use your guide. Yes, pasting the above modifications into your guide would indeed be easier to follow, I just haven't gotten around to asking you for permission since I haven't had much spare time since writing the above guide.
But I will definitely do it when I have some more time on my hands.

Alternatively, anyone here are also free to use my guide above and copy and paste the relevant modifications into andrew's guide, if they don't wish waiting for me to do it.

---

### Post by psychok9 on 2009-04-06
I can't understand why we need a special version of ffmpeg-mt libraries, if I can see on Smplayer (mplayer gui) some multithread decode options... ?

Thank you.

---

### Post by zhark1 on 2009-04-07
> **psychok9 said:**
> I can't understand why we need a special version of ffmpeg-mt libraries, if I can see on Smplayer (mplayer gui) some multithread decode options... ?

Thank you.

The options in Smplayer are *probably* related to an older implementation of multithreading in ffmpeg which doesn't work with most modern x264 encoded videos. ffmpeg-mt is not stable yet, therefore it has to be manually copied to the mplayer source if one wishes to use it.

---

### Post by disembowler on 2009-04-26
First of all, many thanks for this HOWTO. I have been looking for something like this already for some time...

However, I've ran into a problem: Mplayer (r 29238) doesn't compile anymore when I replace the folders libavcodec libavformat libavutil with the ones from ffmpeg-mt.
FYI, I used the following configure options
```

./configure --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer --enable-gui --prefix=/usr

```


make throws the following error:
```

make -C libswscale
make[1]: Entering directory `/home/ingo/SOURCE/mplayer/libswscale'
cc -DHAVE_AV_CONFIG_H -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -Ilibdvdread4  -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3   -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o swscale.o swscale.c
swscale.c: In function 'sws_format_name':
swscale.c:482: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:482: error: (Each undeclared identifier is reported only once
swscale.c:482: error: for each function it appears in.)
swscale.c:484: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:486: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:488: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:490: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:492: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
In file included from swscale.c:1196:
swscale_template.c: In function 'yuv2yuv1_MMX2':
swscale_template.c:961: warning: initialization from incompatible pointer type
swscale_template.c:961: warning: initialization from incompatible pointer type
swscale_template.c:961: warning: initialization from incompatible pointer type
swscale_template.c:961: warning: initialization from incompatible pointer type
swscale_template.c: In function 'yuv2packed2_MMX2':
swscale_template.c:1246: warning: dereferencing type-punned pointer will break strict-aliasing rules
swscale_template.c:1246: warning: assignment discards qualifiers from pointer target type
swscale_template.c:1247: warning: dereferencing type-punned pointer will break strict-aliasing rules
swscale_template.c:1247: warning: assignment discards qualifiers from pointer target type
swscale_template.c: In function 'hScale_MMX2':
swscale_template.c:2244: warning: initialization discards qualifiers from pointer target type
swscale_template.c: In function 'swScale_MMX2':
swscale_template.c:2946: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2947: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2952: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2953: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2959: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2960: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2969: warning: cast from pointer to integer of different size
swscale_template.c:2975: warning: cast from pointer to integer of different size
swscale_template.c:2983: warning: cast from pointer to integer of different size
swscale_template.c:2998: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale_template.c:2998: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale_template.c:2998: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale_template.c:2998: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale_template.c:2998: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale_template.c:2998: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale_template.c: In function 'sws_init_swScale_MMX2':
swscale_template.c:3155: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale_template.c:3156: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale_template.c:3157: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale_template.c:3158: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale_template.c:3159: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale_template.c:3160: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c: In function 'getSwsFunc':
swscale.c:1795: warning: unused variable 'flags'
swscale.c: In function 'planarCopy':
swscale.c:2166: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2166: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2166: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2166: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2166: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:2166: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c: In function 'getSubSampleFactors':
swscale.c:2223: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2224: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2243: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2244: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c:2249: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2250: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c: In function 'sws_setColorspaceDetails':
swscale.c:2288: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2288: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2288: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2288: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2288: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:2288: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c: In function 'sws_getColorspaceDetails':
swscale.c:2336: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2336: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2336: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2336: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2336: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:2336: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c: In function 'sws_getContext':
swscale.c:2408: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2408: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2408: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2408: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2408: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:2408: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c: In function 'reset_ptr':
swscale.c:2917: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2917: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2917: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2917: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2917: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:2917: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c: In function 'sws_getCachedContext':
swscale.c:3404: warning: assignment discards qualifiers from pointer target type
make[1]: *** [swscale.o] Error 1
make[1]: Leaving directory `/home/ingo/SOURCE/mplayer/libswscale'
make: *** [libswscale/libswscale.a] Error 2

```

When I use the original libraries sources from svn trunk, then it compiles without errors. :confused:

Any ideas how this can be fixed?
Thanks.

btw: I am running Jaunty 9.04

---

### Post by markitoxs on 2009-04-26
Thx!

---

### Post by disembowler on 2009-04-27
Does this HWOTO work for all of guys on Januty or is there experiencing similar problems as I am, when using the libavcodec libavformat libavutil libs from ffmpeg-mt instead of the ones shipped with mplayer trunk?

If I am the only one having those troubles, then it might be something wrong on my end here...cuz I have basically just followed the HOWTO step-by-step and still getting these errors when compiling mplayer. I tried the previous and current svn revision of mplayer, but it fails on both :-(

I appreciate any ideas...Thanks

---

### Post by tim__b on 2009-04-27
I'm having the same problems as disembowler. Maybe there's something changed in ffmpeg-mt...

---

### Post by mc4man on 2009-04-27
I don't have any h.264/good enough hardware to test so can't see if there are any issues. (mplayer build works fine for what I do use for

MPlayer SVN-r29241

If you also replace the libswscale folder in mplayer  using  the one from the 0.5 release then the build succeeds
(( 'replace' meant merge. not rm & cp
(again  may be unintended consequences, could be narrowed down to a file(s) and or line(s)

[http://www.ffmpeg.org/download.html](http://www.ffmpeg.org/download.html)
(at very bottom of page

(interesting that there is nothing in the libswscale folder in ffmpeg-mt source

---

### Post by disembowler on 2009-04-28
> **mc4man said:**
> 
MPlayer SVN-r29241

If you also replace the libswscale folder in mplayer  using  the one from the 0.5 release then the build succeeds
(( 'replace' meant merge. not rm & cp
(again  may be unintended consequences, could be narrowed down to a file(s) and or line(s)

[http://www.ffmpeg.org/download.html](http://www.ffmpeg.org/download.html)
(at very bottom of page

(interesting that there is nothing in the libswscale folder in ffmpeg-mt source

Nope, still doesn't work for me. 

Step-by-step description of what I did:
1. Get the current SVN version of mplayer (r 29241), ffmpeg, ffmpeg-mt
```

svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
git clone git://gitorious.org/ffmpeg/ffmpeg-mt.git

```

2. Replace the folders in the mplayer directory with the ones from ffmpeg-mt
```

cd mplayer
rm -rf libavcodec libavformat libavutil
cp -a ../ffmpeg-mt/libavcodec .
cp -a ../ffmpeg-mt/libavformat .
cp -a ../ffmpeg-mt/libavutil .

```

3. Use the libswscale stuff from ffmpeg sources and "merge" it into my mplayer/libswscale folder
```

cd ..
cp -fr ffmpeg/libswscale/* mplayer/libswscale/

```

4. Configure and Make mplayer
```

cd mplayer
./configure --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer --enable-gui --prefix=/usr
make

```


make produces the same error. 
```

swscale.c: In function 'sws_format_name':
swscale.c:482: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:482: error: (Each undeclared identifier is reported only once
swscale.c:482: error: for each function it appears in.)
swscale.c:484: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:486: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:488: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:490: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:492: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
In file included from swscale.c:1196:
swscale_template.c: In function 'yuv2yuv1_MMX2':
swscale_template.c:961: warning: initialization from incompatible pointer type
swscale_template.c:961: warning: initialization from incompatible pointer type
swscale_template.c:961: warning: initialization from incompatible pointer type
swscale_template.c:961: warning: initialization from incompatible pointer type
swscale_template.c: In function 'yuv2packed2_MMX2':
swscale_template.c:1246: warning: dereferencing type-punned pointer will break strict-aliasing rules
swscale_template.c:1246: warning: assignment discards qualifiers from pointer target type
swscale_template.c:1247: warning: dereferencing type-punned pointer will break strict-aliasing rules
swscale_template.c:1247: warning: assignment discards qualifiers from pointer target type
swscale_template.c: In function 'hScale_MMX2':
swscale_template.c:2244: warning: initialization discards qualifiers from pointer target type
swscale_template.c: In function 'swScale_MMX2':
swscale_template.c:2946: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2947: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2952: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2953: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2959: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2960: warning: assignment discards qualifiers from pointer target type
swscale_template.c:2969: warning: cast from pointer to integer of different size
swscale_template.c:2975: warning: cast from pointer to integer of different size
swscale_template.c:2983: warning: cast from pointer to integer of different size
swscale_template.c:2998: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale_template.c:2998: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale_template.c:2998: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale_template.c:2998: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale_template.c:2998: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale_template.c:2998: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale_template.c: In function 'sws_init_swScale_MMX2':
swscale_template.c:3155: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale_template.c:3156: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale_template.c:3157: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale_template.c:3158: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale_template.c:3159: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale_template.c:3160: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c: In function 'getSwsFunc':
swscale.c:1795: warning: unused variable 'flags'
swscale.c: In function 'planarCopy':
swscale.c:2166: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2166: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2166: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2166: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2166: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:2166: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c: In function 'getSubSampleFactors':
swscale.c:2223: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2224: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2243: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2244: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c:2249: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2250: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c: In function 'sws_setColorspaceDetails':
swscale.c:2288: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2288: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2288: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2288: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2288: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:2288: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c: In function 'sws_getColorspaceDetails':
swscale.c:2336: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2336: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2336: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2336: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2336: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:2336: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c: In function 'sws_getContext':
swscale.c:2408: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2408: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2408: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2408: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2408: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:2408: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c: In function 'reset_ptr':
swscale.c:2917: error: 'PIX_FMT_YUV420PLE' undeclared (first use in this function)
swscale.c:2917: error: 'PIX_FMT_YUV422PLE' undeclared (first use in this function)
swscale.c:2917: error: 'PIX_FMT_YUV444PLE' undeclared (first use in this function)
swscale.c:2917: error: 'PIX_FMT_YUV420PBE' undeclared (first use in this function)
swscale.c:2917: error: 'PIX_FMT_YUV422PBE' undeclared (first use in this function)
swscale.c:2917: error: 'PIX_FMT_YUV444PBE' undeclared (first use in this function)
swscale.c: In function 'sws_getCachedContext':
swscale.c:3404: warning: assignment discards qualifiers from pointer target type
make[1]: *** [swscale.o] Error 1
make[1]: Leaving directory `/home/ingo/SOURCE/mplayer/libswscale'
make: *** [libswscale/libswscale.a] Error 2

```


@mc4man: Is this what you did as well and where it worked for you???

The funny thing is though that it works if I do not replace the three libav* folders with the stuff from ffmpeg-mt (step 2). So I don't actually think it' just related to libswscale but (also) to something else.

Fresh ideas are welcome ... :-)

---

### Post by BarryBooze on 2009-04-28
mc4man's solution worked fine for me.
Try the libswscale folder from the 0.5 ffmpege release, not from current SVN ffmpeg.

---

### Post by mc4man on 2009-04-28
@disembowler
I didn't see the errors, warnings you show 
> svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg


> ..........using the one from the 0.5 release

(link in orig. post

If you know ffmpeg's code well I'm sure it could be patched, if not then some time spent could point to the differences.

As a start a merge worked, noting I can't test other than normal (for me) use of mplayer in which I've noticed no ill effects

For the moment I'd assumme BarryBooze is using the patched mplayer for what it's meant for and seems ok with it

---

### Post by vanuch on 2009-04-29
> **BarryBooze said:**
> mc4man's solution worked fine for me.
Try the libswscale folder from the 0.5 ffmpege release, not from current SVN ffmpeg.

thanks, it realy work for me. after copy folder from version 0.5 to mplayer/libswscale all configured and maked correctly.

---

### Post by disembowler on 2009-04-29
[QUOTE=mc4man]try the libswscale folder from the 0.5 ffmpege release, not from current SVN ffmpeg.[/QUOTE]


Alright! After using the libswscale libraries from the 0.5 ffmpeg release I got it working! Many thanks for helping me out here! 
Well ... I thought because 0.5 was just released March 10, there probably weren't many changes to the libswscale libs and I could just use them ... which was obvisouly wrong. :(


It might be good to update the initial post as well to reflect the necessity of having to update the libswscale sources, too.

---

### Post by Zorael on 2009-04-30
Nevermind, I omitted *--enable-live* when ./configuring and then it compiled.
> **me]I get the following and then it stops.
```
cc -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -D__STDC_LIMIT_MACROS -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -Ilibdvdread4  -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3      -c -o libmpdemux/demux_rtp.o libmpdemux/demux_rtp.cpp                                                                                
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++                  
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++      
cc1plus: warning: command line option "-std=gnu99" is valid for C/ObjC but not for C++                         
In file included from libmpdemux/demux_rtp.cpp:12:                                                             
libmpdemux/demux_rtp_internal.h:20:24: error: liveMedia.hh: No such file or directory                          
libmpdemux/demux_rtp.cpp:14:36: error: BasicUsageEnvironment.hh: No such file or directory                     
libmpdemux/demux_rtp.cpp:16:30: error: GroupsockHelper.hh: No such file or directory                           
In file included from libmpdemux/demux_rtp.cpp:12:                                                             
libmpdemux/demux_rtp_internal.h:25: error: 'MediaSubsession' has not been declared                             
libmpdemux/demux_rtp_internal.h:27: error: 'MediaSubsession' has not been declared                             
libmpdemux/demux_rtp_internal.h:36: error: 'Boolean' does not name a type                                      
libmpdemux/demux_rtp.cpp:22: error: expected `)' before '*' token                                              
libmpdemux/demux_rtp.cpp:26: error: ISO C++ forbids declaration of 'FramedSource' with no type                 
libmpdemux/demux_rtp.cpp:26: error: expected ' said:**
>  Error 1
```
Any ideas? mplayer vanilla compiles properly, but pulling ffmpeg-mt and copying those directories to the mplayer directory breaks things.

I also get the libswscale thing, but fetching the 0.5 tarball and copying its files into the svn mplayer's libswscale subdirectory made it compile properly.

---

### Post by white_hat on 2009-05-01
Hi all!
I've just compiled latest mplayer with multi-threaded h.264 support. It's easier then in this guide, just:
```

1. $ sudo apt-get install build-essential checkinstall subversion git-core libgpac-dev yasm
2. $sudo apt-get build-dep mplayer mencoder
3. $ git clone git://repo.or.cz/mplayer && cd mplayer && git checkout origin/mt && git submodule init && git submodule update && ./configure && make && sudo make install 
```That's all! Now 1080 movies can be smoothly played on my 1.3Ghz c2d without dropped frames :guitar:

$mplayer -benchmark -lavdopts threads=2 somemovie.mkv

---

### Post by HighInBC on 2009-05-02
Thanks white hat this allowed me to watch 1080p mkv files that I could not watch before. That is very helpful.

Though I assume you meant:

sudo apt-get build-dep mplayer mencoder

---

### Post by xMbx on 2009-05-02
> **white_hat said:**
> Hi all!
I've just compiled latest mplayer with multi-threaded h.264 support. It's easier then in this guide, just:
```

1. $ sudo wget http://www.medibuntu.org/sources.list.d/hardy.list \
--output-document=/etc/apt/sources.list.d/medibuntu.list
2. $ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
3. $ sudo apt-get install build-essential checkinstall subversion git libgpac-dev yasm
4. $sudo apt-get build-deb mplayer mencoder
5. $ git clone git://repo.or.cz/mplayer && cd mplayer && git checkout origin/mt && git submodule init && git submodule update && ./configure && make && sudo make install 


```That's all! Now 1080 movies can be smoothly played on my 1.3Ghz c2d without dropped frames :guitar:

$mplayer -benchmark -lavdopts threads=2 somemovie.mkv
It could be that  I missed something, your comments are wellcome
P.S. I'm not really sure if the 1st and 2nd steps are needed, You can skip them if You want...

I tried it all. I just got the problem with hardy, that it seems, that x264 cannot be found.

Checking for x264 ... no (in libavcodec: no)

So what todo to fix that ? Thanks.

---

### Post by rvm4000 on 2009-05-03
> **xMbx said:**
> I tried it all. I just got the problem with hardy, that it seems, that x264 cannot be found.

Checking for x264 ... no (in libavcodec: no)

So what todo to fix that ? Thanks.

Probably your x264 is too old. You can find a recent version for hardy (and intrepid) here:

[https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs)

(don't forget to install the -dev package too)

---

### Post by xMbx on 2009-05-03
> **rvm4000 said:**
> Probably your x264 is too old. You can find a recent version for hardy (and intrepid) here:

[https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs)

(don't forget to install the -dev package too)

Thanks; didn´t know that existed!
Looking forward to check the performance with the Phenom II 940. One Core is kinda disappointing.

---

### Post by xMbx on 2009-05-03
> **xMbx said:**
> Thanks; didn´t know that existed!
Looking forward to check the performance with the Phenom II 940. One Core is kinda disappointing.

Hmm.. mencoder is still using only one core. So what todo now ?

+ getting now alot

Too many audio packets in the buffer: (4097 in 1523941 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

---

### Post by Longinus00 on 2009-05-05
> **xMbx said:**
> Hmm.. mencoder is still using only one core. So what todo now ?

+ getting now alot

Too many audio packets in the buffer: (4097 in 1523941 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

What settings are you passing mencoder? Did you remember to use the "threads" option?

---

### Post by arimakun on 2009-05-06
Hi I've compiled mplayer with initial instructions downloading leatest svn and ffmpeg-mt from git, using libswscaler from ffmpeg 0.5, also compiled leatest smplayer and installe, every seems to be ok and play better than totem-gstreamer but I cant activate xv overlay :( has anybody tryed that? (with -vo xover and -vo xv) it allways falls back to X11 wich causes tearing and uses more cpu eating frames, it could play better on overlay. Is it something to do with the svn of mplayer having disabled xv? has anybody tryed some version of mplayer with xv successfully?
I'm using 8.04 (is the leatest stable with intel video driver until 9.10 I hope).
wich output do you use?
from command line it returns audio but no video with -vo xv and xover

---

### Post by xMbx on 2009-05-07
> **Longinus00 said:**
> What settings are you passing mencoder? Did you remember to use the "threads" option?

Yes, i do. But it does not seem to use all 4 cores. At best 2.

And this "Too many audio packets in the buffer" issue. Dunno why that is no problem with the old player, but the new one.

---

### Post by mc4man on 2009-05-07
There is an alternate way to build using a specific mplayer source, maybe you'll have better luck there

[http://ubuntuforums.org/showthread.php?t=1104967&highlight=compiling%2Bmplayer](http://ubuntuforums.org/showthread.php?t=1104967&highlight=compiling%2Bmplayer)

Are you using mencoder straight up as in mencoder blah, blah ?

---

### Post by xMbx on 2009-05-07
> **mc4man said:**
> There is an alternate way to build using a specific mplayer source, maybe you'll have better luck there

[http://ubuntuforums.org/showthread.php?t=1104967&highlight=compiling%2Bmplayer](http://ubuntuforums.org/showthread.php?t=1104967&highlight=compiling%2Bmplayer)

Are you using mencoder straight up as in mencoder blah, blah ?

Yes!

---

### Post by Longinus00 on 2009-05-07
> **arimakun said:**
> Hi I've compiled mplayer with initial instructions downloading leatest svn and ffmpeg-mt from git, using libswscaler from ffmpeg 0.5, also compiled leatest smplayer and installe, every seems to be ok and play better than totem-gstreamer but I cant activate xv overlay :( has anybody tryed that? (with -vo xover and -vo xv) it allways falls back to X11 wich causes tearing and uses more cpu eating frames, it could play better on overlay. Is it something to do with the svn of mplayer having disabled xv? has anybody tryed some version of mplayer with xv successfully?
I'm using 8.04 (is the leatest stable with intel video driver until 9.10 I hope).
wich output do you use?
from command line it returns audio but no video with -vo xv and xover

I used the instructions provided in the first post and XV output works fine for me. What are your graphics settings? I suppose if you were very unlucky then the svn code you pulled might have had some bugs in the XV implementation. I'm running SVN-r29247-4.3.2

---

### Post by Longinus00 on 2009-05-07
> **xMbx said:**
> Yes, i do. But it does not seem to use all 4 cores. At best 2.

And this "Too many audio packets in the buffer" issue. Dunno why that is no problem with the old player, but the new one.

How many threads are you telling mencoder to use? Which codec are you using to encode with? Can you show us the command you're passing to mencoder?

---

### Post by Siggma on 2009-05-15
> **Longinus00 said:**
> How many threads are you telling mencoder to use? Which codec are you using to encode with? Can you show us the command you're passing to mencoder?

Huh? Threaded **mencoder**? Now that could be cool.

If only we had a threaded C++ or GCC compiler life, for the moment, would be peaceful... ;);)

---

### Post by hanbin973 on 2009-05-18
I have a error while compiling mplayer-1.0rc2. 

```
declaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o cfg.o cfg.c
cfg.c: In function 'cfg_write':
cfg.c:299: warning: cast from pointer to integer of different size
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o bitmap.o bitmap.c
bitmap.c: In function 'pngRead':
bitmap.c:42: warning: 'avcodec_decode_video' is deprecated (declared at ../libavcodec/avcodec.h:3280)
bitmap.c:36: warning: ignoring return value of 'fread', declared with attribute warn_unused_result
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o skin/skin.o skin/skin.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o skin/font.o skin/font.c
skin/font.c: In function 'fntRead':
skin/font.c:71: warning: ignoring return value of 'fgets', declared with attribute warn_unused_result
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o skin/cut.o skin/cut.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/widgets.o mplayer/widgets.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/play.o mplayer/play.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/mw.o mplayer/mw.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/sw.o mplayer/sw.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/menu.o mplayer/menu.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/pb.o mplayer/pb.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/common.o mplayer/common.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/gtk/menu.o mplayer/gtk/menu.c
mplayer/gtk/menu.c: In function 'AddMenuCheckItem':
mplayer/gtk/menu.c:97: warning: cast to pointer from integer of different size
mplayer/gtk/menu.c: In function 'AddMenuItem':
mplayer/gtk/menu.c:128: warning: cast to pointer from integer of different size
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/gtk/mb.o mplayer/gtk/mb.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/gtk/about.o mplayer/gtk/about.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/gtk/pl.o mplayer/gtk/pl.c
mplayer/gtk/pl.c: In function 'plRowSelect':
mplayer/gtk/pl.c:189: warning: cast from pointer to integer of different size
mplayer/gtk/pl.c: In function 'plUnRowSelect':
mplayer/gtk/pl.c:198: warning: cast from pointer to integer of different size
mplayer/gtk/pl.c: In function 'plButtonReleased':
mplayer/gtk/pl.c:207: warning: cast from pointer to integer of different size
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/gtk/sb.o mplayer/gtk/sb.c
mplayer/gtk/sb.c: In function 'prButton':
mplayer/gtk/sb.c:82: warning: cast from pointer to integer of different size
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/gtk/fs.o mplayer/gtk/fs.c
mplayer/gtk/fs.c: In function 'ShowFileSelect':
mplayer/gtk/fs.c:294: warning: ignoring return value of 'chdir', declared with attribute warn_unused_result
mplayer/gtk/fs.c: In function 'fs_fsFilterCombo_activate':
mplayer/gtk/fs.c:349: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/fs.c: In function 'fs_fsFilterCombo_changed':
mplayer/gtk/fs.c:358: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/fs.c: In function 'fs_fsPathCombo_activate':
mplayer/gtk/fs.c:396: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/fs.c: In function 'fs_fsPathCombo_changed':
mplayer/gtk/fs.c:404: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/fs.c: In function 'fs_Up_released':
mplayer/gtk/fs.c:411: warning: ignoring return value of 'chdir', declared with attribute warn_unused_result
mplayer/gtk/fs.c: In function 'fs_Ok_released':
mplayer/gtk/fs.c:449: warning: assignment discards qualifiers from pointer target type
mplayer/gtk/fs.c:436: warning: ignoring return value of 'chdir', declared with attribute warn_unused_result
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/gtk/opts.o mplayer/gtk/opts.c
mplayer/gtk/opts.c: In function 'prEntry':
mplayer/gtk/opts.c:483: warning: cast from pointer to integer of different size
mplayer/gtk/opts.c: In function 'prButton':
mplayer/gtk/opts.c:515: warning: cast from pointer to integer of different size
mplayer/gtk/opts.c: In function 'prHScaler':
mplayer/gtk/opts.c:651: warning: cast from pointer to integer of different size
mplayer/gtk/opts.c: In function 'prToggled':
mplayer/gtk/opts.c:697: warning: cast from pointer to integer of different size
mplayer/gtk/opts.c:726: warning: cast from pointer to integer of different size
mplayer/gtk/opts.c: In function 'prCListRow':
mplayer/gtk/opts.c:757: warning: cast from pointer to integer of different size
mplayer/gtk/opts.c: In function 'getGtkEntryText':
mplayer/gtk/opts.c:1462: warning: return discards qualifiers from pointer target type
mplayer/gtk/opts.c: In function 'audioButton':
mplayer/gtk/opts.c:1525: warning: cast from pointer to integer of different size
mplayer/gtk/opts.c:1529: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1531: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1533: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1539: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1541: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1543: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1549: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c:1555: warning: passing argument 1 of 'gfree' from incompatible pointer type
mplayer/gtk/opts.c: In function 'dxr3Button':
mplayer/gtk/opts.c:1726: warning: cast from pointer to integer of different size
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/gtk/url.o mplayer/gtk/url.c
mplayer/gtk/url.c: In function 'on_Button_pressed':
mplayer/gtk/url.c:64: warning: cast from pointer to integer of different size
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/gtk/eq.o mplayer/gtk/eq.c
mplayer/gtk/eq.c: In function 'eqHScaleMotion':
mplayer/gtk/eq.c:163: warning: cast from pointer to integer of different size
mplayer/gtk/eq.c:178: warning: cast from pointer to integer of different size
mplayer/gtk/eq.c: In function 'eqVScaleMotion':
mplayer/gtk/eq.c:192: warning: cast from pointer to integer of different size
mplayer/gtk/eq.c: In function 'eqButtonReleased':
mplayer/gtk/eq.c:205: warning: cast from pointer to integer of different size
mplayer/gtk/eq.c: In function 'ecButtonReleased':
mplayer/gtk/eq.c:542: warning: cast from pointer to integer of different size
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o mplayer/gtk/common.o mplayer/gtk/common.c
ar r libgui.a wm/ws.o wm/wsxdnd.o app.o interface.o cfg.o bitmap.o skin/skin.o skin/font.o skin/cut.o mplayer/widgets.o mplayer/play.o mplayer/mw.o mplayer/sw.o mplayer/menu.o mplayer/pb.o mplayer/common.o mplayer/gtk/menu.o mplayer/gtk/mb.o mplayer/gtk/about.o mplayer/gtk/pl.o mplayer/gtk/sb.o mplayer/gtk/fs.o mplayer/gtk/opts.o mplayer/gtk/url.o mplayer/gtk/eq.o mplayer/gtk/common.o
ar: creating libgui.a
true libgui.a
make[3]: Leaving directory `/home/hanbin973/mplayer-1.0~rc2/gui'
/usr/bin/make -C libmenu
make[3]: Entering directory `/home/hanbin973/mplayer-1.0~rc2/libmenu'
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o menu.o menu.c
menu.c: In function 'render_txt':
menu.c:303: warning: passing argument 1 of 'utf8_get_char' from incompatible pointer type
menu.c: In function 'menu_draw_text':
menu.c:370: warning: passing argument 1 of 'utf8_get_char' from incompatible pointer type
menu.c: In function 'menu_draw_text_full':
menu.c:463: warning: passing argument 1 of 'utf8_get_char' from incompatible pointer type
menu.c:537: warning: passing argument 1 of 'utf8_get_char' from incompatible pointer type
menu.c: In function 'menu_text_length':
menu.c:565: warning: passing argument 1 of 'utf8_get_char' from incompatible pointer type
menu.c: In function 'menu_text_size':
menu.c:577: warning: passing argument 1 of 'utf8_get_char' from incompatible pointer type
menu.c: In function 'menu_text_num_lines':
menu.c:597: warning: passing argument 1 of 'utf8_get_char' from incompatible pointer type
menu.c: In function 'menu_text_get_next_line':
menu.c:612: warning: passing argument 1 of 'utf8_get_char' from incompatible pointer type
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o vf_menu.o vf_menu.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o menu_cmdlist.o menu_cmdlist.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o menu_pt.o menu_pt.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o menu_list.o menu_list.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o menu_filesel.o menu_filesel.c
menu_filesel.c: In function 'open_dir':
menu_filesel.c:214: warning: ignoring return value of 'write', declared with attribute warn_unused_result
menu_filesel.c: In function 'open_fs':
menu_filesel.c:427: warning: ignoring return value of 'getcwd', declared with attribute warn_unused_result
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o menu_txt.o menu_txt.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o menu_console.o menu_console.c
menu_console.c: In function 'run_shell_cmd':
menu_console.c:302: warning: ignoring return value of 'pipe', declared with attribute warn_unused_result
menu_console.c:303: warning: ignoring return value of 'pipe', declared with attribute warn_unused_result
menu_console.c:304: warning: ignoring return value of 'pipe', declared with attribute warn_unused_result
menu_console.c: In function 'read_key':
menu_console.c:443: warning: ignoring return value of 'write', declared with attribute warn_unused_result
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o menu_param.o menu_param.c
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o menu_dvbin.o menu_dvbin.c
menu_dvbin.c: In function 'fill_channels_menu':
menu_dvbin.c:112: warning: format '%d' expects type 'int', but argument 4 has type 'long unsigned int'
menu_dvbin.c: In function 'fill_cards_menu':
menu_dvbin.c:143: warning: format '%d' expects type 'int', but argument 3 has type 'long unsigned int'
ar r libmenu.a menu.o vf_menu.o menu_cmdlist.o menu_pt.o menu_list.o menu_filesel.o menu_txt.o menu_console.o menu_param.o menu_dvbin.o
ar: creating libmenu.a
true libmenu.a
make[3]: Leaving directory `/home/hanbin973/mplayer-1.0~rc2/libmenu'
/usr/bin/make -C libmpcodecs
make[3]: Entering directory `/home/hanbin973/mplayer-1.0~rc2/libmpcodecs'
cc -I../libavcodec -I../libavformat -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -I. -I.. -I../libavutil -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -DHAVE_CONFIG_H -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT   -I/usr/include/freetype2 -I/usr/include -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c -o native/nuppelvideo.o native/nuppelvideo.c
native/nuppelvideo.c: In function 'decode_nuv':
native/nuppelvideo.c:53: warning: passing argument 1 of 'RTjpeg_init_decompress' from incompatible pointer type
native/nuppelvideo.c:64: error: 'LZO_OUTPUT_PADDING' undeclared (first use in this function)
native/nuppelvideo.c:64: error: (Each undeclared identifier is reported only once
native/nuppelvideo.c:64: error: for each function it appears in.)
native/nuppelvideo.c:83: warning: implicit declaration of function 'lzo1x_decode'
make[3]: *** [native/nuppelvideo.o] Error 1
make[3]: Leaving directory `/home/hanbin973/mplayer-1.0~rc2/libmpcodecs'
make[2]: *** [libmpcodecs/libmpcodecs.a] Error 2
make[2]: Leaving directory `/home/hanbin973/mplayer-1.0~rc2'
make[1]: *** [build-gui-stamp] Error 2
make[1]: Leaving directory `/home/hanbin973/mplayer-1.0~rc2'
make: *** [install] Error 2
```


Any one have solution? same error coming on svn version and ubuntu repositerires version.

---

### Post by Malart on 2009-05-19
```
Initialized empty Git repository in /home/malart/ffmpeg-mt/.git/
/usr/bin/git-clone: 374: curl: not found
malart@malart-laptop:~$
```

this its what i get when i try to download the source code for ffmpeg


i know ive installed git, i made sure... so im not sure what to do

can someone with a moment help a linux noob lol


its strange... even when things f**k up, its still kinda fun :p

---

### Post by Tomasu82 on 2009-05-19
Edit, nevermind. Somehow I expected bash to run the new copy of mplayer, but it decided to be clever and run the old one, regardless of what 'which mplayer' says. stupid bash.

---

### Post by Siggma on 2009-06-02
> **hanbin973 said:**
> I have a error while compiling mplayer-1.0rc2. 

Any one have solution? same error coming on svn version and ubuntu repositerires version.

This thread is about compiling a THREADED version of mplayer. See the mplayer site and make sure you've installed all the necessary dependencies.

```
sudo apt-get build-dep mplayer mencoder
sudo apt-get -b source mplayer
```

FYI, build-dep is short for "build dependencies". In the first command, apt-get finds the mplayer source code from the *ubuntu repo* for your distro/architecture and installs all listed dependencies for you. In the second line it downloads, compiles and installs the source code (hint, hint). If you can't figure it out from there you won't find much solace in any of these "compiling" threads.

---

### Post by Siggma on 2009-06-02
[URL="http://kovensky.project357.com/indexold.html"][SIZE="4"]MPlayer[/SIZE]
Build by Kovensky[/URL]

Gleaned from all the previous posts, here is a working "handful" that will download and compile the latest Kovensky mplayer using ffmpeg-mt branch. Not meant for the lazy but for the time-deprived, finger-tired novice. Feel free to skip any steps that are not necessary. If you don't know what this does, you probably should not run it. Note the $ prevents grabbing the entire block and running it like the hopeful, lazy noob I once was and you may well be. Don't be too intimidated, it probably won't break anything important except perhaps mplayer if it fails. This is probably not something you should be doing while the kids, or your hot date/wife are waiting for you to play a new Blue Ray DVD or the latest episode of "Bones" in HD.

**Synopsis:**
a) removes the current smplayer and mplayer leaving smplayer skins and your settings. ([COLOR="DarkRed"]REMOVED[/COLOR])
b) adds medibuntu repository
c) installs necessary compile packages
d) installs optional 32 bit codecs
e) installs optional 64 bit codecs
f) installs build dependencies for mplayer/mencoder
g) uses git to clone Kovensky mplayer and ffmpeg-mt branch in $HOME
h) configures and compiles the cloned mplayer-mt source
i) uses checkinstall to create a new package and install it
j) reinstalls smplayer, if all went well, without the repo mplayer
NOTE: Step (g) can take an hour or more to download and compile, even on a fast connection with a fast processor. Kovensky's git repo is a real worm, kind of like my 3.4GHz home server on a 640K DSL modem. 

One line at a time there noob, don't get in too big a hurry, it's worth the wait.
```

$sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
$sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
$sudo apt-get install build-essential checkinstall git-core libgpac-dev yasm
$sudo apt-get -y build-dep mplayer mencoder
$cd $HOME && wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2 && sudo mkdir -pv /usr/lib/codecs && cd /usr/lib/codecs && sudo tar xjvf $HOME/all-20071007.tar.bz2 && sudo mv all-20071007/* . && sudo rm -rf all-20071007
$cd $HOME && wget http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-amd64-20071007.tar.bz2 && cd /usr/lib/codecs && sudo tar xjvf $HOME/essential-amd64-20071007.tar.bz2 && sudo mv essential-amd64-20071007/* . && sudo rm -rf essential-amd64-20071007
$cd $HOME && git clone git://repo.or.cz/mplayer && cd mplayer && git checkout origin/mt && git submodule init && git submodule update && ./configure --prefix=/usr --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer && make -j 2
$sudo apt-get install smplayer
$sudo make install

Optional install:
$sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
--pkgname mplayer --provides "mplayer,mencoder" --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
--pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"

```

[COLOR="DarkRed"]UPDATED July 15th 2009: There is no need to uninstall smplayer or your previous mplayer version.[/COLOR]

Note: on a multi core CPU you can add "-j x" where x is the number of cores to the make command to leverage multiple processors and compile this thing faster.
Dual core Example: 
```
cd $HOME && git clone git://repo.or.cz/mplayer && cd mplayer && git checkout origin/mt && git submodule init && git submodule update && ./configure --prefix=/usr --codecsdir=/usr/lib/codecs --confdir=/etc/mplayer && make -j 2
```

If you are a hopeful noob and your smplayer fails to perform up to your expectations:
```
sudo apt-get -y remove smplayer mplayer
sudo apt-get install smplayer

```Should get you back to where you started.

```
sudo apt-get remove build-dep mplayer mencoder
```Will probably remove all the build-dep packages and you can go hunt for another noob guide to fiddle with. Don't forget to delete the $HOME/mplayer directory if you decide to give up and do visit the link at the top of this post for more information.

Don't blame me if this fails on your system and you can't figure out what happened. The repos can be a bit slow and repos change over time but it's working for me as of June 2nd 2009.

Afterthought:
The latest updates will try to overwrite your newly compiled mplayer. To keep it, use Synaptic and search for "Mplayer". Highlight just the "mplayer" package, select properties from the menu and tick the "locked" option. 

-Tom

---

### Post by rvm4000 on 2009-06-12
I've just build some deb packages for mplayer-mt. You can find them here (for hardy, intrepid and jaunty):

[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

Some notes:

* The package and the executable have been renamed to mplayer-mt. This allows to have the normal mplayer and the multithreaded one installed at the same time. Just remember to run mplayer-mt instead of mplayer. If you use smplayer, remember also to change the executable in preferences -> general (it's also recommended to upgrade smplayer to at least svn r3072).

* It has no gui (gmplayer), no mencoder and no html documentation (only the manpage is installed).

* It doesn't install any configuration file, although the files in /etc/mplayer will be used if found.

* No patches have been used (only the manpage has been patched).

* This version has also support for mkv ordered chapters.

Users of hardy and intrepid will need some dependencies from here:
[https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs)

---

### Post by andrew.46 on 2009-06-12
Hi jamiyoel,

> **jamiyoel said:**
> How can I compile FFMPEG in Ubuntu 9.04?

The best guide for this is here:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Andrew

---

### Post by Siggma on 2009-06-16
> **jamiyoel said:**
> How can I compile FFMPEG in Ubuntu 9.04?

```
sudo apt-get source -b ffmpeg
```

Unless, of course, you were referring to ffmpeg-mt

---

### Post by Siggma on 2009-06-16
> **andrew.46 said:**
> Hi jamiyoel,



The best guide for this is here:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Andrew

Very nice guide, especially for a complete mencoder solution. **But** it's not a [Kovensky build]("http://kovensky.project357.com/"). In my 10+ compiles now it performs the best for playback and overall stability.
-Tom

---

### Post by n3had on 2009-08-16
> **rvm4000 said:**
> I've just build some deb packages for mplayer-mt. You can find them here (for hardy, intrepid and jaunty):

[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

Some notes:

* The package and the executable have been renamed to mplayer-mt. This allows to have the normal mplayer and the multithreaded one installed at the same time. Just remember to run mplayer-mt instead of mplayer. If you use smplayer, remember also to change the executable in preferences -> general (it's also recommended to upgrade smplayer to at least svn r3072).

* It has no gui (gmplayer), no mencoder and no html documentation (only the manpage is installed).

* It doesn't install any configuration file, although the files in /etc/mplayer will be used if found.

* No patches have been used (only the manpage has been patched).

* This version has also support for mkv ordered chapters.

Users of hardy and intrepid will need some dependencies from here:
[https://launchpad.net/~rvm/+archive/libs](https://launchpad.net/~rvm/+archive/libs)

I've installed mplayer-mt from your ppa and everything is working fine but how am i supposed to check if its using more than one core? and just to clear some confusion mplayer-mt has been compiled with multithreaded ffmpeg right?

thank you for your support

---

### Post by n3had on 2009-08-16
```
/usr/bin/mplayer-mt -noquiet -nofs -nomouseinput -vc coreserve, **-lavdopts threads=2** -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 75497487 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/tru3m0sl3m/.config/smplayer/styles.*** -fontconfig -font DejaVu Sans -subfont-autoscale 0 -subfont-osd-scale 14 -subfont-text-scale 14 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -volume 100 -cache 2000 -osdlevel  -vf-add screenshot -noslices -channels 6 -af scaletempo /media/disk-1/good.mkv -loop 0
```

and does this means i am using dual cores?

thanks again

---

### Post by n3had on 2009-08-16
i just tested two 1080p videos both on totem movie player and mplayer-mt and totem had like 5ps and mplayer-mt worked fine though its using a lot of cpu.. compared to coreavc

fair enough major improvements with regards to ffmpeg 

thanks again

---

### Post by ERamseth on 2009-09-09
OK this is driving me crazy...

I'm trying to improve my mplayer/mencoder/ffmpeg performance by compiling with dual core support.

I have tried the steps in the first post and got an error on install.

I have tried the steps here: [http://ubuntuforums.org/showpost.php?p=7391005&postcount=38](http://ubuntuforums.org/showpost.php?p=7391005&postcount=38) and installed packages from the repo here: [http://ubuntuforums.org/showpost.php?p=7443731&postcount=39](http://ubuntuforums.org/showpost.php?p=7443731&postcount=39) and that all worked well.

BG info: I am trying to transcode 1080p in real time to 720p mpeg 2 video (for streaming to an xbmc machine that is not powerful enough to decode 720p h.264 in real time, and probably for streaming to a ps3 in the future, via mediatomb.)

So before I embarked on the search for multi-core support I was getting about 16fps. After: 21 fps. Shouldn't I have noticed a much larger jump in fps? I did notice a jump in CPU usage ("measured" by looking at the output of top) from around 80 to around 166 for the mencoder process, so I'm pretty sure I am getting dual core usage...

Are there some other things I can check to see what the deal is?

My system SHOULD (I hope/think) have the horsepower to do this:

CPU: AMD Athlon 64 X2 5200+
RAM: 2GB (.5 GB to on board gfx card)
Files are being read from local HD... I'm certain it's fast enough...

If someone can point me in the right direction that'd be great....

(While typing this message I had the idea that maybe scaling from 1080p to 720p resolution is what is causing the slow down. I guess this is where I'll start my troubleshooting tomorrow...)

EDIT: I just tried without the scaling and I still hang around 18-21 fps...

---

### Post by mocha on 2009-09-10
With my Intel E6420 overclocked to 3 GHz and able to do SuperPi 1M in 11 seconds, mencoder could encode ~1000 kbps H.264 at about 35 fps as far as I remember.  Now I'm back at the default 2.13 GHz clock due to system stability issues and a similar encode goes about 25 fps.  I believe the Intel C2D processors are generally faster than the AMD X2's, when was the X2 5200+ released?  1 to 2 years ago?  If yes, then your results sound about right.

---

### Post by cord-factor on 2009-10-06
Hey, guys!
Install gcc-4.4* and all of you compile with 'cflags=-ftree-parallelize-loops=4 -fopenmp' wil be multithreaded :)

---

### Post by bofphile on 2009-11-07
I've successfully compiled mplayer with ffmpeg-mt following andrew's guide ([http://ubuntuforums.org/showthread.php?t=1305181]("http://ubuntuforums.org/showthread.php?t=1305181")). The only thing changed was this part:
```
$ cd $HOME
$ wget -N http://just.mooo.com/mplayer-svn-mt.tar.bz2
$ tar xjvf mplayer-svn-mt.tar.bz2
$ cd $HOME/mplayer
```

instead of this:
```
$ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
$ cd $HOME/mplayer
```

But I when I play Bluray files, frames are dropped while my dual core CPU is not fully used and the load is not spread evenly between the 2 cores. By default the governor is set to ondemand but even when I fix the frequency of my 2 cores at their maximum speed, the problem remains.

I've tried several options like noframedrop and cache size, but the issue is still there. Here is a screenshot to show the CPU load when playing a m2ts file:
[http://bofphile.free.fr/Images/Capture-1.jpg](http://bofphile.free.fr/Images/Capture-1.jpg)

I'm using a Thinkpad T500 with a 2,67GHz dual core CPU and an integrated intel 4500MHD graphic card.

Any idea what could be the problem ?

---

### Post by stevenpusser on 2009-12-17
Issues such as this may be due to problems with the CFS scheduler--perhaps trying a Liquorix kernel with the BFS scheduler might help...

---

### Post by industrai on 2010-01-27
Big thanks for putting this together!  I just went through the steps, and I'm now watching 720p mkv rips on my little acer aspire one netbook with Ubuntu 9.10 Karmic.  If anyone else is in the same boat as me I had to do a couple of additional tweaks in smplayer to boost performance, specifically:

-video output driver: gl (fast)
-enable direct rendering
-audio out: alsa
-threads for decoding h.264: 2
-Loop Filter: Skip only on HD videos

Now I don't have to buy a broadcom hd card or coreavc.  THANKS!

---

### Post by tito_torrisi on 2010-02-27
Or you could use new versions from debian sid:

[http://ubuntuforums.org/showthread.php?p=8889887#post8889887](http://ubuntuforums.org/showthread.php?p=8889887#post8889887)

---

### Post by Redsandro on 2011-03-15
This is nice! I wanted mplayer-mt. I read the guide, thought meh it never gets any easier, and then found this:

```
sudo apt-add-repository ppa:ripps818/coreavc
sudo apt-get update
sudo apt-get upgrade
```

mplayer gets updated to mt version. CoreAVS has nothing to do with it. It's easy indeed! :)

Note: This works for MPlayer. Gnome MPlayer does not use MPlayer. Use a different GUI to experience the improvement. KMPlayer for example.

---

### Post by cuongvt101 on 2011-05-10
Hi all. I notice that ffmpeg has two options for multithread decoding: Slice threading and Frame threading. How would select which option to use in Mplayer? Thanks

---

### Post by Redsandro on 2011-05-10
Is it new? Because I never had to select anything. Just installing the thing and everything is multicored out of the box. I use it as external player for XBMC, and it works with movies that are too slow on singe core. But I never had to choose anything.

---

### Post by cuongvt101 on 2011-05-11
Yeah I know. Mine works out of the box as well, I just don't know which method mplayer (ffmpeg) is using, Slide or Frame (one of them is being used for sure). I want to test the speed of each method for my specific case.

---

### Post by Redsandro on 2011-05-11
Ah ok, sorry I haven't got a clue. Don't know the difference. It's enough for me that it works, but I can understand you want to benchmark.

If you figure it out, please don't hesitate to share your benchmark results. :)

---

### Post by cuongvt101 on 2011-05-11
Sure will. I just figured out that seems like Frame Threading is set by default!

---

### Post by cuongvt101 on 2011-05-16
Still haven't figured out yet. Even sent a message to Strange. Any one have any idea?

---

### Post by trancephorm on 2011-05-18
Been struggling for days now to make multithreaded mplayer work... I think I did pretty much straightforward things, and it seems that it is played multithreaded (which I can see from htop), but every few seconds, playback of h.264 1080p freezes for a moment, not to mention sound isn't working at all (but that's the easier problem I think)... it freezes even with -nosound option.

So I grabbed latest mplayer source from SVN which should include latest multithreaded ffmpeg too, compiled it all and tried mplayer -lavdopts threads=4... freezes every few seconds, then I replaced ffmpeg source under mplayer dir with ffmpeg-mt from git, recompiled mplayer - still the same...

I just don't know what should I do next, maybe it's not the problem in mplayer/ffmpeg at all, maybe it's video drivers, video output... I have Core 2 Duo T5800 2 GHz, 3 GB DDR2, it's Asus X65VA laptop.

Actually, in this 11.04 installation I managed to make it work in ripps mplayer/CoreAVC combination, but only for short period. Now I get something like "x11 not initialized", when I try it that way... Under previous Ubuntu 10.04 installation CoreAVC combination worked, but there were some nasty bugs fast forwarding the movies in SMPlayer, so I decided I should try it again..

Huh...... Hope someone will help a poor man that understands the value of Linux, but still... I must make an observation: In Windows, these kind of problems are much less frequent... There, everything tends to be simpler and most of the time it works at once... 

The more... Really I can't consider any Linux distro to be serious if it doesn't use all cores when decoding 1080p, out of a box... And so far, I think no distro supports it. Yeah I know, it's all still experimental with mplayer/vlc, but how many more fu*king years do we have to wait??? I mean, things like this are serious disadvantage for Linux compared to Windows, and may be part of the reason Linux is not adopted more widely...

While I'm here, need to continue my rant... Today I installed Linux Mint 10 LXDE.. Guess what, network proxy support is completely broken! And it seems that is the problem with previous versions too. Sometimes, Linux lacks some really basic things, which is sad because the whole philosophy behind is much much better than using proprietary operating systems...

---

### Post by Redsandro on 2011-05-18
I am sorry, I don't know what the problem is. But the first thing that comes to mind is your distro.

Please don't compare Windows, investing billions of dollars into a hassle free user experience, with Ubuntu, volunteers and charity.

Remember you're running Ubuntu, one of the most cutting edge unstable desktop distributions. And you're not even running LTS, you're running the in-between releases which can be considered bleeding edge beta at best. 11.04 is rubbish. Much complaints over media related applications. I've seen VLC (media player) break in this installation and there have been reported driver issues.

Fixing issues goes in this order, I think you missed step 2. :)

1) You can do it yourself
2) You need to stick to LTS
3) Ask for help
4) Change distro

Just my 4 cents, based on all the troubles I've seen with 11.04. Remember, it took me 3 lines of terminal code (earlier in this thread) to get this working without the need for extra command line options or whatever, in 10.04 LTS.

---

### Post by trancephorm on 2011-05-19
okies, Linux still rule, don't get me wrong :)... But let's be constructive and helpful... I managed to make it work flawlessly...
It's Asus X56VA laptop, Core 2 Duo 2 GHz, 3 GB DDR2, ATI Radeon Mobility HD 3650. Ubuntu 11.04, installed proprietary video drivers regularily from menus...

Used ripps version of mplayer, CoreAVC decoder 2.5 in Wine... Here's my .mplayer/config file:
```

vo=gl   #vith xv I get occasional small but visible stuttering
stop-xscreensaver=yes

#seems like coreavc codec is using 2 cores itself, when I put 2 or more, actually I get stuttering... Anybody can confirm?
lavdopts=threads=1

vc=coreserve
subcp=cp1250

```

When I use any of the mplayer GUIs I get stuttering, tried several of them... But now I don't really see a need for using them because mplayer itself is pretty much powerful and fast when you learn keyboard commands....

---

