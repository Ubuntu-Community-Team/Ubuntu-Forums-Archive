---
title: "HOWTO: Rip DVDs in MPEG-4 AVC (x264), multi audio, subtitles, Matroska"
date: 2006-10-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Heinz on 2006-10-08
[MPlayer]("http://en.wikipedia.org/wiki/Mplayer") and [MEncoder]("http://en.wikipedia.org/wiki/Mencoder") are amazing tools not only for watching but also for backing up DVD content. This HOWTO demonstrates how to create a very high quality rip with next generation video ([H.264]("http://en.wikipedia.org/wiki/H.264")/[x264]("http://en.wikipedia.org/wiki/X264")/[MPEG-4 AVC]("http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC")) serveral audio tracks ([Vorbis]("http://en.wikipedia.org/wiki/Vorbis") in this case, can be other formats like [AC3]("http://en.wikipedia.org/wiki/Ac3"), [MP3]("http://en.wikipedia.org/wiki/Mp3")) and subtiles (vobsubs) in a [Matroska]("http://en.wikipedia.org/wiki/Matroska") container. In order to install the necessary applications you will need the multiverse repository ([https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)).

**[SIZE="3"]1. Install needed applications[/SIZE]**

> sudo apt-get install mplayer mencoder normalize-audio vorbis-tools mkvtoolnix mkvtoolnix-gui gpac x264-bin

**[SIZE="3"]2. Rip DVD to harddisk[/SIZE]**

> mplayer dvd://1 -v -dumpstream -dumpfile title.vob[LIST]
[*]*1* is the stream you want to rip.[/LIST]

**[SIZE="3"]3. Subtitles[/SIZE]**

In order to determine which subtitles are available on your DVD run the following command

> mplayer dvd:// -v -vo null -ao null | grep "subtitle"

**3.1 Rip subtitles**

> mencoder dvd://1 -nosound -ovc frameno -o /dev/null -slang en -vobsubout title[LIST]
[*]*1* is the stream we extract the subs from
[*]*slang* is the desired language (en, de, fr, etc.)
[*]*title* is the basename of the vobsub files, in this case *title.idx* and *title.sub*[/LIST]

**[SIZE="3"]4. Audio[/SIZE]**

In order to determine which audio tracks are available on your DVD run the following command

> mplayer dvd:// -v | grep "audio stream"

In case you want to keep the original AC3 audio step forward to 4.4.

**4.1 Convert audio to [PCM]("http://en.wikipedia.org/wiki/PCM")**

> mplayer title.vob -ao pcm:file=audio1.wav -vc dummy -aid 128 -vo null[LIST]
[*]*title.vob* is the stream we already ripped in step 2
[*]*audio1.wav* is the name of the resulting PCM file
[*]*-aid 128* chooses the first audio track[/LIST]
If you would like to rip another audio track (e.g. commentary or different language) repeat the above with the next track number (*-aid 129* would be the second track) and save as *audio2.wav*.

**4.2 [Normalize audio]("http://en.wikipedia.org/wiki/Audio_normalization")**

> normalize-audio audio1.wavRepeat on *audio2.wav* etc. if you have more than one audio track.

**4.3 Encode audio into Ogg Vorbis**

> oggenc -q5 audio1.wav[LIST]
[*]*-q5* is the desired quality of the first track. *Wikipedia: Many users feel that Vorbis reaches transparency (sound quality that is indistinguishable from the original source recording) at a quality setting of -q5, approximately 160 kbit/s.* Additional audio tracks can be encoded accordingly with lesser quality in order to save disc space.[/LIST]

**4.4 Keep original Dolby Digital AC3 audio**

In case you do not want to compress audio but keep the original AC3 track simply extract it from the VOB with

> mplayer title.vob -aid 128 -dumpaudio -dumpfile title.ac3

**[SIZE="3"]5. Video[/SIZE]**

This example uses the two-pass-method and presumes progressive PAL video. Read [here]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html") how to deal with telecined, interlaced and NTSC video.

First, we have to get rid of black borders around the movie. Hence we playback the file with the cropdetect filter.

> mplayer title.vob -vf cropdetectMove a little forward in the movie using the arrow-up key and let MPlayer find the correct settings for you. If you are finished quit MPlayer and copy the part *-vf crop=720:432:0:76* from the console. Of course your values might differ from this example.

**5.1 Determine video bitrate**

The choice of the bitrate depends. If you don't care about filesize anything above 1000 deliveres superb quality. If you do however plan the final file size to be about 700 MB or a multiple calculate like this (copied from MPlayer documentation):

*If you aim at a certain size, you will have to somehow calculate the bitrate. But before that, you need to know how much space you should reserve for the audio track(s), so you should rip those first. You can compute the bitrate with the following equation: bitrate = (target_size_in_Mbytes - sound_size_in_Mbytes) * 1024 * 1024 / length_in_secs * 8 / 1000  For instance, to squeeze a two-hour movie onto a 702MB CD, with 60MB of audio track, the video bitrate will have to be: (702 - 60) * 1024 * 1024 / (120*60) * 8 / 1000 = 740kbps*

**5.2 Start video encoding process**

Create a file which runs the first and second pass consecutively.

> gedit videncPaste the following into that file and adjust the cropping and video bitrate values with the ones you got from the procedures above 


```
# First pass
mencoder -v\
         title.vob\
        -vf crop=720:432:0:76,harddup\
        -ovc x264 -x264encopts subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000\
        -oac copy\
        -of rawvideo\
        -o title.264

# Second pass
mencoder -v\
         title.vob\
        -vf crop=720:432:0:76,harddup\
        -ovc x264 -x264encopts subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000\
        -oac copy\
        -of rawvideo\
        -o title.264
```
*x264encopts threads=auto* will speed things up if you own a dual-core cpu.

Since MEncoder is not able to save directly into Matroska containers we encode the video in raw format convert it later into .mp4 and finally mux everything (video, audio, subtitles) together with mkvmerge. [Interested in what all those options mean?]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html") If everything fits your needs save *videnc*.

Encoding of MPEG-4 AVC  video is a time consuming matter. On my AMD Athlon64 3000+ a 90 minute movie takes about 3 hours for the first and again about 5 hours for the second pass. Best is to let your machine work over night while you sleep.

Run *videnc*
> 
sh videnc

**[SIZE="3"]6. Muxing[/SIZE]**

**6.1 Mux video into MP4 container**

Good morning! ;) 

If encoding went fine we are ready to put that x264 file into an MP4 container

> MP4Box -add title.264 title.mp4You can already verify the result by playing it in MPlayer.

**6.2 Muxing it all together into Matroska container**

Start up the MKV files creator

> mmgand simply drag & drop your files into the *Input files* box
[LIST]
[*]title.mp4
[*]audio1.ogg or audio.ac3
[*]audio2.ogg
[*]title.idx (not title.sub!)[/LIST]
You might have noticed that we did not scale the video during the encoding process. That is because Matroska handles the aspect ratio itself. Simply define the languages and track names in the *Tracks* box and choose the correct aspect ratio. Choose an *output filename* (the default would produce title.mkv) and hit *Start muxing*.

Changelog:
[LIST]
[*]09.10.2006 - fixed encoding parameters
[*]09.10.2006 - added telecined, interlaced, NTSC
[*]10.10.2006 - added encode to certain file size
[*]10.10.2006 - added determine audio and subtitle tracks, overworked document structure
[*]13.10.2006 - changed -oac copy instead of -nosound due to sync issues
[*]28.01.2007 - added option "harddup" to video filter chain, added support for dual-core cpus (thanks to NobodySpecial)
[/LIST]

ToDo:
[LIST]
[*]Rip chapters with OGMTools
[/LIST]

---

### Post by abu_nawas on 2006-10-09
it's nice. 
what about the interlaced movie?

---

### Post by Heinz on 2006-10-09
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html) describes how to percept and handle interlaced video. I received good results by using the deinterlce postprocessing filter *-vf pp=lb*. As the documentation reads there are serveral filters available and it should be done after cropping and before scaling.

---

### Post by encho on 2006-11-09
I have just seen this guide, nice one. But there is one point I wish to make.
Using matroska is cool, it is open source, etc. Also vorbis - excellent quality, small sizes, etc. But, if you really want to make your video archive, I suggest that you go with x264/avc (video) and faac/aac (audio), all muxed in mp4 container. Why? Because future HD DVD devices and Blue Ray are going to support that format straight from your file. Even now you can buy some classic dvd players - check the [Nero certified devices]("http://ww2.nero.com/nerodigital/enu/DVD_Player_Recorder.html").

And it is not huge difference for the encoding process - you still create x264 video stream - the only difference is in audio and container.

After a lot of researching, testing and waiting, I have found out that:

> 
ffmpeg -i %f -r 23.976 -pix_fmt yuv420p -f rawvideo -s 640x360 - | x264 --min-keyint 24 --keyint 240 --crf 23 --qpmin 5 --qpmax 51 --qcomp 0.75 --me umh --subme 6 --ref 6 --bframes 3 --ipratio 1.25 --pbratio 1.33 --filter -1,-1 --no-psnr --b-rdo --b-pyramid --weightb --mixed-refs --bime --trellis 2 --8x8dct --analyse all --fps 23.976 --output %f.264 - 640x360


produces the best results in one pass - constant quality based (where %f is input file - I am using thunar's scripts).
And:
> 
ffmpeg -i %f -r 23.976 -ac 2 -vn -f wav -y - | faac -q 90 - -o %f.aac

produces hi-quality aac audio.
Finally:
> 
MP4Box -add %f.264#video -add %f.aac#audio -fps 23.976 %f.aac.mp4

mux them together in MP4 container, very compatible and reliable.

I also got few tricks for converting pal to ntsc and vice versa.

Instead of having 4 gig mpegs or 1 gig Xvids, I have 500mb(!) hi quality mp4s in my video collection.

Even if you have your collection in mkv format (I did), there is an easy way to remux them to mp4 (without any quality loss). Just something like:
> 
mkvextract tracks %f 1:%f.264 2:%f.ogg && MP4Box -add %f.264#video -add %f.ogg#audio -fps 23.976 %f.ogg.mp4 && rm %f.264 && rm %f.ogg


Although you will have non-standard MP4 (with vorbis audio), but maybe those will be supported some time. You can always reencode audio as well.

Hope this helps to someone.:)

---

### Post by Aditz on 2006-11-14
I think it is better to use neroaacenc with wine. It has better quality than faac. Discussion: [http://forum.doom9.org/showthread.php?t=113694](http://forum.doom9.org/showthread.php?t=113694)

---

### Post by encho on 2006-11-15
> **Aditz said:**
> I think it is better to use neroaacenc with wine. It has better quality than faac. Discussion: [http://forum.doom9.org/showthread.php?t=113694](http://forum.doom9.org/showthread.php?t=113694)

It stands for 5 channel audio, as for 2 channels, faac is more than enough.

---

### Post by the ev on 2006-11-18
Great tutorial!!  Makes my switch from Windows/StaxRip much easier.

But here's my question.  I've taken your steps and put them in a Bash script (of which I'm very proud of myself for doing, as my programming skills are pretty limited), but I was wondering if there was anyway to do a few things with it.

Here's the script: 
```
#!/bin/bash
echo Name of the DVD?
read NAME
mkdir ~/$NAME
cd ~/$NAME
echo "Device? (/dev/hda or /dev/hdb)"
read DEVICE 
mplayer -dvd-device $DEVICE dvd://1 -v -dumpstream -dumpfile $NAME.vob
echo "Starting Crop detection - copy <-vf crop=*:*:*:*> for editing videnc!!"
mplayer $NAME.vob -vf cropdetect
cp ~/videnc ~/$NAME/
echo "Starting GEdit to modify Video encoding settings.  Close the window when done."
gedit videnc
echo "Extracting Audio..."
mplayer $NAME.vob -ao pcm:file=audio1.wav -vc dummy -aid 128 -vo null
echo "Normalizing Audio..."
normalize-audio audio1.wav
echo "Encoding Audio..."
oggenc -q6 audio1.wav
echo "Encoding Video..."
sh videnc
echo "Packaging Video..."
MP4Box -add $NAME.264 $NAME.mp4
echo "Packaging Movie..."
mkvmerge -o $NAME.mkv $NAME.mp4 audio1.ogg
echo "All done!!"

```

...And here are my questions:
1) Is there anyway to export the crop value from mplayer -vf crop to the videnc file automatically, rather than manually cutting and pasting? And if there isn't, is there anyway to have a break waiting on "Enter" before going to the next step (configuring videnc)?

2) Is there anyway to take the input for the local variable $NAME and automatically update the corresponding entries in videnc?

I know these are more scripting questions than ripping questions, but if you've got any insights on how I can clean up this script, I'd love to hear them.  I'm trying to automate the process as much as possible, so I can just stick in the DVD and start the script.

---

### Post by the ev on 2006-11-18
Oh, I forgot my third question:

Is there anyway to export the entire process to a log file?  Even better, a time-stamped one?

---

### Post by Heinz on 2006-11-25
@encho: I've given up on standalone players and only use Linux boxes for video playback. So, this guide mainly aims on best quality (imho) combined with a convenient container which handles vobsubs.

Having said that you are completely right about hardware support of MP4 files. You should use MP4 with AAC in this case.

@the ev: I'm not much of a script guru meself but a quick search found this link [http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2004-July/027662.html](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2004-July/027662.html) which invokes an automated cropping routine. Perhaps that will be useful for you. Linux offers a couple of tools to manipulate text files with. Hence automated editing of the videnc file with grep, sed and the like should not be a problem. I'm sure you can cope with that.

---

### Post by dkaplowitz on 2006-11-28
Cool guide, thanks for taking the time to post it all!

---

### Post by ixus_123 on 2006-11-28
If anyone is after a GUI frontend to do all this the **OGMrip** is up to the task

---

### Post by encho on 2006-11-28
> **Heinz said:**
> @encho: I've given up on standalone players and only use Linux boxes for video playback. So, this guide mainly aims on best quality (imho) combined with a convenient container which handles vobsubs.


It makes sense. I am also considering buying wireless device for streaming stuff from computer to tv. It would be cool to output video played by mplayer to screen in another room. Anyone has any experience? I've heard that D-Link has something like that. Sorry if I'm off the topic.

---

### Post by finite9 on 2006-12-05
I am trying to install gpac on Ubuntu 6.06 but it is dependant on libavcodec2 which isn't available in Dapper repos.  I notice that noone else here is a 6.06 user according to theirs profiles...is this an Edgy specific guide?

---

### Post by jocheem67 on 2006-12-05
It's a great guide and I'm very satisfied with the H264 codec.

However I encoded a dvd, succeeded easily but the A/V is out of sync.
That's a major setback, and I must say that mencoder is notrious for not syncing very well.

I'm considering to try another rip one of these days using ffmpeg.


Another note: using transcode ( through dvd::rip, using xvid ) the A/V is always perfectly okay!!

---

### Post by finite9 on 2006-12-08
I tried your method of muxing encho, but it does not work.  The video and audio encoding went fine with ffmpeg, but your command:

> MP4Box -add %f.264#video -add %f.aac#audio -fps 23.976 %f.aac.mp4

does not work.  -add is not a valid option in mp4box in the Ubuntu 6.06 repos, so I used -import instead, but even then it complains that:

> Import failed MP4 File is truncated

I assume that it does not recognise the input files.  I tried with just the video and just the audio but no luck.  Looks like ill have to read the manual. :)


UPDATE:


AAAARRRGGGHHHH!!!!!!  Im sad.

gpac in dapper is 0.2.0 and dont support "-add".  bummer.  This is now Big Reason #5 to move to Edgy and unfortunately for me, Edgy has a serious issue with my wireless adapter where the kernel panics if the adapter is not turned on and I cant turn it on until after kernel boot.

---

### Post by encho on 2006-12-09
It is actually easy to compile gpac, you just need some libs. Try it.

---

### Post by finite9 on 2006-12-11
> **encho said:**
> It is actually easy to compile gpac, you just need some libs. Try it.

I will, thanks.  This is the only thing left for me to *finally* be able to encode and burn all the dv tapes I have!  It's taken over 1 year to get this far :/

---

### Post by Heinz on 2006-12-11
> **jocheem67 said:**
> However I encoded a dvd, succeeded easily but the A/V is out of sync.
That's a major setback, and I must say that mencoder is notrious for not syncing very well.

In any case use -oac copy instead of -nosound during the video encode. No sync issues for me. I remember once having solved audio sync probs by changing audio from sdl to alsa in the mplayer config file.

---

### Post by jocheem67 on 2006-12-15
Thanks, will try that. I using avidemux now though. Compiled it myself with great results ( mp4, AAC, x264 ).

---

### Post by manish_m on 2006-12-25
Encho,
i tried encoding using ur way. But A/V is out of sync.
can this be fixed ?

---

### Post by encho on 2006-12-29
These are settings for ntsc-film. 

1. If you are using PAL source, you have to change all 23.976 to 25.
2. Or 29.97 if you are using real ntsc.

You can check your video properties with:

> 
mplayer -vo dummy -identify %f


I have encoded more than 100 videos without single problem. You can also omit -r 23.976; --fps 23.976 in my script,  most likely it will be recognized anyway. The reason for me using it is because some fps' of wmv files were not recognized automatically.

---

### Post by Placenta Juan on 2007-01-03
If you are using inverse telecine with mencoder using -vf pullup,softskip, there can be audio sync problems due to dropped frames. Use the option harddup to create duplicate frames to fix these sync problems. The command I use for nice, two pass x264 encodes from a telecined NTSC source is
```

mencoder test.vob -o pass1.264 -ofps 24000/1001 -vf pullup,softskip,scale=512:384,harddup -ovc x264 -x264encopts subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000 -oac copy -of rawvideo
mencoder test.vob -o pass2.264 -ofps 24000/1001 -vf pullup,softskip,scale=512:384,harddup -ovc x264 -x264encopts subq=6:partitions=all:8x8dct:me=umh:frameref=6:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000 -oac copy -of rawvideo

```
assuming your source is named test.vob
audio is encoded using faac
```
mplayer test.vob -ao pcm:file=audio1.wav -vc dummy -aid 128 -vo null
faac audio1.wav -w -q 100
```
then muxed with
```
MP4Box -add pass2.264 -add audio1.m4a -fps 23.976 test.mp4
```
results have been good, but I'll admit I'm still rather newbish, so any advice would be appreciated.

---

### Post by gurgle on 2007-01-03
is there a GUI interface for doing this yet? kinda like MeGUI on WinXP?

---

### Post by Heinz on 2007-01-05
Well, if you're happy with x264+AAC in MP4 container [Avidemux]("http://fixounet.free.fr/avidemux/") is a great program for that sort of thing. Somehow comparable to Windows' VirtualDub. However it does not support the ripping process and doesn't support Matroska containers.

---

### Post by monkman on 2007-01-10
Is ubuntu 6.06 necissary or 6.10 to do ripping with this guide? Or does it run on both?

---

### Post by hackeron on 2007-01-18
Question, if I want AC3 sound, doesn't -oac copy already do that for me without having to dump the sound out separately?

Then the MP4 step becomes redundant.

---

### Post by NobodySpecial on 2007-01-21
Heinz, thanks for a GREAT post.  A couple tricks:

To solve audio / video sync issue, add "harddup" command on the crop line, like:

```
-vf crop=720:480:0:0,harddup -ofps 23.976\
```

If you have a dual-core processor, you can significantly speed up by adding "threads=auto" to the x264encopts line, like:
```
-ovc x264 -x264encopts threads=auto:
```
By using both processors, a sample run on my machine went from 2:30 mins to 1:37 mins.

---

### Post by Heinz on 2007-01-28
@monkman: I'm using Edgy on all my machines hence I can't vouch for Dapper. There might be an issue with MP4Box in Dapper missing the "-add" switch. Maybe someone using Dapper could verify?

@hackeron: MEncoder can as yet neither mux into an MP4 nor Matroska container. Using AVI for AVC content is not a good idea. Also the resulting AVI cannot be handled by neither MMG nor MP4Box. So the step of seperately extracting the audio stream is mandatory.

@NobodySpecial: Greatly appreciated advise! Added to the Howto.

---

### Post by monkman on 2007-02-14
anybody knows how to add chapters to the mkv file? and maybe rename them?

THX

---

### Post by HIGHLIFE on 2007-02-14
Hey when I encode the video with x264 it becomes slower than the original, which also causes the a/v to be out of sync and the movie about 20 minutes longer.  Any Ideas?

---

### Post by leha on 2007-03-07
Thanks for this great howto. I have a couple of remarks though:

my mencoder curses on 
```
mplayer title.vob -ao pcm:file=audio1.wav -vc dummy -aid 128 -vo null
```
basically he does not know video codec dummy and offers to use null at some point
```
Forced video codec: dummy
Cannot find codec matching selected -vo and video format 0x10000002.
Read DOCS/HTML/en/codecs.html!

```

for some reason > threads=auto is not good for x264 encoder , it wants a number. Looks like n+1 rule works and > threads=3 loads my dual core processor better then > threads=2 

it might be easier to add command line parameters to your script , so you can provide filename, bitrate and crop options without editing the file.

---

### Post by gmc on 2007-03-09
Hi Folks,

I'm borrowing a few idea's from this thread and am trying to figure out how I can get the following code to work.

```

mencoder -demuxer 2 -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate=6000:aspect=4/3 -vf crop=704:464:6:8,scale=528:368 $1.mpeg -o - | \
ffmpeg -r 29.970 -pix_fmt yuv420p -f rawvideo -s 528x368 -i - | \
x264 --threads=auto --min-keyint 24 --keyint 240 --crf 23 --qpmin 5 --qpmax 51 --qcomp 0.75 --me umh --subme 6 --ref 6 --bframes 3 \
     --ipratio 1.25 --pbratio 1.33 --filter -1,-1 --no-psnr --b-rdo --b-pyramid --weightb --mixed-refs --bime --trellis 2 --8x8dct \
     --analyse all --fps 29.970 --output $1.264 - 528x368

```I'm attempting to pipe the output from mencoder to the input of ffmpeg, then pipe the output from ffmpeg to the input of x264. I can't seem to get mencoder to pipe it's output to the input of ffmpeg.

Can someone offer a suggestion? I realize I could have mencoder write a temporary file and use that for the input to ffmpeg, but I'm trying to avoid that due to the amount of disk access and file sizes.

Regards
Gord

---

### Post by aroman on 2007-03-14
Hello,

First of all, great tutorial!

I'd like to do AAC encoding instead of OGG. I am able to do 2 channel AAC encoding, but wasn't able to do 6 channel. The audio output would be all static.

Has anyone done this before and have any hints?

Thank you!

---

### Post by pkerling on 2007-03-15
Hi all,

I made a quick´n´dirty script to convert the output of dvdxchap (part of OGMTools) to the XML chapter format of Matroska.
You can get it here: [http://rafb.net/p/EvzSRh32.txt](http://rafb.net/p/EvzSRh32.txt) (rename to chap2xml and make executable)

Usage: ./chap2xml <language>

Use example:
1) Run ```
dvdxchap /dev/dvd | ./chap2xml ger > chapters.xml
``` to convert the chapters of DVD title 1 to XML.
2) Start mmg, go to "Chapter Editor" and load the created XML via the menu.
3) Edit the chapters as you want, e.g. change chapter names.
4) Save the chapter file via the menu.
5) Use the edited XML as "Chapter file" in section "General".

Works fine for me :)

Best regards,
Philipp Kerling

---

### Post by balance07 on 2007-04-02
@pkerling:

i don't think any of that needs to be done. mkvmerge can take dvdxchap output directly. this is what i use:

```

dvdxchap /dev/dvd > chapters.txt
mkvmerge -o movie.mkv --chapters chapters.txt video.mp4 audio.ogg

```

seems to work great.

---

### Post by pkerling on 2007-04-03
I didn´t know that, thank you for telling me :)

---

### Post by balance07 on 2007-04-03
i really don't like using the MKV container's aspect ratio functionality, as i've found that not all players use it. i'm trying to figure out how to crop and scale my movies properly (preferably using the awesome cropdetect in the process) any ideas out there?

---

### Post by balance07 on 2007-04-03
ok let's see how much i can post here... most of this is modified from the script that 'the ev' made. here's my system (NTSC DVDs) that i think works pretty well.

ripdvd.sh:
```

#!/bin/bash

echo "Put DVD in the top drive."
read NOTHING

echo "Name of the DVD?"
read NAME

mkdir ~/Desktop/$NAME
cd ~/Desktop/$NAME

cp ~/videoencode.sh ~/Desktop/$NAME/
cp ~/videopackage.sh ~/Desktop/$NAME/

echo "Ripping DVD..."

mplayer dvd://1 -v -dumpstream -dumpfile title.vob

echo "Determine Scale Value - note 'VO: [xv] 720x480 => 854x480 Planar YV12' for calculating scale!"

mplayer title.vob

echo "Starting Crop detection - copy <-vf crop=*:*:*:*> for editing videoencode.sh!"

mplayer title.vob -vf cropdetect

echo "Starting GEdit to modify video encoding settings. Close the window when done."

gedit videoencode.sh

echo "Starting GEdit to modify video packaging settings. Close the window when done."

gedit videopackage.sh

echo "Extracting chapter information..."

dvdxchap /dev/dvd > chapters.txt

echo "Extracting Audio..."

mplayer title.vob -ao pcm:file=audio.wav -vc dummy -aid 128 -vo null

echo "Normalizing Audio..."

normalize-audio audio.wav

echo "Encoding Audio..."

oggenc -q5 audio.wav

echo "Encoding Video..."

sh videoencode.sh

echo "Packaging Video..."

sh videopackage.sh

echo "All done!!"

```

videoencode.sh:
```

#!/bin/bash

# First pass

mencoder -v\
	title.vob\
	-ofps 24000/1001\
	-sws 9\
	-vf crop=656:464:30:8,pullup,softskip,harddup,scale=784:464\
	-ovc x264 -x264encopts subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1100\
	-oac copy\
	-of rawvideo\
	-o pass1.264

# Second pass

mencoder -v\
	title.vob\
	-ofps 24000/1001\
	-sws 9\
	-vf crop=656:464:30:8,pullup,softskip,harddup,scale=784:464\
	-ovc x264 -x264encopts subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1100\
	-oac copy\
	-of rawvideo\
	-o pass2.264

```

videopackage.sh:
```

#!/bin/bash

MP4Box -add pass2.264 -fps 23.976023976 video.mp4

echo "Packaging Movie..."

mkvmerge -o COMPLETE.mkv --chapters chapters.txt --display-dimensions 1:784x464 video.mp4 audio.ogg

```

please give me comments on this if you have any. and to anyone struggling, i hope it helps!

---

### Post by finite9 on 2007-04-05
> **encho said:**
> These are settings for ntsc-film. 

1. If you are using PAL source, you have to change all 23.976 to 25.
2. Or 29.97 if you are using real ntsc.


Can someone please explain to me why PAL video at 25fps should be specified at 23.976 when transcoding??  I don't understand.  Why is it not just 25fps all the time?  Does it have something to do with lowering the frame rate to save space whilst still getting flowing motion?

---

### Post by balance07 on 2007-04-05
@finite9:

i think you are mis-reading that quote. for PAL video, use 25 fps. for NTSC, use 23.976 or 29.97.

---

### Post by finite9 on 2007-04-06
yeah I might be misreading it, but PAL is 25fps and NTSC is 30fps, so I guess my question is, why would you ever specifc something like 23.976?

---

### Post by balance07 on 2007-04-06
we're getting into pretty complicated stuff here. here's the gist of it. movies are generally filmed at 24 frames per second. the NTSC standard is ~60 fps interlaced video. when movies are converted to dvd, with a process called telecine, the framerate is converted. but on your monitor or say a nice hdtv connected by vga or something, you don't want interlaced video. so it's best to convert it BACK to 24 fps (24000/1001 to be exact), which is the original format.

check out these links:

