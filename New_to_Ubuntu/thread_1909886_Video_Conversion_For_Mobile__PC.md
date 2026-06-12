---
title: "Video Conversion For Mobile / PC"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by msinfo on 2012-01-16
Hello Friends.  :popcorn:

1. Using Ubuntu from past few months. I am now facing problem with video conversion.
2. I have mplayer installed, and then installed = winff, pytube, handbrake, Transmageddon, and other converters.
3. But none of them were able to convert videos/audios, and displayed messages, stating some codecs, componenets were missing.
4. Then I installed mobile media converter. It was hassle free and converted audio/videos sucessfully.

:confused:

5. So I want to know what I missed while using Winff, and other converters, why they were asking for more codecs, components, even while I was having mplayer installed.
6. I presume, with mplayer we get all codecs, and above converters do conversion using mplayer codes. Am I right here ?
7. Or can anyone, put some light on this video conversion process and its background (how it all works in union. . . )

Thanks for consideration.

---

### Post by WasMeHere on 2012-01-16
Hi msinfo

Sometimes the multimedia software brings its own codecs (instead of relying on the general libraries). But if you do the tasks suggested in the following thread, your general libraries should be updated.
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=766683_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

Have fun finding out :-)
Olle

---

### Post by nhasian on 2012-01-16
You mentioned that you used handbrake. What error messages did it give you?  I've used handbrake in the past to convert videos for both iphones and android phones with no problems.  Its just time consuming on slower CPUs :popcorn:

---

### Post by msinfo on 2012-01-17
Hey ! Olle Wiklund :P
Thanks for showing above thread. It gave little light on confusion, and helped in  getting medibuntu easily.
 
Hey ! nhasian :P
Thanks for consideration. But since Handbrake is Apple products centric, I could not use it. I have Sony Ericsson Naite, so I was looking for 3gp or Mobile mp4 format. I can't exactly say what was error message, but it said I lacked codec or something needed for conversion.
 
:) Ok! Till now I have understood, Medibuntu will help me with all audio video libraries. Next, I need converter and I have to define presets (if in defaults I could not find one I am looking for) manually, to get conversion done.
(Am I correct ?) 
 
:( But what I have to read in order to gain knowledge about tweaking conversion parameters like bit rate, frame, aspect ratio, etc in right manner for my mobile device or pc (specially converting 700 mbs movies into 400 hq mk videos, without loosing quality, but saving space.)

---

### Post by WasMeHere on 2012-01-17
Have a look at this thread
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=786095_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by msinfo on 2012-01-18
Hmm. . . It's really big thread. Need few days to read and understand it. Probably Iam getting some structure in mind regarding video conversion using ffmpeg and x264.
 
Thanks for guidance.:P :P

---

### Post by WasMeHere on 2012-01-18
> **msinfo said:**
> Hmm. . . It's really big thread. Need few days to read and understand it. Probably Iam getting some structure in mind regarding video conversion using ffmpeg and x264.
 
Thanks for guidance.:P :P
You are welcome!

I suggest that you do some trial and error, using the scripts in the first post in the thread, and I guess that *FakeOutdoorsman* might help you, if there is something you cannot get working, providing that you post in his thread.

Good luck :-)

---

### Post by FakeOutdoorsman on 2012-01-18
> **msinfo said:**
> 5. So I want to know what I missed while using Winff, and other converters, why they were asking for more codecs, components, even while I was having mplayer installed.
By default the version of ffmpeg from the repository requires installation of an additional package to enable more encoders. See **Option B** or **Option C** here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

> **msinfo said:**
> 7. Or can anyone, put some light on this video conversion process and its background (how it all works in union. . . )
Instead of giving you a huge block of text perhaps some examples would be most useful to you if you want to use ffmpeg directly. Unfortunately, some devices are very picky so you may have to do some experimentation. Otherwise, WinFF should now work for you once you followed the link above. What version of Ubuntu do you have? This will determine your ffmpeg syntax.

To get started you probably don't need to compile and install FFmpeg. The version from the repository should do fine for now.

---

### Post by msinfo on 2012-01-19
Hey, FakeOutdoorsman Thanks for considering this problem of mine. 
 
A
1. So ubuntu, doesn't add additional encoders in default installation of ffmpeg.
2. I have info about getting all encoders/codecs. (link provided by you above).
 
3. How can I convert video or audio using Winff or any other converter, when I can't find preset of my choice.
 
4. Will audio/video converters would be using mine installed codecs, or they would use their custom codecs.
 
