---
title: "HowTo: Rip DVD audio to mp3 or ogg"
date: 2007-01-03
forum: Outdated Tutorials &amp; Tips
---

### Post by lwr on 2007-01-03
I found [this]("http://www.linuxtopia.org/online_books/linux_beginner_books/debian_linux_desktop_survival_guide/DVD_Sound.shtml") the other day, after much searching on Google.
First thing you need to do is make sure you have lsdvd and transcode installed:
```
sudo apt-get install lsdvd transcode
```
Then do ```
lsdvd
``` to find the track information, and the longest track (which will probably be what you want.
To rip to ogg:
```
transcode -i /dev/dvd -x dvd -T *a*,*b*,1 -a 0 -y ogg -m *track-a*.ogg
```
where *a* is replaced with the number of the title you want to rip from, and *b* is replaced with the track number. The *track-a*.ogg can be replaced with whatever you want to call the track, e.g. "/home/user/music/artist/album/track name.ogg", but make sure the directory already exists.
Similarly with mp3:
```
transcode -i /dev/dvd -x dvd -T *a*,*b*,1 -a 0 -y raw -m *track-a*.mp3
```
I hope this is useful to others; I know I couldn't do without it. Perhaps someone with more knowledge about these things than I can shed some light on what other options there are.

Luke

---

### Post by Poptart on 2007-02-07
Thanks so much, this was so helpful to me. :D I had to rip an audio portion of an old film for a stage performance, and I knew the forums would come through!

---

### Post by sirmrmatt on 2007-03-13
Wow! Good stuff...would be nice to be able to somehow specify exactly what seconds to record, and then also tell it to continue on with adjacent chapters, if possible. I had two songs I needed which jumped to the next chapters, and so I had to "sew" them back together in Audacity.

Any ideas on this?

- Matt

---

### Post by tonique on 2007-04-01
> **sirmrmatt said:**
> Wow! Good stuff...would be nice to be able to somehow specify exactly what seconds to record, and then also tell it to continue on with adjacent chapters, if possible. I had two songs I needed which jumped to the next chapters, and so I had to "sew" them back together in Audacity.


Hopefully this will still be of some use... The manpage for transcode tells
```

-T t[,c[,a]]
        select DVD title[,chapter[,angle]] [1,1,1]. Only a single chapter
        is transcoded. Use -T 1,-1 to trancode all chapters in a row. You
        can even specify chapter ranges.
```

which means that if you use the option ```
-T title,a-b
``` in the command line, you get chapters from a to b in the same file.

The manpage tells also
```
       -c f1-f2[,f3-f4[, ... ] ]
              encode  only  frames  f1-f2 [and f3-f4]. Default is to encode all
              available frames.  Use  this  and  you’ll  get  statistics  about
              remaining  encoding  time.  The f[N] parameters may also be time&#8208;
              codes in the HH:MM:SS.FRAME format. Example:
              -c 500-0:5:01,:10:20-1:18:02.1

                     Will encode only from frame 500 to 5 minutes and 1  second
                     and  from  10 min, 20 sec to 1 hour, 18 min, 2 sec and one
                     frame.

              Note that transcode starts counting frames at 0 and excludes  the
              last frame specified. That means that "-c 0-100" will encoded 100
              frames starting at frame 0 up to frame 99
```

HTH. :>

---

### Post by sirmrmatt on 2007-04-01
Sweet! 

Very nice. Wish I'd had this before, but oh well! :) 

Thanks for contributing to the community like this, I know I certainly appreciate it, even if just for future reference.

Best,
Matt

---

### Post by dfm21 on 2007-06-28
**Error:**
Ogg encoding throws this error:
```
[transcode] warning : (encoder.c) video codec not supported by export module
[transcode] warning : failed to init export modules
[transcode] critical: plug-in initialization failed

```
**Solution:**
```
transcode -i /dev/dvd -x dvd -T 1,-1 -a 0 -y null,ogg -m audiotrack.ogg
```
Note the ```
-y null,ogg
``` argument!
Found it [here]("http://www.ubuntugeek.com/how-to-rip-dvd-audio-to-mp3-or-ogg.html#comment-5239").

Nice tutorial. Thanks!

---

### Post by blackcougar on 2007-12-04
thanks it works a treat on gutsy

---

### Post by dragonfixed on 2007-12-04
I have converted mp3 to cda and the cd pops and skips when i burn with nero on linux. The dvd is protected. Is this the reason why the music skips

---

### Post by atomicpc on 2007-12-29
Thanks for the find. I've spent countless hours and at least 5 today on my old 56k downloading different approches just to get a 4 sercond clip off a DVD to use as a message tone. After trying the hard way for so long it's ironic that it was this easy.

---

### Post by isecore on 2008-01-01
I tried this since I also want to extract a bit of audio from a DVD, but lsdvd fails with a long list of errors looking kinda like this:

```
*** libdvdread: CHECK_VALUE failed in ifo_read.c:778 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:776 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:777 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:778 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:776 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:777 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:778 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:776 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:777 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:778 ***
*** for pgc->cell_position_offset == 0 ***

Can't open ifo 15!
```

Same goes for when I try to transcode something. Long list of errors. Anyone know why this is so? I'm running Ubuntu Gutsy, latest Medibuntu and such.

Thanks!

---

### Post by mac-duff on 2008-01-23
Hi, sorry but I dont get it. When I run the command: lsdvd it tells me:

Disc Title: DVDVOLUME
Title: 01, Length: 02:40:08.240 Chapters: 27, Cells: 27, Audio streams: 03, Subpictures: 01

Longest track: 01


ok, fine. but how do I have to fill a and b now if I want the hole DVD as mp3? or better every chappter as own track

thx for help ;)
cu

