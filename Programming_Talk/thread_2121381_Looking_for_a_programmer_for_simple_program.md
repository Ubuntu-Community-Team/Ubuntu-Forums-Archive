---
title: "Looking for a programmer for simple program"
date: 2013-03-01
forum: Programming Talk
---

### Post by maxsideburn on 2013-03-01
I have the idea, but no knowledge whatsoever of coding to pull it off.

Coming from a Mac I had no problem making timelapses using images taken by my Canon 60D at set intervals. In Quicktime you'd just go to File > Open Image Sequence and it click on the first image and they would compile into a movie instantly.

I have had zero luck finding something similar in the Linux world, the closest thing is to either use all kind of command-line fu with ffmpeg or to use a full-fledged editor like KDEnlive or something similar.

I'm looking for someone to code a very simple little app (GTK preferably) that when opened will ask you to select a folder, once you select the folder it will ask you what frames per second you want your movie to be (24fps, 25fps, 30fps or 60fps), ask you where you want to save the file, and then upon clicking OK it would just output a .mov or .avi of the images at the proper framerate in the motionjpeg codec (highest possible quality).

I'm sure for someone with coding knowledge this would be a very simple app to code...but I don't know the first thing and I've seen quite a few posts online where people are looking for similar software.

Any takers? Thanks!

---

### Post by MG&amp;TL on 2013-03-01
I'm afraid I'm going to have to disappoint you - I haven't the time* to do that to any degree of quality.