[http://en.wikipedia.org/wiki/Telecine]("http://en.wikipedia.org/wiki/Telecine")

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html")

---

### Post by finite9 on 2007-04-07
that did explain it for me...thanks :)

---

### Post by Azakus on 2007-04-08
I'm following this guide for my own script, but mplayer seems to only want to dump the first chapter. Does anyone know how to fix this?
Here's my script
```

#!/bin/bash
#Usage dvdrip <MoveName>.mkv <CROP>
CROP=$2
NAME=$1
mkdir ~/$NAME
cd ~/$NAME
dvdxchap -t 1 /media/cdrom0 >> $NAME.chaps.txt
mplayer dvd://1  -dumpstream -dumpfile $NAME.vob
mplayer $NAME.vob -ao pcm:file=$NAME.wav -vc dummy -aid 128 -vo null
oggenc -q5 $NAME.wav
mencoder $NAME.vob -ofps 24000/1001 -vf scale=720:-3:pullup,softskip,crop=$CROP,harddup -nosound -ovc x264 -x264encopts bitrate=1000:subq=5:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:threads=auto -of rawvideo -o /dev/null
mencoder $NAME.vob -ofps 24000/1001 -vf scale=720:-3,pullup,softskip,crop=$CROP,harddup -nosound -ovc x264 -x264encopts bitrate=1000:subq=5:8x8dct:frameref=2:bframes=3:b_pyramid:weight_b:pass=2:threads=auto -of rawvideo -o $NAME.264
MP4Box -add $NAME.264 $NAME.mp4
mkvmerge $NAME.avi $NAME.ogg --chapters $NAME.chaps.txt -o $NAME.mkv --title $NAME

```

---

### Post by Azakus on 2007-04-09
Ahh. Seems that ivman was screwing up the dumping process (I don't know why).
Now it all works well!

---

### Post by finite9 on 2007-05-23
ive been playing with this a lot lately, to encode my home vids from DV tape, but im not that impressed by the quality.  there is quite a difference in the quality of the original compared to an encoded XviD or x264 done using mencoder with the best quality settings according to mencoders docs page.

Is this just apparent on the computer?  I have seen similar issues with ripped DVDs, but when I play the DVD on the TV, I can no longer discern the quality drop.

I tried lavc but this was not as good quality as x264.  Has anyone tried ffmpeg or transcode?  do they give better results or is it just me being too fussy?

mencoder file.dv -o file.h264 \
-ovc x264 \
-vf harddup,hq3ddn,scale=-10:-1 \
-x264encopts <insert opts from mencoder docs here for best quality> \
-nosound \
-of rawvideo

I do two pass with same opts.

The reason I ask is because when i download ripped stargate atlantis XviDs, they seem very high quality on TV with no blurring, blockiness etc, that I seem to get with my DV tapes.  This is what raises my suspicion.

Also, I cannot just copy an ac3 track and mux it into an AVI container with XviD video...it will not play on my standalone DVD player, as it thinks its a Divx and automatically assumes that the audio must be MP3.  Does anyone else have this issue?  It plays fine on the PC, because mplayer recognises the format and just plays it, but maybe most DivX players assume same thing, that it has to be MP3 sound format in an AVI container?

---

### Post by Azakus on 2007-05-23
No difference between Xvid and H.264? You must not be using the best encoding options then.
Post which x264encopts you're using.
Here's mine for comparison
```
Pass 1:
x264encopts subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000:threads=3 -of rawvideo -o /dev/null

Pass 2:
x264encopts subq=6:8x8dct:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000:threads=3 -of rawvideo -o $MOVIE.264
```

---

### Post by finite9 on 2007-05-23
mencoder $infile -o /dev/null \
-ovc x264 -vf harddup,kerndeint,hqdn3d,scale=-10:-1 -of rawvideo \
-x264encopts subq=6:partitions=all:me=umh:frameref=5:threads=auto:pass=1:turbo=1 \
-nosound
## second pass
mencoder $infile -o /tmp/"$infile2"h264 \
-ovc x264 -vf harddup,kerndeint,hqdn3d,scale=-10:-1 -of rawvideo \
-x264encopts subq=6:partitions=all:me=umh:frameref=5:threads=auto:pass=2 \
-nosound

and for xvid...

mencoder $infile -o $file -ovc xvid \
-vf harddup,kerndeint,hqdn3d,scale=-10:-1 \
-xvidencopts fixed_quant=4 \
-oac mp3lame -lameopts preset=192

I didnt say there was no difference between xvid and x264.  I said there was a big drop in quality between DV original and x264 encode OR between DV and XviD encode.

---

### Post by Azakus on 2007-05-23
> **finite9 said:**
> mencoder $infile -o /dev/null \
-ovc x264 -vf harddup,kerndeint,hqdn3d,scale=-10:-1 -of rawvideo \
-x264encopts subq=6:partitions=all:me=umh:frameref=5:threads=auto:pass=1:turbo=1 \
-nosound
## second pass
mencoder $infile -o /tmp/"$infile2"h264 \
-ovc x264 -vf harddup,kerndeint,hqdn3d,scale=-10:-1 -of rawvideo \
-x264encopts subq=6:partitions=all:me=umh:frameref=5:threads=auto:pass=2 \
-nosound

and for xvid...

mencoder $infile -o $file -ovc xvid \
-vf harddup,kerndeint,hqdn3d,scale=-10:-1 \
-xvidencopts fixed_quant=4 \
-oac mp3lame -lameopts preset=192

I didnt say there was no difference between xvid and x264.  I said there was a big drop in quality between DV original and x264 encode OR between DV and XviD encode.

Oh, that's what you meant. Well, there's always a quality drop from DV to any codec. That's the point. A tradeoff in quality for filesize. The only way to get even close to originial quality would be to have a massive filesize in any codec, defeating the whole purpose of a lossy codec. The best you can do is tweak your encoding options to have a high bitrate (>800) and use one of the best profiles [http://en.wikipedia.org/wiki/H.264#Profiles](http://en.wikipedia.org/wiki/H.264#Profiles).
I don't know how to make x264 create lossless video streams, but according to Wikipedia, it can.

---

### Post by balance07 on 2007-05-23
my settings, if anyone cares (with inverse telecine):
```

# First pass
mencoder -v\
	title.vob\
	-ofps 24000/1001\
	-sws 9\
	-vf crop=720:464:0:8,pullup,softskip,harddup,pp=lb,scale=848:464\
	-ovc x264\
	-x264encopts subq=1:frameref=1:bframes=3:b_pyramid:weight_b:pass=1:psnr:bitrate=1000\
	-oac copy\
	-of rawvideo\
	-o pass1.264

# Second pass
mencoder -v\
	title.vob\
	-ofps 24000/1001\
	-sws 9\
	-vf crop=720:464:0:8,pullup,softskip,harddup,pp=lb,scale=848:464\
	-ovc x264\
	-x264encopts subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000\
	-oac copy\
	-of rawvideo\
	-o pass2.264

```

---

### Post by finite9 on 2007-05-24
> **Azakus said:**
> Oh, that's what you meant. Well, there's always a quality drop from DV to any codec. That's the point. A tradeoff in quality for filesize. The only way to get even close to originial quality would be to have a massive filesize in any codec, defeating the whole purpose of a lossy codec <snip> 

Yeah, I realise it's not going to be as good as DV original, and that's ok....I want the smaller file sizes.  However, I think of it like this:

I download Stargate Atlantis off bittorrent and its 640x352@25fps XviD.  It is probably created from a TV tuner card, where the TV signal is probably (im guessing here) not as good as DV quality, or maybe the same as DV quality.

I compare this video (on the PC screen, not TV as you do not see the loss in quality that much on TV) to my encoded Xvid or x264 video 25fps at 1024x576 native widescreen resoution.  Mine looks pixelated (blocky) despite using deblocking filter.  Mine looks blurry also compared to original DV tape.

I cannot compare startgate rip to original stargate source signal like I compare my encode to original DV, but when I play stargate and my Xvid side by side, mine looks significantly worse than stargate.

I am fully aware this is very subjective, but my gut feeling is that either mencoder is not producing as good output as the encoder used for stargate (yeah, i know i have now way of knowing what encoder was used, but the difference in quality is apparent), in which case, does anyone know how well mencoder/ffmpeg/transcode compare to each other or to Windows programs?  Or, my settings are not optimal, despite going off the mencoder html docs for best possible quality.  Note that in my x264 encode, I am not using best settings, but settings to make it Windows Quicktime7 compatible, but I have tried best settings and there was truthfully not much difference that I could see with naked eye.

---

### Post by regeya on 2007-05-25
> **finite9 said:**
>  Or, my settings are not optimal, despite going off the mencoder html docs for best possible quality.  Note that in my x264 encode, I am not using best settings, but settings to make it Windows Quicktime7 compatible, but I have tried best settings and there was truthfully not much difference that I could see with naked eye.

Is the original signal fairly noisy?  As in, are you getting it from, say, a crummy cable TV connection and dumping that via analog to DV?  If so, you might want to try a combination of the hqdn3d and unsharp filters; you'll need to fiddle with the settings to get optimal results, of course.  The upside of this is that cleaning dirty signals makes for more easily-compressible video, which means better use of that bitrate than trying to encode static. ;)

The only thing that makes me answer this is that I've been fiddling with writing a Kino export script using mencoder, and one thing I discovered about my miniDV camera is that video shot on it is NOISY.  With hqdn3d, not only was the video clearer (once I'd discovered more or less optimal settings) but the encoding process went FASTER (mpeg2 ps with mp2 audio)  than it had without cleaning.  Not at all what I suspected!

---

### Post by finite9 on 2007-05-25
no, it's not a tv signal...im filming home videos with a Canon MVX4i DV camera, which is a high end  (not high def.) DV camera.  The signal was quite noisy on the original DV tape actually, becuase it was low light conditions, and despite being reasonably high end consumer, it does not cope well in low light.

I will give the unsharp filter a try...thanks for the tip!

By the way, another open question...If I encode x264 for QT7 compatibility, will this play on a bluray/HDDVD player???  Same goes for 'best settings' options on mencoder htmldocs...will that play on nextgen highdef players??

---

### Post by Azakus on 2007-05-25
Yes, it will play on HD-DVD/BluRay, but you need to have it in a specific configuration.
x264 video, AAC audio (faac encoder), in a .mp4 container (MP4Box in gpac).

---

### Post by johanhake on 2007-05-26
Hello!

Thanks for the very understandable how-to! Good work!

I am using feisty and it seems like some of the mencoder options has been changed.

I get this output:
Option x264encopts: Unknown suboption 4x4mv
Option x264encopts: Bad argument me=3

I search the net and found that 4x4mv has changed.
4x4mv => partitions=all 

I did not find a similar change for the me setting, but reading the [x264-options]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html") provided by Heinz, it seems like
me=umh
should correspond to me=3. Correct?

If this is correct it is strange that they do not accept these options and then present a warning message when deprecated options are used.

I also got the error message 
FATAL: Cannot initialize video driver

when initializing the second pass. I will try again with the new options. I just have to run the first pass, one more time because even if the initialization failed it manage to erase the .264 file :(

Johan

---

### Post by Azakus on 2007-05-26
> **johanhake said:**
> Hello!

Thanks for the very understandable how-to! Good work!

I am using feisty and it seems like some of the mencoder options has been changed.

I get this output:
Option x264encopts: Unknown suboption 4x4mv
Option x264encopts: Bad argument me=3

I search the net and found that 4x4mv has changed.
4x4mv => partitions=all 

I did not find a similar change for the me setting, but reading the [x264-options]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html") provided by Heinz, it seems like
me=umh
should correspond to me=3. Correct?

If this is correct it is strange that they do not accept these options and then present a warning message when deprecated options are used.

I also got the error message 
FATAL: Cannot initialize video driver

when initializing the second pass. I will try again with the new options. I just have to run the first pass, one more time because even if the initialization failed it manage to erase the .264 file :(

Johan
Yeah, the mencoder options changed slightly in feisty. Took me forever to figure it out too.
Those options should work, me=umh and partitions=all are legitimate options.
Post your entire mencoder cli options so everyone can see what the error might be in your second pass.
Also, you might want to think about doing -o /dev/null for the first pass, as it will then just generate the divx2pass.log file and not an extraneous .264 file (as soon as your second pass starts working that is).

---

### Post by johanhake on 2007-05-26
I just used the second run from Heinzes post, with different crop values

This was the command I used for the second run
```

mencoder -v\
         title.vob\
        -vf crop=720:416:0:80,harddup\
        -ovc x264 -x264encopts subq=6:partitions=all:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000\
        -oac copy\
        -of rawvideo\
        -o title.264

```

and heres the entire output.
```
MEncoder 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(TM) XP 2000+ (Family: 6, Model: 6, Stepping: 2)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
[B]Option x264encopts: Unknown suboption 4x4mv
Option x264encopts: Bad argument me=3
[/B]init_freetype
get_path('font/font.desc') -> '/home/hake/.mplayer/font/font.desc'
font: can't open file: /home/hake/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
[file] File size is 7176613888 bytes
STREAM: [file] title.vob
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
success: format: 0  data: 0x0 - 0xabc27000
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename title.vob ext: .vob
Trying demuxer 2 based on filename extension
system stream synced at 0xD (13)!
==> Found video stream: 0
==> Found audio stream: 129
==> Found audio stream: 128
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG-PS file format detected.
Searching for sequence header... OK!
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x576  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
Using SSE optimized IMDCT transform
AC3: 5.1 (3f+2r+lfe)  48000 Hz  384.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0xA
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [crop w=720 h=416 x=0 y=80]
Crop: 720 x 416, 0 ; 80
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=48000 sample-1)
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (720x576->1024x576,flags=0,'MPlayer',0x32315659)
SwScaler: using unscaled yuv420p -> yuv420p special converter
REQ: flags=0x403  req=0x0
REQ: flags=0x403  req=0x400
REQ: flags=0x403  req=0x0
REQ: flags=0x3  req=0x0
**FATAL: Cannot initialize video driver.**

```

> Also, you might want to think about doing -o /dev/null for the first pass, as it will then just generate the divx2pass.log file and not an extraneous .264 file (as soon as your second pass starts working that is).


He, he, then I probably wouldn't have had to run the first pass one more time! As the divx2pass.log file was present from the first, first run, because this is the only information the second run needs to do the job better, right?

At least the second run is up and going now! We see tomorrow if it all worked out!

Thanks for the answers!

Johan

---

### Post by Azakus on 2007-05-26
Replace "me=3" with "me=umh"
You might also want to try -vf scale=720:-3
This keeps the aspect ratio intact, and your 720:416 might be messing with the 720x576 aspect of the file.

---

### Post by NobodySpecial on 2007-06-06
For anybody interested, [this thread]("http://ubuntuforums.org/showthread.php?t=452694") talks about installing MediaTomb to stream video to the PS3.  Here is my script to convert video to h.264 format that the PS3 will play:
```

#!/bin/bash

#Encode Audio & Video then make mp4
#Compatible with PS3

#Set crop via command:
#mplayer VTS_01_1.VOB -vf cropdetect
CROP=640:320:6:94

#Rip audio wav, normalize, then AAC
#Check streams: mplayer VTS_01_1.VOB -vo null -v | grep "audio stream"
mplayer -ao pcm:fast:file=rip.wav -vc null -vo null -aid 128 VTS_01_1.VOB
normalize rip.wav
faac --mpeg-vers 4 rip.wav

# Routine encoding in two passes
# First pass
mencoder -v\
         VTS_01_1.VOB\
        -vf crop=$CROP,harddup -ofps 24000/1001\
        -ovc x264 -x264encopts threads=auto:subq=4:trellis=1:level_idc=41:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000\
        -oac copy\
        -of rawvideo\
        -o /dev/null

# Second pass
mencoder -v\
         VTS_01_1.VOB\
        -vf crop=$CROP,harddup -ofps 24000/1001\
        -ovc x264 -x264encopts threads=auto:subq=6:partitions=all:8x8dct:me=umh:frameref=5:trellis=1:level_idc=41:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000\
        -oac copy\
        -of rawvideo\
        -o rip.264

#Mux audio & video into mp4 container
MP4Box -add rip.264 -add rip.aac -fps 23.976 rip.mp4

```

This makes high-quality video.  If you want smaller file size, simply change the bitrate setting for each pass.

---

### Post by RockTonic3 on 2007-06-16
what am i doing wrong?  


```
christopher@chris-voltaire:/$ mplayer dvd://1 -v -dumpstream -dumpfile title.vobMPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 2.00GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/christopher/.mplayer/codecs.conf'
Reading /home/christopher/.mplayer/codecs.conf: Can't open '/home/christopher/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: 'dvd://1' '-v' '-dumpstream' '-dumpfile' 'title.vob'
init_freetype
get_path('font/font.desc') -> '/home/christopher/.mplayer/font/font.desc'
font: can't open file: /home/christopher/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
get_path('input.conf') -> '/home/christopher/.mplayer/input.conf'
Can't open input config file /home/christopher/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 67 binds
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('1.conf') -> '/home/christopher/.mplayer/1.conf'

Playing dvd://1.
get_path('sub/') -> '/home/christopher/.mplayer/sub/'
URL: dvd://1
Reading disc structure, please wait...
There are 11 titles on this DVD.
There are 2 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: dts (5.1) language: en aid: 137.
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: es
subtitle ( sid ): 2 language: fr
number of subtitles on disk: 3
DVD start cell: 0  pack: 0x0-0x2896  
DVD start=0 end=3796827  
STREAM: [null] dvd://1
STREAM: Description: DVD stream
STREAM: Author: 
STREAM: Comment: 
DVD Seek! lba=0x0  cell=0  packs: 0x0-0x2896  
[B]Angle-seek synced by cell/vob IDN search!  
Cannot open dump file.
vo: x11 uninit called but X11 not inited..

Exiting... (Fatal error)
```[/B]

---

### Post by hyper_ch on 2007-07-01
How can I rip it from an .iso?

I tried to mount the iso at /media/cdrom0 but mplayer refers to dvd:// which is /dev/dvd... I tried to change it to:

```

mplayer /media/cdrom0/1 -v dumpstream -dumpfile title.vob

```

But that didn't work either.

I have it already solved thx to Jester45 in #xubuntu

```

mplayer -dvd-device /media/cdrom0 dvd://1 -v -dumpstream -dumpfile title.vob

```

---

### Post by justforgarbage on 2007-07-18
> **HIGHLIFE said:**
> Hey when I encode the video with x264 it becomes slower than the original, which also causes the a/v to be out of sync and the movie about 20 minutes longer.  Any Ideas?

I have exactly same problem.
I know it can be fixed by using -fps option, but are there no other ways?

---

### Post by balance07 on 2007-07-18
@justforgarbage:

are you using the -ofps option in mencoder? and the -fps option in MP4Box?

see post #38 in this thread for an example.

---

### Post by DasCrushinator on 2007-07-20
> **balance07 said:**
> ok let's see how much i can post here... most of this is modified from the script that 'the ev' made. here's my system (NTSC DVDs) that i think works pretty well.

ripdvd.sh:
```

#!/bin/bash

echo "Put DVD in the top drive."
read NOTHING

echo "Name of the DVD?"
read NAME

mkdir ~/Desktop/$NAME
cd ~/Desktop/$NAME

cp ~/videoencode.sh ~/Desktop/$NAME/
cp ~/videopackage.sh ~/Desktop/$NAME/

echo "Ripping DVD..."

mplayer dvd://1 -v -dumpstream -dumpfile title.vob

echo "Determine Scale Value - note 'VO: [xv] 720x480 => 854x480 Planar YV12' for calculating scale!"

mplayer title.vob

echo "Starting Crop detection - copy <-vf crop=*:*:*:*> for editing videoencode.sh!"

mplayer title.vob -vf cropdetect

echo "Starting GEdit to modify video encoding settings. Close the window when done."

gedit videoencode.sh

echo "Starting GEdit to modify video packaging settings. Close the window when done."

gedit videopackage.sh

echo "Extracting chapter information..."

dvdxchap /dev/dvd > chapters.txt

echo "Extracting Audio..."

mplayer title.vob -ao pcm:file=audio.wav -vc dummy -aid 128 -vo null

echo "Normalizing Audio..."

normalize-audio audio.wav

echo "Encoding Audio..."

oggenc -q5 audio.wav

echo "Encoding Video..."

sh videoencode.sh

echo "Packaging Video..."

sh videopackage.sh

echo "All done!!"

```

videoencode.sh:
```

#!/bin/bash

# First pass

mencoder -v\
	title.vob\
	-ofps 24000/1001\
	-sws 9\
	-vf crop=656:464:30:8,pullup,softskip,harddup,scale=784:464\
	-ovc x264 -x264encopts subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1100\
	-oac copy\
	-of rawvideo\
	-o pass1.264

# Second pass

mencoder -v\
	title.vob\
	-ofps 24000/1001\
	-sws 9\
	-vf crop=656:464:30:8,pullup,softskip,harddup,scale=784:464\
	-ovc x264 -x264encopts subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1100\
	-oac copy\
	-of rawvideo\
	-o pass2.264

```

videopackage.sh:
```

#!/bin/bash

MP4Box -add pass2.264 -fps 23.976023976 video.mp4

echo "Packaging Movie..."

mkvmerge -o COMPLETE.mkv --chapters chapters.txt --display-dimensions 1:784x464 video.mp4 audio.ogg

```

please give me comments on this if you have any. and to anyone struggling, i hope it helps!

I am using these scripts and they solved some problems for me and automates almost the entire process for me (thank you!), but I appear to be having problems with video that is 4:3 (I haven't tried anything widescreen or a different ratio than this...YET), but the video comes out slightly shorter (but the same height).  I find this especially strange because I have narrowed down that it is happening sometime between video.mp4 and COMPLETE.MKV which I guess means it is happening with mkvmerge.  So then I tried to add an aspect ratio line into it to try and force it to 4:3.  Still no go.  Anyone know what might be causing this?  Thanks in advance!

Edit: I also wanted to add that I am modifying the 'vf crop' and 'scale=' lines in videoencode.sh and '--display-dimensions' in videopackage.sh.

Thanks again!

Edit 2: Just to clarify, it appears that the entire picture is still in the file, just the height of the video is smaller therefore giving the whole picture a stretched look.

---

### Post by Azakus on 2007-07-20
In that script where has 656x464, that is not 4:3. 656x492 is 4:3. That would explain the "stretched" look you complained about. And the last script has a different aspect ratio than the script before it. Honestly, you can avoid all that by just not using that --display-dimensions option in mkvmerge. I just always use -vf scale=720:-3 because it automatically keeps the aspect ratio of the movie whether 16:9, 4:3, or anything. (-3 automatically calculates the height that keeps the aspect ratio)

---

### Post by DasCrushinator on 2007-07-20
> **Azakus said:**
> In that script where has 656x464, that is not 4:3. 656x492 is 4:3. That would explain the "stretched" look you complained about. And the last script has a different aspect ratio than the script before it. Honestly, you can avoid all that by just not using that --display-dimensions option in mkvmerge. I just always use -vf scale=720:-3 because it automatically keeps the aspect ratio of the movie whether 16:9, 4:3, or anything. (-3 automatically calculates the height that keeps the aspect ratio)

Alright, I will try that.  Like I said though, I was modifying the lines to fit whatever I got as a -vf line when the file was played in MPlayer.

Do you just use 720:-3?  Or do you just use those two values and whatever the trailing values are as well (e.g. 720:-3:0:10)?

---

### Post by justforgarbage on 2007-07-21
> **balance07 said:**
> @justforgarbage:
are you using the -ofps option in mencoder? and the -fps option in MP4Box?


I'm using (and don't have any problems with the result), but that is what I don't like, e.g. there is information about fps in video mencoder reads, so why should I specify it myself?

I thought about making mencoder write directly to MP4 (supposedly preserving fps info) but found that MP4 support in mencoder is pretty broken.

---

### Post by Azakus on 2007-07-21
> **justforgarbage said:**
> I'm using (and don't have any problems with the result), but that is what I don't like, e.g. there is information about fps in video mencoder reads, so why should I specify it myself?

I thought about making mencoder write directly to MP4 (supposedly preserving fps info) but found that MP4 support in mencoder is pretty broken.

You have to specify the fps in MP4Box at least because it is set to default to 25 fps unless told otherwise. You don't really have to do anything with mencoder, but you can't always be sure that the fps of the movie you are ripping is 24000/1001, 30000/1001, or 25 unless you specify it yourself. (First two are NTSC standards ~23.97 and ~29.97, last one is PAL).

---

### Post by sebas.rhcp on 2007-07-28
Can't start 2nd pass... pls help Kubuntu Feisty

```
Audio stream:  192.000 kbit/s  (24000 B/s)  size: 6534144 bytes  272.256 secs
Uninit audio filters...
[libaf] Removing filter dummy
Uninit audio: liba52
Uninit video: libmpeg2
x264 [info]: slice I:128   Avg QP:35.24  size: 12326  PSNR Mean Y:32.16 U:98.15
V:99.18 Avg:33.92 Global:33.23
x264 [info]: slice P:5736  Avg QP:37.57  size:  4729  PSNR Mean Y:30.97 U:95.64
V:98.35 Avg:32.73 Global:32.08
x264 [info]: slice B:2293  Avg QP:38.77  size:  1594  PSNR Mean Y:30.84 U:92.21
V:96.91 Avg:32.60 Global:31.38
x264 [info]: mb I  I16..4: 62.5%  0.0% 37.5%
x264 [info]: mb P  I16..4: 25.2%  0.0% 10.6%  P16..4: 15.9%  5.6%  0.9%  0.0%  0
.0%    skip:41.9%
x264 [info]: mb B  I16..4:  1.6%  0.0%  1.5%  B16..8: 13.9%  0.0%  0.0%  direct:
 4.5%  skip:78.5%
x264 [info]: final ratefactor: 32.06
x264 [info]: PSNR Mean Y:30.956 U:94.715 V:97.959 Avg:32.711 Global:31.889 kb/s:
951.07
MEncoder 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz (Family: 6, Model: 15, Step
ping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option x264encopts: Unknown suboption 4x4mv
init_freetype
get_path('font/font.desc') -> '/home/sebastian/.mplayer/font/font.desc'
font: can't open file: /home/sebastian/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
[file] File size is 221341696 bytes
STREAM: [file] title.vob
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
success: format: 0  data: 0x0 - 0xd316800
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename title.vob ext: .vob
Trying demuxer 2 based on filename extension
system stream synced at 0xD (13)!
==> Found video stream: 0
==> Found audio stream: 129
==> Found audio stream: 128
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)
MPEG-PS file format detected.
Searching for sequence header... OK!
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  7500.0 kbps (937.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
Using SSE optimized IMDCT transform
AC3: 2.0 (stereo)  48000 Hz  192.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0x2
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [crop w=704 h=480 x=10 y=0]
Crop: 704 x 480, 10 ; 0
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=24000 sample-1                                                                            )
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (720x480->720x540,flags=0,'MPlayer',0x32315659)
SwScaler: using unscaled yuv420p -> yuv420p special converter
REQ: flags=0x403  req=0x0
REQ: flags=0x403  req=0x400
REQ: flags=0x403  req=0x0
REQ: flags=0x3  req=0x0
FATAL: Cannot initialize video driver.
```

---

### Post by justforgarbage on 2007-07-29
> **sebas.rhcp said:**
> Can't start 2nd pass... pls help Kubuntu Feisty

```

Option x264encopts: Unknown suboption 4x4mv
FATAL: Cannot initialize video driver.
```

Remove ":4x4mv" from -x264encopts.
This option is substituted by "particles=" option in newer versions of x264, AFAIU.

---

### Post by bdonkey on 2007-08-01
When I start encoding to x264, mencoder keeps skipping frames every few seconds. In the output file, these skips are pretty annoying.

I've tried some solutions I searched for, such as adding -mc 0, using softskip, using -ofps 24000/1001, but none of it helped.

Is there something I'm missing? mplayer tells me that it's progressive 24.976 fps video, so the 24000/1001 should be right. In fact, the only reason that I'm using the -ofps argument is because mencoder assumes 30 fps instead, and it screws up the output severely.

Anybody else having the same problem?

Thanks in advance.

---

### Post by hyper_ch on 2007-08-01
I now also have a problem... based on the code given here i have written myself a script, ripped of single eps from my fav. tv show as .vob to my harddisk to convert them to matroska so that can put all on my notebook.

This is the script
```

#!/bin/bash -x

for EP in $(cat list.txt);

do

	# Umount existing image
	umount /media/cdrom0;

	# Mount image
	mount -t iso9660 -o loop /media/hda1/B5/$EP.iso /media/cdrom0;

	# Rip files
	nice -n20 mplayer -dvd-device /media/cdrom0 dvd://1 -v -dumpstream -dumpfile $EP.vob;
	nice -n20 mencoder -dvd-device /media/cdrom0 dvd://1 \
		-nosound -ovc frameno -o /dev/null -slang en -vobsubout $EP.en;
	nice -n20 mencoder -dvd-device /media/cdrom0 dvd://1 \
		-nosound -ovc frameno -o /dev/null -slang de -vobsubout $EP.de;


	echo "nice -n20 mplayer $EP.vob -ao pcm:file=$EP.wav -vc dummy -aid 128 -vo null";
	nice -n20 mplayer $EP.vob -ao pcm:fast:file=$EP.wav -vc dummy -aid 128 -vo null;



	nice -n20 normalize-audio $EP.wav;
	nice -n20 oggenc -q5 $EP.wav;


	# First pass
	nice -n20 \
		mencoder -v $EP.vob \
		-vf harddup \
		-ovc x264 \
		-x264encopts subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000 \
		-oac copy \
		-of rawvideo \
		-o $EP.264;

	# Second pass
	nice -n20 \
		mencoder -v $EP.vob \
		-vf harddup \
		-ovc x264 \
		-x264encopts subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000 \
		-oac copy \
		-of rawvideo \
		-o $EP.264;
	
	nice -n20 MP4Box -add $EP.264 $EP.mp4;

	rm $EP.vob;
	rm $EP.wav;
	rm title.264;

	chown hyper.hyper *;

      	echo "$EP done";

done

```
It works fine until the 2nd pass.

For the second pass I get this output here:
```

MEncoder 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm)   2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
init_freetype
get_path('font/font.desc') -> '/home/hyper/.mplayer/font/font.desc'
font: can't open file: /home/hyper/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
[file] File size is 1719713792 bytes
STREAM: [file] S02E01.vob
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
success: format: 0  data: 0x0 - 0x6680c000
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename S02E01.vob ext: .vob
Trying demuxer 2 based on filename extension
system stream synced at 0xD (13)!
==> Found video stream: 0
==> Found audio stream: 128
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG-PS file format detected.
Searching for sequence header... OK!
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x576  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
AC3: 5.1 (3f+2r+lfe)  48000 Hz  384.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0xA
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Trying filter chain: harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale harddup expand x264
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=48000 sample-1)
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (720x576->1024x576,flags=0,'MPlayer',0x32315659)
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x0  
REQ: flags=0x3  req=0x0  

Exiting...

```
I can't really say which of that is still the second pass and which of that is the "nice -n20 MP4Box -add $EP.264 $EP.mp4;"-conversion.

However the second pass will render the .264 to a size of 0 bytes! Before the second pass the .264 file is about 315MB.

I really don't know what's wrong with the second pass there. anyone can help?

Addon: The .vob files work great and also does the .246 file play nicely after the first pass in VLC.

---

### Post by Azakus on 2007-08-01
This line is the problem:
```
-x264encopts subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000 \
```
4x4mv has been renamed in the newer versions of mencoder.
Replace it with partitions=all

---

### Post by hyper_ch on 2007-08-01
I have now replaced that part with what you have suggested:

```

-x264encopts subq=6:partitions=all:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000 \

```

This returns:

```

MEncoder 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm)   2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
init_freetype
get_path('font/font.desc') -> '/home/hyper/.mplayer/font/font.desc'
font: can't open file: /home/hyper/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
[file] File size is 1719713792 bytes
STREAM: [file] S02E01.vob
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
success: format: 0  data: 0x0 - 0x6680c000
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename S02E01.vob ext: .vob
Trying demuxer 2 based on filename extension
system stream synced at 0xD (13)!
==> Found video stream: 0
==> Found audio stream: 128
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG-PS file format detected.
Searching for sequence header... OK!
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x576  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
AC3: 5.1 (3f+2r+lfe)  48000 Hz  384.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0xA
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Trying filter chain: harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale harddup expand x264
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=48000 sample-1)
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (720x576->1024x576,flags=0,'MPlayer',0x32315659)
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x0  
REQ: flags=0x3  req=0x0  

Exiting...

```

resp.:
```

Option x264encopts: Bad argument me=3
Using SSE optimized IMDCT transform
Using MMX optimized resampler
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
SwScaler: using unscaled yuv420p -> yuv420p special converter
FATAL: Cannot initialize video driver.

```

---

### Post by hyper_ch on 2007-08-07
Hiho

sorry for the late reply but I have it now finally:

```

#!/bin/bash -x

for EP in $(cat list.txt);

do

        # Umount existing image
        umount /media/cdrom0;

        # Mount image
        mount -t iso9660 -o loop /media/hda1/B5/$EP.iso /media/cdrom0;

        # Rip files
        nice -n20 mplayer -dvd-device /media/cdrom0 dvd://1 -v -dumpstream -dumpfile $EP.vob;
        nice -n20 mencoder -dvd-device /media/cdrom0 dvd://1 \
                -nosound -ovc frameno -o /dev/null -slang en -vobsubout $EP.en;
        nice -n20 mencoder -dvd-device /media/cdrom0 dvd://1 \
                -nosound -ovc frameno -o /dev/null -slang de -vobsubout $EP.de;

        echo "nice -n20 mplayer $EP.vob -ao pcm:file=$EP.wav -vc dummy -aid 128 -vo null";
        nice -n20 mplayer $EP.vob -ao pcm:fast:file=$EP.wav -vc dummy -aid 128 -vo null;

        nice -n20 normalize-audio $EP.wav;
        nice -n20 oggenc -q5 $EP.wav;


        # First pass
        nice -n20 \
                mencoder -v $EP.vob \
                -vf harddup \
                -ovc x264 \
                -x264encopts subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000 \
                -oac copy \
                -of rawvideo \
                -o $EP.264;

        # Second pass
        nice -n20 \
                mencoder -v $EP.vob \
                -vf harddup \
                -ovc x264 \
                -x264encopts subq=6:partitions=all:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000 \
                -oac copy \
                -of rawvideo \
                -o $EP.264;

        nice -n20 MP4Box -add $EP.264 $EP.mp4;

        # Put it in matroska container
        nice -n20 \
                mkvmerge \
                -o $EP.mkv \
                -d 1 -A \
                -S $EP.mp4 \
                -a 0 -D -S $EP.ogg \
                --language 0:eng -s 0 -D -A $EP.en.idx \
                --language 0:ger -s 0 -D -A $EP.de.idx \
                --track-order 0:1,1:0,2:0,3:0;

        # Delete unused files
        rm $EP.vob;
        rm $EP.wav;
        rm $EP.264;
        rm $EP.en.idx;
        rm $EP.en.sub;
        rm $EP.de.idx;
        rm $EP.de.sub;
        rm $EP.mp4;
        rm $EP.ogg;
        rm divx2pass.log;

        chown hyper.hyper *;

        echo "$EP done";

done

```

That just works fine - I only need a faster cpu ;)

