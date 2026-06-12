---
title: "Mini guide: Download high quality youtube vids suitable for your phone ..."
date: 2009-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2009-01-12
[B][COLOR="Red"][B]======================================
This guide is no longer supported and 
should not be used. 
======================================[/B][/COLOR][/B]

Like to download music videos from youtube for your phone or ipod but sick of the low quality flash video files? Many youtube videos now come with h264 video and aac sound, details of how to download these are in this 'mini guide'.

Warning: Please check that the music video you download from youtube.com does not violate the copyright laws in your country.

More information on the thorny topic of youtube and its policies on copyright can be [found here]("http://en.wikipedia.org/wiki/YouTube#Copyrighted_Material").

First clean out any old copies of youtube-dl and download the newest version (the version in Intrepid Ibex will not work correctly with high quality video):

```
$ sudo apt-get remove youtube-dl
$ sudo wget http://bitbucket.org/rg3/youtube-dl/raw/2009.08.08/youtube-dl -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl
```

Now use the following syntax to download a sample high quality music video:

```
$ cd Desktop
$ youtube-dl -b -o '%(stitle)s.%(ext)s' 'http://www.youtube.com/watch?v=doTBT46wMvA'
```

And there you have it! A quick look at this particular file shows the following specs:

```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Ramstein_Du_Hast.mp4':
Duration: 00:03:54.10, start: 0.000000, bitrate: 378 kb/s
Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
Stream #0.1(und): Video: h264, yuv420p, 352x234, 25 tbr, 24.98 tbn, 24.98 tb
```

Simply add the address of your own music video in place of mine and off you go. No more scratching around for flash video converters I reckon :-). For more details about this amazing Python script have a look at the author's website:

youtube-dl: Download videos from YouTube.com
[http://bitbucket.org/rg3/youtube-dl/wiki/Home](http://bitbucket.org/rg3/youtube-dl/wiki/Home)

Andrew

---

### Post by lukjad on 2009-01-25
Sounds interesting, but what does **-b -o '%(stitle)s.%(ext)s' ** do, and is it needed?

---

### Post by andrew.46 on 2009-01-25
Hi lukjad007,

> **lukjad007 said:**
> Sounds interesting, but what does **-b -o '%(stitle)s.%(ext)s' ** do, and is it needed?

Wooo hooo!! Somebody finally read my guide :-). Usage details are reasonably poorly documented but for the most part can be seen on the [creator's website]("http://www.arrakis.es/~rggi3/youtube-dl/").

The -b or --best-quality option is an alias for -f 18, or '&fmt=something' as is conventionally done. This downloads the highest quality file available from youtube.

-o '%(stitle)s.%(ext)s' governs the name of the output file and is what the creator calls an 'output template':

> stitle: The sequence will be replaced by a simplified video title, restricted to alphanumeric characters and dashes.

ext: The sequence will be replaced by the appropriate extension (like flv or mp4).

A shortened form of all of this can be seen by runnning:

```
andrew@skamandros:~$ youtube-dl --help
Usage: youtube-dl [options] url...

Options:
  -h, --help            print this help text and exit
  -v, --version         print program version and exit
  -u UN, --username=UN  account username
  -p PW, --password=PW  account password
  -o TPL, --output=TPL  output filename template
  -q, --quiet           activates quiet mode
  -s, --simulate        do not download video
  -t, --title           use title in file name
  -l, --literal         use literal title in file name
  -n, --netrc           use .netrc authentication data
  -g, --get-url         simulate, quiet but print URL
  -e, --get-title       simulate, quiet but print title
  -f FMT, --format=FMT  video format code
  -b, --best-quality    alias for -f 18
  -m, --mobile-version  alias for -f 17
  -i, --ignore-errors   continue on download errors
  -r L, --rate-limit=L  download rate limit (e.g. 50k or 44.6m)

```

All the best,

Andrew

---

### Post by lukjad on 2009-01-26
Thanks! :) I'll do some reading. I didn't realize that youtube vids could be of any quality. Thanks for the tips.

