---
title: "How To: Convert videos to MP4 / rip DVD's"
date: 2009-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by phenest on 2009-11-01
You will need:
```
apt-get install lsdvd mplayer mencoder ffmpeg faac x264
```
**lsdvd**
... is used for getting info on the titles of your DVD.
```
lsdvd
```
... will list all titles and their lengths. That makes it easy to identify what titles to play or rip.

**mplayer**
...is a great tool for both playing videos/DVDs and for ripping DVD's.
```
mplayer dvd://1
```
...will play a dvd title. The '1' is the title number.
```
mplayer dvd://1 -dumpstream -dumpfile filename.mpg
```
... will rip that title to the given filename.

**mencoder**
... is a great decoder/encoder to encode your videos. However, mencoder does not support MP4 files fully. Be warned!
```
mencoder $input -o $output -ovc x264 -x264encopts qp=26:frameref=3:bframes=15:b_pyramid:deblock=$db:direct_pred=auto:cabac:weight_b:partitions=all:8x8dct:me=esa:me_range=24:subq=7:mixed_refs:trellis=2:nofast_pskip:threads=0 -nosound
```
$input is the video file to encode
$output is the filename to save to (give it the .mp4 extension).
Where it says 'qp=26' is the quality setting. 26 is a good default and you will be happy with the results. A lower number gives higher quality, whereas a higher number gives lower quality (0=lossless). Less than 16 is overkill, and more than 40 tends to give unwatchable video.
$db is for deblocking. Deblocking control the smoothness of the video. The default is 0:0 and is recommended. Both numbers are in the range 6 to -6. The first (alpha), is for controlling the sharpness, with -6 creating a sharper video, and 6 making it less sharp. The second (beta), controls the threshold, with negative numbers giving better detail but flat areas may look "blocky", and positive numbers give the opposite.

**x264**
The x264 package is a great alternative to mencoder and supports the MP4 format. Unfortunately, it only accepts a rawvideo input so decoding needs to be done via ffmpeg and piped to x264...
```
ffmpeg -i $input -deinterlace -r $fps -f rawvideo - | x264 -q $qp -f $db --sar $par -o $output - ${width}x$height --fps $fps
```
-deinterlace can be omitted if you don't require it. It kinda speaks for itself as to what it does.
$input & $output are the filenames for the input and output videos.
$fps is the framerate: frames per second.
$qp is the quality.
$db is deblocking.
$par is the pixel aspect ratio for the output video. PAL is 16:15 or 64:45 widescreen.
$width and $height is the size of the video frame in pixels **BEFORE** the par is applied.

**ffmpeg**
ffmpeg has built in presets for encoding which make it far simpler to use.
```
ffmpeg -i $input -an -vcodec libx264 -crf $crf -vpre hq -threads 0 $output
```
See! Really simple.
$input & $output as before.
$crf (Constant Rate Factor) is the same value as $qp used before.
-vpre tells ffmpeg to use a preset. Values: default, normal, hq, & max. (max takes ages to encode anything!)
-threads 0 tells ffmpeg to use multi-threading to use your cpu efficiently.

If you compile ffmpeg with x264 and aac encoding support, then the whole task becomes even simpler...
```
ffmpeg -i $input -vcodec libx264 -crf $crf -vpre hq -acodec libfaac -aq $aq -ac 2 -threads 0 $output
```
...which means no need to encode the audio separately as this does it in one.
All as before with the additions:
$aq is the audio quality. 10 to 500. 200 is a good value with pleasing results.

**aac encoding**
Here, I will use faac to do the encoding which is piped from ffmpeg. In Karmic, aac encoding has been removed from ffmpeg, so this is the alternative.
```
ffmpeg -i $input -vn -map 0:$as -f wav - | faac -q 200 - -o $output
```
$input is the video file
$output is the filename to save it to (give it the m4a extension)
$as represents the audio stream. 1 is a good default. Some videos, such as mpeg2's (ripped from DVD's), have more than one audio stream. If you need to determine the stream number you need, use:
```
ffmpeg -i filename
```
... and it will list all the streams.
-q 200 is the audio quality. 200 is an ideal default. Adjust to taste: higher/lower numbers give higher/lower quality.

**Muxing**
... is putting both video and audio file into one file.
```
ffmpeg -i video.mp4 -vcodec copy -i audio.m4a -acodec copy output.mp4
```
This is pretty self explanatory.

**Compiling ffmpeg with x264 and aac encoding support**
There is a guide in the Tutorials & Tips section of this forum which shows how to compile the latest version of ffmpeg and codecs. It can be found [here]("http://ubuntuforums.org/showthread.php?t=786095").



You should find the file size of the encoded mp4 is surprisingly small (if all went well).


Enjoy!

NOTES:
[LIST]
[*]As of Karmic, the x264 package is no longer compiled with mp4 support. There is a guide [here]("http://ubuntuforums.org/showthread.php?t=786095") that will show you how to compile ffmpeg with x264 support.
[*]As of Karmic, ffmpeg no longer supports aac encoding. The guide for compiling ffmpeg will also give you aac encoding.
[/LIST]

EDIT 11/1/10: Added section for x264 package. Added NOTES.

---

### Post by sisyphus1978 on 2009-12-15
I gave this a go. Seems to work fine. A word of warning: it took a long time to encode the dvd to h264 (on my system about 9 hours for 1 50 minute episode), so probably best to leave it over night.

Thanks.

---

### Post by phenest on 2010-01-11
I decided mencoder is not the best way to encode x264 video, so I've added a section for using the x264 package which gives very good results.

---

### Post by FakeOutdoorsman on 2010-01-11
> **phenest said:**
> **aac encoding**
Here, I will use faac to do the encoding which is piped from ffmpeg. In Karmic, aac encoding has been removed from ffmpeg, so this is the alternative.


Nice guide.  Medibuntu now offers a **libavcodec-extra-52** package for Karmic that will allow FFmpeg to encode with *libfaac*.  For more info, see *Option C* in this guide:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

> **phenest said:**
> As of Karmic, the x264 package is no longer compiled with mp4 support. I resort to using the packages for Jaunty.

I can think of three solutions to this other than using a package from a different Ubuntu version:
[indent]1. Why not include an example of using FFmpeg with the libx264 presets?  This way you can encode directly to the MP4 container.

2. Output to *.264* with x264 and then just use that for your video input in your muxing example.

3. Install **libgpac-dev** and then compile x264 as shown here to enable mp4 output in x264:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)[/indent]

---

### Post by phenest on 2010-01-11
> **FakeOutdoorsman said:**
> Nice guide.

Thanks

> **FakeOutdoorsman said:**
> 1. Why not include an example of using FFmpeg with the libx264 presets?  This way you can encode directly to the MP4 container.

2. Output to *.264* with x264 and then just use that for your video input in your muxing example.

3. Install **libgpac-dev** and then compile x264 as shown here to enable mp4 output in x264:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

I think 1 & 2 are worth adding. As for 3, I'll leave that possibility to the reader.

---

### Post by phenest on 2010-01-29
Added encoding video with ffmpeg.

I looked at using x264 to encode to .264 format but the video seemed stuttery. I tried to .mkv, but couldn't mux into anything else. I think I prefer the ffmpeg way.

---

### Post by phenest on 2010-02-09
Added compiling ffmpeg with x264 and aac encoding support.

---

