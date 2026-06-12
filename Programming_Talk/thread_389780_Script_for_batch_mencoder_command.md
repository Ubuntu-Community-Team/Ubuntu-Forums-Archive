---
title: "Script for batch mencoder command"
date: 2007-03-21
forum: Programming Talk
---

### Post by elreteipos on 2007-03-21
First of all, I am not familiar with shell scripting, so I'm asking for your help. I want to do > mencoder aVideoFile.avi -of mpeg -oac lavc -lavcopts acodec=mp2:abitrate=192 -af resample=44100:0:0 -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=50 -vf scale,harddup -ofps 25 -zoom -xy 176 -o aVideoFile.mpgfor all files in /media/ipod and its subdirectories. How can I do that?

---

### Post by colo on 2007-03-21
```
find /media/ipod -type f -exec mencoder {} -of mpeg -oac lavc -lavcopts acodec=mp2:abitrate=192 -af resample=44100:0:0 -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=50 -vf scale,harddup -ofps 25 -zoom -xy 176 -o {}.mpg \;
```

---

### Post by elreteipos on 2007-03-21
Thanks. There's one more thing I want to do: if both FILENAME.avi and FILENAME.avi.mpg exist, don't let mencoder convert the file again since it has already been converted. Is that possible by, perhaps, adding a "do-not-overwrite" parameter to the mencoder command?

---

### Post by Mr. C. on 2007-03-22
Do you want FILENAME.avi to convert to FILENAME.mpg or FILENAME.avi.mpg ?

Sometimes the find command gets too difficult to use to build complex commands, so its better to use find in combination with a shell script.  The shell script does the basic job of encoding the file, but only if the file.mpg does not exist.  The find command is responsible for sending do_encode the filenames to work on.

Here's your new find command:

```
find /media/ipod  -name '*.avi' -type f  -exec ~/do_encode {} \;
```

it will call a shell script called do_encode, which you will create as follows:

```
#!/bin/bash

function encode
{
    echo mencoder "$1" -o "$2" -of mpeg -oac lavc -lavcopts \
        acodec=mp2:abitrate=192 -af resample=44100:0:0 \
       -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=50 \
       -vf scale,harddup -ofps 25 -zoom -xy 176
}

mpg=$(echo $1 | sed 's/\.avi$/\.mpg/')
if [ -e "$mpg" ] ; then
    echo $1 already encoded to $mpg
else
    encode "$1" "$mpg"
fi
```

Save the code above into a file named **do_encode** in your home directory, and changer permissions on it:

```
chmod a+x ~/do_encode
```

MrC

---

### Post by elreteipos on 2007-03-22
> Do you want FILENAME.avi to convert to FILENAME.mpg or FILENAME.avi.mpg ?I think FILENAME.avi.mpg is easier for the program to recognize, so I'll use that format.

Does this work? ipodConvert:```
#! /bin/bash
find /media/ipod -wholename *.avi -exec mencoderAVI {} \;
find /media/ipod -wholename *.mp4 -exec mencoderMP4 {} \;
find /media/ipod -wholename *.mov -exec mencoderMOV {} \;
```mencoderAVI:```
#!/bin/bash

function encode
{
    echo mencoder "$1" -o "$2" -of mpeg -oac lavc -lavcopts \
        acodec=mp2:abitrate=192 -af resample=44100:0:0 \
       -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=100 \
       -vf scale,harddup -ofps 25 -zoom -xy 176
}

mpg=$(echo $1 | sed 's/\.avi$/\.mpg/')
if [ -e "$mpg" ] ; then
    echo $1 already encoded to $mpg
else
    encode "$1" "$mpg"
fi
```Same for mencoderMP4 and mencoderMOV, but I replaced```
mpg=$(echo $1 | sed 's/\.avi$/\.mpg/')
```with```
mpg=$(echo $1 | sed 's/\.mp4$/\.mpg/')
```and```
mpg=$(echo $1 | sed 's/\.mov$/\.mpg/')
```ipodConvert and the mencoder scripts are included in $PATH.

---

### Post by Mr. C. on 2007-03-22
It doesn't sound like there is a question here.  You have it under control ?

MrC

---