---

### Post by dannyboy79 on 2009-02-18
> **andrew.46 said:**
> Hi,

Like to download music videos from youtube for your phone or ipod but sick of the low quality flash video files? Many youtube videos now come with h264 video and aac sound, details of how to download these are in this 'mini guide'.

**[COLOR="Red"]Warning: Please check that the music video you download from youtube.com does not violate the copyright laws in your country.[/COLOR]** 

More information on the thorny topic of youtube and its policies on copyright can be [found here]("http://en.wikipedia.org/wiki/YouTube#Copyrighted_Material").

First clean out any old copies of youtube-dl and download the newest version (the version in Intrepid Ibex will not work correctly with high quality video):

```
$ sudo apt-get remove youtube-dl
$ sudo wget http://www.arrakis.es/~rggi3/youtube-dl/youtube-dl -O /usr/local/bin/youtube-dl
$ sudo chmod +x /usr/local/bin/youtube-dl
```

Now use the following syntax to download a sample high quality music video:

```
$ cd Desktop
$ youtube-dl -b -o '%(stitle)s.%(ext)s' 'http://www.youtube.com/watch?v=4FT3mmvtpSs'
```

And there you have it! A quick look at this particular file shows the following specs:

```
Duration: 00:03:45.90, start: 0.000000, bitrate: 338 kb/s
Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
Stream #0.1(und): Video: h264, yuv420p, 352x264, 24.99 tb(r)
```

Simply add the address of your own music video in place of mine and off you go. No more scratching around for flash video converters I reckon :-).

Andrew

awesome program! I use it all the time. I was curious as to what program you used to get the video info. I use MediaInfo to get tons of info on a video file, it's great. Your program has tons of options, is what your example shows the best way to run your program to get the best output file from youtube?

---

### Post by andrew.46 on 2009-02-19
Hi dannyboy79,

> **dannyboy79 said:**
> awesome program! I use it all the time. I was curious as to what program you used to get the video info. I use MediaInfo to get tons of info on a video file, it's great. Your program has tons of options, is what your example shows the best way to run your program to get the best output file from youtube?

The program I use to demonstrate the media file properties is simply FFmpeg run as:

```
$ ffmpeg -i filename.mp4
```

As for the *best* way to use youtube-dl, that could be argued. It is very true however that most people are not aware of the extra options available with the program. These can be seen as follows:

```

[COLOR="Red"]**andrew@skamandros~$ youtube-dl -h**[/COLOR]
Usage: youtube-dl [options] url...

Options:
  -h, --help            print this help text and exit
  -v, --version         print program version and exit
  -u UN, --username=UN  account username
  -p PW, --password=PW  account password
  -o TPL, --output=TPL  output filename template
  -q, --quiet           activates quiet mode
  -s, --simulate        do not download video
  -t, --title           use title in file name
  -l, --literal         use literal title in file name
  -n, --netrc           use .netrc authentication data
  -g, --get-url         simulate, quiet but print URL
  -e, --get-title       simulate, quiet but print title
  -f FMT, --format=FMT  video format code
  -b, --best-quality    alias for -f 18
  -m, --mobile-version  alias for -f 17
  -i, --ignore-errors   continue on download errors
  -r L, --rate-limit=L  download rate limit (e.g. 50k or 44.6m)

```

All the best,

Andrew

---

### Post by binbash on 2009-02-19
Works like a charm!!! Thanks

---

### Post by Clancy_s on 2009-02-19
I didn't know youtube-dl existed: thanks for the info and the how-to.  :) I'll check it out this weekend.

---

### Post by Nixie Pixel on 2009-02-21
I tried this and I get "unable to extract "t" parameter."  What am I doing wrong?

---

### Post by andrew.46 on 2009-02-21
Hi Nixie,

> **Nixie Pixel said:**
> I tried this and I get "unable to extract "t" parameter."  What am I doing wrong?

Does the example I gave you work? :

```
youtube-dl -b -o '%(stitle)s.%(ext)s' 'http://www.youtube.com/watch?v=4FT3mmvtpSs'
```