---

### Post by supertux on 2008-02-01
I made a little bash script for ripping audio from dvd..

Fill in the approriate tile, totaltracks and the source. 

```
#!/bin/bash

export src=/media/cdrom0
export totaltracks=18
export title=02


export tracks=1

until [ $tracks -gt  $totaltracks ]; do
transcode -i $src -x dvd -T $title,$tracks,1 -a 0 -y raw -b 192 -m track-$tracks.mp3
let tracks+=1
done

```

---

### Post by jimbojones on 2008-04-04
> **isecore said:**
> I tried this since I also want to extract a bit of audio from a DVD, but lsdvd fails with a long list of errors looking kinda like this:

```
*** libdvdread: CHECK_VALUE failed in ifo_read.c:778 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:776 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:777 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:778 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:776 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:777 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:778 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:776 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:777 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:778 ***
*** for pgc->cell_position_offset == 0 ***

Can't open ifo 15!
```

Same goes for when I try to transcode something. Long list of errors. Anyone know why this is so? I'm running Ubuntu Gutsy, latest Medibuntu and such.

Thanks!



Can you confirm that you have the proper video codec installed and can actually play this dvd?

---

### Post by isecore on 2008-04-04
> **jimbojones said:**
> Can you confirm that you have the proper video codec installed and can actually play this dvd?

If by this you mean can I play a dvd in regular old Totem? Then the answer is no. I've never been able to do that. Never under Edgy, Feisty or Gutsy, and right now Hardy won't do it either. 

I've played my DVD's through VLC and that works fine, but I do know that VLC is a bit special.

---

### Post by purduephotog on 2008-04-06
> **isecore said:**
> If by this you mean can I play a dvd in regular old Totem? Then the answer is no. I've never been able to do that. Never under Edgy, Feisty or Gutsy, and right now Hardy won't do it either. 

I've played my DVD's through VLC and that works fine, but I do know that VLC is a bit special.

I"m getting the same error; the dvd plays the menu just fine but when you choose 'play all' or select individual episodes, it just sits there.

Pressing the 'pause' button/key allows you to see that the movie is playing- the time code is updating- but nothing is sent to either the screen or the audio.

---

### Post by heylookitsmewow on 2008-11-03
When I try to rip the entire audio from a DVD to an mp3 I am using 

