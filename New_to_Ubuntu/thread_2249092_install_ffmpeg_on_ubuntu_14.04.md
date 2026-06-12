---
title: "install ffmpeg on ubuntu 14.04"
date: 2014-10-19
forum: New to Ubuntu
---

### Post by micahpage on 2014-10-19
I dont know why ubuntu is the odd man out in linux now that they use avconv instead of ffmpeg. Every other distro still uses ffmpeg. 

I am trying to install ffmpeg on ubuntu 14.04 to concatenate 4 VOB files to mp4. I had ffmpeg working fine in 13.10, but i forgot the process to install it now that it is no longer in the repos in 14.04. The command in ffmpeg that i use in other distros is:

```
ffmpeg -i concat:"VTS_01_1.VOB|VTS_01_2.VOB|VTS_01_3.VOB|VTS_01_4.VOB" -acodec libmp3lame -aq 100 -ac 2 -vcodec libx264 -crf 20 -threads 0 output.mp4
```

I dont know what the equivalent would be in avconv. 

my history of installation is:
```
  501  ffmpeg -i concat:"VTS_01_1.VOB|VTS_01_2.VOB|VTS_01_3.VOB|VTS_01_4.VOB" -acodec libmp3lame -aq 100 -ac 2 -vcodec libx264 -crf 20 -threads 0 output.mp4  502  sudo apt-get install ffmpeg
  503  sudo apt-cache search ffmpeg
  504  sudo apt-add-repository ppa:jon-severinsson/ffmpeg
  505  sudo apt-get update
  506  sudo apt-get install ffmpeg
  507  ffmpeg -i concat:"VTS_01_1.VOB|VTS_01_2.VOB|VTS_01_3.VOB|VTS_01_4.VOB" -acodec libmp3lame -aq 100 -ac 2 -vcodec libx264 -crf 20 -threads 0 output.mp4
  508  sudo add-apt-repository 'deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu '"$(cat /etc/*-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f2)"' main' && sudo apt-get update
  509  ffmpeg -i concat:"VTS_01_1.VOB|VTS_01_2.VOB|VTS_01_3.VOB|VTS_01_4.VOB" -acodec libmp3lame -aq 100 -ac 2 -vcodec libx264 -crf 20 -threads 0 output.mp4
  510  sudo apt-get install frei0r-plugins
  511  ffmpeg -i concat:"VTS_01_1.VOB|VTS_01_2.VOB|VTS_01_3.VOB|VTS_01_4.VOB" -acodec libmp3lame -aq 100 -ac 2 -vcodec libx264 -crf 20 -threads 0 output.mp4
  512  cat /etc/apt/sources.list
  513  sudo apt-cache search libavcodec
  514  sudo apt-get install libavcodec-extra-54
  515  sudo apt-cache search libavdevices
  516  sudo apt-get install libavdevice-extra-54
  517  sudo apt-get install libavdevice-extra-53
  518  sudo apt-cache search libavfilter-extra
  519  sudo apt-get install libavfilter-extra-3
  520  sudo apt-caceh search libavformat-extra
  521  sudo apt-cache search libavformat-extra
  522  sudo apt-get install libavformat-extra-54
  523  sudo apt-cache search libavutil-extra
  524  sudo apt-cache search libavutil-extra-52
  525  sudo apt-get install libavutil-extra-52
  526  sudo apt-cache search libpostproc-extra
  527  sudo apt-get install libpostproc-extra-52
  528  sudo apt-cache search libswscale-extra
  529  sudo apt-get install libswscale-extra-2
  530  ffmpeg -i concat:"VTS_01_1.VOB|VTS_01_2.VOB|VTS_01_3.VOB|VTS_01_4.VOB" -acodec libmp3lame -aq 100 -ac 2 -vcodec libx264 -crf 20 -threads 0 output.mp4
  531  sudo remove ffmpeg
  532  sudo agpt-get remove ffmpeg
  533  sudo apt-get remove ffmpeg
  534  sudo apt-get install ffmpeg
  535  ffmpeg -i concat:"VTS_01_1.VOB|VTS_01_2.VOB|VTS_01_3.VOB|VTS_01_4.VOB" -acodec libmp3lame -aq 100 -ac 2 -vcodec libx264 -crf 20 -threads 0 output.mp4
  536  history



```

