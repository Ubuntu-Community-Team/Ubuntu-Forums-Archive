---
title: "Finding video file info from command line (FFMpeg Mplayer etc)"
date: 2007-06-15
forum: Programming Talk
---

### Post by HedonismBot on 2007-06-15
Hello forumers

I'm creating a media manager script for Ubuntu that's going to handle a website we've inherited with thousands of older video files, and I need a way to get the file info (size, bitrate, dimensions) of these files into a txt/csv document to being importing into a SQL db.

I've tried to use FFMPEG, but it only halts at the end of the ffmpeg -i (filename) command so using it with a wild card and a > output is useless. 

Does nyone know of a method to either pipe the output of FFMPEG or Mplayer to a file or any other app / hack that will let me output the dimensions of files in a dir to a txt dump?

Thanks!
;)

---

### Post by jyba on 2007-06-15
You could try something like this, but it's a bit slow...

```
for filename in $(ls *mpg *avi)
	do mplayer -nosound -vo null -ss 03:00:00 -really-quiet -identify $filename
	echo -e "\n**************\n"
	done >>info.txt
```

---

### Post by jyba on 2007-06-15
A much quicker and better way...

```
sudo apt-get install libimage-exiftool-perl
exiftool *.mp4 *.mpg *avi *mov
```

---

### Post by HedonismBot on 2007-06-29
Bingo.

jyba, respect. *applause* =D>

---

### Post by kwaanens on 2007-08-16
> **jyba said:**
> A much quicker and better way...

```
sudo apt-get install libimage-exiftool-perl
exiftool *.mp4 *.mpg *avi *mov
```

Is the formatting of the output consistent on all types of files?

I've been using idvid from Tovid, but it is somewhat lacking.
I'm making a script including lines like 
```
INPUT_FRAMERATE=$(grep 'Framerate:' $IDVID_FILE | awk '{print $2}')
```
so the wording must be consistent.

Are there other tools that will list properties of video files?

Any info that this tool misses?

- Ketil

---

### Post by kwaanens on 2007-08-17
> **kwaanens said:**
> Any info that this tool misses?

Yes, I found out myself. It misses video fps on the two wmvs that I tried. idvid from Tovid gets this info.

- Ketil

---

### Post by cthlhu1987 on 2009-09-08
idvid is a lil' slow.

---

### Post by andrew.46 on 2009-09-08
Hi,

I can see a little necroposting has resurrected this old thread :-). Many are perhaps not aware that the svn MPlayer source tree has a few scripts in the TOOLS directory and one is a little script that improves the *mplayer -identify* function a little. I am pretty sure the GNU GPL licensing allows me to reproduce it here in full:

```

#!/bin/sh
#
# This is a wrapper around the -identify functionality.
# It is supposed to escape the output properly, so it can be easily
# used in shellscripts by 'eval'ing the output of this script.
#
# Written by Tobias Diedrich <ranma+mplayer@tdiedrich.de>
# Licensed under GNU GPL.

if [ -z "$1" ]; then
	echo "Usage: midentify.sh <file> [<file> ...]"
	exit 1
fi

mplayer -vo null -ao null -frames 0 -identify "$@" 2>/dev/null |
	sed -ne '/^ID_/ {
	                  s/[]()|&;<>`'"'"'\\!$" []/\\&/g;p
	                }'

```

This can be *very* useful for scripting...

Andrew

---