Anyway, this little script will convert ISO contained in a text list into matroska... the ISOs I use are cleanly ripped (no black borders), contain only one audio stream and in my case two subtitles... so for you, little alterations must be made :)

---

### Post by Azakus on 2007-08-08
> **hyper_ch said:**
> I have now replaced that part with what you have suggested:

```

-x264encopts subq=6:partitions=all:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000 \

```

This returns:

```

MEncoder 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm)   2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
init_freetype
get_path('font/font.desc') -> '/home/hyper/.mplayer/font/font.desc'
font: can't open file: /home/hyper/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
[file] File size is 1719713792 bytes
STREAM: [file] S02E01.vob
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
success: format: 0  data: 0x0 - 0x6680c000
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename S02E01.vob ext: .vob
Trying demuxer 2 based on filename extension
system stream synced at 0xD (13)!
==> Found video stream: 0
==> Found audio stream: 128
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG-PS file format detected.
Searching for sequence header... OK!
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x576  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
AC3: 5.1 (3f+2r+lfe)  48000 Hz  384.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0xA
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Trying filter chain: harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale harddup expand x264
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=48000 sample-1)
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (720x576->1024x576,flags=0,'MPlayer',0x32315659)
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x0  
REQ: flags=0x3  req=0x0  

Exiting...

```

resp.:
```

Option x264encopts: Bad argument me=3
Using SSE optimized IMDCT transform
Using MMX optimized resampler
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
SwScaler: using unscaled yuv420p -> yuv420p special converter
FATAL: Cannot initialize video driver.

```
Whoops, I forgot. Replace me=3 with me=umh as well.

---

### Post by IronLike Monkey on 2007-08-11
has anyone seen this?
When I run [I]$ MP4Box -add pass2.264 -fps 23.976 test.mp4
[/I]
I get this output:
[I]
Adjusting AVC SizeLength to 16 bits
AVC-H264 import - frame size 512 x 384 at 23.9760 FPS
Adjusting AVC SizeLength to 24 bits02/100)
MP4Box: media_tools/media_import.c:3716: gf_import_h264: Assertion `nal_start' failed.
Aborted (core dumped)
[/I]

---

### Post by xanas3712 on 2007-08-13
Ugh, desync not fixing no matter what I do, here's line from my script
```

 mencoder $2 -vf pullup,softskip,harddup$8 -nosound -ofps 24000/1001 -ovc x264 -x264encopts qp=$6:subq=6:bframes=4:8x8dct:frameref=5:partitions=all:b_pyramid:weight_b:threads=3 -of rawvideo -o $3;

```

I just plug in qp18 and $8 I use to add the crop filter

rather than using mp4box I'm using mp4creator (shouldn't be a difference) 
mp4creator -c movie.264 -rate 23.976023976 movie.mp4

Only way I know how to somewhat resolve is just play around with stretching/etc.

BTW this is a video with mixed 24k/1001 & 30k/1001 video (anime - melancholy of haruhi suzumiya), but according to mencoder docs pullup should be safe on pretty much anything, the mixed content would tend to signal that it's telecined or somesuch to me.  I thought maybe the -ofps suggested here setting a common framerate would help but nope, not at all.

It's annoying because for some reason the video ends up being 5896.5 seconds long, while audio is only 5588.2 seconds long, and I'd think stretching the audio by 5896.5/5588.2 in mmg would fix this but instead that doesn't work, and I have to play with it more than that to get a value that works.. but of course I have no logic for it and pretty much just keep playing around till I'm happy with it.

But there's no way for me to script the ending merge if I can't get something that works on every video!!!

It's frustrating..

Hmm.. ok -oac copy, didn't notice that was different here, I'm not sure how that should help sync or why that should work.. but will try it.
EDIT: seems to have worked

---

### Post by DasCrushinator on 2007-08-20
> **hyper_ch said:**
> Hiho

sorry for the late reply but I have it now finally:

```

#!/bin/bash -x

for EP in $(cat list.txt);

do

        # Umount existing image
        umount /media/cdrom0;

        # Mount image
        mount -t iso9660 -o loop /media/hda1/B5/$EP.iso /media/cdrom0;

        # Rip files
        nice -n20 mplayer -dvd-device /media/cdrom0 dvd://1 -v -dumpstream -dumpfile $EP.vob;
        nice -n20 mencoder -dvd-device /media/cdrom0 dvd://1 \
                -nosound -ovc frameno -o /dev/null -slang en -vobsubout $EP.en;
        nice -n20 mencoder -dvd-device /media/cdrom0 dvd://1 \
                -nosound -ovc frameno -o /dev/null -slang de -vobsubout $EP.de;

        echo "nice -n20 mplayer $EP.vob -ao pcm:file=$EP.wav -vc dummy -aid 128 -vo null";
        nice -n20 mplayer $EP.vob -ao pcm:fast:file=$EP.wav -vc dummy -aid 128 -vo null;

        nice -n20 normalize-audio $EP.wav;
        nice -n20 oggenc -q5 $EP.wav;


        # First pass
        nice -n20 \
                mencoder -v $EP.vob \
                -vf harddup \
                -ovc x264 \
                -x264encopts subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000 \
                -oac copy \
                -of rawvideo \
                -o $EP.264;

        # Second pass
        nice -n20 \
                mencoder -v $EP.vob \
                -vf harddup \
                -ovc x264 \
                -x264encopts subq=6:partitions=all:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000 \
                -oac copy \
                -of rawvideo \
                -o $EP.264;

        nice -n20 MP4Box -add $EP.264 $EP.mp4;

        # Put it in matroska container
        nice -n20 \
                mkvmerge \
                -o $EP.mkv \
                -d 1 -A \
                -S $EP.mp4 \
                -a 0 -D -S $EP.ogg \
                --language 0:eng -s 0 -D -A $EP.en.idx \
                --language 0:ger -s 0 -D -A $EP.de.idx \
                --track-order 0:1,1:0,2:0,3:0;

        # Delete unused files
        rm $EP.vob;
        rm $EP.wav;
        rm $EP.264;
        rm $EP.en.idx;
        rm $EP.en.sub;
        rm $EP.de.idx;
        rm $EP.de.sub;
        rm $EP.mp4;
        rm $EP.ogg;
        rm divx2pass.log;

        chown hyper.hyper *;

        echo "$EP done";

done

```

That just works fine - I only need a faster cpu ;)

Anyway, this little script will convert ISO contained in a text list into matroska... the ISOs I use are cleanly ripped (no black borders), contain only one audio stream and in my case two subtitles... so for you, little alterations must be made :)

What is the syntax for this script?  Do i just run it as whatever I call the script, or does it require me to enter the episode number as well (e.g.: 'sh rip.sh 1')?

Also, I get an error asking for a file called list.txt?

Exact error message is 'cat: list.txt: No such file or directory'

---

### Post by hyper_ch on 2007-08-20
It's a bash script...

Well, the list.txt just contains the single episodes that I have ripped to an ISO file each... it will loop through the list...

So the script must run as root to actually be ablet o mount the .ISOs

This part here is the loop:

```

for EP in $(cat list.txt);

do

...
...
...

done

```

and this part here is the ISO mount
```

        # Umount existing image
        umount /media/cdrom0;

        # Mount image
        mount -t iso9660 -o loop /media/hda1/B5/$EP.iso /media/cdrom0;

```

The actual conversion is everything in it...

My current list.txt looks ilke this:
```

S03E01
S03E02
S03E03
S03E04
S03E05
S03E06
S03E07
S03E08
S03E09
S03E10
S03E11
S03E12
S03E13
S03E14
S03E15
S03E16
S03E17
S03E18
S03E19
S03E20
S03E21
S03E22


```
(Note: There is a empty line at the end of the file)

---

### Post by DasCrushinator on 2007-08-27
Anyone know what could be causing the lines around the guy in the foreground?

[http://img209.imageshack.us/img209/5362/screenshotun6.png](http://img209.imageshack.us/img209/5362/screenshotun6.png)

And for that matter, does anyone know how to fix it?

Here is the script used to create this video file:

```

#!/bin/bash

echo "Title:"
read NAME

echo "Video Stream:"
read STREAM1

echo "Audio Stream:"
read STREAM2

mkdir ~/Desktop/$NAME
cd ~/Desktop/$NAME

echo "Ripping Title..."

nice -n20 mplayer dvd://$STREAM1 -v -dumpstream -dumpfile $NAME.vob

echo "Extracting Audio..."

nice -n20 mplayer $NAME.vob -ao pcm:file=$NAME.wav -vc dummy -aid $STREAM2 -vo null

echo "Normalizing Audio..."

nice -n20 normalize-audio $NAME.wav

echo "Encoding Audio..."

nice -n20 oggenc -q5 $NAME.wav

echo "Encoding Video..."

# First pass

       nice -n20 \
	mencoder -v $NAME.vob\
	-ofps 24000/1001\
	-sws 9\
	-vf scale=1440:-3\
	-ovc x264 -x264encopts subq=4:bframes=3:b_pyramid:weight_b:threads=auto:turbo=1:pass=1:psnr:bitrate=1000\
	-oac copy\
	-of rawvideo\
	-o pass1.264

# Second pass

       nice -n20 \
	mencoder -v $NAME.vob\
	-ofps 24000/1001\
	-sws 9\
	-vf scale=1440:-3\
	-ovc x264 -x264encopts subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:threads=auto:pass=2:psnr:bitrate=1000\
	-oac copy\
	-of rawvideo\
	-o pass2.264

echo "Packaging Video..."

nice -n20 MP4Box -add pass2.264 -fps 23.976023976 $NAME.mp4

echo "Packaging Movie..."

nice -n20 mkvmerge -o $NAME.mkv $NAME.mp4 $NAME.ogg

nice -n20 mv $NAME.mkv /media/Video/

echo "All done!!"

```

---

### Post by HoverHell on 2007-08-28
> **DasCrushinator said:**
> Anyone know what could be causing the lines around the guy in the foreground?


It's the matter of deinterlacing/detelecining.
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html)

* By the way, all (or almost all) of software DVD players (non-free ones) don't use detelecining, only deinterlacing (and, sometimes, very bad one).
* You can find more on interlacing at 100fps.com

---

### Post by DasCrushinator on 2007-08-28
> **HoverHell said:**
> It's the matter of deinterlacing/detelecining.
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html)

* By the way, all (or almost all) of software DVD players (non-free ones) don't use detelecining, only deinterlacing (and, sometimes, very bad one).
* You can find more on interlacing at 100fps.com

Alright, good to know.  I am re-ripping/encoding the episode again with some different options.  I'll report back to see if this fixes my problems.

Thanks!

---

### Post by IronLike Monkey on 2007-09-08
This thread has been a great help!  I do have a new problem that I haven't sorted out yet. When ripping subtitles, and their are multiple subtitles in the same language, how do I rip the others?  For example, when I check to see the available subtitles I get this:

~$ mplayer dvd:// -v -vo null -ao null | grep "subtitle"
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: en
subtitle ( sid ): 2 language: es
subtitle ( sid ): 3 language: fr
subtitle ( sid ): 4 language: en
subtitle ( sid ): 5 language: en
subtitle ( sid ): 6 language: en
number of subtitles on disk: 7


How do I rip SID 1?  When I do the normal slang en option, I always get SID 0.  I tried changing the stream option but that didn't help either. Any suggestions?

---

### Post by hyper_ch on 2007-09-08
I haven't encountered that problem... I first rip the dvd to an iso file using only the selected things (audio/subs) and then I batch convert them... so I don't even have to care about the black boxes around as the movie....

---

### Post by marko_4454 on 2007-09-15
I still have another question....
Is there any way of ripping more than 1 subtitles WITHOUT having to rip the movie more than once? 
If someone knows the answer, can you post here? 
Thanks

---

### Post by hyper_ch on 2007-09-15
marko:

Have a look at my script, that does it.

---

### Post by DasCrushinator on 2007-09-15
> **hyper_ch said:**
> I haven't encountered that problem... I first rip the dvd to an iso file using only the selected things (audio/subs) and then I batch convert them... so I don't even have to care about the black boxes around as the movie....

That reminds me, how do you do that (rip the ISOs without the black boxes)?

---

### Post by marko_4454 on 2007-09-15
> **hyper_ch said:**
> marko:

Have a look at my script, that does it.

hyper,
I dont think it does what I want. 
What I mean is that I have only one movie, and want to rip a title in it (#1 most of the time). This title has subtitles of English, Spanish and French. I want to get 1 movie file (avi or whatever) but 3 subtitle files (.vob? right?).
If it can do that, could you tell me more about it? 
Thanks

---

### Post by hyper_ch on 2007-09-16
DasCrushinator: I use DVDShrink
marko_4454: Look at my script... I first rip the video, the sound and then the subtitles (.idx and .sub)...

---

### Post by DasCrushinator on 2007-09-18
Alright, I have a working script that works fine for material which does not need to be cropped; however I was wanting to take it one step further and make cropping automated so I could do widescreen movies.

I did a search on the internet that gave me a bunch of ideas for how to do it (namely: [http://presbrey.mit.edu/DVD_Backups](http://presbrey.mit.edu/DVD_Backups) [http://www.smlug.org/wiki/index.php/DVD_Encoding](http://www.smlug.org/wiki/index.php/DVD_Encoding) and [http://www.paehl.com/forum/index.php?topic=90.0](http://www.paehl.com/forum/index.php?topic=90.0) ).  However this is not working because I get a picture that is either starting at the wrong point and/or not capturing the entire video.

I did not implement this in my script yet, so that could not be the problem.  Here it what I am doing:

```

mplayer dvd://1 -vf cropdetect

```
The line above tells me the supposed area for the correct cropping points

```

mplayer dvd://1 -vf crop=xxx:xxx:xx:xx

```
I enter the values where the Xs are above and all I get is either the video being cropped too high (resulting in a black bar in the first 1/3 of the video), too short (resulting in the video not showing the entire horizontal area of the movie), or a combination of the two.

I have tried this with two different movies and have even tried taking the exact code from some of the above websites to see if it works.

All to which give the me the same incorrect values.

Does anyone know why this is happening?

---

### Post by Azakus on 2007-09-19
> **DasCrushinator said:**
> Alright, I have a working script that works fine for material which does not need to be cropped; however I was wanting to take it one step further and make cropping automated so I could do widescreen movies.

I did a search on the internet that gave me a bunch of ideas for how to do it (namely: [http://presbrey.mit.edu/DVD_Backups](http://presbrey.mit.edu/DVD_Backups) [http://www.smlug.org/wiki/index.php/DVD_Encoding](http://www.smlug.org/wiki/index.php/DVD_Encoding) and [http://www.paehl.com/forum/index.php?topic=90.0](http://www.paehl.com/forum/index.php?topic=90.0) ).  However this is not working because I get a picture that is either starting at the wrong point and/or not capturing the entire video.

I did not implement this in my script yet, so that could not be the problem.  Here it what I am doing:

```

mplayer dvd://1 -vf cropdetect

```
The line above tells me the supposed area for the correct cropping points

```

mplayer dvd://1 -vf crop=xxx:xxx:xx:xx

```
I enter the values where the Xs are above and all I get is either the video being cropped too high (resulting in a black bar in the first 1/3 of the video), too short (resulting in the video not showing the entire horizontal area of the movie), or a combination of the two.

I have tried this with two different movies and have even tried taking the exact code from some of the above websites to see if it works.

All to which give the me the same incorrect values.

Does anyone know why this is happening?

Honestly, I don't even bother with crop detection. I just use scaling and I never have any black bars, nor scaling issues. The trick is to use -vf scale=720:-3, where (-3) tells mplayer to keep the aspect ratio in the height (16:9, 4:3, 16:10, etc).

---

### Post by DasCrushinator on 2007-09-19
> **Azakus said:**
> Honestly, I don't even bother with crop detection. I just use scaling and I never have any black bars, nor scaling issues. The trick is to use -vf scale=720:-3, where (-3) tells mplayer to keep the aspect ratio in the height (16:9, 4:3, 16:10, etc).

Interesting, I have that setup in my script already, but hadn't tried it.  I'll report back to see if that "just works."

Thanks!

Edit: That doesn't seem to work for me.  The script as of right now.

```
#!/bin/bash -x
for EP in $(cat ~/.list);
do
mkdir ~/Desktop/$EP;
cd ~/Desktop/$EP;
mplayer dvd://$EP -v -dumpstream -dumpfile $EP.vob;
mplayer $EP.vob -ao pcm:file=$EP.wav -vc dummy -aid 128 -vo null;
normalize-audio $EP.wav;
faac $EP.wav -w -q 100;
mencoder -v\
	$EP.vob\
	-ofps 24000/1001\
	-sws 9\
	-vf pullup,softskip,scale=720:-3,harddup\
	-ovc x264 -x264encopts subq=4:bframes=3:b_pyramid:weight_b:threads=auto:turbo=1:pass=1:psnr:bitrate=1000\
	-oac copy\
	-of rawvideo\
	-o pass1.264;
mencoder -v\
	$EP.vob\
	-ofps 24000/1001\
	-sws 9\
	-vf pullup,softskip,scale=720:-3,harddup\
	-ovc x264 -x264encopts subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:threads=auto:pass=2:psnr:bitrate=1000\
	-oac copy\
	-of rawvideo\
	-o pass2.264;
MP4Box -add pass2.264 -add $EP.m4a -fps 23.976023976 $EP.mp4;
mv ~/Desktop/$EP/$EP.mp4 /media/Video/$EP.mp4;
rm -r ~/Desktop/$EP/;
done
```

---

### Post by Azakus on 2007-09-20
Your script is actually almost exactly the same as mine. Did you also copy from the Gentoo script? I actually put scale first in -vf, as in -vf scale=720:-3,pullup,softskip,harddup. I don't use the -sws option though. I can't say if that may be doing it (probably not), but you could try a dry run with a few minutes of video and removing (or commenting out) the -sws option.

---

### Post by DasCrushinator on 2007-09-20
> **Azakus said:**
> Your script is actually almost exactly the same as mine. Did you also copy from the Gentoo script? I actually put scale first in -vf, as in -vf scale=720:-3,pullup,softskip,harddup. I don't use the -sws option though. I can't say if that may be doing it (probably not), but you could try a dry run with a few minutes of video and removing (or commenting out) the -sws option.

Strange, I put scale at the front of the -vf options and completely removed the -sws option, and still the same result.  Would you mind posting your most current script?

Edit: Are you sure that the DVDs you ripped had black bars?  I have the first season of a TV show that is widescreen, but the black bars weren't encoded into the video.  However, I do have movies that have the black bars encoded into the DVD.

Edit 2: Also, are there any disadvantages to encoding video with the black bars in?  I read on MPlayer's site that there is no filesize difference (unless I misread it).  [http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-dvd-mpeg4-resolution-bitrate](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-dvd-mpeg4-resolution-bitrate)

---

### Post by Azakus on 2007-09-20
Sure, here's my script. I added a few lines to automate the ripping of subtitles if I want them.
```

#!/bin/bash 
#Usage: dvdrip <MovieName>
sudo aptitude install mplayer mencoder mkvtoolnix vorbis-tools ogmtools
MOVIE=$1
mkdir ~/$MOVIE
cd ~/$MOVIE
dvdxchap -t 1 /media/cdrom0 >> $MOVIE.chaps.txt
echo "Dumping Video, may take a while"
mplayer dvd://1 -dumpstream -dumpfile $MOVIE.vob
echo "Dumping Audio Stream"
mplayer $MOVIE.vob -ao pcm:file=$MOVIE.wav -vc dummy -aid 128 -vo null
echo -n "Rip english subtitles? [y/n]:"
read SUB
if [ $SUB = "y" ]
then
echo "Dumping English Subtitles"
mencoder $MOVIE.vob -oac copy -ovc frameno -o /dev/null -slang en -vobsubout $MOVIE
fi
echo "Encoding Audio"
normalize-audio $MOVIE.wav
oggenc -q5 $MOVIE.wav
mencoder $MOVIE.vob -ofps 24000/1001 -vf scale=720:-3,pullup,softskip,harddup -oac copy -ovc x264 -x264encopts\
subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000:threads=3 -of rawvideo -o /dev/null
mencoder $MOVIE.vob -ofps 24000/1001 -vf scale=720:-3,pullup,softskip,harddup -oac copy -ovc x264 -x264encopts\ subq=6:partitions=all:me=umh:8x8dct:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000:threads=3 -of rawvideo -o $MOVIE.264
echo "Packaging Movie"
MP4Box -add $MOVIE.264 -fps 23.976023976 $MOVIE.mp4
if [ $SUB = "y" ]
then
mkvmerge -o $MOVIE.mkv $MOVIE.mp4 $MOVIE.ogg --language eng $MOVIE.idx --language eng --chapters $MOVIE.chaps.txt
else
mkvmerge -o $MOVIE.mkv $MOVIE.mp4 --language eng $MOVIE.ogg --chapters $MOVIE.chaps.txt
fi
rm $MOVIE.264
rm $MOVIE.mp4
rm $MOVIE.ogg
rm $MOVIE.wav
rm $MOVIE.idx
rm $MOVIE.chaps.txt
rm $MOVIE.vob
echo "Rip Completed"
gnome-open ~/$MOVIE
```

---

### Post by DasCrushinator on 2007-09-20
> **Azakus said:**
> Sure, here's my script. I added a few lines to automate the ripping of subtitles if I want them.
```

