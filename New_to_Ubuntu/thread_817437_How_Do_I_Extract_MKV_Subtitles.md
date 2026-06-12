---
title: "How Do I Extract MKV Subtitles?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by theragingking on 2008-06-03
So a while back I posted looking for a decent MKV->AVI converter. mencoder, after two days of fiddling, was perfect.

But now I've got a new problem...

So, I've been using mencoder to convert subbed MKV format episodes of Death Note into slightly more digestible (by my machine, at least) AVI files. Problem is, one of these files use a subtitle track instead of actually having been added to the video track. Ergo, converting the file yields an episode with lovely Japanese voice acting but no subtitles.

And me without my phrase book... :-k

Now, my understanding of MKVs is that they are, like AVIs, actually container files that actually have the seperate tracks (video, audio, subtitles, etc.) inside them. I also know that it is possible to sync up subtitle files with AVI files via a similarly named text file.

So my question is this:

Does anyone know how I might go about exporting or extracting that subtitle track from this MKV? I have VLC and mencoder installed, if they're useful... but I haven't found anything pointing towards.

Any help would be much appreciated!

-TRK

To answer my own question:

> [http://ubuntuforums.org/showthread.php?t=494001](http://ubuntuforums.org/showthread.php?t=494001)

---

### Post by jjgomera on 2008-06-03
for this i use [avinaptic]("http://fsinapsi.altervista.org/")

---

### Post by shirilover on 2008-06-03
To convert a soft-subbed mkv to a hard-subbed avi, I do the following.

Requires: mkvtoolnix, avidemux (both in the repos)

First, we need to extract the subtitle stream and any fonts that are used by it; otherwise, the subtitles will not look how they were intended to.

I use mkvinfo -g(gui version of mkvinfo) to find the subtitle track number and the attachment IDs of the fonts. It is wise to leave this open while performing the extraction.

So, then -- assuming the subtitles are track 3 and Advanced SubStation alpha
```

mkvextract tracks file.mkv 3:file.***
mkvextract attachments file.mkv FontID:

```
By not specifying a file name for the font, the filename of the attached font will be used. This needs to be done for each font that is attached.
Then, we need to install the fonts and regenerate the font cache so that the subtitles will be rendered properly.
```

cp *.ttf ~/.fonts
sudo fc-cache -v ~/.fonts

```

Now, to convert the audio/video to xvid/mp3 with avidemux.
Start avidemux and open the mkv file.
Some helpful suggestions for the video portion can be found here -> [http://avidemux.org/admWiki/index.php?title=Encoding_animation_with_Xvid](http://avidemux.org/admWiki/index.php?title=Encoding_animation_with_Xvid)
To add the subtitle stream to the video, press the filters button.
Select the subtitles tab on the left and choose 'Add ***/SSA subtitles to the picture'.
Then press the large '+' button to add the filter.
In the resultion dialog, browse for the subtitle file you previously extracted and press OK, then close.

For the audio portion, at the left under audio, select MP3 (LAME) from the drop-down list. The default settings are stereo/128 kbps. You can alter these by pressing the configure button.

Finally press the save button in the toolbar. A standard open/save dialog will pop up. Give the new file a name and press save.

It may take anywhere from 15 minutes to an hour to complete a 2-pass encode depending on your hardware.

---

### Post by blenderfox on 2011-04-15
This was a very useful post. Just wanted to add a few points.

I used these steps to hardsub a video of my own, but avidemux kept freezing on me for an unknown reason (assertion failures popped up in the console.) Maybe it was to do with the fact the mkv I had was a H.263 video which wasn't formatted correctly. Eventually, I had to convert the MKV to a MP4 via Arista Transcoder, then hardsub that instead.

It helps if you have a lot of space -- a 300MB MKV turned into a 1.5GB MP4 after going through Arista, but the hardsub then ran without a hitch.

---

### Post by anewbie on 2012-02-01
I want to do something very similar but I want 'soft' subtitles associated with my avi file. 

The basically issue is I want to use hard-ware decoding on my tablet and mkv files cannot be decoded via hardware accl on the tablet. I only want soft subtitles since I listen to some films that small sections foreign. Those are the sections I want subtitles without having subtitles in the entire film.
-
basically I am using mencoder to transencode (reducing bit rate and resolution) and it is perfectly capable  of emedding hard subtitles into the output container (avi in this case). However for the life of me I cannot get soft subtitles :(

---

### Post by blenderfox on 2012-02-01
> **anewbie said:**
> I want to do something very similar but I want 'soft' subtitles associated with my avi file. 

The basically issue is I want to use hard-ware decoding on my tablet and mkv files cannot be decoded via hardware accl on the tablet. I only want soft subtitles since I listen to some films that small sections foreign. Those are the sections I want subtitles without having subtitles in the entire film.
-
basically I am using mencoder to transencode (reducing bit rate and resolution) and it is perfectly capable  of emedding hard subtitles into the output container (avi in this case). However for the life of me I cannot get soft subtitles :(

Try finding an app for your tablet that supports MKV decode. I have an Android tablet, and use BSPlayer, which supports MKV decoding and hardware acceleration.

---

### Post by anewbie on 2012-02-01
Ok if I play the mkv files on the tablet (I can do this); how can i have mencoder keep the soft titles when it transencode (to reduce bit rate/resolution).
-
I can only get hard subtitles or no subtitles; but not soft subtitles (the original has soft subtitles that work fine).


> **momokoyukino said:**
> Try finding an app for your tablet that supports MKV decode. I have an Android tablet, and use BSPlayer, which supports MKV decoding and hardware acceleration.

---

### Post by blenderfox on 2012-02-01
If your player is not displaying the softsubs when playing an MKV on your tablet, it probably means the player you're using on it doesn't understand the MKV format (or incorrectly thinks it's a non-container format.) But, seriously, most tablets these days have a player capable of handling MKV and should be more than capable of playing MKV without having to transcode or re-encode anything.

What kind tablet are you using?

---

### Post by anewbie on 2012-02-01
You misunderstand. THe problem is not with the tablet dispalying them. THe problem is that when I transencode the mkv files (to reduce bit rate/resolution) mencoder will not copy the soft subtitles. I can either have mencoder convert to hard subtitles or no subtitles.

So the question is how to create soft subtitles in the newly transencoded mkv files ?

> **momokoyukino said:**
> If your player is not displaying the softsubs when playing an MKV on your tablet, it probably means the player you're using on it doesn't understand the MKV format (or incorrectly thinks it's a non-container format.) But, seriously, most tablets these days have a player capable of handling MKV and should be more than capable of playing MKV without having to transcode or re-encode anything.

What kind tablet are you using?

---

### Post by blenderfox on 2012-02-02
> **anewbie said:**
> You misunderstand. THe problem is not with the tablet dispalying them. THe problem is that when I transencode the mkv files (to reduce bit rate/resolution) mencoder will not copy the soft subtitles. I can either have mencoder convert to hard subtitles or no subtitles.

So the question is how to create soft subtitles in the newly transencoded mkv files ?

I'm sure there are other ways of doing this, but one way I can think of doing that is to use mkvextract to split out the streams. Then use mencoder to do your transcoding or reprocessing. Then use mkvmux to combine the streams back together again.

---

### Post by anewbie on 2012-02-02
Thanks. Yea I discovered this morning that works; but it is very slow since you have to manually find the track to extract via mkvinfo. Hum. Don't really have time now but maybe I should learn the mkv format and write something to automate this - it seems like it would not be too hard for a program to look at hte same info mkvinfo is looking at and pick the right track to extract.

> **momokoyukino said:**
> I'm sure there are other ways of doing this, but one way I can think of doing that is to use mkvextract to split out the streams. Then use mencoder to do your transcoding or reprocessing. Then use mkvmux to combine the streams back together again.

---

### Post by blenderfox on 2012-02-02
You could probably put the whole thing into a bash script quite easily.

---

### Post by anewbie on 2012-02-02
Well the biggest problem I see is identifying which subtitle track to extract but you are right I could write a little wrapper program to execute the various command and analyzie the output. I am a bit confused; as I just checked one of my mkv files and it has three english sub-title tracks. No clue how they differ; two are nearly the same size and the third is 1/4 the size.
-
Btw kind of had hoped to use avi container as tablet seems to handle this better and they are smaller but i think i will just stick with mkv for now.


> **momokoyukino said:**
> You could probably put the whole thing into a bash script quite easily.

---

### Post by blenderfox on 2012-02-02
The small one is probably the signs only. As for the other two, its common to have "English" and "English for the hard of hearing" as separate subtitle tracks, so you probably have three English tracks for this reason.

---

### Post by anewbie on 2012-02-02
But how do I pick which one(s) to insert in the transencoded file :(

That is the annoying part. I wonder if I can just mux all three and then let the player figure out what to do with them.

> **momokoyukino said:**
> The small one is probably the signs only. As for the other two, its common to have "English" and "English for the hard of hearing" as separate subtitle tracks, so you probably have three English tracks for this reason.

---

### Post by blenderfox on 2012-02-02
You can. And if memory serves correctly, you can set one of the subtitle streams as default.

---

### Post by anewbie on 2012-02-02
How does mkvinfo identify which one is currently the default ?

> **momokoyukino said:**
> You can. And if memory serves correctly, you can set one of the subtitle streams as default.

---

### Post by blenderfox on 2012-02-02
The "default flag" option (see example below. On this one, my subs are default on, meaning they will display as standard without me having to specify them)

> + EBML head
|+ EBML version: 1
|+ EBML read version: 1
|+ EBML maximum ID length: 4
|+ EBML maximum size length: 8
|+ Doc type: matroska
|+ Doc type version: 2
|+ Doc type read version: 2
+ Segment, size 287497780
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4027)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v0.8.0 + libmatroska v0.9.0
| + Writing application: mkvmerge v3.4.0 ('Rapunzel') built on May 15 2010 09:38:20
| + Duration: 1404.821s (00:23:24.821)
| + Date: Tue Jul 20 15:27:01 2010 UTC
| + Segment UID: 0x95 0xf5 0x55 0x26 0x42 0x7c 0xd4 0x2b 0xa5 0x98 0x41 0x4f 0x51 0x77 0xdb 0xe2
|+ Segment tracks
| + A track
|  + Track number: 1
|  + Track UID: 1
|  + Track type: video
|  + Enabled: 1
**|  + Default flag: 0**
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 1
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: V_MPEG4/ISO/AVC
|  + Codec decode all: 1
|  + CodecPrivate, length 42 (h.264 profile: High @L4.1)
|  + Default duration: 41.708ms (23.976 fps for a video track)
|  + Language: eng
|  + Video track
|   + Pixel width: 1280
|   + Pixel height: 720
|   + Interlaced: 0
|   + Display width: 16
|   + Display height: 9
| + A track
|  + Track number: 2
|  + Track UID: 3881583497
|  + Track type: audio
|  + Enabled: 1
**|  + Default flag: 1**
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: A_AAC
|  + Codec decode all: 1
|  + CodecPrivate, length 2
|  + Default duration: 21.333ms (46.875 fps for a video track)
|  + Language: und
|  + Audio track
|   + Sampling frequency: 48000
|   + Channels: 2
| + A track
|  + Track number: 3
|  + Track UID: 4005446063
|  + Track type: subtitles
|  + Enabled: 1
**|  + Default flag: 1**
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 0
|  + Timecode scale: 1
|  + Max BlockAddition ID: 0
|  + Codec ID: S_TEXT/***
|  + Codec decode all: 1
|  + CodecPrivate, length 1027
|  + Language: und
|+ EbmlVoid (size: 1024)
|+ Cluster


---

### Post by anewbie on 2012-02-03
Thanks! It seems that mkv did not set these correctly (I think) or something odd happen. Any ways its not perfect but i can copy these well enough now. Still can't do it with one pass with mencoder but when I have time i'll work on a little c program or perl script to mencode, mkv extract and mkv merge.

---