> transcode -i /dev/dvd -x dvd -T 1,-1 -a 0 -y raw -m track-a.mp3

It works just fine until it gets to 1:25:29 and I get the following error.


> Adding a new RIFF chunk: 32976],  95.87 fps, EMT: 1:25:29, ( 0| 0| 4)
Internal error in avilib - redefine NR_IXNN_CHUNKS
[avilib dump] cur_std_idx=32 NR_IXNN_CHUNKS=32POS=63753278968 towrite=549184
[transcode] warning : error encoding video frame
Segmentation fault00000-122977],  95.87 fps, EMT: 1:25:29, ( 0| 0| 4)

It produces a usable mp3 that will play perfectly except it ends at 1:25:29.  It is doing this on 3 different DVD's at the exact same time and they are all longer than that.  What could be causing this?

---

### Post by mjitkop on 2008-12-11
Cool thread. :guitar:

Does this work no matter what protections are used on DVDs?

---

### Post by gtmaneki on 2008-12-11
Thanks for the tutorial!  I used it to rip some audio tracks from *Babylon 5* episodes to listen to at work on my first-gen iPod Nano.  :)

One thing I noticed about the tracks, however: While the tracks play perfectly on my iPod, they don't have any time info. Instead of running from 0:00 to 45:00 (or thereabouts), it goes from 0:00 to -0:00, and the progress bar doesn't change.  More importantly, I can't pause and resume tracks.  Instead, if I pause, I have to restart from the beginning, which isn't fun when the track is 45 minutes long.  Any suggestions to fix this?

---

### Post by NTolerance on 2008-12-12
> **supertux said:**
> I made a little bash script for ripping audio from dvd..

Fill in the approriate tile, totaltracks and the source. 

```
#!/bin/bash

export src=/media/cdrom0
export totaltracks=18
export title=02


export tracks=1

until [ $tracks -gt  $totaltracks ]; do
transcode -i $src -x dvd -T $title,$tracks,1 -a 0 -y raw -b 192 -m track-$tracks.mp3
let tracks+=1
done

```

This script works very well.  Just used it on a couple of concert DVDs.  It also gives you the ability to change the bitrate.  The OP's post gives you 128kbps mp3s, but with this script you can go higher if you like.

---

### Post by gtmaneki on 2008-12-18
I straightened out my problem.  I was using transcode with the "-T 1,-1" setting to convert an entire track to an MP3.  When I encode like this, the time info is messed up on my iPod.  However, when I specify individual chapters in a title, for example "-T 1,1,1", there is no problem.

Of course, when I'm dealing with a DVD containing 4 titles and each title has 6 chapters, that makes for a lot of typing.  So I modified the excellent script supertux provided.

Here is what I used to encode Babylon 5, Season 1, Disk 2.  Titles 1-4 contain episodes 5-8, and each title has 6 chapters.

```

#!/bin/bash

src=/media/cdrom0

title=1 #Set to number of first title track
total_titles=4 #set to maximum number of title tracks
total_chapters=6 #set to maximum number of chapters
season=1 #set to season number
audio_track=0 #set to 0 for English, other number for commentaries/other languages

until [ $title -gt $total_titles ]; do

chapter=1 #start at chapter 1
let episode="title + 4 " #set episode number

until [ $chapter -gt $total_chapters ]; do
transcode -i $src -x dvd -T $title,$chapter,1 -a $audio_track -y raw -b 192 -m b5_s${season}_e${episode}_c${chapter}.mp3
#converts DVD audio to MP3

let chapter+=1 #increment chapter
done

let title+=1 #increment title
done

```

This gives me a series of MP3 files specifying the series, episode, and chapter numbers.  For example, "b5_s1_e4_c1.mp3" stands for "Babylon 5, Season 1, Episode 4, Chapter 1."

---