#!/bin/bash 
#Usage: dvdrip <MovieName>
sudo aptitude install mplayer mencoder mkvtoolnix vorbis-tools ogmtools
MOVIE=$1
mkdir ~/$MOVIE
cd ~/$MOVIE
dvdxchap -t 1 /media/cdrom0 >> $MOVIE.chaps.txt
echo "Dumping Video, may take a while"
mplayer dvd://1 -dumpstream -dumpfile $MOVIE.vob
echo "Dumping Audio Stream"
mplayer $MOVIE.vob -ao pcm:file=$MOVIE.wav -vc dummy -aid 128 -vo null
echo -n "Rip english subtitles? [y/n]:"
read SUB
if [ $SUB = "y" ]
then
echo "Dumping English Subtitles"
mencoder $MOVIE.vob -oac copy -ovc frameno -o /dev/null -slang en -vobsubout $MOVIE
fi
echo "Encoding Audio"
normalize-audio $MOVIE.wav
oggenc -q5 $MOVIE.wav
mencoder $MOVIE.vob -ofps 24000/1001 -vf scale=720:-3,pullup,softskip,harddup -oac copy -ovc x264 -x264encopts\
subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000:threads=3 -of rawvideo -o /dev/null
mencoder $MOVIE.vob -ofps 24000/1001 -vf scale=720:-3,pullup,softskip,harddup -oac copy -ovc x264 -x264encopts\ subq=6:partitions=all:me=umh:8x8dct:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000:threads=3 -of rawvideo -o $MOVIE.264
echo "Packaging Movie"
MP4Box -add $MOVIE.264 -fps 23.976023976 $MOVIE.mp4
if [ $SUB = "y" ]
then
mkvmerge -o $MOVIE.mkv $MOVIE.mp4 $MOVIE.ogg --language eng $MOVIE.idx --language eng --chapters $MOVIE.chaps.txt
else
mkvmerge -o $MOVIE.mkv $MOVIE.mp4 --language eng $MOVIE.ogg --chapters $MOVIE.chaps.txt
fi
rm $MOVIE.264
rm $MOVIE.mp4
rm $MOVIE.ogg
rm $MOVIE.wav
rm $MOVIE.idx
rm $MOVIE.chaps.txt
rm $MOVIE.vob
echo "Rip Completed"
gnome-open ~/$MOVIE
```

Odd, got an error when it was parsing the x264 options.

Also, just so no one misses my previous edits:

Azakus: Are you sure that the DVDs you ripped had black bars? I have the first season of a TV show that is widescreen, but the black bars weren't encoded into the video. However, I do have movies that have the black bars encoded into the DVD.

Anyone: Also, are there any disadvantages to encoding video with the black bars in? I read on MPlayer's site that there is no filesize difference (unless I misread it). [http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-dvd-mpeg4-resolution-bitrate](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-dvd-mpeg4-resolution-bitrate)

---

### Post by DasCrushinator on 2007-09-24
What video drivers does everyone have set in their ~/.mplayer/config files?

---

### Post by Azakus on 2007-09-24
I've never ripped a dvd that had black bars in it. I'm not sure, but those black bars may be in the video, as I don't know what DVD you're trying to rip.

---

### Post by Azakus on 2007-09-24
> **DasCrushinator said:**
> What video drivers does everyone have set in their ~/.mplayer/config files?

I don't have anything in there actually.

---

### Post by DasCrushinator on 2007-09-25
> **Azakus said:**
> I've never ripped a dvd that had black bars in it. I'm not sure, but those black bars may be in the video, as I don't know what DVD you're trying to rip.

What I mean to say is, when you put the DVD in the drive of your computer, played it in Mplayer (using the DVD option or mplayer dvd:// in the terminal) did it have black bars?  I have some widescreen things that didn't have the black bars encoded into the DVD and some that do.

What I was asking is, did youjust happen to have DVDs that didn't have black bars encoded while watching the DVD of it (not the file you ripped).

So, basically, if you could take something that you ripped that is widescreen, would you be able to go to a terminal and type "mplayer dvd://"?  Does this video have black bars?  If so, then when you ripped it, did the black bars show up in your file?  O did they not (and yu're just really lucky :()

---

### Post by HoverHell on 2007-09-25
If anyone wonders, my x264 options for ripping anime (mostly got from bencos ([www.detritus.qc.ca](www.detritus.qc.ca))):
pass 1:
```
-x264encopts bitrate=1350:psnr:deblock=1,1:bframes=5:frameref=6:b_pyramid:nofast_pskip:pass=1:turbo=2
```
pass 2: 
```
-x264encopts bitrate=1350:psnr:deblock=1,1:bframes=5:frameref=6:b_pyramid:nofast_pskip:8x8dct:weight_b:mixed_refs:me=umh:bime:partitions=all:subq=7:brdo:trellis=1:pass=2
```

(I prefer quality, not encoding speed, and, somewhat, quality in cost of size (bitrate=1350))
Results are pretty fine (although sources I tried it on not quite good, so I cannot be much sure).

---

### Post by Azakus on 2007-09-25
> **DasCrushinator said:**
> What I mean to say is, when you put the DVD in the drive of your computer, played it in Mplayer (using the DVD option or mplayer dvd:// in the terminal) did it have black bars?  I have some widescreen things that didn't have the black bars encoded into the DVD and some that do.

What I was asking is, did youjust happen to have DVDs that didn't have black bars encoded while watching the DVD of it (not the file you ripped).

So, basically, if you could take something that you ripped that is widescreen, would you be able to go to a terminal and type "mplayer dvd://"?  Does this video have black bars?  If so, then when you ripped it, did the black bars show up in your file?  O did they not (and yu're just really lucky :()

The only time I ever have black bars playing a widescreen dvd is if it's on a 4:3 monitor, and those would be at the tob and bottom. They've never shown up in a file.
EDIT: I found a dvd of mine with extra black bars (possibly hardcoded into video). I'll see if they are when I'm done ripping, but if they are hardcoded, they would show up as being part of the video in -vf cropdetect.

---

### Post by DasCrushinator on 2007-09-25
> **Azakus said:**
> The only time I ever have black bars playing a widescreen dvd is if it's on a 4:3 monitor, and those would be at the tob and bottom. They've never shown up in a file.
EDIT: I found a dvd of mine with extra black bars (possibly hardcoded into video). I'll see if they are when I'm done ripping, but if they are hardcoded, they would show up as being part of the video in -vf cropdetect.

Thank you, Azakus.  Your continued help is much appreciated.

---

### Post by dvdgorila on 2007-09-25
> **Azakus said:**
> Sure, here's my script. I added a few lines to automate the ripping of subtitles if I want them.
```

#!/bin/bash 
#Usage: dvdrip <MovieName>
sudo aptitude install mplayer mencoder mkvtoolnix vorbis-tools ogmtools
MOVIE=$1
mkdir ~/$MOVIE
cd ~/$MOVIE
dvdxchap -t 1 /media/cdrom0 >> $MOVIE.chaps.txt
echo "Dumping Video, may take a while"
mplayer dvd://1 -dumpstream -dumpfile $MOVIE.vob
echo "Dumping Audio Stream"
mplayer $MOVIE.vob -ao pcm:file=$MOVIE.wav -vc dummy -aid 128 -vo null
echo -n "Rip english subtitles? [y/n]:"
read SUB
if [ $SUB = "y" ]
then
echo "Dumping English Subtitles"
mencoder $MOVIE.vob -oac copy -ovc frameno -o /dev/null -slang en -vobsubout $MOVIE
fi
echo "Encoding Audio"
normalize-audio $MOVIE.wav
oggenc -q5 $MOVIE.wav
mencoder $MOVIE.vob -ofps 24000/1001 -vf scale=720:-3,pullup,softskip,harddup -oac copy -ovc x264 -x264encopts\
subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000:threads=3 -of rawvideo -o /dev/null
mencoder $MOVIE.vob -ofps 24000/1001 -vf scale=720:-3,pullup,softskip,harddup -oac copy -ovc x264 -x264encopts\ subq=6:partitions=all:me=umh:8x8dct:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000:threads=3 -of rawvideo -o $MOVIE.264
echo "Packaging Movie"
MP4Box -add $MOVIE.264 -fps 23.976023976 $MOVIE.mp4
if [ $SUB = "y" ]
then
mkvmerge -o $MOVIE.mkv $MOVIE.mp4 $MOVIE.ogg --language eng $MOVIE.idx --language eng --chapters $MOVIE.chaps.txt
else
mkvmerge -o $MOVIE.mkv $MOVIE.mp4 --language eng $MOVIE.ogg --chapters $MOVIE.chaps.txt
fi
rm $MOVIE.264
rm $MOVIE.mp4
rm $MOVIE.ogg
rm $MOVIE.wav
rm $MOVIE.idx
rm $MOVIE.chaps.txt
rm $MOVIE.vob
echo "Rip Completed"
gnome-open ~/$MOVIE
```


I tried using your script and i get an error about mencoder options. any ideas?


```
MEncoder dev-SVN-r24586-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

-x264encoptssubq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000:threads=3 is not an MEncoder option

Exiting... (error parsing command line)
MEncoder dev-SVN-r24586-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

-x264encopts subq=6:partitions=all:me=umh:8x8dct:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000:threads=3 is not an MEncoder option

Exiting... (error parsing command line)
Packaging Movie
 (Requested URL is not valid or cannot be found)Cannot find file matrixreloaded.264
Error importing matrixreloaded.264: Requested URL is not valid or cannot be found
mkvmerge v2.0.0 ('After The Rain Has Fallen') built on Feb  7 2007 18:53:46

Error: The source file 'matrixreloaded.mp4' could not be opened successfully, or retrieving its size by seeking to the end did not work.
rm: cannot remove `matrixreloaded.idx': No such file or directory
Rip Completed

```

---

### Post by Azakus on 2007-09-27
There should be a space between x264encoptssubq=4.
I'm not quite sure why that's happening. 
You are running it from cli right, not just copying and pasting line by line?
That'll happen if you don't just run the script.
Better yet, you could remove the "\"'s after x264ecopts and make sure the whole of the x264encopts are on the same line.

---

### Post by phreeq on 2007-09-27
I hate to jump on the bandwagon, but I am also having a little problem.

Azakus, I got the fix for the missing space in the first run of mencoder, but now there are problems with the second run.

```
MEncoder 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-60 (Family: 15, Model: 72, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-x264encopts subq=6:partitions=all:me=umh:8x8dct:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000:threads=3 is not an MEncoder option

Exiting... (error parsing command line)
```

If there is any way I can get some help, I would really appreciate it.

---

### Post by Azakus on 2007-09-28
> **phreeq said:**
> I hate to jump on the bandwagon, but I am also having a little problem.

Azakus, I got the fix for the missing space in the first run of mencoder, but now there are problems with the second run.

```
MEncoder 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-60 (Family: 15, Model: 72, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
-x264encopts subq=6:partitions=all:me=umh:8x8dct:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000:threads=3 is not an MEncoder option

Exiting... (error parsing command line)
```

If there is any way I can get some help, I would really appreciate it.
Honestly, I don't know why it's not working for you. It works perfectly fine for me, and it's exactly the same (I checked). Unless you don't have x264-bin installed, I don't know what's wrong. Sorry.

---

### Post by ZingZingZingBah on 2007-09-28
I know why.

Put this

> threads=3

as the first option instead of at the end.

Fixed the same problem for me.

---

### Post by phreeq on 2007-09-28
x264-bin is installed, so that shouldn't be a problem. Hopefully, Zing's fix will work. It's testing now, but I'm about to leave for work, so I'll let y'all know when I get home this evening.

---

### Post by innocenceisdeath on 2007-09-28
Can anyone help me as to why this code in the videnc file doesn't work?
It returns the error

Cannot initialize driver

```
# First pass
mencoder -v\
         title.vob\
	-vf yadif=3:1,mcdeint=2:1:10\      
	-vf crop=720:560:0:10,harddup\
        -ovc x264 -x264encopts threads=auto:subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=100\
        -oac copy\
        -of rawvideo\
        -o title.264

# Second pass
mencoder -v\
         title.vob\
	-vf yadif=3:1,mcdeint=2:1:10\
	-vf crop=720:560:0:10,harddup\
        -ovc x264 -x264encopts threads=auto:subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=100\
        -oac copy\
        -of rawvideo\
        -o title.264
```

---

### Post by DasCrushinator on 2007-09-28
> **innocenceisdeath said:**
> Can anyone help me as to why this code in the videnc file doesn't work?
It returns the error

Cannot initialize driver

```
# First pass
mencoder -v\
         title.vob\
	-vf yadif=3:1,mcdeint=2:1:10\      
	-vf crop=720:560:0:10,harddup\
        -ovc x264 -x264encopts threads=auto:subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=100\
        -oac copy\
        -of rawvideo\
        -o title.264

# Second pass
mencoder -v\
         title.vob\
	-vf yadif=3:1,mcdeint=2:1:10\
	-vf crop=720:560:0:10,harddup\
        -ovc x264 -x264encopts threads=auto:subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=100\
        -oac copy\
        -of rawvideo\
        -o title.264
```
It looks like both of those are deinterlacing filters. Are you supposed to use them together like that?

---

### Post by innocenceisdeath on 2007-09-28
> **DasCrushinator said:**
> It looks like both of those are deinterlacing filters. Are you supposed to use them together like that?
It doesn't make any difference if I don't use them at all. I think the problem lies within these lines

```
-ovc x264 -x264encopts threads=auto:subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=100\

-ovc x264 -x264encopts threads=auto:subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=100\
```

These with the rest of the code return these problems:
```
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=24000 sample-1)
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (720x576->768x576,flags=0,'MPlayer',0x32315659)
SwScaler: using unscaled yuv420p -> yuv420p special converter
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x400  
REQ: flags=0x403  req=0x0  
REQ: flags=0x3  req=0x0  
FATAL: Cannot initialize video driver.
```

If I alter them to this:
```
-ovc x264 -x264encopts threads=auto subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=100\

-ovc x264 -x264encopts threads=auto subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=100\
```

It appears to go through the encoding process but then disregards everything after the threads=auto in the lines, from what I can tell, but then spits this error out:
```
File not found: 'subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=100'
Failed to open subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=100.
Cannot open file/device.

```

---

### Post by phreeq on 2007-09-28
> **ZingZingZingBah said:**
> I know why.

Put this



as the first option instead of at the end.

Fixed the same problem for me.

Alright, I tried that, but it didn't work. Any chance you can give me the exact line you're using?

---

### Post by DasCrushinator on 2007-09-28
> **innocenceisdeath said:**
> It doesn't make any difference if I don't use them at all. I think the problem lies within these lines

```
-ovc x264 -x264encopts threads=auto:subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=100\

-ovc x264 -x264encopts threads=auto:subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=100\
```

These with the rest of the code return these problems:
```
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=24000 sample-1)
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (720x576->768x576,flags=0,'MPlayer',0x32315659)
SwScaler: using unscaled yuv420p -> yuv420p special converter
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x400  
REQ: flags=0x403  req=0x0  
REQ: flags=0x3  req=0x0  
FATAL: Cannot initialize video driver.
```

If I alter them to this:
```
-ovc x264 -x264encopts threads=auto subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=100\

-ovc x264 -x264encopts threads=auto subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=100\
```

It appears to go through the encoding process but then disregards everything after the threads=auto in the lines, from what I can tell, but then spits this error out:
```
File not found: 'subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=100'
Failed to open subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=100.
Cannot open file/device.

```

Ahh just noticed you have 4x4mv.  You need to replace that with partitions=all.

I think that will solve your problem.

---

### Post by ZingZingZingBah on 2007-09-28
@phreeq

Here's the full monty - ruthlessly borrowed from this thread and tweaked a little for my purposes.

```


#!/bin/bash

#Usage dvdrip <NAME>

NAME=$1

mkdir ~/$NAME

cd ~/$NAME

dvdxchap /dev/dvd > $NAME.chaps.txt

mplayer dvd://1  -dumpstream -dumpfile $NAME.vob

mplayer $NAME.vob -aid 128 -dumpaudio -dumpfile $NAME.ac3

mencoder $NAME.vob -vf scale=720:-3,harddup -nosound -ovc x264 -x264encopts threads=auto:subq=5:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1350 -oac copy -of rawvideo -o /dev/null

mencoder $NAME.vob -vf scale=720:-3,harddup -nosound -ovc x264 -x264encopts threads=auto:bitrate=1350:subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr oac copy -of rawvideo -o $NAME.264

MP4Box -add $NAME.264 $NAME.mp4

mkvmerge $NAME.mp4 $NAME.ac3 --chapters $NAME.chaps.txt -o $NAME.mkv --title $NAME

```

---

### Post by innocenceisdeath on 2007-09-29
@ZingZingBah

In the third line form the bottom, don't you need a hyphon (-) in front of oac like this?
```
mencoder $NAME.vob -vf scale=720:-3,harddup -nosound -ovc x264 -x264encopts threads=auto:bitrate=1350:subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr -oac copy -of rawvideo -o $NAME.264
```

---

### Post by ZingZingZingBah on 2007-09-29
Yes, absolutely. Well spotted.

---

### Post by innocenceisdeath on 2007-09-29
@DasCrushinator

Thanks too btw, that helped!

---

### Post by DasCrushinator on 2007-09-29
> **innocenceisdeath said:**
> @DasCrushinator

Thanks too btw, that helped!

:)

Glad I could help.

---

### Post by Vajrapaat on 2007-10-14
Hi,
  
   I am interested in experimenting with the x264 code a bit, and am wondering what would be the best way to run mencoder with the fresh libraries. Can someone advise me with this. 
 
   I am currently trying to recompile mplayer using the flag --with-extralibdir=MY_X264_DIR, but it is giving me some errors. I was wondering if i can simply replace the original libx264 (not sure where it is stored) with the new libraries?

---

### Post by HoverHell on 2007-10-15
> **Vajrapaat said:**
> Hi,
  
   I am interested in experimenting with the x264 code a bit, and am wondering what would be the best way to run mencoder with the fresh libraries. Can someone advise me with this. 
 
   I am currently trying to recompile mplayer using the flag --with-extralibdir=MY_X264_DIR, but it is giving me some errors. I was wondering if i can simply replace the original libx264 (not sure where it is stored) with the new libraries?

Well, this seems more like a question for mplayer development list, not this topic...
But, anyway, I suggest you 1. make sure mplayer links to libx264.so (or what you need) and 2. you don't change headers for library (x264.h).
I might be wrong, but.. just try it. :)

P.S. What type of things are you going to try on x264 code?

---

### Post by Vajrapaat on 2007-10-15
Thanks for the mail. My question was on how to make sure that mplayer links to the new library (sorry but i'm sort of a newbie to linux :)).

I am interested in playing a bit with preprocessing filters prior to encoding

---

### Post by rootkit on 2007-12-04
What about tryng my mp4tools? [http://teknoraver.campuslife.it/software/mp4tools/](http://teknoraver.campuslife.it/software/mp4tools/)

I have also ubuntu packages for my AAC+ encoder

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) gutsy main

Cheers,
matteo

---

### Post by DasCrushinator on 2007-12-05
> **rootkit said:**
> What about tryng my mp4tools? [http://teknoraver.campuslife.it/software/mp4tools/](http://teknoraver.campuslife.it/software/mp4tools/)

I have also ubuntu packages for my AAC+ encoder

deb [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) hardy main

PS: You need a newer mplayer an gpac than the one in ubuntu.

Cheers,
matteoLooks interesting.  I'm going to check it out in the next few days.

---

### Post by rootkit on 2007-12-06
Sorry, the repository was wrong, corrected.
Also, I put informations on how to install the tools on the homepage.

Cheers to all ubunteros ;)

---

### Post by DasCrushinator on 2007-12-07
> **rootkit said:**
> Sorry, the repository was wrong, corrected.
Also, I put informations on how to install the tools on the homepage.

Cheers to all ubunteros ;)

I seem to be getting an error with the device not found being found.  How can I tell which device it is?

```

matthew@matthew-desktop:~$ dvd2mp4
usage: /usr/bin/dvd2mp4 <filmname.mp4> [input device|input iso|input dir] [title] [chapter]
        example: /usr/bin/dvd2mp4 myfilm.mp4 /dev/hdc 2 3
matthew@matthew-desktop:~$ dvd2mp4 se7en.mp4 /dev/dvdrw 1 1

Analysing input file

Ripping DVD...
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (Family: 15, Model: 67, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Cannot open file/device.

Muxing
Saving to se7en.mp4: 0.500 secs Interleaving

saved to 
se7en.mp4


```

Also, what does the title variable do?  Is it the stream from which it grabs?  If I want to do a full movie from a DVD, what would I type?  What about for a single episode of a TV show set?

Thanks!

---

### Post by rootkit on 2007-12-07
> **DasCrushinator said:**
> I seem to be getting an error with the device not found being found.  How can I tell which device it is?

```

matthew@matthew-desktop:~$ dvd2mp4
usage: /usr/bin/dvd2mp4 <filmname.mp4> [input device|input iso|input dir] [title] [chapter]
        example: /usr/bin/dvd2mp4 myfilm.mp4 /dev/hdc 2 3
matthew@matthew-desktop:~$ dvd2mp4 se7en.mp4 /dev/dvdrw 1 1

Analysing input file

Ripping DVD...
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (Family: 15, Model: 67, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Cannot open file/device.

Muxing
Saving to se7en.mp4: 0.500 secs Interleaving

saved to 
se7en.mp4


```

Also, what does the title variable do? Is it the stream from which it grabs?  If I want to do a full movie from a DVD, what would I type?  What about for a single episode of a TV show set?

Thanks!
You can omit the title to rip all the DVD.
I added it since some DVDs has the first title with copyright info and the movie in the 2nd title.
The device is the unix device of your DVD rom.
Usually a DVD rip is done by:

Btw i'm uploading a fixed script, cya
```
dvd2mp4 film.mp4 /dev/dvd
```

---

### Post by rootkit on 2007-12-07
Yeah, found the bug. It seems that it rips only from /dev/sr0.
Please edit mp4toools, there this line in the beginning:

```
export DEV=/dev/sr0
```

I'll fix it later, bye

---

### Post by rootkit on 2007-12-07
Fixed, and added language detection via the LANG env variable, older versions always rips in Italian, sorry :)

Cheers from Italy,
Matteo

---

### Post by DasCrushinator on 2007-12-07
> **rootkit said:**
> Fixed, and added language detection via the LANG env variable, older versions always rips in Italian, sorry :)

Cheers from Italy,
Matteo

Matteo, modified the file and that appeared to fix the problem.  Haven't updated yet from the repos, though.  I have an AMD 5600+ (Dual Core 2.8GHz), 2GB DDR2 800, and an nVidia 7600GT, but while ripping, the script says my computer is too slow to play the file.  Could this be because I have scaling enabled?  Also, why did the 2nd pass fail?  Where does the final file get saved to? 

```
matthew@matthew-desktop:~$ dvd2mp4 se7en.mp4 /dev/dvd

Analysing input file

Detecting crop area...

Ripping DVD...
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (Family: 15, Model: 67, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Using SSE optimized IMDCT transform
Using MMX optimized resampler

Ripping Audio
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (Family: 15, Model: 67, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not open config files /home/matthew/.lircrc and /etc/lirc//lircrc
mplayer: No such file or directory
Using SSE optimized IMDCT transform
Using MMX optimized resampler


           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.


Normalizing Audio
Computing levels...
Audio File Library: '/tmp/audio.7109.wav': unrecognized audio file format [error 0]
normalize-audio: error reading /tmp/audio.7109.wav


Encoding AAC+ Audio

*************************************************************
* Enhanced aacPlus Encoder
* Build Dec  6 2007, 02:03:50
* Matteo Croce <rootkit85@yahoo.it>
*************************************************************

could not open /tmp/audio.7109.wav

Encoding H.264 Video (1st pass)
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (Family: 15, Model: 67, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 3DNow! 
x264 [info]: slice I:1413  Avg QP:20.12  size: 19712
x264 [info]: slice P:90829 Avg QP:22.32  size:  3910
x264 [info]: slice B:80396 Avg QP:23.71  size:  1534
x264 [info]: mb I  I16..4: 21.2% 43.3% 35.5%
x264 [info]: mb P  I16..4:  4.2%  9.2%  2.1%  P16..4: 23.3%  6.5%  2.3%  0.0%  0.0%    skip:52.4%
x264 [info]: mb B  I16..4:  0.4%  1.1%  0.4%  B16..8: 16.4%  0.0%  0.0%  direct: 8.4%  skip:73.3%
x264 [info]: final ratefactor: 22.10
x264 [info]: 8x8 transform  intra:57.7%  inter:45.0%
x264 [info]: direct mvs  spatial:99.7%  temporal:0.3%
x264 [info]: kb/s:703.3

Encoding H.264 Video (2nd pass)
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (Family: 15, Model: 67, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 3DNow! 
x264 [error]: ratecontrol_init: can't open stats file
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 3DNow! 
x264 [error]: ratecontrol_init: can't open stats file

Muxing
 (BitStream Not Compliant)Cannot find H264 start code
Error importing /tmp/video.7109.264: BitStream Not Compliant

saved to 
se7en.mp4

```

Edit: Just updated mp4tools, but the sr0 entry is still in /usr/bin/mp4tools.

---

### Post by rootkit on 2007-12-07
The fix is in mp4tools 0.5.1
the warning is harmless, it also appears while ripping, since the video output (the hd) is slower than the CPU

---

### Post by rootkit on 2007-12-08
The real issue seems that your mplayer produces an invalid WAV file:

```
Audio File Library: '/tmp/audio.7109.wav': unrecognized audio file format [error 0]
```

cant you run it in debug mode and see what /tmp/audio.*.wav is?

```
KEEPTEMP=1 dvd2mp4 film.mp4 dev
```

---

### Post by DasCrushinator on 2007-12-09
> **rootkit said:**
> The real issue seems that your mplayer produces an invalid WAV file:

```
Audio File Library: '/tmp/audio.7109.wav': unrecognized audio file format [error 0]
```

cant you run it in debug mode and see what /tmp/audio.*.wav is?

```
KEEPTEMP=1 dvd2mp4 film.mp4 dev
```

Ok, I did this, but where does it store the log file?

---

### Post by rootkit on 2007-12-09
There aren't log files, all is printed in the console, but KEEPTEMP=1 will leave temp files in /tmp, the script normally removes them.
If you want extra logging do:

```
DEBUG=1 KEEPTEMP=1 dvd2mp4
```

BTW, i'll be away for 4 days, see you next week

---

### Post by DasCrushinator on 2007-12-09
.

---

### Post by rootkit on 2007-12-12
..

---

### Post by DasCrushinator on 2007-12-12
> **rootkit said:**
> ..

He he.  I thought I had figured something out, tried it, and it wasn't causing the problem.

---

### Post by rootkit on 2007-12-12
Does it works now?

---

### Post by DasCrushinator on 2007-12-12
> **rootkit said:**
> Does it works now?

Nope, Tried the command you advised me on:
```
DEBUG=1 KEEPTEMP=1 dvd2mp4 se7en.mp4 /dev/dvd
```

Not exactly sure what I am supposed to be lookiing for though, sorry.

