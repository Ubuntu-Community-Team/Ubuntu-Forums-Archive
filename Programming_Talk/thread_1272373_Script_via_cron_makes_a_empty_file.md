---
title: "Script via cron makes a empty file"
date: 2009-09-22
forum: Programming Talk
---

### Post by szczym on 2009-09-22
Helo

I have a script that makes a movie. When i run it from command line as normal user, it works. But when i run it from cron as ordinary user, it makes empty file.

Code:

#!/bin/sh
# make a movie every 10 min and overide the temps
dump=/home/photocapture/dump
imgtempdir=/var/www/tutturu/sites/default/files/temp/images
videotempdir=/var/www/tutturu/sites/default/files/temp/video
fname=`date +%Hh-%d-%b-%Y`
dirname=`date +%d-%b-%Y`
webcamdir=/var/www/tutturu/sites/default/files/webcam

logger -t tutturu "copy images from working dir into temp"
cp ~/image-input/$dirname/1280x1024/*.jpg $imgtempdir/
logger "copied"
logger "making avi movie"
cd $imgtempdir
mencoder "mf://*.jpg" -mf fps=25 -o $videotempdir/$fname.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2500
logger "finish making movie $fname.avi"
logger "start of making ogv videobin"
ffmpeg2theora $videotempdir/$fname.avi -p videobin -o $videotempdir/$fname-videobin.ogv
logger "made movie $fname.ogv, coping to webcam/today-videobin.ogv"
cp $videotempdir/$fname-videobin.ogv $webcamdir/today-videobin.ogv
logger "copied"
logger "start of making ogv preview"
ffmpeg2theora $videotempdir/$fname.avi -p preview -o $videotempdir/$fname-preview.ogv
logger "made movie $fname-prevew.ogv, coping"
cp $videotempdir/$fname-preview.ogv $webcamdir/today-videobin.ogv
logger "finished movies now delete"
rm $imgtempdir/*.jpg
logger "deleted photos"


The files $webcamdir are accessible via website. I run it as ordinary user becouse i want to avoid problems with permissions down the round. user is member of the www-data group.

What is a reason of empty files from cron ?

---

### Post by geirha on 2009-09-22
Install the package [bsd-mailx](apt://bsd-mailx). When that package is installed, cron will mail you any output from the script, and hopefully there'll be a useful error message. Have the script run by cron, then type ```
mail
``` to read such mails.

---

