---
title: "Bash shell script race condition"
date: 2012-06-03
forum: Programming Talk
---

### Post by TheEnglishman on 2012-06-03
I have a shell script that monitors a directory with inotifywait.  This all works fine if I only transfer one file in.  The script transcodes a video file using ffmpeg .  If I transfer multiple files into the directory at the same time and don't process them with ffmpeg everything works fine( just comment out the ffmpeg... line in the script)

But if I transcode files while copying in multiple files at the same time I get errors and the script doesn't transcode all the files I copied.  

I think it's the fact that inotifywait notifications happen while the script is busy with transcoding or something.  But I don't know how to 'store/buffer' the notifications.  I tried waiting for ffmpeg to finish by adding in a loop but that didn't work.

Any pointers/ideas from those who are good that this kind of thing?

Here's the script:-
```
#!/bin/bash
shopt -s nocasematch
    DIR="/transcode/transcode"
    SUFFIX="MOV"

function doWork () {
    if [ ${1##*.} = $SUFFIX ]; then # If a file ext matches SUFFIX
         echo "Transcoding "$1 " to "${1%%.*}".mpg"
         ffmpeg -threads 0 -i $1 -s 320x240 -r 30000/1001 -b:v 200k -bt 240k -vcodec libx264 -acodec libfaac -ac 2 -ar 48000 -ab 192k ${1%%.*}.mp4
         # PROCRUN=`/bin/pidof ffmpeg` # check to see if ffmpeg running
         # while [ -n "$PROCRUN" ]
         # do
         #    PROCRUN=`/bin/pidof ffmpeg`
         # done
         echo "Deleting " $1
         rm $1
    fi
}

# inotify 
inotifywait -qme close_write --format %w%f $DIR/ | while read filename;
do
    doWork $filename
done
```

---

### Post by matt_symes on 2012-06-03
Hi

I have done something very, very similar in the past but i used symlinks to the files and the name of the symlink identified the type of transcoding to be done; a bit like busybox.

I also used incron !

```
sudo apt-get install incron
```

```
man incrontab
```

```
incrontab -e
```

> But if I transcode files while copying in multiple files at the same time I get errors and the script doesn't transcode all the files I copied. 

What are the exact error messages ?

You are not doing any logging. Append to a log file in your script to see what is happening.

Kind regards

---

### Post by TheEnglishman on 2012-06-03
I can run the script ./transcodemonMOV.sh >> transcode.log

If I comment out the ffmpeg line and copy in 3 files I see the 'echo' commands I put in the script in the log file for all 3 files.

If I uncomment out the ffmpeg line and copy in 3 files the script only processes 1 file and I only see 1 file's worth of echo commands in the log file.

So somehow I loose two of the notifications when running ffmpeg.  I just wondered if there was a way to buffer these notifications.

---

### Post by matt_symes on 2012-06-03
Hi

> I just wondered if there was a way to buffer these notifications.

You can add a lock file to the script.

```
man lockfile
```

Are you sure you cannot have multiple instances of ffmpeg transcoding at the same time...

*cough* as i said, i used incron.

Kind regards

---

### Post by matt_symes on 2012-06-03
Hi

You may want to quote your variables that contain filenames. Spaces in the filenames will cause problems.

doWork **"$filename"**

ffmpeg -threads 0 -i **"$1"** -s 320x240 -r 30000/1001 -b:v 200k -bt 240k -vcodec

Have a read of this.

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

Kind regards

---

