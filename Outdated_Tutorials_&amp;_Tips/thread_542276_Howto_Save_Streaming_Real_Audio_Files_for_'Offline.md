---
title: "Howto: Save Streaming Real Audio Files for 'Offline' Listening"
date: 2007-09-03
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2007-09-03
This walkthrough aims to give a demonstration of how to download a Real Audio stream and convert it to either Ogg Vorbis or mp3 format for offline listening at a later time. I will use a BBC news broadcast to demonstrate this technique.

First download the required tools from the repository:

```
sudo apt-get install mplayer vorbis-tools lame
```Next use the following commands to download the stream to your Desktop:

```

$ cd $HOME/Desktop
$ mplayer -playlist http://www.bbc.co.uk/worldservice/meta/tx/nb/summary5min_au_nb.ram \
-vc null -vo null -ao pcm:fast:waveheader:file=news_stream.wav 
```

I have a certain loathing for blindly copying CLI options into a Terminal without actually understanding what I am doing. So I will pause while the file is encoding in realtime to explain a few terms and options, drawing this material directly from the man pages:[LIST]
[*]**mplayer**
    mplayer is a movie player for Linux. It plays most MPEG/VOB, AVI, ASF/WMA/WMV, RM, QT/MOV/MP4, Ogg/OGM, MKV, VIVO, FLI, NuppelVideo, yuv4mpeg, FILM and RoQ files, supported by many native and binary codecs. You can watch Video CD, SVCD, DVD, 3ivx, DivX 3/4/5 and even WMV movies, too.
[*]**- playlist**
    Plays files according to a playlist file: ASX, Winamp, SMIL, or one-file-per-line format. The ram file is not a media file in itself, it contains directions to the actual media file. mplayer's -playlist option can read these directions and subsequently open the media file. How cool is that!
[*]**-ao pcm:file=news_stream.wav**
    Audio output is PCM (Pulse Code Modulation: the most common method of encoding an analogue audio signal into a digital bit stream) and the resulting default wav file will be named news_stream.wav.
[*]**-vc null -vo null**
    Do not play/encode video. This setting may result in faster encoding and obviously in a Real Audio sound broadcast there will be no video anyway.[/LIST]Now there should be a large wav file sitting on your desktop, so before anything else run it through any music player on your system and make sure it works! The following commands show the syntax to convert this file to either  Ogg Vorbis or mp3 format:

**Ogg Vorbis:**

```
$ cd $HOME/Desktop
$ oggenc news_stream.wav -q 6 -o BBC_news.ogg
```**mp3:**

```
$ cd $HOME/Desktop
$ lame news_stream.wav --preset standard -o BBC_news.mp3
```How easy is that? There are of course many more exciting streams out there than the BBC World News and I encourage you to explore. But perhaps you will also visit [For the God Who Sings]("http://www.abc.net.au/classic/ftgws/") and see the radio series that started *my* exploration of this technique?

Andrew

---

### Post by paulvbrown on 2007-10-02
Oy!

this is fantastic!

1 question, though, and I have to admit that I haven't done much searching for the answer yet on my own...  I like to listen to some streams that are about 1 hour in length.  Using your method everything seem to go along just fine, but then "hangs" somewhere, and I end up only getting about 20min. of the show.  Now, I haven't bothered to WAIT for those 20 min. to see if mplayer starts to function again at that point, but I'd think the whole point of this is that you don't HAVE to wait -- just download the raw data as fast as you can, and store it.  Those 20 min. I got in about 30 seconds.  Seems that your example stream had some sort of limiter on it, though -- it ended up taking considerably longer, as if the download speed was regulated.

SO -- might there be some other setting or flag that I need to pass in order to get larger streams to work?  Or have I just run into a restriction on the download rate  put in place by the stream provider?

Thanks!

---

### Post by andrew.46 on 2007-10-02
Hi,

 Glad you have found a use for this technique:

> **paulvbrown said:**
> [....]  I like to listen to some streams that are about 1 hour in length.  Using your method everything seem to go along just fine, but then "hangs" somewhere, and I end up only getting about 20min. of the show. [....]

SO -- might there be some other setting or flag that I need to pass in order to get larger streams to work?  Or have I just run into a restriction on the download rate  put in place by the stream provider?

Thanks!

 I have not experienced this problem although I suspect that it relates to the vagaries of a Real Audio stream rather than a limitation imposed by mplayer.

 Usually if there is a problem with delivery of the stream you increase the cache size that mplayer uses. The relevant manual section says:

     >   -cache <kBytes>
              This option specifies how much memory (in kBytes)  to  use  when
              precaching a file or URL.  Especially useful on slow media.

 It might be useful to experiment with this. 

 I think the special feeling when you save a stream like this is that somehow you have beaten the system :-)

    All the best,

          Andew

---

### Post by paulvbrown on 2007-10-03
Dude!

You are SO "the man"!

Yep, -cache 500 worked a charm.  (The default was 320, so not even that much increase needed.)