I posted merely to point out that (in the event that nobody shows up) [programming isn't voodoo]("http://docs.python.org/3.0/tutorial/index.html") , and that the best way to get the result that you want is often to do it yourself. Just a thought. :)

[SIZE=1]*This is a horrible excuse, and I hate it when people use it. That said, I'm a sixth-former and my 20-odd-page physics coursework is due in next week, along with a CS writeup and some maths homework, and my weekend is already mostly filled for one reason or another. I really haven't got time. :([/SIZE]

---

### Post by r-senior on 2013-03-01
> **maxsideburn said:**
> upon clicking OK it would *just* output a .mov or .avi
This looks like a big 'just' to me.

It would probably help if you did some work in terms of working out what that 'just' means, i.e. how to make these files and how to deal with framerate and quality.

Otherwise it looks a bit like a request for someone to work for nothing while you sit back and wait for results.

---

### Post by QIII on 2013-03-01
"Just" in English for a layman often means "weeks" for a developer.

---

### Post by diesch on 2013-03-01
I guess it could be just a simple GUI frontend for ffempeg or mencoder. May be a project for a GUI programming beginner.

A simple version should be possible with a shell script and Zenity. I'll have a look if someone gets me the parameters for ffempeg, mencode or whatever.

---

### Post by maxsideburn on 2013-03-02
Programming is just one of those things I've attempted to learn before and am simply not good at. I've spent years teaching myself 3d modelling, video editing, graphic design and countless other computer (and non-computer) skills and just can't see myself spending years more learning another skill just for something that's probably a breeze to a skilled coder ;)

An entirely new infrastructure doesn't need to be coded, it would likely just be a frontend for ffmpeg or mencoder.

this link explains how to do it in ffmpeg, which is fine, but there really should be a simple way to do this without command-line tinkering in this day and age since it is so easy in Windows or on Mac. the only thing to keep in mind with this one is that he mentions ffmpeg has to be told to allow for larger resolutions...many of us shoot at 18 megapixels and up these days to produce 4k resolution videos, so any frontend for ffmpeg would have to make sure that ffmpeg is set to allow at least 18 megapixel images.

[http://programmer-art.org/articles/tutorials/ffmpeg-time-lapse](http://programmer-art.org/articles/tutorials/ffmpeg-time-lapse)

(18 megapixels equals 5196x3464)


this link explains the procedure with mencoder, again, it seems fairly easy and I've done it this way before, but there really should be a simple way to do this with a few mouse clicks in a modern OS.
[www.cenolan.com/2009/05/simple-time-lapse-video-in-linux](www.cenolan.com/2009/05/simple-time-lapse-video-in-linux)


Again, thanks for taking the time to look at this stuff guys, I know I and quite a few other professionals out there would appreciate any software that adds to what can be done (creatively speaking) in a Linux environment.

---

### Post by Vaphell on 2013-03-02
frankly every time i wanted to play with vids and images, some neat oneliner proved more useful than banging the head against the unintuitive software with pretty gui, overloaded with meaningless at the first glance info and options.
Every time i forget how i did things last time i can be up and running in 15 minutes with bash thanks to questions to google, like "linux images to video" (this time is no different).

```
#!/bin/bash

sel=$( zenity --file-selection --title="img2vid" )
[ -z "$sel" ] && exit
d=${sel%/*}

if [[ $sel =~ ^.*[^0-9][0-9]+[.].+$ ]]
then
  w=$( echo "$sel" | sed -r 's/[^0-9]+$//; s/^.*[^0-9]//' )
  [ ${#w} -le 1 ] && w="" || w=0${#w} 
  mask=$( echo "$sel" | sed -r "s/^(.*[^0-9])[0-9]+([.].+)$/\1%${w}d\2/" )
fi
mask=${mask##*/}
mask=$( zenity --entry --title="img2vid" --text "file mask" --entry-text="$mask" --width=500 )
[ -z "$mask" ] && exit

echo $d
echo $mask
out="${d##*/}__${mask%.*}.avi"

fps=$( zenity --entry --title="img2vid" --text "framerate" --entry-text="15" --width=500 )
[ -z "$fps" ] && exit
out=$( zenity --entry --title="img2vid" --text "output file" --entry-text="$out" --width=500 )
[ -z "$out" ] && exit


cd "$d"
ffmpeg -i "$mask" -r "$fps" "$out"


```
rough bash script (utilizing zenity) presenting user with windows asking for input. If you wrap it in a pretty launcher you won't even know it's a cli script.
How it works: selected image file gives dir and a base to guess the file format (required to serialize images with %d placeholder pointing to index), purpose of framerate and output name windows is clear.
It does work on my 10.04 with dummy images, but real world scenarios may show some weaknesses that need fixing.
Last line where ffmpeg is executed probably needs some more info (quality/bitrate/dimensions/whatever).

---

### Post by maxsideburn on 2013-03-02
That's totally fine, i was not suggesting any write a complete framework, just a simple frontend that would ask for files and framerate and output a video...i just dont know how to make that frontend.

---

### Post by FakeOutdoorsman on 2013-03-02
> **diesch said:**
> A simple version should be possible with a shell script and Zenity. I'll have a look if someone gets me the parameters for ffempeg, mencode or whatever.

Here is an example command for ffmpeg. This is for real ffmpeg (the program) from FFmpeg (the project) and not the bizarro/fake/buggy junk from libav in the repo which also does not have some important image related features. Simply use a [static build of ffmpeg](ffmpeg.org/download.html#LinuxBuilds) or [compile ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide).

For your inputs you can use a numerical sequence, a glob pattern, or even pipe from cat (for jpeg, png, bmp, ppm, pgm, pbm, and pam).

[size=4]Numerical Sequence[/size]
Such as image0001.jpg to image1689.jpg. See [How do I encode single pictures into movies?](http://ffmpeg.org/faq.html#How-do-I-encode-single-pictures-into-movies_003f)
```
ffmpeg -start_number 100 -r 25 -i input%04d.jpg -codec:v libx264 -preset medium -crf 23 -filter:v format=yuv420p -movflags faststart output.mp4
```

[size=4]Glob Pattern[/size]
Generally more flexible than using "input%04d.jpg". Used for file names that are sequential, but not specifically numerically sequential.
```
ffmpeg -pattern_type glob -r 30000/1001 -i foo-*.jpg -codec:v libx264 -preset medium -crf 23 -filter:v format=yuv420p -movflags faststart output.mp4
```

[size=4]Option Explanations[/size]
[list]
[*]**-start_number** Start sequence with "input0100.jpg". Optional.

[*]**-r 25** Input frame rate. 25 is the default. The output will then inherit this frame rate. You can also use an additional "-r" as an output option if you want to vary the input and output frame rates, and ffmpeg will drop or duplicate frames to reach the desired output frame rate.

[*]**-r 30000/1001** Example of NTSC video frame rate. You could also use an alias, such as "-r ntsc". See [list of video rate aliases](http://ffmpeg.org/ffmpeg-utils.html#Video-rate).

[*]**-codec:v libx264 ** The H.264 video encoder.

[*]**-preset medium -crf 23** Encoding preset and "constant rate factor". Basically you want to use the slowest preset you have patience for and the highest "-crf" number that still provides an acceptable quality level (unless you're uploading it to YouTube or similar, then use as high quality that is still practical since they will re-encode anyway). 18 is usually considered visually lossless or "close enough". Sane range is 18-28. See the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide).

[*]**-filter:v format=yuv420p** Make output YUV 4:2:0. ffmpeg may use a different "pixel format" depending on your input and the encoder; this behavior is technically correct, but most players (and YouTube) only support yuv420p.

[*]**-movflags faststart** Relocate the moov atom from end of file to beginning to allow playback before file is completely downloaded by client. Same as using "qt-faststart" tool. Typically used if the video is going to be played on a web site (not required for uploading to YouTube and other video sites). Optional.
[/list]

---

### Post by Tony Flury on 2013-03-04
This is a classic example of the software design maxim : 

Just because a program is easy to describe by the user does not neccessarily mean it is easy to develop.

---

### Post by ofnuts on 2013-03-04
> **Tony Flury said:**
> This is a classic example of the software design maxim : 

Just because a program is easy to describe by the user does not neccessarily mean it is easy to develop.
I would even that if it is easy to describe then it is hard to develop because the specs are too vague :) Some say that coding is mostly filling the blanks in the specs... (when it's not debugging a blank page).

---