### Post by clarknova on 2008-12-19
I'm ripping to wave (-y wav) and gnome reports that the audio files are twice as long as they actually are. I tried burning some of these to CD and every track has silence in length equal to actual audio. In other words, when I rip a 3-minute track, gnome reports that the file is 6 minutes. When I burn it to CD, a standard CD player plays the three minutes of audio followed by 3 minutes of silence.

Any idea why? Is there another lossless audio output format supported by transcode?

db

edit: It turns out vlc works well for ripping dvd to wav. Stream options works while Convert does not for some reason.

---

### Post by kzilka113 on 2008-12-19
[img]http://www.top1gaming.com/cosplay2/20081216/XChobits-1.jpg[/img] See the answer [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-211.html).  Want to see [[color=#800080]more pics[/color]](http://www.top1gaming.com/cosplayer.php)? Show yourself  on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/index.php?gid=27)**Recommend:**[[color=orange]Christmas version Meer Campbell [/color]](http://www.top1gaming.com/coscontent-206.html)[[color=orange]Christmas Sailor Moon[/color]](http://www.top1gaming.com/coscontent-209.html)

---

### Post by WildeBeest on 2009-01-02
I'm attempting to rip the audio tracks from a concert DVD.

I'm using the following command:

transcode -i /media/cdrom0 -x dvd -T 2,1,1 -a 0 -y raw -m track1.mp3

The file name is written, but 0 bytes long.

The output is:

```
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
(dvd_reader.c) DVD title 2/2: 20 chapter(s), 1 angle(s), title set 2
(dvd_reader.c) title playback time: 01:58:10.15  7091 sec
(dvd_reader.c) [Chapter 01] 00:00:00.000 , block from 0 to 121075
(dvd_reader.c) [Chapter 02] 00:03:42.200 , block from 121076 to 332917
(dvd_reader.c) [Chapter 03] 00:10:10.900 , block from 332918 to 489913
(dvd_reader.c) [Chapter 04] 00:14:59.000 , block from 489914 to 615173
(dvd_reader.c) [Chapter 05] 00:18:48.800 , block from 615174 to 760219
(dvd_reader.c) [Chapter 06] 00:23:14.900 , block from 760220 to 869345
(dvd_reader.c) [Chapter 07] 00:26:35.100 , block from 869346 to 1076922
(dvd_reader.c) [Chapter 08] 00:32:56.000 , block from 1076923 to 1199194
(dvd_reader.c) [Chapter 09] 00:36:40.400 , block from 1199195 to 1454322
(dvd_reader.c) [Chapter 10] 00:44:28.600 , block from 1454323 to 1585467
(dvd_reader.c) [Chapter 11] 00:48:29.200 , block from 1585468 to 1768904
(dvd_reader.c) [Chapter 12] 00:54:05.900 , block from 1768905 to 2080509
(dvd_reader.c) [Chapter 13] 01:03:37.700 , block from 2080510 to 2237145
(dvd_reader.c) [Chapter 14] 01:08:25.100 , block from 2237146 to 2616192
(dvd_reader.c) [Chapter 15] 01:20:00.700 , block from 2616193 to 2966254
(dvd_reader.c) [Chapter 16] 01:30:42.800 , block from 2966255 to 3096637
(dvd_reader.c) [Chapter 17] 01:34:42.100 , block from 3096638 to 3286866
(dvd_reader.c) [Chapter 18] 01:40:31.200 , block from 3286867 to 3580636
(dvd_reader.c) [Chapter 19] 01:49:30.300 , block from 3580637 to 3863847
(dvd_reader.c) [Chapter 20] 01:58:10.100 , block from 3863848 to 3864095
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV 0 ms | 0 ms
[transcode] auto-probing source /media/cdrom0 (ok)
[transcode] V: import format    | MPEG-2 DVD NTSC (V=dvd|A=dvd)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x480  1.50:1  encoded @ 4:3
[transcode] V: bits/pixel       | 0.217
[transcode] V: decoding fps,frc | 23.976,1
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x1000f unknown      [48000,16,2]
[transcode] A: export format    | 0x55    MPEG layer-3 [48000,16,2]  128 kbps
[transcode] V: encoding fps,frc | 23.976,1
[transcode] A: language         | en
[transcode] A: bytes per frame  | 8008 (8008.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
tc_memcpy: using amd64 for memcpy
[transcode] V: video buffer     | 10 @ 720x480
[import_dvd.so] v0.4.0 (2003-10-02) (video) DVD | (audio) MPEG/AC3/PCM
[export_raw.so] v0.3.12 (2003-08-04) (video) * | (audio) MPEG/AC3/PCM
[import_dvd.so] 
[import_dvd.so] tccat -T 2,1,1 -i "/media/cdrom0" -t dvd -d 0 | tcdemux -s 0x80 -x mpeg2 -S 0 -M 2 -f 23.976024 -P /tmp/fileLOyf8G -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yv12
[import_dvd.so] delaying DVD access by 3 second(s)
...tc_memcpy: using amd64 for memcpy
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: mmxext
Audio: using new version
Audio: using lame-3.97
[export_raw.so] codec=YV12, fps=23.976, width=720, height=480
Read failed for 184 blocks at 1

[transcode] (sighandler) SIGINT received

clean up | frame threads | unload modules | cancel signal | internal threads | done
[transcode] encoded 0 frames (0 dropped, 0 cloned), clip length   0.00 s

```