Thanks again!

This will SO help me -- I like to download educational streams related to my studies, then I can listen to them in the car (with my handy dandy MP3 player) on the way to and from classes.

Fantastic!

[EDIT: AH!  But, I *do* still seem to have an odd problem - perhaps someone can shed some light on it -- this only works EVERY OTHER TIME.  It seems as though the cache or something else gets "clogged", but after I initiate a download which I know will hang at about the 30 minute mark, if I use Ctrl-C to interrupt the download, (either before or after the hang, it doesn't seem to matter), then the NEXT download will go off without a hitch.]

---

### Post by andrew.46 on 2007-10-03
Hi,

 I still have a suspicion that the stream is the problem:

> **paulvbrown said:**
> 
[EDIT: AH!  But, I *do* still seem to have an odd problem - perhaps someone can shed some light on it -- this only works EVERY OTHER TIME.  It seems as though the cache or something else gets "clogged", but after I initiate a download which I know will hang at about the 30 minute mark, if I use Ctrl-C to interrupt the download, (either before or after the hang, it doesn't seem to matter), then the NEXT download will go off without a hitch.]

 but I suspect that you are using the repository version of mplayer? If you feel like getting your hands a little dirty there is a guide on the forums to compiling the most recent svn mplayer.

 You could try it if you were interested and that would eliminate any thought of a problem with mplayer:

[http://ubuntuforums.org/showthread.php?t=558538&highlight=howto+svn+mplayer](http://ubuntuforums.org/showthread.php?t=558538&highlight=howto+svn+mplayer)

It is the version I use myself, and I wrote this guide as well :-)
   

 Andrew

---

### Post by AlanRogers on 2008-04-16
I just want to add a Thank You for this How To; it just works. The only issue I had, and this isn't the OP's fault, was not to include the \ where the line of code splits over two!

I got what I wanted, in the format that I wanted it in, and it's marvellous. Thank you.

---

### Post by andrew.46 on 2008-04-16
Hi:

> **AlanRogers said:**
> I just want to add a Thank You for this How To; it just works. The only issue I had, and this isn't the OP's fault, was not to include the \ where the line of code splits over two!

I got what I wanted, in the format that I wanted it in, and it's marvellous. Thank you.

It is totally my pleasure!

    Andrew

---

### Post by paulvbrown on 2008-10-07
Oh, huge ARGH!!!!  Now for some reason this has STOPPED working for me, and now I get something "weird"...

> mplayer -playlist ElectricCars.ram -vc null -vo null pcm:fast:waveheader:file=ElectricCars.wav

MPlayer dev-SVN-r27668-4.2.3 (C) 2000-2008 MPlayer Team
CPU: Genuine Intel(R) CPU           T2060  @ 1.60GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing rtsp://a716.v53807c.c53807.g.vr.akamaistream.net/ondemand/5/716/53807/48c182e0/1a1a1aa21688ed4ebb2e5cd334a11644b3258cbb1f91c0f0285787c0/r2080901.rm.
Resolving a716.v53807c.c53807.g.vr.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a716.v53807c.c53807.g.vr.akamaistream.net
Resolving a716.v53807c.c53807.g.vr.akamaistream.net for AF_INET...
Connecting to server a716.v53807c.c53807.g.vr.akamaistream.net[80.15.236.134]: 554...
Cache size set to 640 KBytes
Cache fill:  6.25% (40960 bytes)

If I sit there long enough, the clip begins playing, and it seems to be copying to the .wav file at the same time, but before it just went straight to the .wav file, and NOT in real time -- the whole point being that I don't want to record an hour long radio program for an hour.  I want to download it in less than 5 minutes, THEN listen to it later for an hour.  Can't think what changes I've made to my own system since this worked for me last.  Would swear I've used this method after upgrading to Hardy Heron....

Any ideas anyone?

---

### Post by andrew.46 on 2008-10-14
Hi paulvbrown,

I note that you may have left out the vital 'audio output' option from your commandline. You gave:

```
mplayer -playlist ElectricCars.ram -vc null -vo null \
 pcm:fast:waveheader:file=ElectricCars.wav
```

Try:

```
mplayer -playlist ElectricCars.ram -vc null -vo null \ 
-ao pcm:fast:waveheader:file=ElectricCars.wav
```

But if the file *is* a streaming one I suspect that this will all happen in real time?

  Andrew

---

### Post by paulvbrown on 2008-10-15
Hey Andrew -- thanks - I don't think that was actually a problem - (I mean I *THINK* I actually did have the -ao flag in there, it just got leftout when I was posting my message) - I did try WITH the -ao flag and still got the same result.

The thing is that this *WAS* working with files from the same source earlier.  By "was working" I mean specifically that the download took a matter of 5-10 minutes (no real recollection at this point) instead of an hour.  I'll have to try again with one of the older files that I've downloaded - perhaps they've changed they way they package/stream the files?

---

