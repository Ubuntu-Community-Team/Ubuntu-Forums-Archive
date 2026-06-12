---
title: "HOWTO: Quickly convert videos to Ipod / Smartphone format"
date: 2007-07-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Footissimo on 2007-07-23
Found a little script that will convert videos to IPod video format (i.e. mp4 with xvid and aac encoding) utilising ffmpeg and ruby.  The nice thing about this is that it will preserve the original aspect ratio and add black bars depending, so videos look like they should do (well aside from being in QVGA 320x240 resolution!).  Some smartphones (such as the Nokia N95) are also able to display this format =)

The script can be found [here](http://thomer.com/howtos/mp4ize)

For a little HOWTO:

Open up synaptic and ensure that you have ffmpeg and ruby installed/

Download the script:

```
wget http://thomer.com/howtos/mp4ize
```

Make it so you can run it:

```
chmod +x mp4ize
```

Move it so it's system-wide:

```
sudo mv mp4ize /usr/local/bin
```

Now, if you want to convert a video, just open up a terminal and type mp4ize [videoname] and it will make an IPod mp4 version in the same folder.  Enterprising Nautilus Actions users may want to add a right click menu version for this by adding /usr/local/bin/mp4ize as a path and %M as a parameter.

---

### Post by phillips321 on 2007-08-09
works great, would be nice if we could adjust the framerame aswell

i find video bitrate of 200 and audio of 64 works best

would like to drop fps to 15 on all the videos as well

any possibility you can add this feature?

---

### Post by Footissimo on 2007-08-09
Hiya

As I mentioned, I didn't do the actual mp4ize script, but I would imagine that it's possible to change the ruby script

```
DEFAULT_ARGS = "-f mp4 -vcodec xvid -maxrate 1000 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac"
``` and add -r 15 (though check with man ffmpeg, then resave the file.

Will try and bit later - good point about the n95 max rate, didn't realise it was 15.

---

### Post by Footissimo on 2007-08-09
Altered the framerate and bitrates to your specs - takes off a fair chunk of the file size (approx a 1/3rd on the two I've tried).

Edit:  The second file is the script with the bitrate changes but not the framerate changes - this increases the resultant file size a little, but gets rid of the choppiness.

---

### Post by DAFORZE on 2007-08-29
Hey thanks for the tutorial..!
But actually i read that the video play of n95 fps was max 30 fps..? 

I tried to do what you did with the first script and it works for several video files but with every video my n95 doesn't play audio but it does play the video.. What should i do to also make the audio work? 
Or should I try another video convertor..?
Thankss

---

### Post by jzlharvey on 2007-08-29
Hi guys, I am getting this when I try to run it.  Any help would be greatly appreciated.

```

jzl@fawn:~/Desktop$ mp4ize test.avi FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, avi, from 'test.avi':
  Duration: 00:42:40.5, start: 0.000000, bitrate: 1146 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 624x352, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 160 kb/s
Must supply at least one output file
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Unknown codec 'xvid'
```

---

### Post by DAFORZE on 2007-08-30
Have u tried running it with an other avi file?

---

### Post by martynp on 2007-08-30
I get the same 'unknown codex xvid' error.

Have tried different .avi files with no change.

I hope someone can direct us on where we are going wrong/what we need to do to fix.

Many Thanks

---

### Post by jzlharvey on 2007-08-30
daforze, I have tried 10 different video files.

---

### Post by DAFORZE on 2007-08-30
I think this guide is better: [http://ubuntuforums.org/showthread.php?t=321943&highlight=n95](http://ubuntuforums.org/showthread.php?t=321943&highlight=n95)

But it wouldn't succeed for me as I already had some weird problems with my repositories so I cant  get trough the guide.. 

So now now i'm converting my videos on WINDOWS :mad: !!!
But eh let me know if it worked?

---

### Post by jzlharvey on 2007-08-30
> **DAFORZE said:**
> I think this guide is better: [http://ubuntuforums.org/showthread.php?t=321943&highlight=n95](http://ubuntuforums.org/showthread.php?t=321943&highlight=n95)

But it wouldn't succeed for me as I already had some weird problems with my repositories so I cant  get trough the guide.. 

So now now i'm converting my videos on WINDOWS :mad: !!!
But eh let me know if it worked?

It's not worth it to me do go thru all that.  I was just wanting the option (easy option) of having it in my context menu should I ever want to throw a show on my iPhone.  Thanks for the link tho!

---

### Post by DAFORZE on 2007-08-30
Oh okay.. well anyway its weird that you get an other error then me.. I think you don't have the codecs that I have installed?
Did u installed the multimedia codecs?
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

---

### Post by jzlharvey on 2007-08-30
> **DAFORZE said:**
> Oh okay.. well anyway its weird that you get an other error then me.. I think you don't have the codecs that I have installed?
Did u installed the multimedia codecs?
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

Yeah, that is what I thought.... I've installed every codec known to man.  On both my edgy 6.10 (production server) and my 7.04 play box.  Neither are a go. :(

---

### Post by Big-Wayne on 2007-08-30
I used this gui freeware from MIKsoft. it works ok for me.
[http://www.miksoft.net/products/mmc-lin.tar.gz]("http://www.miksoft.net/products/mmc-lin.tar.gz")
It uses ffmpeg and allows you to convert to amr, mp3, 3gp and mpeg no mpeg4 support, but most phones play .3gp files.

:)

---

### Post by jzlharvey on 2007-08-30
> **Big-Wayne said:**
> I used this gui freeware from MIKsoft. it works ok for me.
[http://www.miksoft.net/products/mmc-lin.tar.gz]("http://www.miksoft.net/products/mmc-lin.tar.gz")
It uses ffmpeg and allows you to convert to amr, mp3, 3gp and mpeg no mpeg4 support, but most phones play .3gp files.

:)

Thanks.  But now this issue has proven to be a " I will get this to work the way I want to" kinda thing.  I hate when i cant figure crap out. :(

---

### Post by phillips321 on 2007-09-01
Hi guys,

Just reinstalled my system and tried to reinstall mp4ize but for some reason im getting the error as follows:

```
phillips321@LinuxDesktop:/media/data/Videos$ mp4ize EvanAlmighty.avi 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, avi, from 'EvanAlmighty.avi':
  Duration: 01:31:37.9, start: 0.000000, bitrate: 1091 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 672x288, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 192 kb/s
Must supply at least one output file
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Unknown codec 'xvid'
phillips321@LinuxDesktop:/media/data/Videos$ 

```

anyone know why i get the **Unknown codec 'xvid'**

---

### Post by jzlharvey on 2007-09-01
> **phillips321 said:**
> Hi guys,

Just reinstalled my system and tried to reinstall mp4ize but for some reason im getting the error as follows:

```
phillips321@LinuxDesktop:/media/data/Videos$ mp4ize EvanAlmighty.avi 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, avi, from 'EvanAlmighty.avi':
  Duration: 01:31:37.9, start: 0.000000, bitrate: 1091 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 672x288, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 192 kb/s
Must supply at least one output file
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Unknown codec 'xvid'
phillips321@LinuxDesktop:/media/data/Videos$ 

```

anyone know why i get the **Unknown codec 'xvid'**


I still have yet to get mine going either.  I still have the same error.

---

### Post by phillips321 on 2007-09-01
[WEBSITE_LINK_HERE]("http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2005-December/005912.html")
> Long ago I did an install of ffmpeg (without xvid) and most notably a 
'make installlibs', which installed libavcodec.a and a few others into 
'/opt/dvb/lib'. Since this is where I also put libxvidcore I had to give 
the '--extra-ldflags=-L /opt/dvb/lib' to the configure of ffmpeg.
However I have noticed that when 'make' links ffmpeg it does link it 
with libavcodec.a amonst others. But since the -L and -I flags to 
/opt/dvb/include and /opt/dvb/lib are put before the -L and -I flags 
poiting to ./libavcodec in the ffmpeg sourcetree this meant ffmpeg was 
linked to an old libavcodec.a.

I did a 'make installlibs' from the newly build sourcetree. This placed 
the up-to-date libavcodec.a in '/opt/dvb/lib'. Then I built (only 
linking should have sufficed, but I couldn't force make to do this) 
ffmeg again and... hey presto... now ffmpeg lists xvid as a codec. And I 
can now produce xvid avi files.

would this help?

---

### Post by jzlharvey on 2007-09-02
> **phillips321 said:**
> [WEBSITE_LINK_HERE]("http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2005-December/005912.html")


would this help?

If I knew what it was talking about, it might help. LOL

---

### Post by phillips321 on 2007-09-02
SOLVED!!!

basically we needed to include xvid into the build of ffmpeg

```
sudo apt-get build-dep ffmpeg
sudo apt-get install ffmpeg
sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libx264-dev
apt-get source ffmpeg
```
Change line 147 in libavcodec/x264.c from

```
x4->params.rc.i_rf_constant = avctx->crf
```

to

```
x4->params.rc.f_rf_constant = avctx->crf
```

(notice the f instead of the i)
```
cd ffmpeg-*/
./configure --enable-gpl --enable-pp --enable-pthreads \
        --enable-libogg --enable-a52 --enable-dts \
        --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
        --enable-faad --enable-faac --enable-xvid --enable-x264
make
sudo make install
```

links that helped me 
[Error about line 147]("http://ubuntuforums.org/showthread.php?t=418883&highlight=configure+ffmpeg")
[Rebuilding ffmpeg]("https://help.ubuntu.com/community/iPodVideoEncoding")

---

### Post by jzlharvey on 2007-09-03
> **phillips321 said:**
> SOLVED!!!

basically we needed to include xvid into the build of ffmpeg

```
sudo apt-get build-dep ffmpeg
sudo apt-get install ffmpeg
sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libx264-dev
apt-get source ffmpeg
```
Change line 147 in libavcodec/x264.c from

```
x4->params.rc.i_rf_constant = avctx->crf
```

to

```
x4->params.rc.f_rf_constant = avctx->crf
```

(notice the f instead of the i)
```
cd ffmpeg-*/
./configure --enable-gpl --enable-pp --enable-pthreads \
        --enable-libogg --enable-a52 --enable-dts \
        --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
        --enable-faad --enable-faac --enable-xvid --enable-x264
make
sudo make install
```

links that helped me 
[Error about line 147]("http://ubuntuforums.org/showthread.php?t=418883&highlight=configure+ffmpeg")
[Rebuilding ffmpeg]("https://help.ubuntu.com/community/iPodVideoEncoding")


Nice!  It is now encoding for me as well.  That was one hell of job in finding the problem.  Way too technical for me but I did benefit from you work.. Thanks.

---

### Post by niteblind on 2008-04-15
Hi

Can anyone let me know why I cannot find the following file :
"Change line 147 in libavcodec/x264.c"

I cannot seem to find it  anywhere and I have followed both sets of instructions/

niteblind

---

### Post by neonmagnolia on 2008-04-19
> **niteblind said:**
> Hi

Can anyone let me know why I cannot find the following file :
"Change line 147 in libavcodec/x264.c"

I cannot seem to find it  anywhere and I have followed both sets of instructions/

niteblind

I'm having the same issue. Can't find the file.

---

### Post by durand on 2008-06-05
There is a h264.c file so it was probably renamed. I'm currently compiling it without that change on intrepid so I'll get you know how it goes.

EDIT: Didn't go well at all. I got a load of gcc errors and I don't have the time to diagnose them at the moment.

However, I did find a good program called mvPod which is at the moment, converting a video of mine. It seems to work properly. Look [here]("https://help.ubuntu.com/community/iPodVideoEncoding") for more details.

---

### Post by abuakel on 2008-07-19
will this work in Ubuntu Hardy?

---