5. Can I make custom presets in Winff or any other converter.
 
6. :confused: How can I know what should be right values for factors like bitrate, frame, resolution etc. for various devices like pc, mobile, etc.
 
7. Can anyone please, give me a example of command line code, for converting an .avi movie to 3gp, and another one to .mkv. By keeping that as a base I would try to experiment with conversion process
 
 
System info:
3.2 Ghz Intel P4
815 Gigabyte MB
2GB RAM
10.04.3 LTS (Lucid Lynx)

---

### Post by WasMeHere on 2012-01-19
> **msinfo said:**
> Hey, FakeOutdoorsman Thanks for considering this problem of mine. ...
 
7. Can anyone please, give me a example of command line code, for converting an .avi movie to 3gp, and another one to .mkv. By keeping that as a base I would try to experiment with conversion process
 
B
Where is option, for closing this thread as solved issue. I tried but could not find it, as I did with my previous threads.
 
C. System info:
3.2 Ghz Intel P4
815 Gigabyte MB
2GB RAM
10.04.3 LTS (Lucid Lynx)

Last first: At the top of page with your thread, click on [COLOR="Red"]**Thread Tools**[/COLOR]. You get a drop down menu, with the last option 'Mark this thread as Solved'

I will come back with a couple of simple examples to make 3gp and mkv files (but I will be busy for a while now).

---

### Post by msinfo on 2012-01-19
> **Olle Wiklund said:**
> 
 
I will come back with a couple of simple examples to make 3gp and mkv files (but I will be busy for a while now).
 
Ok! Till that time, would be reading forum for this problem. Thanks !

---

### Post by FakeOutdoorsman on 2012-01-19
> **msinfo said:**
> 3. How can I convert video or audio using Winff or any other converter, when I can't find preset of my choice.
You will have to make your own preset or use ffmpeg directly.
 
> **msinfo said:**
> 4. Will audio/video converters would be using mine installed codecs, or they would use their custom codecs.
It depends on the audio/video converters. WinFF uses ffmpeg directly, but Avidemux uses customised versions of the FFmpeg libraries. I'm not sure what Handbrake does since I'm not very familiar with it.

> **msinfo said:**
> 5. Can I make custom presets in Winff or any other converter.
Yes. I don't have WinFF installed, but I believe it would be easy to make your own presets.
 
> **msinfo said:**
> 6. :confused: How can I know what should be right values for factors like bitrate, frame, resolution etc. for various devices like pc, mobile, etc.
Sometimes you don't and you will have to experiment or search for examples. I usually start by looking at the manufacturer's web site for specifications of the device as a starting point, but they are often not very useful. You can also find a video that does work on the device and try to make something similar with ffmpeg.
 
