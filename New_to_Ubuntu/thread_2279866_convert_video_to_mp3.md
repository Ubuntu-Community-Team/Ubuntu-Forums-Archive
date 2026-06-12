---
title: "convert video to mp3"
date: 2015-05-26
forum: New to Ubuntu
---

### Post by briar rabbit on 2015-05-26
Hi
I wanna convert videos to audios.

I did this:
[http://ubuntuforums.org/showthread.php?t=2248814&highlight=convert+video+to+mp3](http://ubuntuforums.org/showthread.php?t=2248814&highlight=convert+video+to+mp3)

AND I GOT THIS:
youtube-dl: error: no such option: --audio-quality

AND THIS:
youtube-dl: error: no such option: --keep-video

I tried with another video: [http://www.ted.com/talks/jessa_gamble_how_to_sleep](http://www.ted.com/talks/jessa_gamble_how_to_sleep)

AND GOT THIS:
Usage: youtube-dl [options] url...
AND THIS:
youtube-dl: error: no such option: --prefer-ffmpeg

It seemed sooooo simple but as usual it ain't soooo.

Would anyone mind sharing how, if it is possible to convert video files to audio?

In searching the internet it seems there is a lot of free virus ware converting software out there but I don't want anything with a virus cuzz I heard those are not very nice.

thank you.

---

### Post by howefield on 2015-05-26
Just tried it and worked flawlessly with both the video in the quoted thread and your other one above.

Maybe you could post a screenshot of your terminal with the error.

---

### Post by Vladlenin5000 on 2015-05-26
If you're asking about how to convert videos, regardless of what they are and where they come from, then you should ask it that way. There are dozens of apps for that and most are already available in Ubuntu repositories.
Downloading from YT is a violation of its terms of service and not allowed here.

---

### Post by Elie_Daou on 2015-05-26
If you just want to convert mp4 formats to mp3 then the code provided in the linked thread works perfectly. In case you overlooked it it's 
```
[COLOR=#000000][FONT=Ubuntu Mono]ffmpeg -i filename.mp4 filename.mp3
```
As for the Youtube download thing, it violates the forums code of conduct so you're better off asking it somewhere else or better still not do it at all.[/FONT][/COLOR]

---

### Post by mc4man on 2015-05-26
1. There has been no mention of any site here other than Ted Talks, seems ok to discuss
2. If you are on 10.04 then who knows what you can do, otherwise you may wish to use a recent version of youtube-dl if yours is lacking
youtube-dl --help would give you available options. A newer version is here - [https://rg3.github.io/youtube-dl/download.html](https://rg3.github.io/youtube-dl/download.html)

3. The command in other thread is a bit more than you appear to need, something like this would suffice - 
```
youtube-dl http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep  --extract-audio --audio-format mp3 --audio-quality 3
```

However you could also first check to see if format desired is available - ex.
```
youtube-dl -F http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep
```
There you'd see mp3 is there already, if that suited then youtube-dl -f format url or *in this particular case*
```
youtube-dl -f audio http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep

```
If on recent Ubuntu release then you could simply install libav-tools which contains avconv which is the current default of youtube-dl, no need to specify in command

---

### Post by briar rabbit on 2015-05-26
If any one can help with this mess, that would be great. cuz i don't get it.

[HTMLferg@ferg-VII-160:~$ sudo curl [https://yt-dl.org/downloads/2015.05.20/youtube-dl](https://yt-dl.org/downloads/2015.05.20/youtube-dl) -o /usr/local/bin/youtube-dl
[sudo] password for ferg: 
sudo: curl: command not found
ferg@ferg-VII-160:~$ youtube-dl [http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep](http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep)  --extract-audio --audio-format mp3 --audio-quality 3
Usage: youtube-dl [options] url...

youtube-dl: error: no such option: --audio-quality
ferg@ferg-VII-160:~$ youtube-dl -F [http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep](http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep)
Usage: youtube-dl [options] url...

youtube-dl: error: no such option: -F
ferg@ferg-VII-160:~$ youtube-dl -f audio [http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep](http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep)
WARNING: Falling back on generic information extractor.
[generic] jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep: Downloading webpage
[generic] jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep: Extracting information
ERROR: Invalid URL: [http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep](http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep)
ferg@ferg-VII-160:~$ ][/HTML]

---

### Post by mc4man on 2015-05-26
> sudo curl [https://yt-dl.org/downloads/2015.05.20/youtube-dl](https://yt-dl.org/downloads/2015.05.20/youtube-dl) -o /usr/local/bin/youtube-dl
[sudo] password for ferg:
sudo: curl: command not found
That means curl isn't installed, youtube-dl was not downloaded & was not installed, so install curl 
(or read that web page a little more carefully
```
sudo apt-get install curl
```
```
sudo curl https://yt-dl.org/downloads/2015.05.20/youtube-dl -o /usr/local/bin/youtube-dl
```
```
sudo chmod a+x /usr/local/bin/youtube-dl
```
Then try, try, again.

---

### Post by monkeybrain20122 on 2015-05-27
You can get youtube-dl from ppa [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8) Advantage is that it gets updated frequently.

---

### Post by jacobpratt909 on 2015-05-27
I saw that it said: > [COLOR=#000000]youtube-dl: error: no such option: --prefer-ffmpeg[/COLOR]

I think it means that it is trying to use ffmpeg, and the newer versions of Ubuntu no longer include ffmpeg. As mc4man said: > [COLOR=#000000]If on recent Ubuntu release then you could simply install libav-tools which contains avconv which is the current default of youtube-dl, no need to specify in command[/COLOR]
Just simply get the libav-tools to use with youtube-dl.
You can probably get it via ```
sudo apt-get install libav-tools
``` or you may need to find a repository, although I am pretty sure it is in the Ubuntu repository.

I also see a lot of errors in what you type. some are as included:
> [COLOR=#000000]youtube-dl: error: no such option: --audio-quality[/COLOR]
> [COLOR=#000000]youtube-dl: error: no such option: -F[/COLOR]
and
> [COLOR=#000000]ERROR: Invalid URL: [/COLOR][http://www.ted.com/talks/jeff_iliff_..._night_s_sleep]("http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep")
You may want to check that out.

---

### Post by monkeybrain20122 on 2015-05-27
Works here

```
$ youtube-dl -F [http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep](http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep)
[ted] jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep: Downloading webpage
[ted] jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep: Extracting information
[ted] jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep: Downloading m3u8 information
[info] Available formats for 2103:
format code  extension  resolution note
hls-meta     mp4        multiple   Quality selection URL 
audio        mp3        audio only 
rtmp-64k     flv        398x224      64k 
hls-67       mp4        audio only   67k 
rtmp-180k    flv        512x288     180k 
hls-188      mp4        320x180     188k , avc1, video only
rtmp-320k    flv        512x288     320k 
rtmp-450k    flv        512x288     450k 
hls-494      mp4        512x288     494k , avc1, video only
rtmp-600k    flv        640x360     600k 
hls-770      mp4        512x288     770k , avc1, video only
rtmp-950k    flv        854x480     950k 
hls-967      mp4        512x288     967k , avc1, video only
hls-1247     mp4        640x360    1247k , avc1, video only
rtmp-1500k   flv        1280x720   1500k 
hls-1597     mp4        853x480    1597k , avc1, video only
hls-2183     mp4        1280x720   2183k , avc1, video only
h264-320k    mp4        unknown     320k 
low          mp4        320x180    
medium       mp4        512x288    
high         mp4        854x480    (best)
```

How did you install youtube-dl?

---

### Post by QIII on 2015-05-27
> **Vladlenin5000 said:**
> 
Downloading from YT is a violation of its terms of service and not allowed here.

Agreed.  But downloading them from ted.com is OK.  However, the YouTube download software won't necessarily work. If it will, as it may in some cases, using youtube-dl to get videos where they are available and legal to download is not an issue.  It's downloading protected content that we won't discuss.

But I was just able to download it perfectly fine from ted.com just by clicking the download button.

For mobile devices, you need to use the TED app and as far as I know you can only get that from the iTunes store or GooglePlay.

---

### Post by briar rabbit on 2015-05-27
I made 3 (I think 3) big steps but, its dark in here and I am not sure if those steps were in the same direction.

[HTML]ferg@ferg-VII-160:~$ sudo apt-get install curl
[sudo] password for ferg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  curl
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 210kB of archives.
After this operation, 324kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main curl 7.19.7-1ubuntu1.11 [210kB]
Fetched 210kB in 0s (219kB/s)
Selecting previously deselected package curl.
(Reading database ... 145351 files and directories currently installed.)
Unpacking curl (from .../curl_7.19.7-1ubuntu1.11_i386.deb) ...
Processing triggers for man-db ...
Setting up curl (7.19.7-1ubuntu1.11) ...
ferg@ferg-VII-160:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ferg@ferg-VII-160:~$ y
y: command not found
ferg@ferg-VII-160:~$ sudo curl https://yt-dl.org/downloads/2015.05.20/youtube-dl -o /usr/local/bin/youtube-dl
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  870k  100  870k    0     0   137k      0  0:00:06  0:00:06 --:--:--  174k
ferg@ferg-VII-160:~$ sudo chmod a+x /usr/local/bin/youtube-dl
ferg@ferg-VII-160:~$ youtube-dl --update
youtube-dl is up-to-date (2015.05.20)
ferg@ferg-VII-160:~$ youtube-dl 'http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep' \
>            --extract-audio --audio-format mp3 --audio-quality 4 --keep-video \
>            --prefer-ffmpeg --output "%(title)s.%(ext)s" --no-part
[ted] jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep: Downloading webpage
[ted] jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep: Extracting information
[ted] jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep: Downloading m3u8 information
[download] Destination: One more reason to get a good night’s sleep.fhls-2183.mp4
FFmpeg version SVN-r0.5.9-4:0.5.9-0ubuntu0.10.04.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.9-0ubuntu0.10.04.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 24 2013 19:42:21, gcc: 4.4.3
http://hls.ted.com/talks/2103/video/1500k.m3u8: Unknown format


ERROR: ffmpeg exited with code 1
ferg@ferg-VII-160:~$ sudo apt-get install libav-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libav-tools
ferg@ferg-VII-160:~$ 
[/HTML]

***   THEN I DID THIS ***

[HTML]ferg@ferg-VII-160:~$ ffmpeg -i http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep.mp4 http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep.mp3
FFmpeg version SVN-r0.5.9-4:0.5.9-0ubuntu0.10.04.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.9-0ubuntu0.10.04.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 24 2013 19:42:21, gcc: 4.4.3
http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep.mp4: I/O error occurred
Usually that means that input file is truncated and/or corrupted.
ferg@ferg-VII-160:~$ 
[/HTML]

It seems things are better.  It seems to me things are better - not working properly, is better than not working.

---

### Post by monkeybrain20122 on 2015-05-27
Lucid???

You are using a unsupported OS. Backup your data and do a fresh install of a currently supported version of Ubuntu (12.04 or 14.04 would be recommended)

---

### Post by briar rabbit on 2015-05-28
lol
[HTML]
ferg@ferg-VII-160:~$ youtube-dl -F http://www.ted.com/talks/jeff_iliff_..._night_s_sleep
[ted] jeff_iliff_: Downloading webpage
ERROR: Unable to download webpage: HTTP Error 404: Not Found (caused by HTTPError()); please report this issue on https://yt-dl.org/bug . Make sure you are using the latest version; type  youtube-dl -U  to update. Be sure to call youtube-dl with the --verbose flag and include its complete output.
ferg@ferg-VII-160:~$ youtube-dl -U
youtube-dl is up-to-date (2015.05.20)
[/HTML]
lol

---