Could you give the full commandline you used + address? And I guess the results of:

```
andrew@skamandros~$ **[COLOR="Red"]youtube-dl --version[/COLOR]**
2008.11.01
```

Thanks,

Andrew

---

### Post by Nixie Pixel on 2009-02-22
Hi, your example does work, but the filename actually shows up as "%(stitle)s.%(ext)s" rather than having been populated with words and an extension.

What I am trying to do is:

youtube-dl -b -o '%(stitle)s.%(ext)s' 'http://www.youtube.com/watch?v=ssq4NENf0ws'

Thanks!

Edit:  Actually, I think I may have solved the mystery - I uninstalled youtube-dl and then got it from synaptic package manager.  This time when I tried the command above, I noticed that it offered suggestions on what could be wrong rather than just the error message.  One of those suggestions was "* Video requires age confirmation but you did not provide an account."  I am sure this is the problem as I believe that video does require age verification.

---

### Post by andrew.46 on 2009-02-22
Hi,

Pretty wild video BTW :-). It can be done with youtube-dl by using the -u (username) and -p (password) options, make sure you are logged off on the web interface. I downloaded this particular clip as follows, I have altered my username and password:

```

andrew@skamandros~/Desktop$ youtube-dl **[COLOR="Red"]-u secret -p secret[/COLOR]** -b -o '%(stitle)s.%(ext)s' \
> 'http://www.youtube.com/watch?v=ssq4NENf0ws'
[youtube] Setting language
[youtube] Logging in
[youtube] Confirming age
[youtube] ssq4NENf0ws: Downloading video webpage
[youtube] ssq4NENf0ws: Extracting video information
[youtube] ssq4NENf0ws: URL: http://www.youtube.com/get_video?video_id=ssq4NENf0ws&t=vjVQa1PpcFONawEGESp3dANo2L_DxiMnT2PBp9j61hQ=&fmt=18
[download] Destination: Dead_Or_Alive_4_Christie_Ending_Great_Quality.mp4
[download] 100.0% of 5.29M at   51.74k/s ETA 00:00 

```

This produces a very nice quality file:

```
Duration: 00:01:11.30, start: 0.000000, bitrate: 622 kb/s
Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
Stream #0.1(und): Video: h264, yuv420p, 480x360, 29.97 tb(r)
```

All the best,

Andrew

---

### Post by Nixie Pixel on 2009-02-23
Thank you, I will try that ASAP.  One more question - is there a way to put the video in a container other than .flv with youtube-dl?  Such as .mp4 or .wmv?

Thanks!

---

### Post by andrew.46 on 2009-02-23
Hi NixiePixel,

> **Nixie Pixel said:**
> Thank you, I will try that ASAP.  One more question - is there a way to put the video in a container other than .flv with youtube-dl?  Such as .mp4 or .wmv?

