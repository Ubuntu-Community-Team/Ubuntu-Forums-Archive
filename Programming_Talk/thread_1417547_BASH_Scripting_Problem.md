---
title: "BASH Scripting Problem"
date: 2010-02-27
forum: Programming Talk
---

### Post by Tristanm1 on 2010-02-27
I have a minor problem. I am attempting to write a script where I need to work on a list of files in a directory. The easiest way would seem to be to simply ls the directory in question and pipe the output into a variable. Unfortunately, I am unaware how to do this as it isn't as simple as pipelining it in or setting it equal to the command. Any suggestion how to do this?

---

### Post by howlingmadhowie on 2010-02-27
one of the standard ways is as follows:
```

for i is `ls`
do
echo $i #### do something with i
done

```

---

### Post by kaibob on 2010-02-27
If I understand your question correctly, a pipeline is not required. In the following, replace the echo command with whatever command you want to use. 

```
for file in * ; do
   echo "$file"
done
```

---

### Post by Tristanm1 on 2010-02-27
The only problem is that there are spaces in the filenames, so I need to find a way to break them up by newlines, not spaces.

EDIT: That second one fixes the space/newline issue. Thanks.

EDIT2: New Problem, the spaces in the filename are causing problems when attempting to work with the file. Here's the script.

```
#!/bin/bash
WORK=/home/tristan/Desktop
SOURCE=$WORK/unconverted
TARGET=$WORK/converted

cd $WORK

for FILE in $SOURCE/*
do

ffmpeg -i $FILE -an -pass 1 -vcodec libx264 -vpre fastfirstpass -b 700k -bt 200k -threads 0 $FILE
rm $FILE
ffmpeg -i $FILE -acodec libmp3lame -ab 96 -pass 2 -vcodec libx264 -vpre hq -b 700k -bt 200k -threads 0 $FILE

done
``` File seems to cut off at the spaces when fed into ffmpeg, causing ffmpeg to complain about the file not existing.

---

### Post by dwhitney67 on 2010-02-27
Try something like:
```

#!/bin/bash

ls | while read file
do
        echo "$file"
done

```
You may need to place $file in double-quotes for your needs.

---

### Post by Tristanm1 on 2010-02-27
Fixed the issue of feeding the filename in by concatenating " on each side of FILE. Now the only problem is that FILE in the loop returns an absolute filepath instead of a relative one. If I had a relative path, it'd be easy to feed the converted into another folder with the same filename.

---

### Post by DaithiF on 2010-02-27
if $FULLPATH contains a full path, then you can get the filename by:
```
FILENAME=${FULLPATH##*/}
```

---

### Post by Tristanm1 on 2010-02-27
Well, that worked, but I'm back to a previous problem with the strings themselves. I thought I fixed the problem of the commands not finding the files properly due to the spaces by concatenating " to each end of the string. That doesn't seem to be working, despite being able to feed filepaths to said said commands encased in ". 

```
#!/bin/bash
WORK=/home/tristan/Desktop
SOURCE=$WORK/unconverted
TARGET=$WORK/converted

cd $WORK

for FILE in $SOURCE/*
do

FILENAME=${FILE##*/}

SOURCEFILE=\"$SOURCE/$FILENAME\"
TARGETFILE=\"$TARGET/$FILENAME\"

ffmpeg -i $SOURCEFILE -an -pass 1 -vcodec libx264 -vpre fastfirstpass -b 700k -bt 200k -threads 0 $TARGETFILE
rm $TARGETFILE
ffmpeg -i $SOURCEFILE -acodec libmp3lame -ab 96 -pass 2 -vcodec libx264 -vpre hq -b 700k -bt 200k -threads 0 $TARGETFILE

done
```

Despite being able to feed filepaths into ffmpeg in the following manner,the script doesn't work.
```
ffmpeg -i "unconverted/Fraggle Rock S2 E10 - A Friend in Need.avi" -an -pass 1 -vcodec libx264 -vpre fastfirstpass -b 700k -bt 200k -threads 0 "converted/Fraggle Rock.avi"
```

---

### Post by Tristanm1 on 2010-02-27
And final issue is fixed. Concatenating " into the string was the wrong thing to do. Feeding in the variable surrounded by " without escape characters seems to be working.

---

### Post by ghostdog74 on 2010-02-27
> **howlingmadhowie said:**
> one of the standard ways is as follows:
```

for i is `ls`
do
echo $i #### do something with i
done

```

useless use of ls. use shell expansion.

---

### Post by FakeOutdoorsman on 2010-02-28
> **Tristanm1 said:**
> ```


ffmpeg -i $SOURCEFILE -an -pass 1 -vcodec libx264 -vpre fastfirstpass -b 700k -bt 200k -threads 0 $TARGETFILE
rm $TARGETFILE
ffmpeg -i $SOURCEFILE -acodec libmp3lame -ab 96 -pass 2 -vcodec libx264 -vpre hq -b 700k -bt 200k -threads 0 $TARGETFILE

done
```

Despite being able to feed filepaths into ffmpeg in the following manner,the script doesn't work.
```
ffmpeg -i "unconverted/Fraggle Rock S2 E10 - A Friend in Need.avi" -an -pass 1 -vcodec libx264 -vpre fastfirstpass -b 700k -bt 200k -threads 0 "converted/Fraggle Rock.avi"
```

I see two potential errors in your FFmpeg commands.  Bitrate is in bits/s, so you need to add a "k" to your *-ab*, otherwise your output audio bitrate is going to be very low.

Secondly, your example is using the avi container.  This is a not recommended container for H.264 video.  Try mp4 or mkv.

If you don't need an exact output file size I recommend using one-pass *-crf* instead of *-b* and *-bt*.  It will give your videos a constant quality instead of trying to adhere to a specific target bitrate (and therefore final file size).  See: [FFmpeg x264 Encoding Guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).

---