If you could tell me exactly what to look for/paste, I would be happy to run it again :)

I hope I am being a help, and not a nuisance.

---

### Post by rootkit on 2007-12-12
> **DasCrushinator said:**
> Nope, Tried the command you advised me on:
```
DEBUG=1 KEEPTEMP=1 dvd2mp4 se7en.mp4 /dev/dvd
```

Not exactly sure what I am supposed to be lookiing for though, sorry.

If you could tell me exactly what to look for/paste, I would be happy to run it again :)

I hope I am being a help, and not a nuisance.
paste the full output, and keep a copy of temp files in /tmp for future hackings please
no nuisance for ubuntu users :)

---

### Post by DasCrushinator on 2007-12-13
> **rootkit said:**
> paste the full output, and keep a copy of temp files in /tmp for future hackings please
no nuisance for ubuntu users :)

Encoding H.264 Video (2nd pass)
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (Family: 15, Model: 67, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x19b7f000
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
AVI: ODML: Building ODML index (2 superindexchunks).
AVI: ODML: Broken (incomplete?) file detected. Will use traditional index.
VIDEO:  [FFVH]  720x352  12bpp  29.970 fps  27531.5 kbps (3360.8 kbyte/s)
[V] filefmt:3  fourcc:0x48564646  size:720x352  fps:29.97  ftime:=0.0334
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffhuffyuv] vfm: ffmpeg (FFmpeg HuffYUV)
==========================================================================
VDec: vo config request - 720 x 352 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 2)
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x8800710]SwScaler: using unscaled yuv420p -> yuv420p special converter
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 3DNow! 
x264 [error]: statistics are damaged at line 44, parser out=9
x264_encoder_open failed.
FATAL: Cannot initialize video driver.
VDec: vo config request - 720 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 2)
Movie-Aspect is undefined - no prescaling applied.
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 3DNow! 
x264 [error]: statistics are damaged at line 44, parser out=9
x264_encoder_open failed.
FATAL: Cannot initialize video driver.

Exiting...

Muxing
 (BitStream Not Compliant)Cannot find H264 start code
Error importing /tmp/video.7750.264: BitStream Not Compliant

saved to 
se7en.mp4

---

### Post by rootkit on 2007-12-13
> **DasCrushinator said:**
> Encoding H.264 Video (2nd pass)
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (Family: 15, Model: 67, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x19b7f000
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
AVI: ODML: Building ODML index (2 superindexchunks).
AVI: ODML: Broken (incomplete?) file detected. Will use traditional index.
VIDEO:  [FFVH]  720x352  12bpp  29.970 fps  27531.5 kbps (3360.8 kbyte/s)
[V] filefmt:3  fourcc:0x48564646  size:720x352  fps:29.97  ftime:=0.0334
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffhuffyuv] vfm: ffmpeg (FFmpeg HuffYUV)
==========================================================================
VDec: vo config request - 720 x 352 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 2)
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x8800710]SwScaler: using unscaled yuv420p -> yuv420p special converter
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 3DNow! 
x264 [error]: statistics are damaged at line 44, parser out=9
x264_encoder_open failed.
FATAL: Cannot initialize video driver.
VDec: vo config request - 720 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 2)
Movie-Aspect is undefined - no prescaling applied.
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 3DNow! 
x264 [error]: statistics are damaged at line 44, parser out=9
x264_encoder_open failed.
FATAL: Cannot initialize video driver.

Exiting...

Muxing
 (BitStream Not Compliant)Cannot find H264 start code
Error importing /tmp/video.7750.264: BitStream Not Compliant

saved to 
se7en.mp4

Have you still have /tmp/x264enc.XXXX.log? It seems to be corrupted between 1st and 2nd paass

---

### Post by DasCrushinator on 2007-12-13
> **rootkit said:**
> Have you still have /tmp/x264enc.XXXX.log? It seems to be corrupted between 1st and 2nd paass

matthew@matthew-desktop:/tmp$ ls -lha
total 25G
drwxrwxrwt 10 root    root    4.0K 2007-12-13 10:40 .
drwxr-xr-x 21 root    root    4.0K 2007-12-06 16:10 ..
-rw-r--r--  1 matthew matthew  25G 2007-12-13 08:55 dvd.6300.avi
drwx------  3 matthew matthew 4.0K 2007-12-13 08:31 gconfd-matthew
-rw-r--r--  1 matthew matthew    0 2007-12-13 09:05 header.6300.wav
drwxrwxrwt  2 root    root    4.0K 2007-12-13 08:31 .ICE-unix
-rw-r--r--  1 matthew matthew 1.2K 2007-12-13 08:33 info.6300.txt
drwx------  2 matthew matthew 4.0K 2007-12-13 08:31 keyring-2EVhjp
srwxr-xr-x  1 matthew matthew    0 2007-12-13 08:31 mapping-matthew
drwx------  2 matthew matthew 4.0K 2007-12-13 12:01 orbit-matthew
drwx------  2 matthew matthew 4.0K 2007-12-13 08:31 ssh-TPgWnR5935
drwx------  3 matthew matthew 4.0K 2007-12-13 08:32 Tracker-matthew.6104
-rw-r--r--  1 matthew matthew    0 2007-12-13 10:40 video.6300.264
drwx------  2 matthew matthew 4.0K 2007-12-13 08:31 virtual-matthew.JXECF8
-r--r--r--  1 root    root      11 2007-12-13 08:31 .X0-lock
drwxrwxrwt  2 root    root    4.0K 2007-12-13 08:31 .X11-unix

I don't have a file with that name.

---

### Post by rootkit on 2007-12-13
> **DasCrushinator said:**
> 
I don't have a file with that name.
Sorry, fixed:
```

 mp4tools (0.5.3) gutsy; urgency=low
   * Don't remove some temp files with KEEPTEMP=1

```

Btw the problem is definitely the log file being damaged:
> **DasCrushinator said:**
> x264 [error]: statistics are damaged at line 44, parser out=9
 x264_encoder_open failed.
 FATAL: Cannot initialize video driver.

---

### Post by rootkit on 2007-12-13
This is my output after a good encoding:
```
Encoding H.264 Video (1st pass)
MEncoder 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (Family: 15, Model: 35, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x2602fe4
AVI file format detected.
AVI_NI: No audio stream found -> no sound.
VIDEO:  [FFVH]  512x368  12bpp  25.000 fps  28893.1 kbps (3527.0 kbyte/s)
[V] filefmt:3  fourcc:0x48564646  size:512x368  fps:25.00  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffhuffyuv] vfm: ffmpeg (FFmpeg HuffYUV)
==========================================================================
VDec: vo config request - 512 x 368 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 2)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: using unscaled yuv420p -> yuv420p special converter
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 3DNow!
Pos:   0.0s      2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Pos:  10.8s    273f (99%) 49.53fps Trem:   0min   0mb  A-V:0.000 [650:0]]
Flushing video frames

Video stream:  643.158 kbit/s  (80394 B/s)  size: 877911 bytes  10.920 secs  273 frames
x264 [info]: slice I:2     Avg QP:15.50  size: 36450
x264 [info]: slice P:130   Avg QP:16.20  size:  5915
x264 [info]: slice B:141   Avg QP:15.91  size:   251
x264 [info]: mb I  I16..4: 66.1%  0.3% 33.6%
x264 [info]: mb P  I16..4:  2.8%  0.2%  1.4%  P16..4: 46.2%  0.7%  0.3%  0.0%  0.0%    skip:48.4%
x264 [info]: mb B  I16..4:  0.0%  0.0%  0.0%  B16..8:  5.3%  0.0%  0.0%  direct:12.7%  skip:82.0%
x264 [info]: final ratefactor: 17.02
x264 [info]: 8x8 transform  intra:3.5%  inter:26.4%
x264 [info]: direct mvs  spatial:97.9%  temporal:2.1%
x264 [info]: kb/s:642.7

Encoding H.264 Video (2nd pass)
MEncoder 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (Family: 15, Model: 35, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x2602fe4
AVI file format detected.
AVI_NI: No audio stream found -> no sound.
VIDEO:  [FFVH]  512x368  12bpp  25.000 fps  28893.1 kbps (3527.0 kbyte/s)
[V] filefmt:3  fourcc:0x48564646  size:512x368  fps:25.00  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffhuffyuv] vfm: ffmpeg (FFmpeg HuffYUV)
==========================================================================
VDec: vo config request - 512 x 368 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 2)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: using unscaled yuv420p -> yuv420p special converter
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 3DNow!
Pos:   0.0s      2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Pos:  10.8s    273f (99%) 13.52fps Trem:   0min   0mb  A-V:0.000 [745:0]]
Flushing video frames

Video stream:  737.213 kbit/s  (92151 B/s)  size: 1006296 bytes  10.920 secs  273 frames
x264 [info]: slice I:2     Avg QP:13.00  size: 30420
x264 [info]: slice P:130   Avg QP:11.98  size:  7135
x264 [info]: slice B:141   Avg QP:12.34  size:   122
x264 [info]: mb I  I16..4: 63.3%  2.2% 34.5%
x264 [info]: mb P  I16..4:  0.7%  0.6%  0.9%  P16..4: 49.1%  1.2%  1.3%  0.1%  0.0%    skip:46.2%
x264 [info]: mb B  I16..4:  0.0%  0.0%  0.0%  B16..8:  5.7%  0.0%  0.0%  direct: 0.6%  skip:93.7%
x264 [info]: 8x8 transform  intra:16.0%  inter:27.8%
x264 [info]: direct mvs  spatial:98.6%  temporal:1.4%
x264 [info]: ref P  91.2%  4.9%  3.9%
x264 [info]: ref B  88.3%  9.9%  1.8%
x264 [info]: kb/s:736.7

Muxing
Adjusting AVC SizeLength to 16 bits
AVC-H264 import - frame size 512 x 368 at 25.0000 FPS
Import results: 273 samples - Slices: 2 I 130 P 141 B - 1 SEI - 2 IDR
        Stream uses B-slice references - max frame delay 2
AAC import SBR (explicit) - sample rate 22050 - MPEG-4 audio - 2 channels
Saving test.mp4: 0.500 secs Interleaving

saved to
test.mp4
[/tmp]$ ll
totale 80M
-rw-r--r-- 1 matteo users 6,8K 2007-12-14 00:06 audio.8452.aac
-rw-r--r-- 1 matteo users 6,8K 2007-12-14 00:14 audio.8836.aac
-rw-r--r-- 1 matteo users  39M 2007-12-14 00:06 dvd.8452.avi
-rw-r--r-- 1 matteo users  39M 2007-12-14 00:14 dvd.8836.avi
drwx------ 2 matteo users   48 2007-12-13 23:25 gconfd-matteo
drwx------ 2 emilio users   80 2007-12-13 22:12 gpg-Bs7bGU
-rw-r--r-- 1 matteo users   44 2007-12-14 00:06 header.8452.wav
-rw-r--r-- 1 matteo users   44 2007-12-14 00:14 header.8836.wav
drwxrwxrwt 2 root   root   112 2007-12-13 22:58 .ICE-unix
-rw-r--r-- 1 matteo users  888 2007-12-14 00:06 info.8452.txt
-rw-r--r-- 1 matteo users  888 2007-12-14 00:14 info.8836.txt
drwx------ 2 emilio users   72 2007-12-13 22:58 kde-emilio
drwx------ 2 matteo users  208 2007-12-14 00:13 kde-matteo
drwx------ 3 emilio users  112 2007-12-13 22:58 ksocket-emilio
drwx------ 2 matteo users  192 2007-12-14 00:11 ksocket-matteo
drwx------ 2 matteo users   48 2007-12-13 23:25 orbit-matteo
-rw-r--r-- 1 matteo users 993K 2007-12-14 00:15 test.mp4
-rw-r--r-- 1 matteo users 983K 2007-12-14 00:07 video.8452.264
-rw-r--r-- 1 matteo users 983K 2007-12-14 00:15 video.8836.264
drwxrwxrwt 2 root   root    48 2007-12-13 22:12 VMwareDnD
drwx------ 2 matteo users  200 2007-12-13 23:42 vmware-matteo
prw------- 1 matteo users    0 2007-12-13 23:33 vmware-matteo.0
prw------- 1 matteo users    0 2007-12-13 23:33 vmware-matteo.1
-r--r--r-- 1 root   root    11 2007-12-13 22:12 .X0-lock
drwxrwxrwt 2 root   root    72 2007-12-13 22:12 .X11-unix
```

---

### Post by DasCrushinator on 2007-12-13
> **rootkit said:**
> This is my output after a good encoding:
```
Encoding H.264 Video (1st pass)
MEncoder 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (Family: 15, Model: 35, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x2602fe4
AVI file format detected.
AVI_NI: No audio stream found -> no sound.
VIDEO:  [FFVH]  512x368  12bpp  25.000 fps  28893.1 kbps (3527.0 kbyte/s)
[V] filefmt:3  fourcc:0x48564646  size:512x368  fps:25.00  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffhuffyuv] vfm: ffmpeg (FFmpeg HuffYUV)
==========================================================================
VDec: vo config request - 512 x 368 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 2)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: using unscaled yuv420p -> yuv420p special converter
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 3DNow!
Pos:   0.0s      2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Pos:  10.8s    273f (99%) 49.53fps Trem:   0min   0mb  A-V:0.000 [650:0]]
Flushing video frames

Video stream:  643.158 kbit/s  (80394 B/s)  size: 877911 bytes  10.920 secs  273 frames
x264 [info]: slice I:2     Avg QP:15.50  size: 36450
x264 [info]: slice P:130   Avg QP:16.20  size:  5915
x264 [info]: slice B:141   Avg QP:15.91  size:   251
x264 [info]: mb I  I16..4: 66.1%  0.3% 33.6%
x264 [info]: mb P  I16..4:  2.8%  0.2%  1.4%  P16..4: 46.2%  0.7%  0.3%  0.0%  0.0%    skip:48.4%
x264 [info]: mb B  I16..4:  0.0%  0.0%  0.0%  B16..8:  5.3%  0.0%  0.0%  direct:12.7%  skip:82.0%
x264 [info]: final ratefactor: 17.02
x264 [info]: 8x8 transform  intra:3.5%  inter:26.4%
x264 [info]: direct mvs  spatial:97.9%  temporal:2.1%
x264 [info]: kb/s:642.7

Encoding H.264 Video (2nd pass)
MEncoder 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (Family: 15, Model: 35, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x2602fe4
AVI file format detected.
AVI_NI: No audio stream found -> no sound.
VIDEO:  [FFVH]  512x368  12bpp  25.000 fps  28893.1 kbps (3527.0 kbyte/s)
[V] filefmt:3  fourcc:0x48564646  size:512x368  fps:25.00  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffhuffyuv] vfm: ffmpeg (FFmpeg HuffYUV)
==========================================================================
VDec: vo config request - 512 x 368 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 2)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: using unscaled yuv420p -> yuv420p special converter
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 3DNow!
Pos:   0.0s      2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Pos:  10.8s    273f (99%) 13.52fps Trem:   0min   0mb  A-V:0.000 [745:0]]
Flushing video frames

Video stream:  737.213 kbit/s  (92151 B/s)  size: 1006296 bytes  10.920 secs  273 frames
x264 [info]: slice I:2     Avg QP:13.00  size: 30420
x264 [info]: slice P:130   Avg QP:11.98  size:  7135
x264 [info]: slice B:141   Avg QP:12.34  size:   122
x264 [info]: mb I  I16..4: 63.3%  2.2% 34.5%
x264 [info]: mb P  I16..4:  0.7%  0.6%  0.9%  P16..4: 49.1%  1.2%  1.3%  0.1%  0.0%    skip:46.2%
x264 [info]: mb B  I16..4:  0.0%  0.0%  0.0%  B16..8:  5.7%  0.0%  0.0%  direct: 0.6%  skip:93.7%
x264 [info]: 8x8 transform  intra:16.0%  inter:27.8%
x264 [info]: direct mvs  spatial:98.6%  temporal:1.4%
x264 [info]: ref P  91.2%  4.9%  3.9%
x264 [info]: ref B  88.3%  9.9%  1.8%
x264 [info]: kb/s:736.7

Muxing
Adjusting AVC SizeLength to 16 bits
AVC-H264 import - frame size 512 x 368 at 25.0000 FPS
Import results: 273 samples - Slices: 2 I 130 P 141 B - 1 SEI - 2 IDR
        Stream uses B-slice references - max frame delay 2
AAC import SBR (explicit) - sample rate 22050 - MPEG-4 audio - 2 channels
Saving test.mp4: 0.500 secs Interleaving

saved to
test.mp4
[/tmp]$ ll
totale 80M
-rw-r--r-- 1 matteo users 6,8K 2007-12-14 00:06 audio.8452.aac
-rw-r--r-- 1 matteo users 6,8K 2007-12-14 00:14 audio.8836.aac
-rw-r--r-- 1 matteo users  39M 2007-12-14 00:06 dvd.8452.avi
-rw-r--r-- 1 matteo users  39M 2007-12-14 00:14 dvd.8836.avi
drwx------ 2 matteo users   48 2007-12-13 23:25 gconfd-matteo
drwx------ 2 emilio users   80 2007-12-13 22:12 gpg-Bs7bGU
-rw-r--r-- 1 matteo users   44 2007-12-14 00:06 header.8452.wav
-rw-r--r-- 1 matteo users   44 2007-12-14 00:14 header.8836.wav
drwxrwxrwt 2 root   root   112 2007-12-13 22:58 .ICE-unix
-rw-r--r-- 1 matteo users  888 2007-12-14 00:06 info.8452.txt
-rw-r--r-- 1 matteo users  888 2007-12-14 00:14 info.8836.txt
drwx------ 2 emilio users   72 2007-12-13 22:58 kde-emilio
drwx------ 2 matteo users  208 2007-12-14 00:13 kde-matteo
drwx------ 3 emilio users  112 2007-12-13 22:58 ksocket-emilio
drwx------ 2 matteo users  192 2007-12-14 00:11 ksocket-matteo
drwx------ 2 matteo users   48 2007-12-13 23:25 orbit-matteo
-rw-r--r-- 1 matteo users 993K 2007-12-14 00:15 test.mp4
-rw-r--r-- 1 matteo users 983K 2007-12-14 00:07 video.8452.264
-rw-r--r-- 1 matteo users 983K 2007-12-14 00:15 video.8836.264
drwxrwxrwt 2 root   root    48 2007-12-13 22:12 VMwareDnD
drwx------ 2 matteo users  200 2007-12-13 23:42 vmware-matteo
prw------- 1 matteo users    0 2007-12-13 23:33 vmware-matteo.0
prw------- 1 matteo users    0 2007-12-13 23:33 vmware-matteo.1
-r--r--r-- 1 root   root    11 2007-12-13 22:12 .X0-lock
drwxrwxrwt 2 root   root    72 2007-12-13 22:12 .X11-unix
```

Awesome!  I should be home in the next couple of hours to try this out.  When do you think the repo will be updated with 0.5.3?

---

### Post by DasCrushinator on 2007-12-13
Also, when I attempt this after the update hits, should I continue using the command I have been using?

---

### Post by rootkit on 2007-12-13
> **DasCrushinator said:**
> Also, when I attempt this after the update hits, should I continue using the command I have been using?
Yes.
But, wasn't it better for you to use a smaller DVD? It takes ages to encode

---

### Post by DasCrushinator on 2007-12-13
> **rootkit said:**
> Yes.
But, wasn't it better for you to use a smaller DVD? It takes ages to encode

I suppose I could.  The main reason I have been trying "Se7en" is because I was in the process of making a script of my own, but sort of stopped a few months back, but when I was testing it, this and another movie gave me a hard time while other movies and TV shows didn't.  I will try just the first few chapters to see how it works.

Edit: By hard time I mean the audio and video didn't sync up properly.

---

### Post by DasCrushinator on 2007-12-13
Ok, now I have that file, but it is blank.  BTW, this is on a pretty fresh install of Gutsy, if that helps any.

---

### Post by rootkit on 2007-12-14
> **DasCrushinator said:**
> Ok, now I have that file, but it is blank.  BTW, this is on a pretty fresh install of Gutsy, if that helps any.
Blank?
It is written by mencoder during the h.264 encoding in the 1st pass.
Have you it while doing the 1st pass?
Also, in the 1st pass what ```
ps ax |fgrep mencoder
``` says?
Keep a copy of that file just before the 1st pass end (eg. 90%)

---

### Post by DasCrushinator on 2007-12-14
> **rootkit said:**
> Blank?
It is written by mencoder during the h.264 encoding in the 1st pass.
Have you it while doing the 1st pass?
Also, in the 1st pass what ```
ps ax |fgrep mencoder
``` says?
Keep a copy of that file just before the 1st pass end (eg. 90%)

I'm at about 3% with the 1st pass now, but I went ahead and ran this command:```
ps ax |fgrep mencoder
``` and got this ```
 6499 pts/0    R+     1:43 mencoder /tmp/dvd.6219.avi -vf harddup -ofps 29.970 -o /dev/null -of rawvideo -ovc x264 -nosound -x264encopts bitrate=700:bframes=3:b-pyramid:merange=32:ref=3:qcomp=0.8:partitions=all:direct=auto:weightb:me=umh:subme=7:b-rdo:mixed-refs:bime:8x8dct:trellis=2:turbo=1:pass=1 -passlogfile /tmp/x264enc.6219.log
```

At this point, x264enc.6219.log.temp, is empty.

---

### Post by rootkit on 2007-12-14
Keep a copy of /tmp/dvd.6219.avi somewhere, there is something weird in your mplayer.

---

### Post by DasCrushinator on 2007-12-14
> **rootkit said:**
> Keep a copy of /tmp/dvd.6219.avi somewhere, there is something weird in your mplayer.

Would my video out make a difference?  What is yours set to?

---

### Post by rootkit on 2007-12-14
> **DasCrushinator said:**
> Would my video out make a difference?  What is yours set to?
What video out?

---

### Post by DasCrushinator on 2007-12-14
> **rootkit said:**
> What video out?

Open mplayer, right click and got Preferences, Video, Available drivers.

Also, what version of mplayer are you using?

---

### Post by rootkit on 2007-12-14
> **DasCrushinator said:**
> Open mplayer, right click and got Preferences, Video, Available drivers.

Also, what version of mplayer are you using?

```
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
```

Ah, the mplayer output module (xv, x11, gl)..
mencoder has no video output modules, it's and encoder.
They are separate programs

---

### Post by DasCrushinator on 2007-12-14
> **rootkit said:**
> ```
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
```

Ah, the mplayer output module (xv, x11, gl)..
mencoder has no video output modules, it's and encoder.
They are separate programs

Yeah, I knew they were two different programs, but kept seeing a video out error so wasn't sure if that had anything to do with it.

```
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
```

Hmm, I remember you saying (either here or on your page) that a newer version of Mplayer was needed, but then I thought you set the scripts up to work with the MPlayer in the repos afterwards.  How would I go about getting rid of this version, and updting to the newer version?

---

### Post by rootkit on 2007-12-14
> **DasCrushinator said:**
> Yeah, I knew they were two different programs, but kept seeing a video out error so wasn't sure if that had anything to do with it.

```
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
```

Hmm, I remember you saying (either here or on your page) that a newer version of Mplayer was needed, but then I thought you set the scripts up to work with the MPlayer in the repos afterwards.  How would I go about getting rid of this version, and updting to the newer version?
You needed a newer version since mplayer changes its cmdline from "avsync" to "statusline", but I get rid of this in the ubuntu packages

---

### Post by DasCrushinator on 2007-12-14
> **rootkit said:**
> You needed a newer version since mplayer changes its cmdline from "avsync" to "statusline", but I get rid of this in the ubuntu packages

Hmm..I wish we knew what the poblem was then :(

---

### Post by rootkit on 2007-12-14
> **DasCrushinator said:**
> Hmm..I wish we knew what the poblem was then :(
have you still the dvd.avi file?
try encoding it manually

```

mencoder X.avi -vf harddup -o X1.264 -of rawvideo -ovc x264 -nosound -x264encopts bitrate=700:bframes=3:b-pyramid:merange=32:ref=3:qcomp=0.8:partitions=all:direct=auto:weightb:me=umh:subme=7:b-rdo:mixed-refs:bime:8x8dct:trellis=2:turbo=1:pass=1 -passlogfile tmp.log
mencoder X.avi -vf harddup -o X2.264 -of rawvideo -ovc x264 -nosound -x264encopts bitrate=700:bframes=3:b-pyramid:merange=32:ref=3:qcomp=0.8:partitions=all:direct=auto:weightb:me=umh:subme=7:b-rdo:mixed-refs:bime:8x8dct:trellis=2:pass=2 -passlogfile tmp.log

```

---

### Post by DasCrushinator on 2007-12-14
> **rootkit said:**
> have you still the dvd.avi file?
try encoding it manually

```

mencoder X.avi -vf harddup -o X1.264 -of rawvideo -ovc x264 -nosound -x264encopts bitrate=700:bframes=3:b-pyramid:merange=32:ref=3:qcomp=0.8:partitions=all:direct=auto:weightb:me=umh:subme=7:b-rdo:mixed-refs:bime:8x8dct:trellis=2:turbo=1:pass=1 -passlogfile tmp.log
mencoder X.avi -vf harddup -o X2.264 -of rawvideo -ovc x264 -nosound -x264encopts bitrate=700:bframes=3:b-pyramid:merange=32:ref=3:qcomp=0.8:partitions=all:direct=auto:weightb:me=umh:subme=7:b-rdo:mixed-refs:bime:8x8dct:trellis=2:pass=2 -passlogfile tmp.log