Actually youtube-dl does not do any conversion of the downloaded files. If you have a taste for the commandline FFmpeg will do this for you, have a look for [the FakeOutdoorsman's guide]("http://ubuntuforums.org/showthread.php?t=786095").

Andrew

---

### Post by andrew.46 on 2009-04-01
Hi,

I note that the author has moved his website and also the download site for youtube-dl so the guide has been updated to reflect this. Current address is [here]("http://bitbucket.org/rg3/youtube-dl/wiki/Home") and current youtube-dl version is:

```

andrew@skamandros~$ youtube-dl -version
2009.03.28

```

All the best,

Andrew

---

### Post by andrew.46 on 2009-04-09
Updated the download link for the 2009.04.06 version.

Andrew

---

### Post by andrew.46 on 2009-04-29
Updated version:

```
2009.04.25

MD5: c9924626fbd1bf7228fd995f497182ab
SHA1: 94ede0c4111954b2c24251e996f2dcb66d9349bd
SHA256: a495be16bf95b52bfb5aaafc91346e5e75bd03e01026a3f2f248737428b27f4e 
```

Andrew

---

### Post by Ampersand. on 2009-04-30
This works great but i have a problem, im not actually sure whether its this script or not.

It seems like whenever i download a video from the web (not torrents though) the sound does not play unless i use Avidemux.
The whole point of me downloading the video is usually to put it in a presentation for uni and if there is no sound this is useless.

Anybody got any ideas?

---

### Post by andrew.46 on 2009-05-01
Hi Ampersand,

> **Ampersand. said:**
> This works great but i have a problem, im not actually sure whether its this script or not. It seems like whenever i download a video from the web (not torrents though) the sound does not play unless i use Avidemux.The whole point of me downloading the video is usually to put it in a presentation for uni and if there is no sound this is useless.

If you are using the settings suggested in this guide the sound will most likely be aac rather than low quality mp3. By default often Ubuntu applications will not read this until the appropriate 'restricted formats' have been enabled. Some more details and links here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

All the best,

Andrew

---

### Post by MrNugget on 2009-05-02
> $ youtube-dl -u mrnugget -p mysecretpassword -d -o '%(stitle)s.%(ext)s' 'http://www.youtube.com/watch?v=V4io9Ehi96Y'
[youtube] Setting language
[youtube] Logging in
[youtube] Confirming age
[youtube] V4io9Ehi96Y: Downloading video webpage
[youtube] V4io9Ehi96Y: Extracting video information
[youtube] V4io9Ehi96Y: URL: [http://www.youtube.com/get_video?video_id=V4io9Ehi96Y&t=vjVQa1PpcFOwodu7iWGvCvSwZapGkFsyGhkZGV5mhp4=&el=detailpage&ps=&fmt=22](http://www.youtube.com/get_video?video_id=V4io9Ehi96Y&t=vjVQa1PpcFOwodu7iWGvCvSwZapGkFsyGhkZGV5mhp4=&el=detailpage&ps=&fmt=22)
[download] Destination: Tropic_Thunder_TOM_CRUISE_GOES_NUTS.mp4
ERROR: unable to write video data: HTTP Error 404: Not Found

Any ideas?

---

### Post by andrew.46 on 2009-05-02
Hi MrNugget,

> **MrNugget said:**
> ```
ERROR: unable to write video data: HTTP Error 404: Not Found 
```
Any ideas?

The -d option appears to be broken at the moment :(.

Andrew

---

### Post by Dan Again on 2009-05-05
Having the same problem...cannot download high def vids due to 404 error.  This option worked fine up until a couple of days ago...and I can still d/l regular quality videos.

Sometimes when I d/l vids, there is a crackling static running over the audio.  I've tried switching the file format (flv to avi), which fixed the problem in the past, but just a second ago that did not work.  I had to restart my machine to d/l a good copy with clean audio.  Any ideas what is causing that?

---

### Post by andrew.46 on 2009-05-06
Hi Dan,

> **Dan Again said:**
> Having the same problem...cannot download high def vids due to 404 error.  This option worked fine up until a couple of days ago...and I can still d/l regular quality videos.

I suspect that something is being changed at the youtube end. I have popped a small notice on the guide that it might be best to hold off for the moment at least for the 'high definition' downloading with youtube-dl.

> Sometimes when I d/l vids, there is a crackling static running over the audio.  I've tried switching the file format (flv to avi), which fixed the problem in the past, but just a second ago that did not work.  I had to restart my machine to d/l a good copy with clean audio.  Any ideas what is causing that?

I am afraid that I cannot duplicate this problem and I am a bit at a loss as to what might be causing it. Sorry!!

Andrew

---

### Post by MSToTheEnd on 2009-05-27
Thanks! Works perfectly!

---

### Post by andrew.46 on 2009-05-28
Hi MSToTheEnd,

> **MSToTheEnd said:**
> Thanks! Works perfectly!

I am a little surprised as this guide has been relegated to 'Outdated.....' at my request as it was broken at the youtube-dl end *and* the youtube end :-). Anyway glad it worked for you!

Andrew

---

### Post by andrew.46 on 2009-05-28
Hi,

Looks like the -b option is now the one to use. In this version:

```

andrew@skamandros~/Desktop$ youtube-dl --version
2009.05.25

```

the options are slightly altered:

```

  Video Format Options:
    -f FMT, --format=FMT
                        video format code
    **[COLOR="Purple"]-b, --best-quality  download the best quality video possible[/COLOR]**
    -m, --mobile-version
                        alias for -f 17
    -d, --high-def      alias for -f 22


```

So the code should be:
```

$ youtube-dl -b -o '%(stitle)s.%(ext)s' 'http://www.youtube.com/watch?v=doTBT46wMvA'
```

All the best,

Andrew

---

### Post by gonkyouka on 2009-08-02
this is actually what im lookin for and it works like a charm however, im thinkin about the difference between the options best quality and high def.

---

### Post by andrew.46 on 2009-08-02
Hi gonkyouka,

> **gonkyouka said:**
> this is actually what im lookin for and it works like a charm however, im thinkin about the difference between the options best quality and high def.

I am a little surprised this guide still lives, it was relegated to the 'Outdated' section a while back :-). Anyway I have just downloaded the newest version:

```

andrew@skamandros~$ **[COLOR="Red"]youtube-dl --version[/COLOR]**
2009.06.29

```

and looks like the video quality options are the same:

```

  Video Format Options:
    -f FMT, --format=FMT video format code
    -b, --best-quality  download the best quality video possible
    -m, --mobile-version alias for -f 17
    -d, --high-def      alias for -f 22


```

Making -b still the best option as youtube-dl negotiates for the best available quality available for the selected video. And still this is most usually reasonable quality h264 video and aac sound.

All the best,

Andrew

---

### Post by andrew.46 on 2009-08-19
New version added to this guide:

```

andrew@skamandros~$ youtube-dl --version
2009.08.08

```

Andrew

---

### Post by lukjad on 2009-08-19
Nice. Thanks andrew.46!

---

### Post by andrew.46 on 2009-08-19
Hi lukjad007,

> **lukjad007 said:**
> Nice. Thanks andrew.46!

Always good to meet a member of the BT :-). Actually I am keeping this little guide updated in the 'Outdated' section pending further thoughts for Forums admin concerning the legitimacy of downloading such videos from youtube, a difficult question unfortunately....

