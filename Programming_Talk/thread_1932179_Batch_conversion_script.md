---
title: "Batch conversion script"
date: 2012-02-27
forum: Programming Talk
---

### Post by risen75 on 2012-02-27
So I'm having a little bit of a problem with this script. I've modified it in that instead of running ffmpeg.. it's running mencoder.

It starts off fine and runs through the first file and makes the conversion.. but it doens't move on to the next one.. any ideas?

```
#!/bin/sh
# video2android
# convert source video into format suitable for android phones
# Darren Wilkinson (http://tinyurl.com/darrenjw)

for name in $*
do
  echo "In: $name"
  short="${name%.*}"
  echo "Short: $short"
  long=${short}.mp4
  if [ $long = $name ]; then
    long=${short}-android.mp4
  fi
  echo "Out: $long"
	mencoder ${name} -oac mp3lame -lameopts cbr:mode=2:br=96 -af resample=44100 -	srate 44100 -ofps 20 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:cbp:trell:vbitrate=300 -vf scale=320:240 -ffourcc XVID -o ${long}
done
exit 0

# eof
```

Thanks

---

### Post by ofnuts on 2012-02-27
Works for me using "echo" on the mencoder line...

You may have a strange character in the middle of "-         srate". Can't tell if it's in your source, or if it was introduced by the copy to this forum.

---

### Post by surfer on 2012-02-27
i'd recommend to put quotes around filenames; should there be spaces in the filenames you will run into trouble.
```
long="${short}.mp4"
...

```
for all the occurences.

---

### Post by risen75 on 2012-02-27
Ok, I saw the weird thing in front of srate.. must have happened when copying over.  Now I don't know.. you said it worked for you by putting echo in the mencoder line?  umm.. ok.. but that still doesn't seem to fix the problem I'm having.. 
It's running through the first one just fine.. but when it's done with that one it just stops.  It doesn't actually exit the command, it just stops. and I have to exit that terminal window to do anything else.. It's almost like Mencoder isn't sending the signal that it's done to move on to the next one.... 
I'm trying to get it to go through my entire library and convert them for my tablet, but i shouldn't have to sit here and do each one manually.. (if i wanted to do that i'd go back to M$) 
So I'm not sure where the problem is.. If you could post up what exactly you made work (as I am very new to bash scripting and have absolutely no clue what would be missing/wrong, seeing a working script would help)

---

### Post by ofnuts on 2012-02-27
> **risen75 said:**
> Ok, I saw the weird thing in front of srate.. must have happened when copying over.  Now I don't know.. you said it worked for you by putting echo in the mencoder line?  umm.. ok.. but that still doesn't seem to fix the problem I'm having.. 
It's running through the first one just fine.. but when it's done with that one it just stops.  It doesn't actually exit the command, it just stops. and I have to exit that terminal window to do anything else.. It's almost like Mencoder isn't sending the signal that it's done to move on to the next one.... 
I'm trying to get it to go through my entire library and convert them for my tablet, but i shouldn't have to sit here and do each one manually.. (if i wanted to do that i'd go back to M$) 
So I'm not sure where the problem is.. If you could post up what exactly you made work (as I am very new to bash scripting and have absolutely no clue what would be missing/wrong, seeing a working script would help)
Since I didn't want to run mencoder I just put an "echo" at the beginning of the line. So at least this isn't a syntax problem (even if as said above you may want to add quotes here and there to handle spaces in file names)

Looks like mencoder gets stuck. Check in a process monitor if mencoder is still around. This may be your true problem. And maybe mencoder is stuck because it itself spawns another process that never ends. Have you tried with different input files?

---

### Post by Khayyam on 2012-02-27
Your problem is probably due to the use of $* .. when it should be "${@}" ..

```
for i in "${@}" ; do
    echo "Input file: ${i}"
    FILEIN="${i%.*}"
    SUFFIX="mp4"
    echo "Input Filename: ${FILEIN}"
    FILEOUT="${FILEIN}.${SUFFIX}"
    fi
    echo "Output Filename: ${FILEOUT}"
    touch "${FILEOUT}"
done
```test ...

```
% touch video{1,2,3,\ 4}.avi
% ../test.sh *.avi
Input file: video 4.avi
Input Filename: video 4
Output Filename: video 4.mp4
Input file: video1.avi
Input Filename: video1
Output Filename: video1.mp4
Input file: video2.avi
Input Filename: video2
Output Filename: video2.mp4
Input file: video3.avi
Input Filename: video3
Output Filename: video3.mp4
% ls *mp4
video 4.mp4  video1.mp4   video2.mp4   video3.mp4
```So, use "${@}" and quote "${FILEOUT}" .. also, note I've changed /bin/sh to /bin/bash

```
#!/bin/bash

for i in "${@}" ; do
    echo "Input file: ${i}"
    FILEIN="${i%.*}"
    SUFFIX="mp4"
    echo "Input Filename: ${FILEIN}"
    FILEOUT="${FILEIN}.${SUFFIX}"
    if [[ $FILENIN = $FILEOUT ]]; then
    FILEOUT="${FILENIN}-android.${SUFFIX}"
    fi
    echo "Output Filename: ${FILEOUT}"
    mencoder ${i} -oac mp3lame -lameopts cbr:mode=2:br=96 -af resample=44100 -srate 44100 -ofps 20 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:cbp:trell:vbitrate=300
 -vf scale=320:240 -ffourcc XVID -o "${FILEOUT}"

done
```

HTH & best ... khay

---

### Post by risen75 on 2012-02-27
Thanks guys/gals (not sure so i don't want to insult anyone.)

I found and even simpler solution to this problem after putting this thread up. (mind you it's been running for the last 8 hours and still has a crap load to do..)

but the solution I figured out is a one line command..

```
find <target directory here> -name "*.avi" -exec mencoder "{}" -oac mp3lame -lameopts cbr:mode=2:br=96 -af resample=44100 -srate 44100 -ofps 20 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:cbp:trell:vbitrate=300 -vf scale=320:240 -ffourcc XVID -o {}.mp4 \;
```

I'm still working on some command line stuff and hadn't realized the power of the find command for what i was doing. But thank you all again.

---