> **msinfo said:**
> 7. Can anyone please, give me a example of command line code, for converting an .avi movie to 3gp, and another one to .mkv. By keeping that as a base I would try to experiment with conversion process
3gp and mkv are container formats. They can utilise a number of audio and video formats, so you need to be more specific as to what you want. For example, 3gp can contain three different video formats, and two different audio formats (with variations of each), and mkv can handle just about any format. See [Comparison of container formats](http://en.wikipedia.org/wiki/Comparison_of_container_formats) for a nice chart.

---

### Post by WasMeHere on 2012-01-20
I am including a script, that is modified from my script to convert files from my video camera to files that can be played by computers (in general) and my TV set. That script converts from 1920x1080-50p MTS files to 1920x1080-30p, 1280x720-50p and 960x540-50p mp4 files encoded with libx264, which as far as i understand should be used for 3g2 files.

According to information on the internet (you can easily browse to find tutorials and detailed examples) ffmpeg can be told to select suitable formats and codecs by specifying the extensions of the file names. This feature needs some 'help' in certain cases; you need to specify more using options. I have run the included script and it works for me in Ubuntu Studio 11.04 (and I can play files converted from my old photo camera's avi files), but as *FakeOutdoorsman* wrote, you need to be more specific or tweak the options yourself, to make it work for your particular purpose. And it might need modifications to run in another version of Ubuntu. Regard it as a starting point, not something to use as it is!

```
#! /bin/bash

if [ "$2" == "" ]
then
 echo "Usage: $0 <avi file> <output video resolution>"
 echo "ex:    $0 file.avi 640x480  or"
 echo "       $0 file.avi 320x240"
 exit
fi

typeset infile="$1"

if test -f $infile
then
 if [ $infile == ${infile/\.avi} ]
 then
  echo "$infile is not an avi file"
  exit
 fi
else
 echo "$infile not found"
 exit
fi

if [ "$2" != "" ]
then
 typeset namex="$2"
 typeset res="$2"
 typeset framerate=30
 typeset bitrate=512k
fi

typeset infile="${infile/\.avi}.mp4"
typeset tmpfile="${infile/.mp4}_tmp.3g2"
typeset outfile="${infile/.mp4}_$namex.3g2"
typeset mkvfile="${infile/.mp4}_$namex.mkv"

if test -f "$infile"
then
 echo "$infile exists, no need to make it again"
sleep 5
else
 ffmpeg  -i $1 -vcodec mpeg2video -sameq "$infile"
sleep 5
fi

# 3g2
typeset options="-vcodec libx264 -s $res -r $framerate -b $bitrate -flags +loop+mv4 -cmp 256 \
	   -partitions +parti4x4+parti8x8+partp4x4+partp8x8+partb8x8 \
	   -me_method hex -subq 7 -trellis 1 -refs 5 -bf 3 \
	   -flags2 +bpyramid+wpred+mixed_refs+dct8x8 -coder 1 -me_range 16 \
           -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -qmin 2\
	   -qmax 51 -qdiff 4"

ffmpeg -y -i "$infile" -an -pass 1 -threads 2 $options "$tmpfile"
ffmpeg -y -i "$infile" -acodec libfaac -ar 48000 -ab 192k -pass 2 -threads 2 $options "$tmpfile"

qt-faststart "$tmpfile" "$outfile"
touch -r "$1" "$outfile"
rm ffmpeg2pass-0.log x264_2pass.log x264_2pass.log.mbtree "$tmpfile"

# mkv
ffmpeg -i "$outfile" -sameq "$mkvfile"
touch -r "$1" "$mkvfile"

```

---

### Post by msinfo on 2012-01-20
>  
Originally Posted by : FakeOutdoorsman
You can also find a video that does work on the device and try to make something similar with ffmpeg.

 
1. Million Thanks for your replies and threads, it helped me to clear my doubts about multimedia conversiona and ffmpeg also.
2. Yes, I will now experiment with ffmpeg as you guided above.
 
>  
Originally Posted by : Olle Wiklund
you can easily browse to find tutorials and detailed examples

 
1. I am happy to see ffmpeg command including script you wrote.
2. Yep, I saw many tutorials and sample code of ffmpeg. But thought before executing anything blindly, I should know what I am doing. 
 
To,
:D FakeOutdoorsman and Olle Wiklund, :D
Thanks for helping and giving solid foundation on conversion subject.

---

### Post by WasMeHere on 2012-01-20
You are welcome :-)

Finally, when you succeed, please share your result at the Ubuntu Forums (for example by posting some scripts)!

Olle

---

### Post by msinfo on 2012-01-20
> **Olle Wiklund said:**
> You are welcome :-)
 
Finally, when you succeed, please share your result at the Ubuntu Forums (for example by posting some scripts)!
 
Olle
 
 
Why not sure! 
Right now, just chopping some big 700 mb videos to test file of 10 mb (using windows Format factory) and would be experimenting with them for conversion under linux environment.

---

### Post by perspectoff on 2012-06-11
I'm not sure why no one mentions mencoder.

I love mencoder. It uses many ffmpeg libraries, but is far faster and more efficient, IMO. I tend to get some strange artifacts with ffmpeg from time to time.

I convert everything with mencoder, including NTSC DVDs.

I converted a 100 movie DVD collection to AVI (with XVID/MP3) in about 3 days. I use .AVI with XVID/MP3 because that is the only format that is recognized on every one of my devices: DVD players, Windows computers, (K)Ubuntu computers, Android tablets/eBook readers, and even MP3 players (although these require a specific 320x240 size). No other format combination works on all of these. (I don't use any Apple products, so I can't vouch for those).

(Yes, yes, .MKV is a superior container, X264/H.264 is a superior video codec, and there are superior audio codecs, but if my devices can't play them what's the point?)

Mencoder will convert to/from any format (provided you have the codecs), including X264/H.264, MP4, whatever. Handbrake is a great program and can handle a lot of encryption (since it rips by streaming), but it has a limited number of output formats and almost none of my devices (except computers) can handle its formats.

I happen to like using mencoder with k9copy as a front end, which I think is a great utility. (k9copy is a frontend for both mencoder and ffmpeg).

The instructions I use for mencoder are here:

[http://ubuntuguide.org/wiki/Video_Conversion](http://ubuntuguide.org/wiki/Video_Conversion)

---