any ideas?

---

### Post by Dr.Dixie on 2009-01-31
I know just about nothing about this, but I used the /dev/dvd input instead of /media/cdrom0 (after some confusion and head-banging anger). So, I think you should do this command instead:

```
transcode *-i /dev/dvd* -x dvd -T 2,1,1 -a 0 -y raw -m track1.mp3
```

Again, I'm inexperienced, and I've only extracted to ogg as of now, but I think this is what it's actually supposed to be.


!Dr.Dixie!

---

### Post by andrew.46 on 2009-02-03
Hi Dr Dixie,

> **Dr.Dixie said:**
> I know just about nothing about this, but I used the /dev/dvd input instead of /media/cdrom0 (after some confusion and head-banging anger). So, I think you should do this command instead:

```
transcode *-i /dev/dvd* -x dvd -T 2,1,1 -a 0 -y raw -m track1.mp3
```

Again, I'm inexperienced, and I've only extracted to ogg as of now, but I think this is what it's actually supposed to be.

Just to add confusion to the mix I have just spent considerable pain and effort in compiling the newest transcode:

```
andrew@skamandros~$ transcode -v
transcode v1.1.0 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
```

and there are a few changes in the new version. The following has worked for me ripping audio from a movie DVD and converting to mp3 (with a few extras thrown in):

```

transcode -x dvd -i /dev/dvd -T 1,3,1 -a 0 -y null,tcaud \
--lame_preset standard -E 44100,16,2 -m $HOME/Desktop/test.mp3

```

I will be the first to agree that transcode is *not* the friendliest program in the world to use :-).

Andrew

---

### Post by NTolerance on 2009-02-20
Was messing around with bash in an attempt allow supertux's script to be used without editing it for each DVD.  Here's what I came up with:

```
#!/bin/bash

# DVD Audio ripping script originally created 
# by supertux from the Ubuntu forums:
# http://ubuntuforums.org/showpost.php?p=4251034&postcount=12
# Modified by NTolerance to list DVD information, 
# accept command line arguments, and output 256kbit MP3 files.
# Requires installation of transcode, lsdvd, and lame packages from the 
# Ubuntu repositories and probably other packages related to DVD
# decryption and playback.
# usage:  dvd-audio-rip.sh [Title] [TotalTracks]
# example:  dvd-audio-rip.sh 04 06
# Running without Title or TotalTracks arguments will 
# display DVD track information.

case "$1" in

	"")     echo "DVD Title and Track Information:"
		echo
		lsdvd -v | grep 'Length:' | cut -d,  -f1,2
		echo
		echo "usage:  dvd-audio-rip.sh [Title] [TotalTracks]"
		echo "example:  dvd-audio-rip.sh 04 06"
		exit $E_PARAM
	;;

	*) 	export title=$1
		export totaltracks=$2
		export src=/media/cdrom0
		export tracks=1
		until [ $tracks -gt  $totaltracks ]; do
		transcode -i $src -x dvd -T $title,$tracks,1 -a 0 -y raw -b 256 -m track-$tracks.mp3
		let tracks+=1
		done     
	;;   

esac
```

