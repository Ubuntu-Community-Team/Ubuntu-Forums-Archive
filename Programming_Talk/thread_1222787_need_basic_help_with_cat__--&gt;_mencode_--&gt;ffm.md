---
title: "need basic help with cat  --&gt; mencode --&gt;ffmpeg  using bash script"
date: 2009-07-25
forum: Programming Talk
---

### Post by awisher on 2009-07-25
I have 9.04 running motion webcam software, which captures movies and writes them to avi files. I would like to have an automated way of concatenating the days avi files, converting them to h.264 m4a files and cleaning up the directory afterward. I have created a bash script that I thought should work, but doesn't. I'm not sure what I've done wrong, but it fails to make the final m4a.

```
#! /bin/sh

# at midnight we move everything into its own dated directory

TEMP=`date +%F`

cd /webcam/Security
mkdir $TEMP

ls -1 | grep avi | xargs -n 10 -i mv {} $TEMP/

mv $TEMP /webcam/archive/$TEMP

# --------------------------------------------------------------------------------
# Concatenate all of the daily AVIs, re-index them, and convert them to H.264 MP4s

mkdir /webcam/archive/$TEMP/temp

# sort the avi files by time and cat them (sort doesn't seem to work?? )
cat $( ls -rt /webcam/archive/$TEMP/*.avi) > /webcam/archive/$TEMP/temp/noindex_A.avi

# reindex the cat avi (works)
mencoder /webcam/archive/$TEMP/temp/noindex_A.avi -o /webcam/archive/$TEMP/temp/noindex_B.avi -forceidx -ovc copy -oac copy

cd /webcam/archive/$TEMP/temp

# convert to m4a (works outside bash script, but not in???)
ffmpeg -y -i noindex_B.avi -pass 1 -vcodec libx264 -vpre fastfirstpass -vpre ipod640 -b 512k -bt 512k -s 640x480 -threads 0 -f ipod -an /dev/null && ffmpeg -i noindex_B.avi -pass 2 -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre ipod640 -b 512k -bt 512k -s 640x480 -threads 0 -f ipod output.m4a


mv output.m4a ../$TEMP.m4a
# rm -f -R /webcam/archive/$TEMP/temp
# rm -f /webcam/archive/$TEMP/*.avi

# -------------------------------------------------------------------------------

```it is all called in a cronjob as: 
59 23 * * * /webcam/motion-organize.sh >/dev/null 2>&1


I would like to log what is happening, but am not sure how to implement that part of it.
the script builds the noindex_A.avi and noindex_b.avi with out trouble, just no m4a file.

Thanks for any pointers.
aaron

---

