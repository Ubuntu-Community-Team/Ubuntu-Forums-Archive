---
title: "can anyone reccomend a lightweight program to cut videos?"
date: 2020-09-07
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-09-07
Hi everyone,

Can anyone recommend a lightweight program that I can use to trim some videos, I don't really want to install an absolute behemoth of a program if I can help it, and I'm ideally looking for something in the Ubuntu repository.

Thanks!

---

### Post by mIk3_08 on 2020-09-07
Try Kdenlive.  It might help you.

---

### Post by ActionParsnip on 2020-09-07
[https://itsfoss.com/best-video-editing-software-linux/](https://itsfoss.com/best-video-editing-software-linux/)

---

### Post by SeijiSensei on 2020-09-07
KDEnlive is nice, but rather overkill if you just want to trim some content.  For that I use ffmpeg from the command prompt. Once I determine the time stamps I want to preserve I can run a command like
```
ffmpeg -i input.mkv -ss hh:mm:ss -t hh:mm:ss output.mkv
```
This creates a new file, output.mkv, that begins at the timestamp defined by -ss and ends at -t. Because of how video is encoded, the start and end points may be adjusted slightly to begin and end on key frames.

---

### Post by jcdenton1995 on 2020-09-07
> **SeijiSensei said:**
> KDEnlive is nice, but rather overkill if you just want to trim some content.  For that I use ffmpeg from the command prompt.

Thanks, this is an ideal solution for me. I was surprised to see my CPU heat up so much trimming a little dash cam video, I guess it's hard work.

Thanks again.

---

### Post by sdsurfer on 2020-09-08
OpenShot is pretty good, works for what I need.

---

### Post by TheFu on 2020-09-08
If you need frame-accurate cuts, then transcoding the entire video is required unless the source is MPEG2.

If you can live with key-frame accurate cuts, then you can use other tools and the cutting process is basically a file copy, but only of the selected parts.  This means that a low-end PC or raspberry pi can be used for editing.

With mplayer, there is an interactive cut file creation aspect:
```
$ mplayer -osdlevel 3  -edlout "$EDLFILE" "$1"
```
Use the 'i' key during playback to set begin-end cuts.  mplayer can playback the source file honoring the cuts from the EDL using:
```
$ mplayer -osdlevel 3  -edl "$EDLFILE" "$1"
```
These are easily scriptable with just a few lines to automatically create the EDL filename.

The problem with this mplayer method is that other video editing software needs exactly he opposite - they want being-end times for the stuff to be kept. Further, mplayer EDL makes times in seconds, whereas mkvmerge (the best cut/merge tool), demands hh:mm:ss.ssss format.  Of course, I whipped up some scripts to handle these conversions, but they aren't safe for public use, since I didn't bother to fix stuff that can trivially be handled in vim using visual-mode selections. My scripts generate other scripts to be run. I like meta-programming.  My scripts read from stdin and write to stdout, so they can be used in a pipeline solution once the itch has been fully scratched. 

mkvmerge is the best of the cutting tools, because it cuts all tracks correctly, unlike almost all fancy editing tools I've seen and it does it at the speed of a file copy. No transcoding mandatory.  If you have 1 video track, 4 audio tracks, and 10 subtitles/SRT/ASS tracks, then having them properly cut is important.  OTOH, if this is a home-made video with 1 video and 1 audio track that is pretty short, then transcode away.

BTW, the mplayer EDL format is supported by Kodi and other players, so if that is your playback method, it is worth using. There are many different EDL formats. Not all are compatible. For example, mpv has a completely different format than mplayer even though mpv is a fork from mplayer. They decided their format was better, but it is significantly harder to generate the mpv EDL files for anything non-trivial.

For example, if you record your girl's softball or basketball games, but only want to retain the parts where she is in the play, there could be 40 cut points to be retained in a 2 hour game.  Creating those edit points using mplayer isn't too hard. Too bad mpv doesn't have the ability to create that EDL file format.

Anyways, here's little script to take manually created in/out cuts for some video and generate a single output file:

```
#!/bin/bash 
##########################
IN="Some_Recored_Sport.ts"
OUT="Some_Recored_Sport-mpg-cut.mkv"

# ########################################
mkvmerge -o "$OUT" --split parts:\
03:08-03:18.00,+03:54-28:52,+32:04-  "$IN" 
exit

```
the ,+ means append this next part to the prior. If the '+' is missing, then the output will have numbered files which need to be merged some method. Just better to remember the '+'.  I have a script that will merge **file-001.mkv, file-002.mkv, file-003.mkv** into file.mkv  

MKV containers can hold pretty much anything video, audio, text, and other related files.  I would take the mpeg2 holding MKV container and transcode that into a high quality h.264 video file with multi-channel vorbis and AAC audio to support direct playback on a wide selection of playback devices, while reducing the file size about 75%.  A 10G mpeg2 file will usually transcode down to a 2.5G h.264 file with no artifacts.

Anyways, this isn't point-n-click, but it is easy to batch up and run a bunch of these cuts overnight.

If the source material is TV recordings, check out **comskip**. It can make EDL files for where commercials are located (really close, if not perfect). Validating the cut areas is manual, but pretty quick with the right tools. Sadly, I've been searching for a Linux tool for this and haven't found one.  vidcutter was sorta working, but the dev has moved on after making an AppImage and snap that seldom works for me.

---

### Post by monkeybrain20122 on 2020-09-08
[Shotcut]("https://shotcut.org/download/")? Very lightweight, gets great review and doesn't require installation. the tar ball is a bundle, just click the binary, the appimage also doesn't need installation, make executable and click, it also offers a snap.

---

### Post by mastablasta on 2020-09-09
Shotcut is the light one with GUI. it can do other complex stuff but it is kind of hidden unless you decided you need it.

cutting videos and recoding or encoding them is hard work on CPU. for video editing you need strong CPU and lots of RAM, and of course you need disk space (fast disk will help). GPU is not that important, though it can help a bit.

for gaming you can get away with weaker CPU and reasonable RAM amount, as long as you have strong GPU.

---

### Post by ajgreeny on 2020-09-09
if you try the ffmpeg command shown at post #4 you can make it very fast by using the options
-acodec copy -vcodec copy

This avoids any re-encoding of the output file; it will simply cut out that chunk and name to your choice.

---

### Post by mastablasta on 2020-09-10
well that's more interesting. are these two appended at the end or after each file (output& input)?
Like this?

```
ffmpeg -i input.mkv -ss hh:mm:ss -t hh:mm:ss output.mkv -acodec copy -vcodec copy
```

or like this?:

```
ffmpeg -i -acodec input.mkv -ss hh:mm:ss -t hh:mm:ss -vcodec output.mkv
```

---

### Post by ajgreeny on 2020-09-10
> **mastablasta said:**
> well that's more interesting. are these two appended at the end or after each file (output& input)?
Like this?

```
ffmpeg -i input.mkv -ss hh:mm:ss -t hh:mm:ss output.mkv -acodec copy -vcodec copy
```

or like this?:

```
ffmpeg -i -acodec input.mkv -ss hh:mm:ss -t hh:mm:ss -vcodec output.mkv
```
I am not sure about that but often it does not make much difference where options are in the command. However, when I've used ffmpeg for this and other things, I always put the ***-acodec copy -vcodec copy*** options just before the **_output.mkv_** file name, not after.

Try both using a different output file name but the same input and you'll quickly see; with the copy options it takes only a very few minutes or even seconds depending how long the clip is, but if iot encodes it will take a great deal longer and use many more CPU resources.

---

### Post by TheFu on 2020-09-10
If ffmpeg uses getopts(), which it should, then only the last argument, the output filename, is positional.

BTW, ffmpeg in copy mode is functionally equivalent to the mkvmerge command I posted. Both perform at the speed of a file copy, though having multiple start-end times is easier with the mkvmerge.  1 other thing, mkvmerge requires that the output container be an MKV container, but that really isn't any hardship, since MKV can hold anything.  There is a GUI for mkvmerge, but it is just a GUI to enter the exact same data that the shell command would use. It is not some graphical mouse point/click begin-end cutting software.  

On Linux, the closest solution to the non-transcoding ffmpeg and mkvmerge commands shown above is a tool called **vidcutter**. The interface is a little clunky and the snap/appimage packages depend on Qt, so about 900MB get downloaded for the 32MB program.  Vidcutter doesn't transcode - or it didn't last time I actually got it working.

To me avoiding any transcoding is important, since there are almost always artifacts and increased file sized as a result for already optimized videos.  For non-optimized videos like mpeg2 and real-time recorded h.264 videos, which can be huge, then transcoding can drastically reduce file size - perhaps 75% smaller. With very conservative RF settings for h.264 transcoding, the resulting files will be much smaller and artifacts barely seen. If transcoding has already been done after the source, each attempt introduces more and more artifacts.

Openshot, Kdenlive, Shotcut  will all transcode. This is why your CPU and all cores get nailed when saving/exporting files using those tools.  If they have a mode that doesn't transcode, I'd love to know about it.
[LIST]
[*]kdenlive ALWAYS transcodes: [https://forum.kde.org/viewtopic.php?f=265&t=130552](https://forum.kde.org/viewtopic.php?f=265&t=130552)
[*]Openshot and Shotcut don't specifically say they do, but they don't say they have an option to prevent transcoding/re-encoding either.
[/LIST]

I have a video recording device that saves as h.264/aac inside an mp4 file container. This device has just 1 setting for recordings and prioritizes saving the data over being efficient.  Basically, it is ffmpeg on a "superfast" encoding setting, so the file sizes are huge.  

Real world example: Yesterday, recorded a 110 minute video.  That mp4 file is 5.9G in size. This morning, I transcoded that file using handbrake with an RF of 19.5 to 1.3G size.  Thanks to a fast CPU with lots of cores, that transcoding took about 20 minutes at +19 nice setting. I use spinning disk storage for this, not SSDs.  Saving 78% of the file size is worth the effort to me.  All our playback devices well support the more efficient h.264 video encoding.  While I'm transcoding, I keep the AAC audio, but also add vorbis multi-channel audio too for compatibility with some devices. Anyways, figured a better explanation for when to transcode and why it can be good wouldn't hurt.  I actually edit the already transcoded file, because dealing with a 2G file is easier than dealing with a 6G file.  The transcoding step can be batched, which allows deletion of the huge original file sooner, that frees up storage and temporary space for other uses.

---

### Post by SeijiSensei on 2020-09-10
The output filename must be the last item in an ffmpeg command.

[https://linux.die.net/man/1/ffmpeg](https://linux.die.net/man/1/ffmpeg)

---

### Post by ra7411 on 2020-09-10
Avidemux might work for you, be careful to do cuts at keyframes which the double arrow buttons go to. It's in the Ub 18.04 repository.

---

### Post by ipv on 2020-09-10
it can't get any lighter than this :

[URL="https://online-video-cutter.com/"]https://online-video-cutter.com/
[/URL]

---

### Post by TheFu on 2020-09-10
> **ipv said:**
> it can't get any lighter than this :

[URL="https://online-video-cutter.com/"]https://online-video-cutter.com/
[/URL]

Except the required browsers to use it are all hogs.  Doubt it supports dillo or lynx. ;)

---

### Post by mastablasta on 2020-09-11
the shotcut is using ffmpeg (as well as a few others) and after you do what you want and before you run the task it will say what commands will run and how ffmpeg was set. i am not sure if it has option to do it without transcoding.

---

### Post by ipv on 2020-09-11
> **TheFu said:**
> Except the required browsers to use it are all hogs.

point taken.

> **TheFu said:**
> Doubt it supports dillo or lynx.

i use neither so i know not, works with falkon & firefox.

am assuming you use them so why not give it a shot & give feedback.

---

### Post by Kanehekili on 2020-12-19
I've written a prog that you could download here: [https://github.com/kanehekili/VideoCut](https://github.com/kanehekili/VideoCut). The lightweight comes from using the ffmpeg libraries to create a real fast remuxer. It does no any fancy stuff, just cutting video precisely. The idea behind it: Do not try to re-encode, just take the I frames and copy them. Makes my 15 year old Thinkpad seem to be fast....

---

### Post by wisjim2 on 2020-12-19
I like Open Shot Editor. I really can't tell you how massive it is though. Takes a little practice. Watch the very short tutorial and it'll get you started. Once you get used to it it works like a charm. And it is in the Ubuntu, now Snap, repository.

---