You can now pass command line arguments to the script to specify which title and how many total tracks from the title you want to rip.  If you run it without command line arguments it will list all the DVD title and track information so you can run it again with settings of your choice.  I'm sure a bash expert could clean this thing up and make a slick menu-driven interface that has some real error control.  Be careful, if you specify invalid parameters there's no telling what may happen.

---

### Post by strangeattractor on 2009-03-10
> **NTolerance said:**
> 

You can now pass command line arguments to the script to specify which title and how many total tracks from the title you want to rip.  If you run it without command line arguments it will list all the DVD title and track information so you can run it again with settings of your choice.

Thank you.  This is what I was looking for.  I have modified the code slightly so that the filenames have title and track numbers that are zero-padded.  I added the title number so that if ripping main tracks and extras from the same dvd there won't be overlap in filenames, and zero-padded so that the tracks will be in the correct order.

```

#!/bin/bash

# DVD Audio ripping script originally created
# by supertux from the Ubuntu forums:
# http://ubuntuforums.org/showpost.php?p=4251034&postcount=12
# Modified by NTolerance to list DVD information,
# accept command line arguments, and output 256kbit MP3 files.
# Requires installation of transcode, lsdvd, and lame packages from the
# Ubuntu repositories and probably other packages related to DVD
# decryption and playback.
# usage: dvd-audio-rip.sh [Title] [TotalTracks]
# example: dvd-audio-rip.sh 04 06
# Running without Title or TotalTracks arguments will
# display DVD track information.

case "$1" in

"") echo "DVD Title and Track Information:"
echo
lsdvd -v | grep 'Length:' | cut -d, -f1,2
echo
echo "usage: dvd-audio-rip.sh [Title] [TotalTracks]"
echo "example: dvd-audio-rip.sh 04 06"
exit $E_PARAM
;;

*) export title=$1
export totaltracks=$2
export src=/media/cdrom0
export tracks=1
until [ $tracks -gt $totaltracks ]; do
transcode -i $src -x dvd -T $title,$tracks,1 -a 0 -y raw -b 256 -m `printf "%02d" $title`-track-`printf "%03d" $tracks`.mp3
let tracks+=1
done
;;

esac

```

There were a few things I had to do to get it to work that I thought I'd mention here, in case it helps someone else.

For one thing, I'm not used to running scripts, so I wasn't sure how that worked.  I saved the above code in a text file named dvd-audio-rip.sh by copying and pasting it into gedit.  Then I opened a terminal, and used the cd command to get to the directory the file was in.  Then I tried to type dvd-audio-rip.sh, but it didn't work, so changed the permissions on the file and added a ./ in front of it in the command and it worked.  These are all things that someone more experienced with scripts would doubtless know.

Then I had to install some packages related to dvds.  I was frustrated for a while since I thought I'd done everything right.  Then I opened and closed the dvd drive and the newly installed packages suddenly started working.

Then, I got a weird error.  It said "Can't open disc /dev/dvd!"  At first, I thought that the symbolic link from /dev/dvd to my dvd drive was missing, but it turns out it was there, just to a different drive (I have two).  Changing to /media/cdrom1 in the script didn't fix this, since lsdvd relies on the symbolic link.  So I put my dvd into the other drive, changed the script back to /media/cdrom0, and it worked.

Thank you supertux and NTolerance for the script, and I hope my small changes and descriptions are useful to someone.

---