the execution of it
```
metulburr@ubuntu ~/Documents  $ ls
VTS_01_1.VOB  VTS_02_1.VOB  VTS_03_1.VOB  VTS_04_1.VOB
metulburr@ubuntu ~/Documents $ ffmpeg -i concat:"VTS_01_1.VOB|VTS_01_2.VOB|VTS_01_3.VOB|VTS_01_4.VOB" -acodec libmp3lame -aq 100 -ac 2 -vcodec libx264 -crf 20 -threads 0 output.mp4
ffmpeg version 1.2.6-7:1.2.6-1~trusty1 Copyright (c) 2000-2014 the FFmpeg developers
  built on Apr 26 2014 18:52:58 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: --arch=amd64 --disable-stripping --enable-avresample --enable-pthreads --enable-runtime-cpudetect --extra-version='7:1.2.6-1~trusty1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  avcodec     configuration: --arch=amd64 --disable-stripping --enable-avresample --enable-pthreads --enable-runtime-cpudetect --extra-version='7:1.2.6-1~trusty1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libvo-aacenc --enable-libvo-amrwbenc
  libavutil      52. 18.100 / 52. 18.100
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.104 / 54. 63.104
  libavdevice    53.  5.103 / 53.  5.103
  libavfilter     3. 42.103 /  3. 42.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
concat:VTS_01_1.VOB|VTS_01_2.VOB|VTS_01_3.VOB|VTS_01_4.VOB: No such file or directory
metulburr@ubuntu ~/Documents  $ 
```

---

### Post by micahpage on 2014-10-19
Oh whoops, the problem was i mistyped the file names.

---

### Post by FakeOutdoorsman on 2014-10-19
You have 3 main options if you want a recent build which is almost always recommended:

[list]
[*][download, extract, and execute a static build of ffmpeg](http://johnvansickle.com/ffmpeg/)
[*][use mc3man's PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) (Jon Severinsson's PPA offers old branches for compatibility with old repo offerings)
[*][compile ffmpeg by following a step-by-step guide](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)
[/list]

If you're concatenating videos from a DVD you may want to investigate tools/dvd2concat (depends on lsdvd) in the ffmpeg source. From [[FFmpeg-user] Can I change overlay color of subtitle?](http://ffmpeg.org/pipermail/ffmpeg-user/2014-October/023857.html):

> As a side note, I see your command line accesses the VOB files directly in
the DVD-Video file structure. That is almost always wrong. You need to use
DVD-Video-aware software to reconstruct the MPEG streams correctly. You can
use the dvd2concat for that for example, or mplayer -dumpstream.

---

### Post by ajgreeny on 2014-10-19
It does looks if you can do the same with avconv.

Here's an extract from **man avconv**
   ```
concat
       Physical concatenation protocol.

       Allow to read and seek from many resource in sequence as if they were a unique resource.

       A URL accepted by this protocol has the syntax:

               concat:<URL1>|<URL2>|...|<URLN>

       where URL1, URL2, ..., URLN are the urls of the resource to be concatenated, each one possibly specifying a
       distinct protocol.

       For example to read a sequence of files split1.mpeg, split2.mpeg, split3.mpeg with avplay use the command:

               avplay concat:split1.mpeg\|split2.mpeg\|split3.mpeg

       Note that you may need to escape the character "|" which is special for many shells.
```

I have just this minute tested this and I can tell you that it has worked with no problem using the command 
```
avconv -i concat:"VTS_02_1.VOB|VTS_02_2.VOB|VTS_02_3.VOB" -vcodec mpeg2video -q 6 -ab 128k mcbeth.mpg
```so if you don't want to bother with installing ffmpeg, avconv will do it for you as well.

---

### Post by andrew.46 on 2014-11-04
> **micahpage said:**
> I dont know why ubuntu is the odd man out in linux now that they use avconv instead of ffmpeg. 

I believe that after the fork the Debian FFmpeg packager started packaging *libav* instead, hence Ubuntu now has avconv instead of FFmpeg... Some details in this thread:

Ubuntu renaming FFmpeg to libav
[https://lists.ubuntu.com/archives/technical-board/2011-May/000883.html](https://lists.ubuntu.com/archives/technical-board/2011-May/000883.html)

This dispute has been sputtering along for years now :(

---