Andrew

---

### Post by FakeOutdoorsman on 2009-08-20
> **andrew.46 said:**
> Hi lukjad007,



Always good to meet a member of the BT :-). Actually I am keeping this little guide updated in the 'Outdated' section pending further thoughts for Forums admin concerning the legitimacy of downloading such videos from youtube, a difficult question unfortunately....

Andrew

I understand that the forum admin may hesitate to give thought to this subject, but in my opinion (there's those magical words that now let me say anything I want), there is no reason to hesitate.  When I watch a movie on YouTube with Firefox it gets downloaded to my */tmp* directory.  I can copy this file and save it for later and I often do.  How different is this than using youtube-dl?  Even if I don't use youtube-dl the file is still being downloaded to my computer.  I'm doing this for personal use.  No distribution, remixing, or commercial use is going on here.  I'm just a regular user.

Secondly, what if the movie I'm downloading is something that I made and uploaded to YouTube?  Is it not legitimate to download my own movie from YouTube?

I didn't read any YouTube terms of service or other legalese so I am ignorant of any download restrictions, but I (possibly ignorantly) do believe the legitimate, real world uses of youtube-dl far outweigh any perceived illegitimacy.

Just a couple of points to bring up.

Post Script:  Also, you have a disclaimer in **[color=#FF0000]bold red[/color]** which should be worth a point or two.

---

### Post by andrew.46 on 2009-08-20
Hi FakeOutdoorsman,

Oh well I am happy to wait for the final determination from the council. I personally do not see that there is any harm in downloading such videos for personal use on a home computer but certainly there are other views :-).

Andrew

---

### Post by lisati on 2010-04-07
Thread closed: see [here]("http://ubuntuforums.org/showthread.php?t=1429211")

---