```

I'm doing that right now.

Worked like a charm.  However, the picture seems to make everything seem a bit skinnier and taller than they really are.  Which is strange because I don't see a scale option in either command.

---

### Post by rootkit on 2007-12-17
Idea, try a VBR, constant quality encoding, edit mp4tools and replace h264enc with the following:

```
#h264enc <infile> <outfile> [options] [bitrate]
h264enc()
{
	if [ -z "$VF" ]
	then
		VF=harddup
	else
		VF="$VF,harddup"
	fi
	VF="-vf $VF"
	[ -z "$OFPS" ] && OFPS=$FPS
	[ -n "$OFPS" ] && MOFPS="-fps $OFPS"
	[ -n "$OFPS" ] && OFPS="-ofps $OFPS"

	CRF=24
	X264OPTS="crf=$CRF:${3:-qcomp=0.8}"

	green "Encoding H.264 Video (VBR)"
	mencoder "$1" $VF $OFPS -o "$2" -of rawvideo -ovc x264 -nosound -x264encopts "$X264OPTS" $MSG
	MP4BOX_VOPTS="$MOFPS -add $2"
}
```

Quality is slighty worse but encoding goes 2x faster since it does one pass only

---

### Post by DasCrushinator on 2007-12-17
> **rootkit said:**
> Idea, try a VBR, constant quality encoding, edit mp4tools and replace h264enc with the following:

```
#h264enc <infile> <outfile> [options] [bitrate]
h264enc()
{
	if [ -z "$VF" ]
	then
		VF=harddup
	else
		VF="$VF,harddup"
	fi
	VF="-vf $VF"
	[ -z "$OFPS" ] && OFPS=$FPS
	[ -n "$OFPS" ] && MOFPS="-fps $OFPS"
	[ -n "$OFPS" ] && OFPS="-ofps $OFPS"

	CRF=24
	X264OPTS="crf=$CRF:${3:-qcomp=0.8}"

	green "Encoding H.264 Video (VBR)"
	mencoder "$1" $VF $OFPS -o "$2" -of rawvideo -ovc x264 -nosound -x264encopts "$X264OPTS" $MSG
	MP4BOX_VOPTS="$MOFPS -add $2"
}
```

Quality is slighty worse but encoding goes 2x faster since it does one pass only
I'll give this a try a little later, but I tested a different DVD and it didn't give the error.  However, it did still have interlaced/telecined marks in it and the wrong aspect ratio.

---

### Post by DasCrushinator on 2007-12-20
> **Heinz said:**
> [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-telecine.html) describes how to percept and handle interlaced video. I received good results by using the deinterlce postprocessing filter *-vf pp=lb*. As the documentation reads there are serveral filters available and it should be done after cropping and before scaling.

@Heinz: Does this mean you just have it in your config file or you used it as a -vf option while encoding?

@rootkit: Thanks for your help, but after taking another look at my script that I ceased working on a few months ago, I found what (stupid) error I made.  Thanks for your time and effort anyways!

---

### Post by DasCrushinator on 2008-01-11
So does anyone run their encoded videos on an HDTV?  How does it look?

Post your script/settings!

---

### Post by xtreme- on 2008-02-04
First of all: thanks for this awesome guide!

I was just wondering if it is possible to encode audio into a 5.1 ogg-file?
I.e. keep all channels (it just keeps two channels when the guide is followed, right?).
Or is the only possibility to keep the AC3 if you want to do that?

Furthermore, I would like to convert the subtitles into text (.srt?) format instead of VobSub.
The reason for this is just that VobSub in mkv doesn't seem to be well supported (e.g. not in VLC, Totem) and that it's possible to choose the size during playback.

Thank you for any help.

---

### Post by IronLike Monkey on 2008-02-04
Any one try making quicktime compatible files?  I have searched around the internet looking for quicktime compatible Mencoder parameters, and most of the posts I found either don't work half the time, or the audio/video are out of sync.  I know about the B Frames limit, the 8x8 stuff, and the SAR =1 requirements. Anyone have some reliable settings? Appreciate any help.

---

### Post by rootkit on 2008-02-04
> **xtreme- said:**
> First of all: thanks for this awesome guide!

I was just wondering if it is possible to encode audio into a 5.1 ogg-file?
I.e. keep all channels (it just keeps two channels when the guide is followed, right?).
Or is the only possibility to keep the AC3 if you want to do that?

Furthermore, I would like to convert the subtitles into text (.srt?) format instead of VobSub.
The reason for this is just that VobSub in mkv doesn't seem to be well supported (e.g. not in VLC, Totem) and that it's possible to choose the size during playback.

Thank you for any help.
Vorbis audio (ogg is the format) can't go into an MP4 file, so not

---

### Post by rootkit on 2008-02-04
> **IronLike Monkey said:**
> Any one try making quicktime compatible files?  I have searched around the internet looking for quicktime compatible Mencoder parameters, and most of the posts I found either don't work half the time, or the audio/video are out of sync.  I know about the B Frames limit, the 8x8 stuff, and the SAR =1 requirements. Anyone have some reliable settings? Appreciate any help.
My "mkipod" script makes iTunes/Quicktime/iPod compliant files, have a look

---

### Post by HoverHell on 2008-02-05
> **xtreme- said:**
> I was just wondering if it is possible to encode audio into a 5.1 ogg-file?
Try experimenting with -C option to oggenc.

> **xtreme- said:**
> 
Furthermore, I would like to convert the subtitles into text (.srt?) format instead of VobSub.

The reason for this is just that VobSub in mkv doesn't seem to be well supported (e.g. not in VLC, Totem) and that it's possible to choose the size during playback.


VobSub is not text, but puctures with rendered text. So you'll have to OCR it. There are specialized software for that...
Also, mplayer supports vobsub in mkv just fine...

---

### Post by xtreme- on 2008-02-05
Just thought I should post what I've found on my question regarding 1) VobSub->SRT (OCR) and 2) AC3 5.1 -> Ogg Vorbis 5.1.

1) Avidemux actually supports OCR, and creates .srt (text) files from VobSub-files (.idx & .sub). I've read that it isn't excellent yet, and my (limited) personal experiences with this supports this claim (but no-one said it was easy to do OCR).
Anyone having success with Avidemux for this purpose? Maybe you could post your glyph-file(s)? Any other programs that does this?

2) Ogg Vorbis does support more than two channels, but compress them "individually" for more than two channels. Thus, if the exact same sound is played on all channels, then ogg would save this information multiple times, leading to redundancy and less compression. It seems as the developers are working on this. AC3 is actually also a (lossy) compressed format, so the savings using ogg isn't really huge (not compared to PCM->ogg at least). I've read that you go from ca. 450 kbps to 220 kbps (is about from 400 -> 200 MB with a normal movie length, using 5.1 audio), and you do lose quality each time you encode. So it might not be worh it to reencode 5.1 audio at this time.

So I'm currently using VobSub as subtitles (annoying to get sub errors). For the audio, I just keep the AC3 if it's 5.1 and reencode to Ogg Vorbis if it's 2-channel.

By the way, please correct me if I'm wrong; and any new information or hints are welcome ;)

---

### Post by HoverHell on 2008-02-17
Note to the main HOWTO:
After few updates (debian unstable, debian-multimedia), MP4Box didn't work out well for adding raw H.264. However, mkvmerge successfully added it directly.
Therefore, using MP4Box with new versions of mkvmerge (2.0.2 for me) is not necessary anymore.

---

### Post by IronLike Monkey on 2008-03-17
Gave up on trying to find a quicktime compatible script/settings. There really is no reason to make a quicktime compatible video when there are great plug ins out there that will allow everyone to play high quality AVC/OGG encoded video.  I really had no clue about encoding till I bumped into this thread, and I am still a novice, but I think I am getting it down.  Used a custom matrix for the first time today, and I finally think I have the right mix of compression with near perfect quality.  
I used Sharktooths custom matrix from the doom9 forum, makes all the difference in dark scenes!  For the those that are just learning like me, don't overlook the custom matrix option, it was the last piece of the puzzle for me.

---

### Post by DasCrushinator on 2008-03-18
> **IronLike Monkey said:**
> Gave up on trying to find a quicktime compatible script/settings. There really is no reason to make a quicktime compatible video when there are great plug ins out there that will allow everyone to play high quality AVC/OGG encoded video.  I really had no clue about encoding till I bumped into this thread, and I am still a novice, but I think I am getting it down.  Used a custom matrix for the first time today, and I finally think I have the right mix of compression with near perfect quality.  
I used Sharktooths custom matrix from the doom9 forum, makes all the difference in dark scenes!  For the those that are just learning like me, don't overlook the custom matrix option, it was the last piece of the puzzle for me.

Could you post link(s)/elaborate some?  Also, have you tried your videos on an HDTV?

---

### Post by IronLike Monkey on 2008-03-18
Details about the matrix is listed below, their is a link to the cfg file if you want to try it.  Also pay attention to the bit rate and type of movies this is targeted, thats very important.

[http://forum.doom9.org/showthread.php?t=96298](http://forum.doom9.org/showthread.php?t=96298)

Using Sharktooths custom matrix, you would add ":cqm=/PATH/eqm_avc_hr.cfg:" in your paratmeters to use it.  I tried it on a very dark movie, which I normally would get lots of noise in the shadows, especially noticable on an HDTV.  With this custom matrix, the video was just as good as the DVD, of course it does not look as good as  a Blu Ray movie.  Some people might be put off at the relatively high bit rate of 1300-1400 that this matrix requires, but thats the price you have to pay for this type of quality.  I have only done one movie so far with it, so I am curious to see what type of results others get.

---

### Post by DasCrushinator on 2008-03-19
> **IronLike Monkey said:**
> Details about the matrix is listed below, their is a link to the cfg file if you want to try it.  Also pay attention to the bit rate and type of movies this is targeted, thats very important.

[http://forum.doom9.org/showthread.php?t=96298](http://forum.doom9.org/showthread.php?t=96298)

Using Sharktooths custom matrix, you would add ":cqm=/PATH/eqm_avc_hr.cfg:" in your paratmeters to use it.  I tried it on a very dark movie, which I normally would get lots of noise in the shadows, especially noticable on an HDTV.  With this custom matrix, the video was just as good as the DVD, of course it does not look as good as  a Blu Ray movie.  Some people might be put off at the relatively high bit rate of 1300-1400 that this matrix requires, but thats the price you have to pay for this type of quality.  I have only done one movie so far with it, so I am curious to see what type of results others get.

Looks very interesting.  Mind posting your other options/commands/script(s)?

---

### Post by IronLike Monkey on 2008-03-19
Don't laugh, I have a dedicated machine for just encoding and its pretty peppy, so I max out all my settings. I bascially beefed up a script I found on this thread:

```
#!/bin/bash

#Usage dvdrip <NAME>

NAME=$1

mkdir ~/$NAME

cd ~/$NAME

mplayer dvd://1 -dumpstream -dumpfile $NAME.vob

mencoder dvd://1 -nosound -ovc frameno -o /dev/null -slang en -vobsubout $NAME

mplayer $NAME.vob -ao pcm:file=$NAME.wav -vc dummy -aid 128 -vo null 

normalize-audio $NAME.wav

oggenc -q5 $NAME.wav 

mencoder $NAME.vob -o /dev/null -ofps 24000/1001 -vf crop=720:464:0:6,pullup,softskip,harddup -ovc x264 -x264encopts threads=auto:subq=7:partitions=all:8x8dct:me=umh:frameref=15:bframes=5:direct_pred=auto:nofast_pskip:b_pyramid:weight_b:nodct_decimate:pass=1:trellis=2:bime:brdo:mixed_refs:cqm=eqm_avc_hr.cfg:psnr:bitrate=1300 -oac copy -of rawvideo

mencoder $NAME.vob -o /dev/null -ofps 24000/1001 -vf crop=720:464:0:6,pullup,softskip,harddup -ovc x264 -x264encopts threads=auto:subq=7:partitions=all:8x8dct:me=umh:frameref=15:bframes=5:direct_pred=auto:nofast_pskip:b_pyramid:weight_b:nodct_decimate:pass=3:trellis=2:bime:brdo:mixed_refs:cqm=eqm_avc_hr.cfg:psnr:bitrate=1300 -oac copy -of rawvideo

mencoder $NAME.vob -o $NAME.264 -ofps 24000/1001 -vf crop=720:464:0:6,pullup,softskip,harddup -ovc x264 -x264encopts threads=auto:subq=7:partitions=all:8x8dct:me=umh:frameref=15:bframes=5:direct_pred=auto:nofast_pskip:b_pyramid:weight_b:nodct_decimate:pass=3:trellis=2:bime:brdo:mixed_refs:cqm=eqm_avc_hr.cfg:psnr:bitrate=1300 -oac copy -of rawvideo

mkvmerge -o $NAME.mkv --default-duration 0:24000/1001fps $NAME.264 $NAME.ogg $NAME.idx
```

---

### Post by DasCrushinator on 2008-03-20
> **IronLike Monkey said:**
> Don't laugh, I have a dedicated machine for just encoding and its pretty peppy, so I max out all my settings...

Me too :D

---

### Post by HoverHell on 2008-03-20
> **IronLike Monkey said:**
> ```
...:pass=3:...
```

You run encoding with "pass=3" twice... is it really right or there should be "pass=2"?

---

### Post by IronLike Monkey on 2008-03-20
> **HoverHell said:**
> You run encoding with "pass=3" twice... is it really right or there should be "pass=2"?

Thats a very logical assumption, but as it turns out pass=3 is correct.

Take a look at the Mencoder manual:
> 
pass=<1&#8722;3>
	

Enable 2 or 3-pass mode. It is recommended to always encode in 2 or 3-pass mode as it leads to a better bit distribution and improves overall quality.
	

1
		

first pass
	

2
		

second pass (of two pass encoding)
	

3
		

Nth pass (second and third passes of three pass encoding)
	

Here is how it works, and how to use it:
The first pass (pass=1) collects statistics on the video and writes them to a file. You might want to deactivate some CPU-hungry options, apart from the ones that are on by default.
In two pass mode, the second pass (pass=2) reads the statistics file and bases ratecontrol decisions on it.
In three pass mode, the second pass (pass=3, that is not a typo) does both: It first reads the statistics, then overwrites them. You can use all encoding options, except very CPU-hungry options.
The third pass (pass=3) is the same as the second pass, except that it has the second pass&#8217; statistics to work from. You can use all encoding options, including CPU-hungry ones.
The first pass may use either average bitrate or constant quantizer. ABR is recommended, since it does not require guessing a quantizer. Subsequent passes are ABR, and must specify bitrate.

---

### Post by dkaplowitz on 2008-04-27
When running the command: 
```

mplayer dvd://1 -v -dumpstream -dumpfile title.vob

```

I am getting: 

```

Angle-seek synced by cell/vob IDN search!  
--- END OF CELL !!! ---
DVD next cell: 1  pack: 0xC58-0xCBC  
--- END OF CELL !!! ---
Core dumped ;)
vo: x11 uninit called but X11 not inited..

Exiting... (End of file)

```

Did I miss something obvious? My google searches aren't yielding much useful (or recent) information about this error I'm getting. I'm running a pretty fresh install of 8.04/Hardy.

---

### Post by HoverHell on 2008-04-27
>>Did I miss something obvious?

What do you think is error there?...

Anyway, I suppose you have few titles on your dvd, so try dvd://2 and so on.

---

### Post by dkaplowitz on 2008-04-27
Error was that no content appeared to be ripped from the DVD. I should have tried your suggestion before posting because at  dvd://3 it seems to be extracting from the DVD. So looks to be working now. Thanks!

---

### Post by DasCrushinator on 2008-05-07
> **IronLike Monkey said:**
> Don't laugh, I have a dedicated machine for just encoding and its pretty peppy, so I max out all my settings. I bascially beefed up a script I found on this thread:

```
#!/bin/bash

#Usage dvdrip <NAME>

NAME=$1

mkdir ~/$NAME

cd ~/$NAME

mplayer dvd://1 -dumpstream -dumpfile $NAME.vob

mencoder dvd://1 -nosound -ovc frameno -o /dev/null -slang en -vobsubout $NAME

mplayer $NAME.vob -ao pcm:file=$NAME.wav -vc dummy -aid 128 -vo null 

normalize-audio $NAME.wav

oggenc -q5 $NAME.wav 

mencoder $NAME.vob -o /dev/null -ofps 24000/1001 -vf crop=720:464:0:6,pullup,softskip,harddup -ovc x264 -x264encopts threads=auto:subq=7:partitions=all:8x8dct:me=umh:frameref=15:bframes=5:direct_pred=auto:nofast_pskip:b_pyramid:weight_b:nodct_decimate:pass=1:trellis=2:bime:brdo:mixed_refs:cqm=eqm_avc_hr.cfg:psnr:bitrate=1300 -oac copy -of rawvideo

mencoder $NAME.vob -o /dev/null -ofps 24000/1001 -vf crop=720:464:0:6,pullup,softskip,harddup -ovc x264 -x264encopts threads=auto:subq=7:partitions=all:8x8dct:me=umh:frameref=15:bframes=5:direct_pred=auto:nofast_pskip:b_pyramid:weight_b:nodct_decimate:pass=3:trellis=2:bime:brdo:mixed_refs:cqm=eqm_avc_hr.cfg:psnr:bitrate=1300 -oac copy -of rawvideo

mencoder $NAME.vob -o $NAME.264 -ofps 24000/1001 -vf crop=720:464:0:6,pullup,softskip,harddup -ovc x264 -x264encopts threads=auto:subq=7:partitions=all:8x8dct:me=umh:frameref=15:bframes=5:direct_pred=auto:nofast_pskip:b_pyramid:weight_b:nodct_decimate:pass=3:trellis=2:bime:brdo:mixed_refs:cqm=eqm_avc_hr.cfg:psnr:bitrate=1300 -oac copy -of rawvideo

mkvmerge -o $NAME.mkv --default-duration 0:24000/1001fps $NAME.264 $NAME.ogg $NAME.idx
```

So I basically just did this script except with 2 passes and 1500 bit rate, and I see no quality difference and a sizable file size increase.  Should I try it with 3 passes?  The video quality is no different than when I was ripping without the matrix and only a bit rate of 1000, but is about 80MB larger (22 minute episode).

---

### Post by DasCrushinator on 2008-05-08
I just completed using your exact script with the matrix and still don't see anything but a size increase :(

---

### Post by DasCrushinator on 2008-05-17
> **DasCrushinator said:**
> I just completed using your exact script with the matrix and still don't see anything but a size increase :(

Any idea Ironlike Monkey?

---

### Post by Nepherte on 2008-05-20
I'm having trouble encoding a vob file. Never had an issue with it until now. This is the output I get:
```
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-arts --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder
init_freetype
get_path('font/font.desc') -> '/home/bart/.mplayer/font/font.desc'
font: can't open file: /home/bart/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
[file] File size is 1837942784 bytes
STREAM: [file] title16.vob
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
success: format: 0  data: 0x0 - 0x6d8cc800
LAVF_check: MPEG PS format
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename title16.vob ext: .vob
Trying demuxer 2 based on filename extension
system stream synced at 0xD (13)!
==> Found video stream: 0
==> Found audio stream: 130
==> Found audio stream: 129
==> Found audio stream: 128
==> Found subtitle: 4
MPEG-PS file format detected.
Searching for sequence header... OK!
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x576  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
Using SSE optimized IMDCT transform
AC3: 2.0 (dolby)  48000 Hz  192.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0xA
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[file] File size is 0 bytes
STREAM: [file] title16.264
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [crop w=720 h=576 x=0 y=0]
Crop: 720 x 576, 0 ; 0
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[libaf] Adding filter format 
[format] Changing sample format from little-endian 16-bit signed int to big-endian 8-bit signed int
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[format] Changing sample format from little-endian 16-bit signed int to big-endian 8-bit signed int
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=24000 sample-1)
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (720x576->1024x576,flags=0,'MPlayer',0x32315659)
[swscaler @ 0x8810770]SwScaler: using unscaled yuv420p -> yuv420p special converter
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x400  
REQ: flags=0x403  req=0x0  
REQ: flags=0x3  req=0x0  
x264 [error]: no ratecontrol method specified
x264_encoder_open failed.
FATAL: Cannot initialize video driver.

Exiting...
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-arts --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder
init_freetype
get_path('font/font.desc') -> '/home/bart/.mplayer/font/font.desc'
font: can't open file: /home/bart/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
[file] File size is 1837942784 bytes
STREAM: [file] title16.vob
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
success: format: 0  data: 0x0 - 0x6d8cc800
LAVF_check: MPEG PS format
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename title16.vob ext: .vob
Trying demuxer 2 based on filename extension
system stream synced at 0xD (13)!
==> Found video stream: 0
==> Found audio stream: 130
==> Found audio stream: 129
==> Found audio stream: 128
==> Found subtitle: 4
MPEG-PS file format detected.
Searching for sequence header... OK!
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x576  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
Using SSE optimized IMDCT transform
AC3: 2.0 (dolby)  48000 Hz  192.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0xA
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[file] File size is 0 bytes
STREAM: [file] title16.264
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [crop w=720 h=576 x=0 y=0]
Crop: 720 x 576, 0 ; 0
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[libaf] Adding filter format 
[format] Changing sample format from little-endian 16-bit signed int to big-endian 8-bit signed int
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[format] Changing sample format from little-endian 16-bit signed int to big-endian 8-bit signed int
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=24000 sample-1)
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (720x576->1024x576,flags=0,'MPlayer',0x32315659)
[swscaler @ 0x8810770]SwScaler: using unscaled yuv420p -> yuv420p special converter
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x400  
REQ: flags=0x403  req=0x0  
REQ: flags=0x3  req=0x0  
x264 [error]: no ratecontrol method specified
x264_encoder_open failed.
FATAL: Cannot initialize video driver.
```

The file I use is the following:
```
# First pass
mencoder -v\
         title16.vob\
        -vf crop=720:576:0:0,harddup\
        -ovc x264 x264encopts threads=auto subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000\
        -oac copy\
        -of rawvideo\
        -o title16.264

# Second pass
mencoder -v\
         title16.vob\
        -vf crop=720:576:0:0,harddup\
        -ovc x264 x264encopts threads=auto subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000\
        -oac copy\
        -of rawvideo\
        -o title16.264
```
Any thoughts on this?

---

### Post by HoverHell on 2008-05-20
> **Nepherte said:**
> 
```

x264 [error]: no ratecontrol method specified
x264_encoder_open failed.
FATAL: Cannot initialize video driver.
Exiting...

``````

x264encopts threads=auto subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000\

```

Shouldn't it be ```
x264encopts threads=auto:subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000\
```?
Anyway, either x264 doesn't understand "bitrate=1000" or (more likely) you didn't supply it properly (forgot a colon).

---

### Post by Nepherte on 2008-05-20
Yea my bad it should be: ```
x264encopts threads=auto:subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000\
```
But changing it didn't work either. I don't really see why it wouldn't understand bitrate=1000. I've used exactly the same code (copy/paste from first topic post) to encode like 100+ vob files, only changing the input and output name.

---

### Post by Nepherte on 2008-05-20
After redoing the whole process again, it starts encoding properly. I guess it was a typo somewhere.

---

### Post by Nepherte on 2008-05-20
I was a bit too fast with my conclusion. The first pass didn't have any problems, the second pass gave me the same error.

Replacing 4x4mv by partitions=all and removing me=3 solved the problem.

---

### Post by DasCrushinator on 2008-05-20
Anyone know how to mux two video files and two audio files together?  I have the 10 Commandments on DVD, but the movie is split into two discs.

---

### Post by Pconfig on 2008-05-27
Heya

i'm trying to get some dvd's (which are alraedy copied) onto my pc. But i seem to get a problem with 1 of them. I'm dealing with a progressive pal video here and it has constant framerate of 25fps (well not very stable).

Still when encoding i get alot of duplicate frames at random moments. Any ideas?
```
Pos:2347.0s  56280f (38%)  40fps Trem:  37min 715mb  A-V:0.013 [990:192] A/Vms 7/22 D/B/S 2404/4/1 
1 duplicate frame(s)!
Pos:2348.0s  56304f (38%)  40fps Trem:  37min 715mb  A-V:0.017 [990:192] A/Vms 7/22 D/B/S 2405/4/1 
1 duplicate frame(s)!
Pos:2349.1s  56330f (38%)  40fps Trem:  37min 715mb  A-V:0.031 [990:192] A/Vms 7/22 D/B/S 2406/4/1 
1 duplicate frame(s)!
Pos:2350.1s  56354f (38%)  40fps Trem:  37min 715mb  A-V:0.002 [990:192] A/Vms 7/22 D/B/S 2407/4/1 
1 duplicate frame(s)!
Pos:2351.0s  56377f (38%)  40fps Trem:  37min 715mb  A-V:0.013 [990:192] A/Vms 7/22 D/B/S 2408/4/1 
1 duplicate frame(s)!
Pos:2351.9s  56397f (38%)  40fps Trem:  37min 715mb  A-V:-0.001 [990:192] A/Vms 7/22 D/B/S 2409/4/1 
1 duplicate frame(s)!
Pos:2352.9s  56421f (38%)  40fps Trem:  37min 716mb  A-V:0.012 [990:192] A/Vms 7/22 D/B/S 2410/4/1  
1 duplicate frame(s)!
Pos:2354.0s  56447f (38%)  40fps Trem:  37min 716mb  A-V:-0.001 [990:192] A/Vms 7/22 D/B/S 2411/4/1 
1 duplicate frame(s)!
Pos:2355.0s  56471f (38%)  40fps Trem:  37min 716mb  A-V:0.013 [990:192] A/Vms 7/22 D/B/S 2412/4/1  
1 duplicate frame(s)!
Pos:2355.9s  56494f (38%)  40fps Trem:  37min 716mb  A-V:0.012 [990:192] A/Vms 7/22 D/B/S 2413/4/1  
1 duplicate frame(s)!
Pos:2356.9s  56518f (38%)  40fps Trem:  37min 716mb  A-V:0.003 [990:192] A/Vms 7/22 D/B/S 2414/4/1 
1 duplicate frame(s)!
Pos:2357.8s  56538f (38%)  40fps Trem:  37min 716mb  A-V:0.014 [990:192] A/Vms 7/22 D/B/S 2415/4/1 
1 duplicate frame(s)!
Pos:2358.8s  56564f (38%)  40fps Trem:  37min 716mb  A-V:0.003 [989:192] A/Vms 7/22 D/B/S 2416/4/1 
1 duplicate frame(s)!
Pos:2359.8s  56588f (38%)  40fps Trem:  37min 716mb  A-V:0.015 [989:192] A/Vms 7/22 D/B/S 2417/4/1 
1 duplicate frame(s)!
Pos:2360.8s  56611f (38%)  40fps Trem:  37min 716mb  A-V:0.003 [989:192] A/Vms 7/22 D/B/S 2418/4/1 
1 duplicate frame(s)!
Pos:2361.8s  56635f (38%)  40fps Trem:  37min 716mb  A-V:0.015 [989:192] A/Vms 7/22 D/B/S 2419/4/1 
1 duplicate frame(s)!
Pos:2362.6s  56655f (38%)  40fps Trem:  37min 716mb  A-V:0.017 [989:192] A/Vms 7/22 D/B/S 2420/4/1 
1 duplicate frame(s)!
Pos:2363.7s  56681f (38%)  40fps Trem:  37min 716mb  A-V:0.029 [989:192] A/Vms 7/22 D/B/S 2421/4/1 
1 duplicate frame(s)!
Pos:2364.7s  56705f (38%)  40fps Trem:  37min 716mb  A-V:0.004 [989:192] A/Vms 7/22 D/B/S 2422/4/1 
1 duplicate frame(s)!
Pos:2365.7s  56728f (38%)  40fps Trem:  37min 716mb  A-V:0.013 [989:192] A/Vms 7/22 D/B/S 2423/4/1 
1 duplicate frame(s)!

```
This is happening all over the movie.

I can't seem to get the subtitle stream either. Normally they have a language assigned, but this one hasn't. How can i rip those subs?

Thanks!

---

### Post by soxs on 2008-05-31
Getting some nasty error:
```
...
[swscaler @ 0xdda790]SwScaler: using unscaled yuv420p -> yuv420p special converter
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x400  
REQ: flags=0x403  req=0x0  
REQ: flags=0x3  req=0x0  
x264 [error]: no ratecontrol method specified
x264_encoder_open failed.
FATAL: Cannot initialize video driver.
```fglrx 8.5 is correctly installed (for sure), so what should I do? I own a readeonHD 3870

EDIT_1: Ok, got it, I misplaced threads=auto
EDIT_2: It finally ends with the same error, while endcoding the .vob to .264, but just at the very end and the title.264 file gets zer0 bytes, but while it is coding I can watch it like the .vob-video???

---

### Post by themuddler on 2008-06-02
For those after a simple way (in my opinion!):

I use [[COLOR="Blue"]dvdshrink[/COLOR]]("http://www.dvdshrink.org/") under wine (wine is available under the add/remove menu option in the ubuntu applications menu) to get the dvd onto my hard disk.  This allows me to only rip the audio and subtitles for my language and cut out dvd extras at that stage.

Then I use [[COLOR="Blue"]Handbrake[/COLOR]]("http://handbrake.fr/?article=download") to do the rest.  The download is a compressed executable.  Once you've extracted it, put it (HandBrakeCLI - note the capital B) in /usr/bin/ so you can access it easily from the command line.  I then put the below aliases in ~/.bashrc

```
alias hb264='/usr/bin/HandBrakeCLI -e x264 -E faac -m -2 -T -P 16'
alias hbxvid='/usr/bin/HandBrakeCLI -e xvid -E faac -m -2 -P 16'
```

Then I set handbrake going (in a new console so it knows the aliases) with ```
hb264 -i Shrek/ -o Shrek.mp4 -S 1000
```

The -S is for the target size in kb. The Shrek/ folder is the one created by dvdshrink and which should contain VIDEO_TS.

Hope that helps someone.  I'll gladly take any advice on how to do this even more easily.

---

### Post by mailbox on 2008-06-13
> **DasCrushinator said:**
> Anyone know how to mux two video files and two audio files together?  I have the 10 Commandments on DVD, but the movie is split into two discs.You could try using *cat* to combine the vobs.

---

### Post by DasCrushinator on 2008-06-13
> **mailbox said:**
> You could try using *cat* to combine the vobs.

I must be a little dense.  Could you elaborate on what I need to do with cat?

---

### Post by mailbox on 2008-06-13
> **DasCrushinator said:**
> I must be a little dense.  Could you elaborate on what I need to do with cat?*cat firsthalf.vob secondhalf.vob > combined.vob*
It doesn't always work out, and could take some time, but give it a shot anyway, and remember to save the originals just in case.

---

### Post by DasCrushinator on 2008-06-14
> **mailbox said:**
> *cat firsthalf.vob secondhalf.vob > combined.vob*
It doesn't always work out, and could take some time, but give it a shot anyway, and remember to save the originals just in case.

Will do, thanks!

It worked!  I was about to just give up and delete the files from ripping the DVD until I saw your post, so thank you very much for taking the time to help me out!

---

### Post by mailbox on 2008-06-15
> **DasCrushinator said:**
> Will do, thanks!

It worked!  I was about to just give up and delete the files from ripping the DVD until I saw your post, so thank you very much for taking the time to help me out!No worries man, just passing along information.

---

### Post by danhm on 2008-08-13
I'm getting the "The selected video_out device is incompatible with this codec" error. :(

The first pass is fine, but it fails on the second pass.

mencoder output:
```

MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ (Family: 15, Model: 107, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option x264encopts: Unknown suboption 8×8dct
Configuration: --enable-runtime-cpudetection --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-arts --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-gui --enable-mencoder
init_freetype
get_path('font/font.desc') -> '/home/dan/.mplayer/font/font.desc'
font: can't open file: /home/dan/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
[file] File size is 1226825728 bytes
STREAM: [file] ep1.vob
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
success: format: 0  data: 0x0 - 0x491fe000
LAVF_check: MPEG PS format
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename ep1.vob ext: .vob
Trying demuxer 2 based on filename extension
system stream synced at 0xD (13)!
==> Found video stream: 0
==> Found audio stream: 128
==> Found audio stream: 129
==> Found audio stream: 130
==> Found audio stream: 131
MPEG-PS file format detected.
Searching for sequence header... OK!
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  3000.0 kbps (375.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
[file] File size is 0 bytes
STREAM: [file] ep1.264
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [crop w=704 h=480 x=10 y=0]
Crop: 704 x 480, 10 ; 0
Opening video filter: [softskip]
Opening video filter: [pullup]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Trying filter chain: pullup softskip crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale pullup softskip crop harddup expand x264
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
Trying filter chain: pullup softskip crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale pullup softskip crop harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (720x480->720x540,flags=0,'MPlayer',0x32315659)
[swscaler @ 0xdd9330]SwScaler: using unscaled yuv420p -> yuv420p special converter
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x400  
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x400  
REQ: flags=0x403  req=0x0  
REQ: flags=0x3  req=0x0  
FATAL: Cannot initialize video driver.

Exiting...

```

My videnc:
```

# First pass
mencoder -v ep1.vob -vf pullup,softskip,crop=704:480:10:0,harddup -ovc x264 -x264encopts threads=auto:subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1125 -nosound -of rawvideo -o ep1.264

# Second pass
mencoder -v ep1.vob -vf pullup,softskip,crop=704:480:10:0,harddup -ovc x264 -x264encopts threads=auto:subq=6:partitions=all:8×8dct:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1125 -nosound -of rawvideo -o ep1.264

```

Did I miss a post that tells me what to do?

---

### Post by danhm on 2008-08-13
Wooo figured it out!

I had "8×8dct" instead of "8x8dct". Dumb cut and paste screwed me!

---

### Post by redrum on 2008-08-22
Hi folks,

Is there any reason related to hardware or configuration that might explain why I can make a second pass with the following option :

```
"subq=4:bframes=2:b_pyramid:weight_b"
```

and not with those ones :

```
"subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b"
```

It's been hours that I've tried to understand where's the bug but I can't find !

---

### Post by snowniak on 2008-09-07
Cool!

It worked smoothly, nice post man,

Thanks!

---

### Post by soxs on 2008-09-07
> **redrum said:**
> Hi folks,

Is there any reason related to hardware or configuration that might explain why I can make a second pass with the following option :

```
"subq=4:bframes=2:b_pyramid:weight_b"
```

and not with those ones :

```
"subq=6:partitions=all:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b"
```

It's been hours that I've tried to understand where's the bug but I can't find !

Same here, and it's a really good question..

```
# First pass (works)
mencoder -v\
         test.vob\
        -vf crop=720:416:0:80,harddup\
        -ovc x264 -x264encopts threads=auto:subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=2000\
        -oac copy\
        -of rawvideo\
        -o test.264

# Second pass (doesn't even start)

mencoder -v\
         f4ss.vob\
        -vf crop=720:416:0:80,harddup\
        -ovc x264 -x264encopts threads=auto:qcomp=0.7:subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=2000\
        -oac copy\
        -of rawvideo\
        -o f4ss.264
```

These are the last lines from console output:
```
----------------------------
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO Config (720x576->1024x576,flags=0,'MPlayer',0x32315659)
[swscaler @ 0xdda790]SwScaler: using unscaled yuv420p -> yuv420p special converter
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x400  
REQ: flags=0x403  req=0x0  
REQ: flags=0x3  req=0x0  
FATAL: Cannot initialize video driver.

Exiting...

```

EDIT:
replacing ```

:4x4mv:8x8dct:me=3
```
 with ```

:partitions=all:me=umh
```
makes the whole thing work again... odd...

---

### Post by redrum on 2008-09-25
Thanks for the reply.

I've noticed the fact that I need to have the same bframes between the two passes otherwise the video driver cannot initialize.

This is not described in this topic.

What do you think?

---

### Post by carterw65 on 2008-10-16
Hi Ev!
I am new here and trying to figure out this DVD stuff. Can you tell me how to use this script. I don't know scripting. I need a DVD ripper for dummies tutorial I am afraid.

Thanks,

Bill

---

### Post by soxs on 2008-10-16
> **carterw65 said:**
> Hi Ev!
I am new here and trying to figure out this DVD stuff. Can you tell me how to use this script. I don't know scripting. I need a DVD ripper for dummies tutorial I am afraid.

Thanks,

Bill

execute the script via opening a terminal and changeing into the directory where your videnc file lies and type ```
./videnc
``` and everything should be done.

Readd here in case you don't know how to chnage your current working directory: [http://ubuntuforums.org/showpost.php?p=5718364&postcount=7](http://ubuntuforums.org/showpost.php?p=5718364&postcount=7)

---

### Post by carterw65 on 2008-10-16
Thanks for replying Soxs, but I am clueless how to take the information and make it a runnable script.I wonder if anyone has made a DVD ripping for dummies guide?

Thanks,

Bill

---

### Post by soxs on 2008-10-17
> **carterw65 said:**
> Thanks for replying Soxs, but I am clueless how to take the information and make it a runnable script.I wonder if anyone has made a DVD ripping for dummies guide?

Thanks,

Bill

To make it runable, you have to check "executable" in the rightclick menu or do it via ```
chmod +x yourfile
```

Btw you could still use frontends like ogmrip or dvdrip

---

### Post by carterw65 on 2008-10-17
I have been trying to use Heinz version of this. When I got to MMG it errored with this:

Maximum number of clients reachedError: Unable to initialize gtk, is DISPLAY set properly?

Anyone have any idea what I should do?

Thanks!

---

### Post by carterw65 on 2008-10-20
> **encho said:**
> I have just seen this guide, nice one. But there is one point I wish to make.
Using matroska is cool, it is open source, etc. Also vorbis - excellent quality, small sizes, etc. But, if you really want to make your video archive, I suggest that you go with x264/avc (video) and faac/aac (audio), all muxed in mp4 container. Why? Because future HD DVD devices and Blue Ray are going to support that format straight from your file. Even now you can buy some classic dvd players - check the [Nero certified devices]("http://ww2.nero.com/nerodigital/enu/DVD_Player_Recorder.html").

And it is not huge difference for the encoding process - you still create x264 video stream - the only difference is in audio and container.

After a lot of researching, testing and waiting, I have found out that:



produces the best results in one pass - constant quality based (where %f is input file - I am using thunar's scripts).
And:

produces hi-quality aac audio.
Finally:

mux them together in MP4 container, very compatible and reliable.

I also got few tricks for converting pal to ntsc and vice versa.

Instead of having 4 gig mpegs or 1 gig Xvids, I have 500mb(!) hi quality mp4s in my video collection.

Even if you have your collection in mkv format (I did), there is an easy way to remux them to mp4 (without any quality loss). Just something like:


Although you will have non-standard MP4 (with vorbis audio), but maybe those will be supported some time. You can always reencode audio as well.

Hope this helps to someone.:)

Can anyone tell me how I figure out the %f? I am not sure what to do here.

Thanks

---

### Post by soxs on 2008-10-21
Path to your input file, e.g. when it is ontop of your dekstop:%f is ```
/home/<yourusername>/Desktop/<videofilename>.<extension>
```

---

### Post by reeseslover531 on 2008-11-11
I am getting horrible out of sync issues between my audio and my video.  I think I have done everything right.  I attached my videnc file, can anyone help me??

thanks!

---

### Post by bluekarasu on 2008-12-12
How to rip all subtitles in one command? 
I use the -sid (or slang), but if the DVD contain 3 languages, I have to run 3 times the command to rip all sutitles in the .idx and .sub files.


thank you

---

### Post by lastchancetosee on 2008-12-14
Hi &thanks for the guide to Heinz.

I've created a script to automate/facilitate this process (attached below). Anyone want to try it, go ahead.
Disclaimer:
It is only my third real bash script (and the last time I programmed something in other languages is some time ago as well) so there are probably thousands of things I could have done better.
If anyone has the patience to read & understand other people's code (I often don't) and finds something I did wrong/stupidly/less than perfect - I'd welcome any hints.

The script basically takes a .vob and

1.) detects the cropping parameters (via -vf cropdetect)
2.) displays the result in mplayer (via -vf rectangle) for you to check
3.) rips&encodes the desired audio streams
4.) calculates the bitrate for desired size
5.) encodes the video and finally
6.) puts it into a mp4-container

Everything requiering user interaction is done first so you can start it and let it run over night. You end up with one .mp4 containing your H.264-encoded video and one .ac3 or .ogg for every audio stream you specified.

Simplest way to use it: invoke "autoenc.sh -a <AIDs_etc> -s <desired_size> inputfile" in the dir where you want the video created.
There are some other options, described in autoenc_man.txt.

USAGE OF -a OPTION:
-a expects a string containing all AIDs to process together with their respective encoding quality in the format '-a AID1:quality1:AID2:quality2:AID3:quality3' an so on. Possible quality-values are identical with oggenc's, default is 5. In addition, using 'c' as quality results in the audiostream being just dumped to .ac3. If a value is omitted, the defaults (AID 128, quality 5) are used.

Examples:
'-a :'		&#8594; Encode default stream to default quality
'-a ::130:7'	&#8594; Same as above, but also encode stream 130 to quality 7
'-a 128:c:129:'	&#8594; Copy stream 128 to ac3-stream and encode stream 129 to default quality
'-a :2'		&#8594; Encode default stream to quality 2

What I don't like about it:
- quiet mode isn't working to well, since I haven't yet found a way to silence mplayer/mencoder.
- anyone know a way to get a reliable video duration from the single huge .vob dumped by mplayer? It seems to me mplayer only ever displays the length of the first .vob on the dvd, i.e. doesn't set the ID_LENGTH-flag to it's new value.
- connected to that: There were some problems getting ID_LENGTH from one of my testing-.ac3's. I'm not yet sure whether that was mplayer's or the file's fault.
- all the ${[])(#%-stuff in bash-scripts gives me eye-cancer.

---

### Post by lastchancetosee on 2008-12-14
> **bluekarasu said:**
> How to rip all subtitles in one command? 
I use the -sid (or slang), but if the DVD contain 3 languages, I have to run 3 times the command to rip all sutitles in the .idx and .sub files.


thank you

You could either string all rip-commands together in one line like this:

<rip_first>;<rip_second>;...

or use a for-loop:
In a bash-script type (assuming you want to use title 1 of the dvd, adapt as necessary):

```
#!/bin/bash

for language in en de fr 
do
   mencoder dvd://1 -nosound -ovc frameno -o /dev/null -slang $language -vobsubout title_$language
done

exit 0
```

Replace "en de fr" with whatever subs you need. This will automatically rip to title_(en,fr,de).sub/.idx files.

---

### Post by drworm01 on 2008-12-17
I'm having a strange problem with MKV File Creator. I generally followed the steps outlined at the beginning of this post except for the MP4Box one. The MKV GUI had a drop down to set the fps of the video and that always did the job for me without the extra MP4 step. Only today when I try to mux my 264 with my audio I get the following error:

```
Error: '30000/1001fps' is not a valid default duration in '--default-duration 30000/1001fps'.
```

--default-duration 0:30000/1001fps is the code the GUI generates for the fps entry on the video. I'd get the same failure with 30fps 29.97fps and trying to do it via the command line. Can anyone tell me what changed between last week, when MKV had no issues with this command (with 30fps video) and this week when it no longer works? The process still works fine if I put the video into an MP4 container first, but I want to know what caused the change.

Thanks for your time.

---

### Post by hopelessone on 2008-12-28
hi,

I'm up to step 5.2 Start video encoding process

i get the following error:

> MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  

Flushing video frames.

Video stream: 1014.261 kbit/s  (126782 B/s)  size: 350680646 bytes  2766.000 secs  69153 frames

Audio stream:  192.000 kbit/s  (24000 B/s)  size: 66362880 bytes  2765.120 secs
Uninit audio filters...
[libaf] Removing filter dummy 
[libaf] Removing filter format 
Uninit audio: liba52
Uninit video: libmpeg2
x264 [info]: slice I:702   Avg QP:28.68  size: 26691  PSNR Mean Y:37.48 U:42.02 V:42.98 Avg:38.51 Global:36.38
x264 [info]: slice P:33622 Avg QP:29.80  size:  7794  PSNR Mean Y:35.51 U:40.63 V:42.00 Avg:36.67 Global:35.04
x264 [info]: slice B:34825 Avg QP:30.47  size:  2006  PSNR Mean Y:36.01 U:40.84 V:42.27 Avg:37.13 Global:35.93
x264 [info]: mb I  I16..4: 42.4%  0.0% 57.6%
x264 [info]: mb P  I16..4: 13.6%  0.0%  7.7%  P16..4: 33.9%  8.9%  1.9%  0.0%  0.0%    skip:33.9%
x264 [info]: mb B  I16..4:  1.1%  0.0%  0.5%  B16..8: 14.8%  0.0%  0.0%  direct:18.1%  skip:65.5%
x264 [info]: final ratefactor: 28.16
x264 [info]: PSNR Mean Y:35.781 U:40.751 V:42.146 Avg:36.919 Global:35.476 kb/s:1014.20
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option x264encopts: Unknown suboption 4x4mv
Option x264encopts: Bad argument me=3
Configuration: --enable-runtime-cpudetection --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-arts --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-gui --enable-mencoder
init_freetype
get_path('font/font.desc') -> '/home/some/.mplayer/font/font.desc'
font: can't open file: /home/some/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
[file] File size is 1924634624 bytes
STREAM: [file] title2.vob
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
success: format: 0  data: 0x0 - 0x72b79800
LAVF_check: MPEG PS format
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename title2.vob ext: .vob
Trying demuxer 2 based on filename extension
system stream synced at 0xD (13)!
==> Found video stream: 0
==> Found audio stream: 128
MPEG-PS file format detected.
Searching for sequence header... OK!
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9250.0 kbps (1156.2 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x576  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
Using SSE optimized IMDCT transform
AC3: 2.0 (stereo)  48000 Hz  192.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0x2
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[file] File size is 0 bytes
STREAM: [file] title2.264
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [crop w=688 h=576 x=14 y=0]
Crop: 688 x 576, 14 ; 0
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[libaf] Adding filter format 
[format] Changing sample format from little-endian 16-bit signed int to big-endian 8-bit signed int
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[format] Changing sample format from little-endian 16-bit signed int to big-endian 8-bit signed int
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=24000 sample-1)
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
Trying filter chain: crop harddup expand x264
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale crop harddup expand x264
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO Config (720x576->768x576,flags=0,'MPlayer',0x32315659)
[swscaler @ 0xe1f8d0]SwScaler: using unscaled yuv420p -> yuv420p special converter
REQ: flags=0x403  req=0x0  
REQ: flags=0x403  req=0x400  
REQ: flags=0x403  req=0x0  
REQ: flags=0x3  req=0x0  
FATAL: Cannot initialize video driver.

What does this mean and how can i fix this?

Thanks for helping..

---

### Post by andrew.46 on 2009-01-02
Hi hopelessone,

You seem to be encountering some trouble with x264. This could be a problem with the version of Mplayer you are using and the age of the x264 library you have installed.

Does your copy of Mencoder encode to x264? This can be seen:

```
andrew@skamandros:~$ mencoder -ovc help
MEncoder dev-SVN-r28237-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2


Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
  **[COLOR="Red"] x264     - H.264 encoding[/COLOR]**

```

Perhaps you might be better anyway to upgrade your copy of MPlayer and x264, results will always be better closer to the bleeding edge :-).

Andrew

---

### Post by Brian96 on 2009-01-26
This thread has been really helpful as I've made my first foray into transcoding DVD movies (tired of the kids rendering DVDs unplayable, so I want to get everything to the HDD). Anyway, I'm just dumping the .vob files at this point as storage space is not a constraint, but I've used the recipe from the OP (thanks!) to test transcoding the video to x264 and muxing it an the ac3 file into an mkv. A couple of questions:

1. When I compare the .mkv version of the movie and the .vob version, I notice some barely perceptible artifacts (e.g., super-faint sound "blips"). I also notice that the runtime is several minutes longer with the mkv. I got a TON of "Duplicate frames!" messages in the output when I ran the transcoding part of the recipe. (I did a double pass with softskip, pullup, and hardup filters.) Is this just the "lossy" part of the transcoding, or might I need to tweak it a bit?

2. When I run the command to grep the audio streams, I get the IDs for the streams (128, 129, etc.) but no info about what each stream contains. Is there a way to amend the code to provide this info? (I ask because I noticed on one of the DVDs I dumped that for some reason the first track was an AC3 with English and 2 channels, but the second track was AC3 with English and 6 channels. So using 128 as my default could let me down. I lean toward dumping the AC3 file and muxing it with the x264 file.)

I appreciate any help you can provide with either of these queries!

---

### Post by Brian96 on 2009-01-29
> **Brian96 said:**
> This thread has been really helpful as I've made my first foray into transcoding DVD movies (tired of the kids rendering DVDs unplayable, so I want to get everything to the HDD). Anyway, I'm just dumping the .vob files at this point as storage space is not a constraint, but I've used the recipe from the OP (thanks!) to test transcoding the video to x264 and muxing it an the ac3 file into an mkv. A couple of questions:

1. When I compare the .mkv version of the movie and the .vob version, I notice some barely perceptible artifacts (e.g., super-faint sound "blips"). I also notice that the runtime is several minutes longer with the mkv. I got a TON of "Duplicate frames!" messages in the output when I ran the transcoding part of the recipe. (I did a double pass with softskip, pullup, and hardup filters.) Is this just the "lossy" part of the transcoding, or might I need to tweak it a bit?

2. When I run the command to grep the audio streams, I get the IDs for the streams (128, 129, etc.) but no info about what each stream contains. Is there a way to amend the code to provide this info? (I ask because I noticed on one of the DVDs I dumped that for some reason the first track was an AC3 with English and 2 channels, but the second track was AC3 with English and 6 channels. So using 128 as my default could let me down. I lean toward dumping the AC3 file and muxing it with the x264 file.)

I appreciate any help you can provide with either of these queries!

bump?

---

### Post by u-slayer on 2009-03-08
I'm trying to encode mkv with this thread. It fails when I try to do the second pass:

```
mencoder -quiet $title.vob -vf crop=$crop,harddup -ovc x264 -x264encopts threads=auto:subq=6:4x4mv:8x8dct:me=3:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=$bitrate -oac copy -of rawvideo -o $title.264

MEncoder 2:1.0~rc1-0ubuntu13.3 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (Family: 15, Model: 107, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option x264encopts: Unknown suboption 4x4mv
Option x264encopts: Bad argument me=3
success: format: 0  data: 0x0 - 0xdca74000
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  7500.0 kbps (937.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [crop w=704 h=480 x=6 y=0]
Crop: 704 x 480, 6 ; 0
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=24000 sample-1)
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
SwScaler: using unscaled yuv420p -> yuv420p special converter
FATAL: Cannot initialize video driver.

Exiting...


```

any ideas?

---

### Post by NobodySpecial on 2009-03-08
u-slayer:

I'm not an expert on this, but I think its complaining about this:
> Option x264encopts: Unknown suboption 4x4mv
Option x264encopts: Bad argument me=3
I use "8x8dct" and "me=umh" instead.

---

### Post by u-slayer on 2009-03-11
Okay I used this thread to write a script. I got every step working but I am getting [COLOR="Red"]**HUGE**[/COLOR] a/v sync issues.

Here are my run lengths as reported by vlc:
```

Original file:
vob: 1:36:24

mp4: 1:55:34
mkv: 1:55:34

Audio tracks:
128.ac3 1:36:24
128.wav 1:36:24
128.ogg 1:19:07

129.ac3 1:36:24
129.wav 1:36:24
129.ogg 1:09:30
```

So the .ac3 and .wav files are behaving properly. But when I convert from .vob to .mp4 I get a big increase in run time which makes the audio off by almost 20 minutes.

Is there some option I'm missing in the conversion to mp4 that will fix my a/v sync issues?

Here's my mencoder:
```
mencoder "$temp/$title.vob" -vf $crop,harddup -ovc x264 -x264encopts threads=auto:subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=$bitrate -oac copy -of rawvideo -o "$temp/$title.264

mencoder "$temp/$title.vob" -vf $crop,harddup -ovc x264 -x264encopts threads=auto:subq=5:8x8dct:me=hex:frameref=2:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=$bitrate -oac copy -of rawvideo -o "$temp/$title.264
```

```
Encoding Video: Second Pass
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0xcd151000
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [crop w=704 h=464 x=10 y=6]
Crop: 704 x 464, 10 ; 6
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=24000 sample-1)
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[swscaler @ 0xe1f8d0]SwScaler: using unscaled yuv420p -> yuv420p special converter
x264 [info]: using SAR=835/704
x264 [info]: using cpu capabilities: MMX MMXEXT SSE SSE2 SSE3 SSSE3 Cache64 
Pos:   0.0s      1f ( 0%)  0.14fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Pos:   0.0s      2f ( 0%)  0.28fps Trem:   0min   0mb  A-V:0.003 [0:0]
1 duplicate frame(s)!
Pos:   0.5s     21f ( 0%)  2.93fps Trem:   0min   0mb  A-V:0.067 [0:192]
Skipping frame!
Pos:   0.9s     33f ( 0%)  4.56fps Trem:   0min   0mb  A-V:0.068 [0:192]
Skipping frame!
Pos:   2.3s     76f ( 0%) 10.14fps Trem:   0min   0mb  A-V:0.010 [7:192]]
1 duplicate frame(s)!
Pos:   2.5s     81f ( 0%) 10.72fps Trem:   0min   0mb  A-V:0.017 [24:192]
1 duplicate frame(s)!
Pos:   2.6s     82f ( 0%) 10.81fps Trem:   0min   0mb  A-V:0.019 [52:192]
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
Pos:   2.6s     83f ( 0%) 10.91fps Trem:   0min   0mb  A-V:0.020 [73:192]
1 duplicate frame(s)!
Pos:   2.8s     87f ( 0%) 11.27fps Trem:   0min   0mb  A-V:0.025 [197:192]
1 duplicate frame(s)!
Pos:   3.1s     95f ( 0%) 11.91fps Trem:   0min   0mb  A-V:0.011 [497:192]
1 duplicate frame(s)!
Pos:   3.2s     99f ( 0%) 12.18fps Trem:   0min   0mb  A-V:0.018 [772:192]
1 duplicate frame(s)!
Pos:   3.4s    103f ( 0%) 12.46fps Trem:   0min   0mb  A-V:0.022 [999:192]
1 duplicate frame(s)!
Pos:   3.6s    107f ( 0%) 12.76fps Trem:   0min   0mb  A-V:0.020 [1218:192]
1 duplicate frame(s)!
Pos:   3.7s    111f ( 0%) 12.96fps Trem:   0min   0mb  A-V:0.015 [1409:192]
1 duplicate frame(s)!
Pos:   3.9s    115f ( 0%) 13.24fps Trem:   0min   0mb  A-V:0.012 [1561:192]
1 duplicate frame(s)!
Pos:   4.1s    119f ( 0%) 13.46fps Trem:   0min   0mb  A-V:0.012 [1677:192]
1 duplicate frame(s)!
Pos:   4.2s    123f ( 0%) 13.70fps Trem:   0min   0mb  A-V:0.013 [1750:192]
1 duplicate frame(s)!
Pos:   4.4s    127f ( 0%) 13.97fps Trem:   0min   0mb  A-V:0.013 [1785:192]
1 duplicate frame(s)!
Pos:   4.6s    131f ( 0%) 14.20fps Trem:   0min   0mb  A-V:0.015 [1819:192]
1 duplicate frame(s)!
Pos:   4.7s    135f ( 0%) 14.45fps Trem:   0min   0mb  A-V:0.018 [1838:192]
1 duplicate frame(s)!
Pos:   4.9s    139f ( 0%) 14.67fps Trem:   0min   0mb  A-V:0.019 [1864:192]
1 duplicate frame(s)!
Pos:   5.1s    143f ( 0%) 14.90fps Trem: 148min 1068mb  A-V:0.022 [1896:192]
1 duplicate frame(s)!
Pos:   5.2s    147f ( 0%) 15.14fps Trem: 150min 1103mb  A-V:0.025 [1895:192]
1 duplicate frame(s)!
Pos:   5.4s    151f ( 0%) 15.36fps Trem: 152min 1147mb  A-V:0.027 [1911:192]
1 duplicate frame(s)!
Pos:   5.6s    155f ( 0%) 15.61fps Trem: 137min 1050mb  A-V:0.023 [1906:192]
1 duplicate frame(s)!
Pos:   5.7s    159f ( 0%) 15.83fps Trem: 138min 1079mb  A-V:0.018 [1902:192]
1 duplicate frame(s)!
Pos:   5.9s    163f ( 0%) 16.06fps Trem: 140min 1110mb  A-V:0.014 [1901:192]
1 duplicate frame(s)!
Pos:   6.1s    167f ( 0%) 16.28fps Trem: 126min 1020mb  A-V:0.013 [1899:192]
1 duplicate frame(s)!
Pos:   6.2s    171f ( 0%) 16.51fps Trem: 127min 1045mb  A-V:0.013 [1894:192]
1 duplicate frame(s)!
Pos:   6.4s    175f ( 0%) 16.73fps Trem: 129min 1070mb  A-V:0.014 [1889:192]
1 duplicate frame(s)!
Pos:   6.6s    179f ( 0%) 16.91fps Trem: 118min 997mb  A-V:0.015 [1889:192]]
1 duplicate frame(s)!
Pos:   6.7s    183f ( 0%) 17.06fps Trem: 120min 1022mb  A-V:0.018 [1889:192]
1 duplicate frame(s)!
Pos:   6.9s    187f ( 0%) 17.26fps Trem: 121min 1048mb  A-V:0.019 [1890:192]
1 duplicate frame(s)!
Pos:   7.1s    191f ( 0%) 17.43fps Trem: 112min 986mb  A-V:0.022 [1890:192]]
1 duplicate frame(s)!
Pos:   7.2s    195f ( 0%) 17.62fps Trem: 113min 1006mb  A-V:0.025 [1884:192]
1 duplicate frame(s)!
Pos:   7.4s    199f ( 0%) 17.81fps Trem: 115min 1026mb  A-V:0.027 [1878:192]
1 duplicate frame(s)!
Pos:   7.6s    203f ( 0%) 17.99fps Trem: 108min 980mb  A-V:0.023 [1873:192]]
1 duplicate frame(s)!
Pos:   7.7s    207f ( 0%) 18.17fps Trem: 109min 996mb  A-V:0.018 [1863:192]
1 duplicate frame(s)!
Pos:   7.9s    211f ( 0%) 18.36fps Trem: 110min 1012mb  A-V:0.014 [1854:192]
1 duplicate frame(s)!
Pos:   8.1s    215f ( 0%) 18.55fps Trem: 104min 965mb  A-V:0.013 [1844:192]]
1 duplicate frame(s)!
Pos:   8.2s    219f ( 0%) 18.73fps Trem: 105min 979mb  A-V:0.013 [1834:192]
1 duplicate frame(s)!
Pos:   8.4s    223f ( 0%) 18.93fps Trem: 106min 993mb  A-V:0.014 [1823:192]
1 duplicate frame(s)!
Pos:   8.6s    227f ( 0%) 19.11fps Trem: 101min 948mb  A-V:0.015 [1813:192]
1 duplicate frame(s)!
Pos:   8.7s    231f ( 0%) 19.28fps Trem: 102min 960mb  A-V:0.018 [1800:192]
1 duplicate frame(s)!
Pos:   8.9s    235f ( 0%) 19.45fps Trem: 102min 971mb  A-V:0.019 [1787:192]
1 duplicate frame(s)!
Pos:   9.1s    239f ( 0%) 19.63fps Trem:  98min 932mb  A-V:0.022 [1775:192]
1 duplicate frame(s)!
Pos:   9.2s    243f ( 0%) 19.79fps Trem:  99min 943mb  A-V:0.025 [1764:192]
1 duplicate frame(s)!
Pos:   9.4s    247f ( 0%) 19.96fps Trem:  99min 955mb  A-V:0.027 [1755:192]
1 duplicate frame(s)!
Pos:   9.6s    251f ( 0%) 20.13fps Trem:  96min 925mb  A-V:0.023 [1748:192]
1 duplicate frame(s)!
Pos:   9.7s    255f ( 0%) 20.29fps Trem:  96min 937mb  A-V:0.018 [1739:192]
1 duplicate frame(s)!
Pos:   9.9s    259f ( 0%) 20.46fps Trem:  97min 948mb  A-V:0.014 [1730:192]
1 duplicate frame(s)!
Pos:  10.1s    263f ( 0%) 20.61fps Trem:  93min 916mb  A-V:0.013 [1722:192]
1 duplicate frame(s)!
Pos:  10.2s    267f ( 0%) 20.78fps Trem:  94min 926mb  A-V:0.013 [1712:192]
1 duplicate frame(s)!
Pos:  10.4s    271f ( 0%) 20.93fps Trem:  95min 933mb  A-V:0.014 [1698:192]
1 duplicate frame(s)!
Pos:  10.6s    275f ( 0%) 21.08fps Trem:  92min 910mb  A-V:0.013 [1687:192]
1 duplicate frame(s)!
Pos:  10.7s    279f ( 0%) 21.25fps Trem:  93min 919mb  A-V:0.012 [1679:192]
1 duplicate frame(s)!
Pos:  10.9s    283f ( 0%) 21.42fps Trem:  93min 939mb  A-V:0.012 [1688:192]
1 duplicate frame(s)!
Pos:  11.1s    287f ( 0%) 21.55fps Trem:  90min 914mb  A-V:0.013 [1685:192]
1 duplicate frame(s)!
Pos:  11.2s    291f ( 0%) 21.71fps Trem:  91min 920mb  A-V:0.015 [1672:192]
1 duplicate frame(s)!
Pos:  11.4s    295f ( 0%) 21.89fps Trem:  92min 930mb  A-V:0.016 [1666:192]
1 duplicate frame(s)!
Pos:  11.6s    299f ( 0%) 22.02fps Trem:  89min 905mb  A-V:0.018 [1660:192]
1 duplicate frame(s)!
Pos:  11.7s    303f ( 0%) 22.12fps Trem:  90min 917mb  A-V:0.021 [1657:192]
1 duplicate frame(s)!
Pos:  11.9s    307f ( 0%) 22.27fps Trem:  90min 924mb  A-V:0.023 [1647:192]
1 duplicate frame(s)!
Pos:  12.1s    311f ( 0%) 22.45fps Trem:  87min 900mb  A-V:0.026 [1640:192]
1 duplicate frame(s)!
Pos:  12.2s    315f ( 0%) 22.55fps Trem:  88min 911mb  A-V:0.029 [1639:192]
1 duplicate frame(s)!
Pos:  12.4s    319f ( 0%) 22.69fps Trem:  89min 919mb  A-V:0.031 [1630:192]
1 duplicate frame(s)!
Pos:  12.6s    323f ( 0%) 22.81fps Trem:  86min 896mb  A-V:0.027 [1625:192]
1 duplicate frame(s)!
Pos:  12.7s    327f ( 0%) 22.94fps Trem:  87min 904mb  A-V:0.021 [1619:192]
1 duplicate frame(s)!
Pos:  12.9s    331f ( 0%) 23.08fps Trem:  87min 915mb  A-V:0.018 [1617:192]
1 duplicate frame(s)!
Pos:  13.1s    335f ( 0%) 23.23fps Trem:  85min 892mb  A-V:0.017 [1611:192]
1 duplicate frame(s)!
Pos:  13.2s    339f ( 0%) 23.35fps Trem:  85min 900mb  A-V:0.017 [1605:192]
1 duplicate frame(s)!
Pos:  13.4s    343f ( 0%) 23.48fps Trem:  86min 906mb  A-V:0.018 [1596:192]
1 duplicate frame(s)!
Pos:  13.6s    347f ( 0%) 23.57fps Trem:  83min 885mb  A-V:0.019 [1595:192]
1 duplicate frame(s)!
Pos:  13.7s    351f ( 0%) 23.71fps Trem:  84min 891mb  A-V:0.022 [1587:192]
1 duplicate frame(s)!
Pos:  13.9s    355f ( 0%) 23.80fps Trem:  84min 900mb  A-V:0.023 [1584:192]
1 duplicate frame(s)!
Pos:  14.1s    359f ( 0%) 23.92fps Trem:  82min 881mb  A-V:0.026 [1583:192]
1 duplicate frame(s)!
^Cs:  14.2s    363f ( 0%) 24.06fps Trem:  83min 889mb  A-V:0.029 [1580:192]
1 duplicate frame(s)!
Pos:  14.3s    364f ( 0%) 24.05fps Trem:  83min 892mb  A-V:0.029 [1578:192]
Flushing video frames.

