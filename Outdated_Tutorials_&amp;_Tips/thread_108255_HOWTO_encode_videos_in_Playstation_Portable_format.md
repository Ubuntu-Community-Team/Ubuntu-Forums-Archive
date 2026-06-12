---
title: "HOWTO encode videos in Playstation Portable format"
date: 2005-12-25
forum: Outdated Tutorials &amp; Tips
---

### Post by daigorobr on 2005-12-25
I suffered a lot trying to get Ubuntu to encode videos for the PSP format.
It is not perfect yet, as it only works in 320x240 resolution and titling doesn't work, but at least it's doable.

First, I had to recompile ffmpeg with faac, faad and xvid enabled - got it from [http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/]("http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/").
Apprently the link is down, so here is the full text (I don't remember the author's name, so let me thank him anonimously):

> Fixing ffmpeg on Ubuntu

For various boring legal reasons, Ubuntu Linux’s various packages are separated out into different repositories based on their licensing restrictions. As a result of this, packages which are in the main repository but require packages in other repositories for additional functionality are compiled without those extra features.

Very tedious.

Here’s how to get a copy of ffmpeg to work with things like AAC, MP3, and so on. I am assuming that you have already enabled the ‘multiverse’ and ‘universe’ repositories. If not, do so first. Now, bust out a terminal, and type this (changing the cvs date as appropriate):

sudo apt-get build-dep ffmpeg
sudo apt-get install liblame-dev libfaad2-dev \
libfaac-dev libxvidcore4-dev checkinstall fakeroot
apt-get source ffmpeg
cd ffmpeg-0.cvs20050121
vi debian/rules

Add the following lines to debian/rules, under the other confflags lines:

confflags += --enable-mp3lame --enable-faad
confflags += --enable-faac --enable-xvid

Continuing in the terminal:

fakeroot debian/rules binary
sudo checkinstall

This will take some time, after which the process asks for some details. You can accept the default choices, except for the following changes:

    * Set ‘Name’ to ‘ffmpeg’.
    * Set ‘Version’ to something newer than the currently installed ffmpeg (I called mine ‘3:0.cvs20050121-1ubuntu2’).

After that, you should have a system-recognised, fully-loaded version of ffmpeg. If you have problems, leave a comment. The above method worked for me on 5.04; it might not work on also works on 5.10 according to reports. (Thanks, Kyle.)

Then, for the settings to be used on ffmpeg, I borrowed a script from [http://my.opera.com/agony_/blog/show.dml/81864]("http://my.opera.com/agony_/blog/show.dml/81864").
Here it is:
```
#!/bin/bash

SRCFILE="$1"
TITLE="$2"

DSTNAME=M4V$(printf '%05d' ${RANDOM})

ffmpeg -i "${SRCFILE}" -title "${TITLE}" -s 320x240 -b 512 -ar 24000 -ab 64 -r 29.970030 -f psp "${DSTNAME}.MP4"

mplayer -vo jpeg -ss 10 "${SRCFILE}" -frames 2
convert -size 160x120 00000001.jpg "${DSTNAME}.THM"
rm -f 00000001.jpg

echo "${DSTNAME}.MP4 and ${DSTNAME}.THM created."
```

Please note that the really important thing to be done is setting the video bitrate to 29.970030 since it's the only way the PSP will read it seamlessly.

Hope it helps someone and if somebody gets it to work more completely, please let us all know.

---

### Post by tofudrifter on 2006-02-27
i followed the howto and placed the script in nautilus scripts directory but when i right click and run the script and file browser the conversion will crash, play the starting ~.5 seconds of audio and then leave me with a .mp4, 2 jpg's and a .thm

---

### Post by daigorobr on 2006-03-02
Sorry, let me understand. You run both the script and the file browser and it crashes. If you run the script "by hand" (I mean, via bash) does it ahppen?

---

### Post by chenno on 2006-07-03
I can confirm that your procedure works on Dapper Dan (6.06 LTS). I'm encoding a video right now, seems to work fine.

---