### Post by tony_clifton on 2009-04-04
I am having a hard time with this.   My preference would be to rip to a lossless format, ideally .wav files, however I cannot get .wav files to work properly.   A .wav file created using a command in the format```
transcode -i /dev/dvd -x dvd -T 1,5,1 -a 0 -y wav -m /media/foldername/track05.wav
``` results in a file that is not quite twice as long as it should be, with 1 second bursts of sound separated by short silent gaps.   

I am able to rip to .mp3 using ```
transcode -i /dev/dvd -x dvd -T 1,5,1 -a 0 -y raw -m /foldername/track05.mp3
```

I have seen others, such as clarknova above and in [*this thread*]("http://ubuntuforums.org/showthread.php?t=1020320"), comment on the same or near same problem with .wav files, but have not seen a solution using transcode.  I do have VLC installed however have not been able to decipher it.

---

### Post by tony_clifton on 2009-04-18
I have figured out how to do this using VLC media player.  

There are many more steps than the command line tool, however if you want a wav file or files, or some other format not supported by transcode, this is a viable option (I would now prefer flac, however VLC is not yet capable of encoding flac, and apparently neither can transcode).

The system I am currently using is Ubuntu 8.10 with VLC 0.9.4.

1. Put the disc in the drive and open VLC (you can use synaptic to install VLC; I'm not sure which repository it comes from).

2. In the VLC GUI, go to Media->Convert/Save.  

3. The "Open" dialog window should now open.  Click on the "Disc" tab and select the "DVD" radio button.

4. Next to Disc device there is a drop down menu.  Mouse over the "Browse" button and you should see a tooltip that reads "Select the device or the VIDEO_TS directory".  Click on the browse button and select the device or VIDEO_TS directory;  I used VIDEO_TS and on my system it can be found at /media/cdrom0/VIDEO_TS/  (note the disc must be in the drive and mounted; I have run into a problem with certain discs not mounting on the first try).

5. Now you must know the starting position.  lsdvd as mentioned earlier in this thread came in very handy for breaking down the title and chapter structure of the dvd.  Choose the title and chapter number you want to encode.  Under "Audio and Subtitles" both Subtitles track and Audio track are preset at -1; I did not change these.

6. Click the "Convert/Save" button and yet another window, this one titles "Stream Output", will open (as I said, many more steps than the command line tool :)).  

7. Select an option under "Output".  I check the box next to "file" and use the "Browse" to select a location to save the file to.

8. Finally we get to "Profile".  First, under "Encapsulation" select an option.  I use "WAV".  Then go to the "Audio" tab, check the "Audio" box, then select a codec (in my example this is "WAV") and adjust the bitrate and number of channels as appropriate.

9. Click the "Save" button.  For me, at this point, one of two things happens.  Either VLC begins working (you can tell this the original window of the VLC player will say "Streaming" or the title of the DVD in the lower left hand corner and show where it is at in terms of minutes and seconds of the title it is working with) and creates the file you want or it crashes (and once again I lament that transcode does not produce a usable wav file).   If it crashes all VLC windows disappear and a 0b file is created.

---

### Post by tony_clifton on 2009-04-18
...and then I decided to test out Ubuntu 9.04RC and found the transcode command ```
transcode -i /dev/dvd -x dvd -T 1,5,1 -a 0 -y wav -m /media/foldername/track05.wav
``` works perfectly on my new system.

---

### Post by Harpie Queen on 2009-06-01
I just ran I cable from the audio output of the device playing the dvd to a device that could record it. It seemed the most logical and intuitive way, and is remarkably easy. I lined my dvd player into my mp3, which I made record and output it to my sound system while I was watching it. Very convenient and easy. The same method could be used to record tapes. My mp3 records to mp3, but if you use your computer you can record to ogg, flac or wav (with jaunty, and no extra audio conversion programs).

---

### Post by eotakos on 2009-09-30
Something that happened to me is that the commands mentioned above produced the .mp3 file, but it was pure noise. 

This was because the parameter "0" in the command stands for combined stereo (or something like that). Changing that to 1 solved the problem for me.

---