```

---

### Post by balance07 on 2009-03-11
u-slayer:

i would suggest using some framerate control in your commands. put '-ofps 24000/1001' into your mencoder command and '-fps 23.976' into your MP4Box command.

if that doesn't help, then also post your MP4Box, mkvmerge and oggenc commands so we can see if those might be the cause of your problems.

---

### Post by u-slayer on 2009-03-11
okay, balance. I tried removing the harddup and it seems to have improved things: runtime of .mp4 1:32:29 (4 minutes off - I am going off the assumption that the original vob time was the correct one.)- 

I am now trying your solution with the -ofps. I'll post the results here in a couple hours.

---

### Post by u-slayer on 2009-03-11
> **balance07 said:**
> u-slayer:

i would suggest using some framerate control in your commands. put '-ofps 24000/1001' into your mencoder command and '-fps 23.976' into your MP4Box command.

if that doesn't help, then also post your MP4Box, mkvmerge and oggenc commands so we can see if those might be the cause of your problems.

Okay - I finished encoding my file and now its perfectly in sync. Thanks balance07. BTW, how did you know what frame rate to use? Is it always 24000/1001 or can it vary by dvd? I'd like to know so I can code my script to find out automatically.

---

### Post by balance07 on 2009-03-12
> **u-slayer said:**
> BTW, how did you know what frame rate to use? Is it always 24000/1001 or can it vary by dvd?

Personally, I determine the source framerate by just playing the .vob in mplayer via the command line, and reading the output. For example, a Futurama DVD has output like this:

```
A:   0.7 V:   0.7 A-V:  0.027 ct:  0.034  17/ 14 28% 52%  5.3% 0 0 
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
A:  29.7 V:  29.7 A-V: -0.000 ct:  0.102 714/711  6% 52%  0.8% 51 0 
demux_mpg: 30000/1001fps NTSC content detected, switching framerate.
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]    0.8% 51 0 
A:  87.2 V:  86.7 A-V:  0.450 ct:  0.174 2423/2420  4% 56%  0.6% 185 0 

```

It starts out as 24 fps then changes to 30 fps. As it continues to play, it switches back and forth. I treat this video as interlaced and use '-vf pullup,softskip,harddup,pp=lb' in the mencoder command. If it had been 24 fps and never changed to 30 fps, then it's a progressive video and doesn't get those filters.

I don't have it automatic in my script, I just have the script start to play, then when I've determined the rate, I CTRL-C the process and have the script READ a '24' or '30' that I type, and it uses the correct commands from there.

Prolly could do some fancy scripting to have it determine if it ever changes, but for me, that's too much work for little payoff. There may be some other tool that just straight-up tells you the .vob framerate, but if there is, i'm unaware of it.

---

### Post by throwaway2 on 2009-05-26
> **lastchancetosee said:**
> 
I've created a script to automate/facilitate this process (attached below). Anyone want to try it, go ahead.


Thank you for that awesome tool! I have made a few local modifications and will post them if they turn out to work as intended.

---

### Post by deece803 on 2009-06-04
...And here are my questions:
1) Is there anyway to export the crop value from mplayer -vf crop to the videnc file automatically, rather than manually cutting and pasting? And if there isn't, is there anyway to have a break waiting on "Enter" before going to the next step (configuring videnc)?

2) Is there anyway to take the input for the local variable $NAME and automatically update the corresponding entries in videnc?

...

Good questions and cool script, i'm playing with it now...as i am a bit of a newbie with scripts and it is now 3 yrs since you posted this so not sure if your questions have been answered :) My answer to question 2) I inserted the line "mv ~/$NAME/videnc ~/$NAME/$NAME" below the line "cp ~/videnc ~/$NAME/". So it copies the videnc script to the new directory then moves and renames the videnc file to the same directory then deleting the now unused videnc file. Dunno if anyone will make sense of that :) As for question 1), I'm still going through the 20+ pages of replies as i don't have a clue either!! Thanks for your script once again have been looking for one for a while.

Also, I want it to recognise when a disc is inserted into the drive and to ask whether to run the script or not. I'm heading in th direction of logfiles and trying to find where the outputs of those logfiles would be when a dvd disc is inserted...to me it's an "out there" idea. Just curious to see if i'm on the right track and/or if someone out there has done something similiar?

Any help would be greatly appreciated!

---

### Post by elektronaut on 2009-06-23
I haven't read the whole thread but noticed that [**h264enc (click here)**](http://h264enc.sourceforge.net/) is not mentioned. It's a script which is constantly updated and comes with a man page as well as installation and deinstallation scripts. Might be superior to the bash scripts posted in this thread?

BTW: I got some bad results with Handbrake, which was also mentioned in this thread. Audio was out of sync quite often. Apparently Handbrake doesn't work well with variable bitrates.

---

### Post by earthmeLon on 2009-06-29
> **hyper_ch said:**
> Hiho

sorry for the late reply but I have it now finally:

```

#!/bin/bash -x

for EP in $(cat list.txt);

do

        # Umount existing image
        umount /media/cdrom0;

        # Mount image
        mount -t iso9660 -o loop /media/hda1/B5/$EP.iso /media/cdrom0;

        # Rip files
        nice -n20 mplayer -dvd-device /media/cdrom0 dvd://1 -v -dumpstream -dumpfile $EP.vob;
        nice -n20 mencoder -dvd-device /media/cdrom0 dvd://1 \
                -nosound -ovc frameno -o /dev/null -slang en -vobsubout $EP.en;
        nice -n20 mencoder -dvd-device /media/cdrom0 dvd://1 \
                -nosound -ovc frameno -o /dev/null -slang de -vobsubout $EP.de;

        echo "nice -n20 mplayer $EP.vob -ao pcm:file=$EP.wav -vc dummy -aid 128 -vo null";
        nice -n20 mplayer $EP.vob -ao pcm:fast:file=$EP.wav -vc dummy -aid 128 -vo null;

        nice -n20 normalize-audio $EP.wav;
        nice -n20 oggenc -q5 $EP.wav;


        # First pass
        nice -n20 \
                mencoder -v $EP.vob \
                -vf harddup \
                -ovc x264 \
                -x264encopts subq=4:bframes=3:b_pyramid:weight_b:turbo=1:pass=1:psnr:bitrate=1000 \
                -oac copy \
                -of rawvideo \
                -o $EP.264;

        # Second pass
        nice -n20 \
                mencoder -v $EP.vob \
                -vf harddup \
                -ovc x264 \
                -x264encopts subq=6:partitions=all:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:pass=2:psnr:bitrate=1000 \
                -oac copy \
                -of rawvideo \
                -o $EP.264;

        nice -n20 MP4Box -add $EP.264 $EP.mp4;

        # Put it in matroska container
        nice -n20 \
                mkvmerge \
                -o $EP.mkv \
                -d 1 -A \
                -S $EP.mp4 \
                -a 0 -D -S $EP.ogg \
                --language 0:eng -s 0 -D -A $EP.en.idx \
                --language 0:ger -s 0 -D -A $EP.de.idx \
                --track-order 0:1,1:0,2:0,3:0;

        # Delete unused files
        rm $EP.vob;
        rm $EP.wav;
        rm $EP.264;
        rm $EP.en.idx;
        rm $EP.en.sub;
        rm $EP.de.idx;
        rm $EP.de.sub;
        rm $EP.mp4;
        rm $EP.ogg;
        rm divx2pass.log;

        chown hyper.hyper *;

        echo "$EP done";

done

```

That just works fine - I only need a faster cpu ;)

Anyway, this little script will convert ISO contained in a text list into matroska... the ISOs I use are cleanly ripped (no black borders), contain only one audio stream and in my case two subtitles... so for you, little alterations must be made :)

THANK YOU!!!

Finally, after days of trying to figure this out, I've finally found a script that works.  I hope the OP modifies his post to reflect the changes in x264's arguments

---

### Post by JDorfler on 2009-06-29
Handbrake

Jaunty

deb [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) jaunty main

Intrepid

deb [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) intrepid main

Hardy

deb [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) hardy main

---

### Post by u-slayer on 2009-07-11
Hey guys, I wrote a script based on this thread. If you give it a list of iso files or dvd folders it will extract the video, audio and subtitles. It will then recompress these and mux them into a mkv file. My script can automatically choose the best audio and subtitle tracks to copy based on preferred languages. For the video it takes samples to decide on the crop setting and based on how grainy it is, whether or not to use hqdn3d. It also detects interlaced video and uses yadif to deinterlace.

It's completely automated, so you can point it at a folder with a hundred dvd iso files, leave and a few days later all of them will have been converted to mkv files using all the right settings.

I'm using this script to convert my entire dvd collection, but I want to share it with others. Where should I post it?

---

### Post by u-slayer on 2009-07-18
> **u-slayer said:**
> Hey guys, I wrote a script based on this thread. If you give it a list of iso files or dvd folders it will extract the video, audio and subtitles. It will then recompress these and mux them into a mkv file. My script can automatically choose the best audio and subtitle tracks to copy based on preferred languages. For the video it takes samples to decide on the crop setting and based on how grainy it is, whether or not to use hqdn3d. It also detects interlaced video and uses yadif to deinterlace.

It's completely automated, so you can point it at a folder with a hundred dvd iso files, leave and a few days later all of them will have been converted to mkv files using all the right settings.

I'm using this script to convert my entire dvd collection, but I want to share it with others. Where should I post it?

Last time I posted a script in these forums, I got yelled at because apparently this isn't the right place for that. So if you have a better place I should post my script so that everyone can see please tell me. Until then here is how to run my script: 

How it works:
iso2mkv is a fully automated script meant to automatically recompress dvd iso files into .mkv This is what it does:
Extracts the vob file from an iso file without mounting and without root access.
(It can also take video directly from a vob file or a disc in your DVD drive)
Extracts audio tracks, normalizes and compress them to OGG Vorbis.
(Can also directly copy the .ac3 audio tracks)
Automatically crops the video to the correct size.
Automatically chooses audio and subtitle tracks to copy based on preferred languages.
Can automatically select the best audio track (based on on language then number of channels) and give it a higher bitrate than the other tracks.
Automatically determines the frame rate and run time.
Detects interlaced video and adds the correct video filters in the correct sequence.
Compresses the video with two pass encoding or crf encoding (reccomended) to specified bitrate.
Encapsulates video in an MP4 container.
Finally it muxes all the video, audio and subtitle tracks into an mkv file.

#Setup:
#Install the programs iso2mkv needs:
Install apps: sudo apt-get install mencoder mplayer normalize-audio gpac mkvtoolnix mpeg4ip-server
#The mplayer/mencoder binary was last updated in 2007. If you want to upgrade mplayer/mencoder:
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
cd mplayer && ./configure --enable-gui && sudo make install
#Edit the top of the script to change the default options to your liking. Specifically you need to change tempdir= and target= to folders you use. (You could also set these on the command line)

**#To Run:**
./iso2mkv.py [options] files [options] files...

I use the settings
**./iso2mkv.py -vq2 -crf 19 -len 0 movie1.iso** to get the feature film only.
(change -len 0 to -len 33 or something to rip all video tracks over 33 seconds)

#Command line options
Everything can be set as a default at the top of the script or via command line to override the defaults
A complete list of command line options is at the very bottom of the script. Below are some examples.

iso2mkv reads the command line options in order. Each option applies to every file after it until the option is overridden by another.
./iso2mkv.py -vq2 -crf 20 -len 0 movie1.iso movie2.iso -crf 22 movie3.iso
will encode the first two movies at a high bitrate (crf works on an inverse scale from 50 to 0) and quality settings and give a lower bitrate to the third movie. (-len 0 will only rip the longest video tracks)

There are a few exceptions to the option rule. For example if you type:
./iso2mkv.py -b 1800 -nr 300 -aids 128,129 movie1.iso movie2.iso
the script will only copy audio tracks 128 and 129 for movie1 but will use its normal decision structure for the audio tracks on movie2. However both movies will be encoded at 1800 kbps and both will have the noise reduction option applied to them.

#vq levels
There are three different quality settings so you can choose between speed of encoding and quality.
For example type -vq2 and iso2mkv will use these x264 encoding options for mencoder:
subq=6:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:partitions=all

#Language Selection
At the top of the script there are options for default languages ( can also be set by command line)
You can change the options to your preferred languages.
For example:
alang='en,es' means that only english and spanish audio tracks will be copied

#Bitrate selection
There are three ways to set the bitrate:
bitrate=1800		#Set the bitrate directly
target_size=700	#Target file size
bitrate_percent=33	#Set the bitrate as a percent of the original source: 40 is great, 30 is good, 25 is okay
crf=22			#Quality mode 0-50 0 is lossless - 18 thru 30 is a useful range. This is a single pass mode which automagically chooses the required bitrate for each frame to match a desired quality level. In my tests I have found it to be about 40% faster than a two pass encoding with no difference in quality. This option makes a lot more sense than trying to guess what bitrate is required to make each individual film look good. The only reason to use the bitrate based modes is if you want a specific file size.
These can be set via the command line with -b, -size, -percent, -crf and -qp respectively.

-size is very flexible: All of the options mean the same thing: 702 MiB = 736 MB = 736 = CD = CDR
You can also say -size cd and iso2mkv will perform the necessary calculations to fit the movie onto a 702 MiB CD.
Search for def get_target_size for a complete list of available sizes such as cd, dvd, mini cd, mini dvd, bd and so on...

#Testing bitrate and quality levels with -sample
./iso2mkv.py -sample -b 500 -ss 31:00 -es 49:10 '/media/disk/mkv/5th Element 1/5th Element 1.vob' -b 1000 same -b 1500 same -b 2000 same -b 2500 same -vq2 -b 500 same -b 1000 same -b 1500 same -b 2000 same -b 2500 same
This will produce 9 minute sample videos without audio at varying bitrates and quality levels.
After a bitrate of 1500 it gets hard to spot differences between videos

#Auto De-noise
Samples the video in several places and compares the bitrates with and without hqdn3d.
Example: -autodn 70 will use the hqdn3d filter if (bitrate with hqdn3d) / (bitrate without hqdn3d) < 70

#Wanted features
Detect Telecined video
Blu-Ray compression
Compare audio tracks and discard duplicates.

Warnings:
If there is corruption in the source file (sg1 1x03) mplayer will fill hard drive with junk and then crash.
Mkvmerge will produce lines like this in the log:
Warning: vobsub_reader: '/media/disk/mkv/I_AM_LEGEND.5.idx', line 711: The current timestamp (1524835:33:20.000) is smaller than the last one (1524838:03:20.000). mkvmerge will sort the entries according to their timestamps. This might result in the wrong order for some subtitle entries. If this is the case then you have to fix the .idx file manually
Warning: spu_extract_duration: Encountered broken SPU packet (next_off < start_off) at timecode 00:09:20.343. This packet might be displayed incorrectly or not at all.
I have tested videos with these errors and the subtitles all look fine to me and appear to be syncing with the audio.

---

### Post by Dawei87 on 2009-07-18
so far so good. works really well. just curious though, ive looked through the script and it autimatically grabs any audio language from the disc for the selected language. but for videos that have more than one english audio it will grab them all. is there a place in the script to set max amount of languages to just one?

---

### Post by khelben1979 on 2009-07-18
> **ixus_123 said:**
> If anyone is after a GUI frontend to do all this the **OGMrip** is up to the task

SourceForge.net has some applications in this regard also: [searched on dvd rip]("http://sourceforge.net/search/?type_of_search=soft&words=dvd+rip").

---

### Post by u-slayer on 2009-07-18
> **Dawei87 said:**
> so far so good. works really well. just curious though, ive looked through the script and it autimatically grabs any audio language from the disc for the selected language. but for videos that have more than one english audio it will grab them all. is there a place in the script to set max amount of languages to just one?

Use best_mode 2 by adding -bm 2 to your command line or editing the top of the script.

From the script:
```
#Let the script determine the best audio track (based on on language then number of channels)
#Language used is the first in the alang list EX: alang=en,es - en would be chosen
#best_mode=0 - All Channels give same encoding options
#best_mode=1 - One Channel is given a higher bitrate (determined below)
#best_mode=2 - All other channels are discarded
#::::::::Example: alang=en,all best_mode=1 best_channels=2
#::::::::English channel with highest channel num is given best bitrate - other channels are give lesser bitrates - However, a 6ch english track is downscaled to 2 channels
```

With the default settings, all other audio tracks are converted to ogg and only take less than 100MB each, so I usually keep them.

---

### Post by oo_void on 2009-07-23
Great looking script save one little issue ... 'qp' on line 1301 seems to be unreferenced.

---

### Post by differ on 2009-07-28
> **u-slayer said:**
> 
I'm using this script to convert my entire dvd collection, but I want to share it with others. 

This is great, thanks for sharing! I've set up a ripping-server to put my entire DVD-collection on my harddrive, so this comes in very handy. Could you (or someone else) maybe help me out with one thing, as I'm not a coder: right now I have my server set up so it automatically rips all the VOBs from a DVD upon inserting a disc into the drive. After finishing, it ejects the DVD. I would like to invoke your script after the eject (easy), but automatically search for the newly created VOBs and convert them. How do I do this? Right now, all the script does is this (mirror the entire DVD):

```

#!/bin/sh
vobcopy -m -i /media/DVD -o /home/rip/DVDs
/bin/pumount -l /dev/sr1
eject /dev/sr1

```

So: how do I tell it to take the VOBs it just created and apply your script to them?

Best,

differ

---

### Post by u-slayer on 2009-07-28
> **differ said:**
> This is great, thanks for sharing! I've set up a ripping-server to put my entire DVD-collection on my harddrive, so this comes in very handy. Could you (or someone else) maybe help me out with one thing, as I'm not a coder: right now I have my server set up so it automatically rips all the VOBs from a DVD upon inserting a disc into the drive. After finishing, it ejects the DVD. I would like to invoke your script after the eject (easy), but automatically search for the newly created VOBs and convert them. How do I do this? Right now, all the script does is this (mirror the entire DVD):

```

#!/bin/sh
vobcopy -m -i /media/DVD -o /home/rip/DVDs
/bin/pumount -l /dev/sr1
eject /dev/sr1

```

So: how do I tell it to take the VOBs it just created and apply your script to them?

Best,

differ

So you want to convert all the vobs in the folder?
```
iso2mkv.py [options] /home/rip/DVDs/*vob
```

The star matches every file in the folder.

Or if you want to get fancy:

```
iso2mkv.py [options] $(find /home/rip/DVDs -name '*vob')
```

BTW: iso2mkv.py should be able to directly read from the dvd if libdvdread takes care of any CSS encryption.

---

### Post by differ on 2009-07-29
Thanks for your quick reply -

what vobcopy does is create a subfolder under my DVDs-folder with the title of the DVD it just ripped. What I would like to do know is to automatically convert the VOBs in this newly created folder using your script (without starting it manually). I gues I would have to include a variable somewhere in my script which first calls vobcopy and then tells your script where to look for the newly created files.

Is that understandable?

(I use vobcopy as I want to save the original VOBs for later purposes.)

---

### Post by mimihu88 on 2009-08-14
> **u-slayer said:**
> Hey guys, I wrote a script based on this thread. If you give it a list of iso files or dvd folders it will extract the video, audio and subtitles. It will then recompress these and mux them into a mkv file. My script can automatically choose the best audio and subtitle tracks to copy based on preferred languages. For the video it takes samples to decide on the crop setting and based on how grainy it is, whether or not to use hqdn3d. It also detects interlaced video and uses yadif to deinterlace.

It's completely automated, so you can point it at a folder with a hundred dvd iso files, leave and a few days later all of them will have been converted to mkv files using all the right settings.

I'm using this script to convert my entire dvd collection, but I want to share it with others. Where should I post it?

The script doesn't work here,I got these errors:
$ ./iso2mkv.py file.iso
/tmp/iso2mkv is not a writeable directory
/home is not a writeable directory
Why?

---

### Post by u-slayer on 2009-08-17
> **mimihu88 said:**
> The script doesn't work here,I got these errors:
$ ./iso2mkv.py file.iso
/tmp/iso2mkv is not a writeable directory
/home is not a writeable directory
Why?

By default, the script does not run as root so the script can't write to /home.

Does /tmp/iso2mkv exist? If not, create it.

---

### Post by prabath_fun on 2010-09-23
Thanks for great How to:
  I tried to encode DVD and end up with audio sync problem. 
  I saw in some other reply, which gives some option. I will try to day....

---

### Post by masteroforion on 2011-01-04
Hey

Is there a uptodate version of this script available ? It don't seem to work with 10.10.
I tried to encode multiple dvds and some images but it stopped every time with the following error:

Audio = 12 MiB = 12727296
Subtitles = 8 KiB = 8766
Run Time = 04:25 = 265 seconds
demux_mpg not found IndexError: list index out of range 1043
Using fps given by mencoder, most likely this video is interlaced
Warning: ofps = 25.0 Expected Value: 23.976
Detecting crop settings:     
Crop set at 704:448:8:64
Interlaced video detected
Testing for Noise:  Unknown error testing for noise
Traceback (most recent call last):
  File "./iso2mkv2.py", line 1793, in <module>
    else: main(file)
  File "./iso2mkv2.py", line 1652, in main
    if not vob2mkv(vob): return
  File "./iso2mkv2.py", line 1664, in vob2mkv
    encode()
  File "./iso2mkv2.py", line 1615, in encode
    if not qp and not crf:
NameError: global name 'qp' is not defined


best regards

masteroforion

---

