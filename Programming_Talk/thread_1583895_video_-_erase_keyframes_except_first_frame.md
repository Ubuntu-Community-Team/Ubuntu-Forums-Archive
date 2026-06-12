---
title: "video - erase keyframes except first frame"
date: 2010-09-28
forum: Programming Talk
---

### Post by johannesgj on 2010-09-28
i need some way of taking a videoclip in a lossy format and delete every keyframe except the first which is needed to play the file.

i want to do it either using avidemux script (which i know nothing about) ffmpeg og mencoder.

do anybody have any ideas of how to do this?

---

### Post by Bachstelze on 2010-09-28
I don't know why you want to do that, but with x264, you can use [font=monospace]--min-keyint n[/font] where n is a number larger than the number of frames in your clip.

---

### Post by johannesgj on 2010-09-28
i guess it would seem pointless. so heres my reason. i have long been researching in the vector movement existing in the p-frames between keyframes.
if i get access to these pframes without the keyframes i could use them for further experiments in glitch art.

well that thing about x264 sounds interesting.
will reply soon again

---

### Post by Bachstelze on 2010-09-28
You might also want to disable b-frames then.

---

### Post by johannesgj on 2010-09-28
i have tried some x264 but without success heres what i wrote:

```
 x264 --min-keyint 249 -o test7.avi test5.avi
```

where test5 is old clip and test7 is the new.

can you maybe give me a line with the exclution of b frames as well.

thanx for reps =D>

---

### Post by Bachstelze on 2010-09-28
x264 does not support AVI as output, and if you are using the version from the repos, probably not as input either.

If you want to encode from an AVI file, either compile a new one with LAVF or FFMS support, or use AviSynth.

For output, you can use .mp4, .mkv or .flv. Any other extension will give you an elementary stream.

---

### Post by johannesgj on 2010-09-28
im sorry but what youve said doesnt help me one step further. 
can you give me a line to do the above to a mp4 file resulting in a mp4 file with nearly none key and b frames.
then ill find an mp4 to test it on

---

### Post by Bachstelze on 2010-09-28
Compile x264: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

To disable b-frames:  [font=monospace]--bframes 0[/font]

---

### Post by johannesgj on 2010-09-29
i just figured out how exactly to do what i wanted.
right now im waiting for ffmpeg to peform my task and heres what i did:

use this site on ubuntu forums :
[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")
to install x264 and ffmpeg all the way from the ground and up

after that i was left with an dysfunct ffmpeg, i soon found out it was because of the lack of ffmpeg.sh in the root/bin directory.
so i copied the ffmpeg.sh to that directory and i was able to at least start ffmpeg.

then the next trouble was lack of presets in the usr/local/share/ffmpeg folder (which didnt exist)
so i created the folder usr/local/share/ffmpeg and copied the files from home/ffmpeg/presets or something to the new directory.

then everything worked about ffmpeg.
next was to figure out how to make files with next to none keyframes and b frames.
that was done using the table here showing popular functions in ffmpeg and x264
[http://rob.opendot.cl/index.php/useful-stuff/x264-to-ffmpeg-option-mapping/]("http://rob.opendot.cl/index.php/useful-stuff/x264-to-ffmpeg-option-mapping/")

from there i managed to make the following line
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow -crf 30 -keyint_min 249 -bf 0 -threads 0 output.mp4
```
which takes an avi input and ouputs a x264 mp4 file
-keyint_min is the interval minimum of keyframes
-bf is how many bframes there should be

---