### Post by elreteipos on 2007-03-23
I customized the script a little bit to suit my needs. I have a problem though:> pdedecker@BETAubuntu:~/Scripts$ vipodconv
[Skipped] /media/ipod/Video/EY5-full.avi
[Skipped] /media/ipod/Video/EY6-full.avi
[Skipped] /media/ipod/Video/EY7-full.avi
[Skipped] /media/ipod/Video/EY3-full.avi
[Skipped] /media/ipod/Video/EY4-full.avi
[Skipped] /media/ipod/Podcasts/Family's Naturally Sadie/0111 - Spring break.mp4
[Skipped] /media/ipod/Podcasts/Family's Naturally Sadie/0112 - Family and Friends.mp4
[Convert] /media/ipod/Podcasts/- Video Package - A PodShow Channel/commandN Episode 83.mp4
MEncoder 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:                 Intel(R) Celeron(R) CPU 2.40GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: '"/media/ipod/Podcasts/-'
Failed to open "/media/ipod/Podcasts/-.
Cannot open file/device.

Exiting...As you can see, mencoder is having trouble interpreting a directory name that contains the - symbol. Do you know how I can fix this?

This is vipodconv:```
#! /bin/bash
find /media/ipod -wholename *.avi -exec vipodconv_mencoder "{}" \;
find /media/ipod -wholename *.mp4 -exec vipodconv_mencoder "{}" \;
find /media/ipod -wholename *.mov -exec vipodconv_mencoder "{}" \;
find /media/ipod -wholename *.m4v -exec vipodconv_mencoder "{}" \;
```

This is vipodconv_mencoder:```
#!/bin/bash

function encode
{
    mencoder \"$1\" -o \"$1.mpg\" -of mpeg -oac lavc -lavcopts \
        acodec=mp2:abitrate=192 -af resample=44100:0:0 \
       -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=100 \
       -vf scale,harddup -ofps 25 -zoom -xy 176 -quiet
}

if [ -e "$1.mpg" ] ; then
    echo [Skipped] $1
else
    echo [Convert] $1
    encode "$1" "$1.mpg"
fi
```Again: both programs are accessible via the $PATH stuff.
And by the way, can mencoder also handle M4V files?

---

### Post by Mr. C. on 2007-03-23
When you escaped the quotes with backslashes in 

```
mencoder \"$1\" -o \"$1.mpg\"
```

you removed the ability to protect the value passed as $1.  The double quotes are required so that mencoder gets exactly what was passed inside $1.

I don't know what mencoder does with its arguments.  See if you can pass a filename that contains a dash directly to mencoder itself.  I also have no idea what mencoder can handle. Search the web for mencoder to find its home page.  Perhaps its this: [http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#mencoder](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#mencoder)

MrC

---

### Post by cgreulich on 2007-04-05
I'm trying to do something similar with FFMPEG, but I can't seem to make it work following this thread as an example.  Here is what I'd like to do:

I'd like to be able to run a script named "encode" in any given directory and have it take all the files in the directory that I execute the script from and have it run this:

ffmpeg -i inputfile.avi -ab 128 -b 1000 -vcodec mpeg4 -s 360x240 -deinterlace outputfile.avi

where inputfile.avi is every file in the directory, and all of the encoded output files go into a subdirectory called /output retaining their original file names.

Is this possible to do?  I'd really appreciate any help, I have about 500 home video files that I captured with Kino that I'm trying to encode and I can't find an easy way to do it.

---

### Post by Mr. C. on 2007-04-05
Put this in a file called ~/encode:

```
#!/bin/bash

mkdir output
for movie in *.avi ; do
    echo Processing $movie
    ffmpeg -i $movie -ab 128 -b 1000 -vcodec mpeg4 -s 360x240 -deinterlace output/$movie
done     
```               

Run this command to make it executable:
```
chmod a+x encode
```

and then run encode from inside your movie directory.
```

cd moviedir
~/encode
```

MrC

---

### Post by cgreulich on 2007-04-06
This works great!!!

Thank you so much for your help:)

---

### Post by Mr. C. on 2007-04-06
You're welcome.

MrC

---

### Post by m2nmx on 2008-08-13
Thank you very much Mr. C., the script works perfectly. Below I give example for using this script for processing whole directory with mencoder:

```
#!/bin/bash


for movie in *.avi ; do
echo Processing "$movie"
mencoder "$movie" -ofps 22 -vf-add scale=320:240 -vf-add expand=320:240:-1:-1:1 -srate 44100 -ovc xvid -xvidencopts bitrate=280:max_bframes=0:quant_type=h263:me_quality=3 -oac lavc -lavcopts acodec=mp2:abitrate=64 -o /home/TypeYourOutputDir/"$movie"
done
```

---