### Post by strangeattractor on 2009-12-06
When I updated to Ubuntu 9.10 Karmic Koala, the script posted earlier in this thread suddenly stopped working.  I was getting errors such as:
> 
[export_raw.so] warning: Usage of this module for audio encoding is deprecated.
[export_raw.so] warning: Consider switch to export_tcaud module.
[transcode] Audio: using lame-3.98.2
[avilib.c] avi open error: avilib - Error opening AVI file
REASON: Bad address

I eventually fixed it by changing the import option to [COLOR="Red"]dvd,dvd[/COLOR] instead of [COLOR="Red"]dvd [/COLOR]and the export to [COLOR="Red"]null,tcaud[/COLOR] instead of [COLOR="Red"]raw[/COLOR].  From what I understand, transcode has changed how things are interpreted from the command line, so that the import and export options refer to the video codec, then the audio codec, separated by a comma.  If you only have one listed, instead of two separated by a comma, it interprets it as a video codec, and won't accept an audio-only codec such as lame.

I also figured out how to modify the script so that it used my second dvd drive.  It involves replacing two lines.

Replace 
```
lsdvd -v /dev/dvd | grep 'Length:' | cut -d, -f1,2
```

with

```
lsdvd -v /dev/dvd[COLOR="Red"]1[/COLOR] | grep 'Length:' | cut -d, -f1,2
```

and replace
```
export src=/media/cdrom[COLOR="Red"]0[/COLOR]
```

with
```
export src=/media/cdrom[COLOR="Red"]1[/COLOR]
```

Here is the modified script.  It uses the first DVD drive in the system, since most people only have one.  If you have two, and want to use the second one, then make the changes described above.

```

#!/bin/bash

# DVD Audio ripping script originally created
# by supertux from the Ubuntu forums:
# http://ubuntuforums.org/showpost.php?p=4251034&postcount=12
# Modified by NTolerance to list DVD information,
# accept command line arguments, and output 256kbit MP3 files.
# Modified by strangeattractor to pad zeros in the file name
# and to use tcaud instead of raw for exporting
# Requires installation of transcode, lsdvd, and lame packages from the
# Ubuntu repositories and probably other packages related to DVD
# decryption and playback.
# usage: dvd-audio-rip.sh [Title] [TotalTracks]
# example: dvd-audio-rip.sh 04 06
# Running without Title or TotalTracks arguments will
# display DVD track information.

case "$1" in

"") echo "DVD Title and Track Information:"
echo
lsdvd -v /dev/dvd | grep 'Length:' | cut -d, -f1,2
echo
echo "usage: dvd-audio-rip.sh [Title] [TotalTracks]"
echo "example: dvd-audio-rip.sh 04 06"
exit $E_PARAM
;;

*) export title=$1
export totaltracks=$2
export src=/media/cdrom0
export tracks=1
until [ $tracks -gt $totaltracks ]; do
transcode -i $src -x dvd,dvd -T $title,$tracks,1 -a 0 -y null,tcaud -b 256 -m `printf "%02d" $title`-track-`printf "%03d" $tracks`.mp3
let tracks+=1
done
;;

esac

```

---

### Post by NTolerance on 2009-12-06
It's cool to see this script continually evolving.  Thanks for the fixes for Karmic.  I haven't had to rip DVD audio in a while, but I probably will need to again in a couple months when Meshuggah's live DVD is released.  :guitar:

---

### Post by strangeattractor on 2009-12-06
You're welcome, NTolerance. :-) Thank you for your work on it.  This script has been quite useful to me.  I use it often, mostly for listening to documentaries as if they were audiobooks.

---

### Post by henwyn on 2010-06-12
My thanks to everyone who contributed to this bash script. I can report that it works well in Lucid.

The one thing that I did somewhat differently was use the program mc, which is run in a terminal, for things like viewing, editing, moving or changing attributes of files rather than doing it all from the command line. It's a program I've used for years and like and as I get older my memory for things like command line usage, which I don't use often, gets questionable.

Again, my thanks. I just successfully ripped the songs from the "Real Live Roadrunning" DVD which means I can listen to them at work.:p:p

---

