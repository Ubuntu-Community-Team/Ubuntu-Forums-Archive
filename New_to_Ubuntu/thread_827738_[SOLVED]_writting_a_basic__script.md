---
title: "[SOLVED] writting a basic  script?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by aggierandy on 2008-06-13
Ok i wanted to convert some movies from avi to 3gp to go on my phone. I got ffmpeg to work using this command

ffmpeg -i input.avi -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 -y output.3gp

Now i want to write a simple script that i can run and it will just ask me to point to the input and point to an output. Would this be difficult? Am I approaching this the right way?

---

### Post by billgoldberg on 2008-06-13
You could just use winff, a gui for ffmpeg.

google it

---

### Post by Vivaldi Gloria on 2008-06-13
I wrote a script named avi23gp but didn't check it - i am away from my ubuntu box. Give it a try.

use as follows: avi23gp input.avi output.3gp

```

#!/bin/bash

# name: avi23gp
# requires ffmpeg !
# Usage:   ffmpeg input output
# If you don't enter an output name then the default "out.3gp" is used.
# Example:
#   avi23gp input.avi output.3gp
 

if [ $# -gt 2 ]
then
 echo
 echo "Too many parameters."
 echo "Usage: avi23gp input.avi output.3gp"
 echo "If you don't enter an output name then the default out.3gp is used."
 echo
fi


if [ $# -eq 0 ]
then
 echo
 echo "No input provided."
 echo "Usage: avi23gp input.avi output.3gp"
 echo "If you don't enter an output name then the default out.3gp is used."
 echo
fi


if [ $# -eq 1 ]
then
 ffmpeg -i $1 -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 -y out.3gp
fi


if [ $# -eq 2 ]
then
 ffmpeg -i $1 -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 -y $2
fi


echo
echo
echo

exit
```

---

### Post by aggierandy on 2008-06-13
Thanks for the quick replies guys

vivaldi i couldn't get your script to work, in the terminal it gave a dash when i executed it so i put the file location of my avi in again and then it gave this error message

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
/home/randy/Downloads/downloads/video: I/O error occured
Usually that means that input file is truncated and/or corrupted.

it gave me something similar before because i didn't put a space before the -s command in the terminal. Don't really know what is going on here, total noob in the script writting department. :/

As for winff, after some searching i found a deb for it here:

[http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60](http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60)

after install it works ok converting to .mov and others but not to 3gp error says "unknown codec libamr_nb" im not sure what this means but i found simple work around for my purposes which is 3g2 format which works just as well on my phone and probably anyone elses. Thanks again guys! exactly what i was trying to achieve. 

For the future i recommend that winff be packaged with ffmpeg and added to the repos. Especially as video on mobile devices is becoming more and more popular

---

### Post by Vivaldi Gloria on 2008-06-13
I don't know anything about ffmpeg. I just used the ffmpeg line you gave in your post. 

I think I get it. Please try using a file without a space in its name. You may need to use quotes if you use one with spaces.

The script simpler is this:

```
#!/bin/bash
ffmpeg -i $1 -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 -y $2

```

where $1 means the first argument and $2 is the second. So I just substituted $1 and $2 for your input.avi and output.3gp respectively. So as long as your line is correct and you are using a filename without spaces then it must work.

---

