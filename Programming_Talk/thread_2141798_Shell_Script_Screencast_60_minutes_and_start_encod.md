---
title: "Shell Script: Screencast 60 minutes and start encoding afterwards"
date: 2013-05-03
forum: Programming Talk
---

### Post by dralban7 on 2013-05-03
Hi,

I´m pure beginner in shell script, but I´m not asking to write me a shell script.

Instead I would like to know how to execute point 1 below for a duration (for example 1 hour).
What kind of command should I use in a shell script?

The basic idea is...
I would like to write a shell script which first screencasts a region of my desktop and afterwards encodes the output file. In that case I would like to write a shell script which runs the command 1 below for 1 hour.
Afterwards the shell script should start encoding (point 2 below).

############ myShellScript.sh: Begin #####################
1.) Screencast a region with ffcast:
ffcast -vvs ffmpeg -f alsa -ac 2 -i pulse -r 30 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv
2.) Encode the output.mkv file
ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -pix_fmt yuv420p -preset slow -crf 22 
threads 0 -profile:v main our-final-product.mp4
############ myShellScript.sh: End #####################

Remark:
Later I would like to pass the duration of the execution as command-line parameter to shell script (for example "./myShellScript.sh 60" for 60 minutes).
In that case I would run point 1 above 60 minutes and would start encoding afterwards.

Thank you.
Greetings
Karl

---

### Post by matt_symes on 2013-05-03
Thread moved to **Programming Talk.**

---

### Post by Isamu715 on 2013-05-03
From ffcast manual:
       ```
-t, --duration <time>
Restrict cast video duration in seconds. hh:mm:ss[.xxx] format is also fully supported.
```
To make it last an hour command 1 will look like this:
```
ffcast -vvs ffmpeg -f alsa -ac 2 -i pulse -r 30 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 -t 01:00:00 output.mkv
```
The first command line parameter is $1, so to pass the number of minutes your script will record it'll be something like this:
```
ffcast -vvs ffmpeg -f alsa -ac 2 -i pulse -r 30 -acodec pcm_s16le  -vcodec libx264 -preset ultrafast -crf 0 -threads 0 -t 00:$1:00  output.mkv
```
However, I don't know how exactly ffcast operates and whether 60+ minutes or one-digit numbers would be accepted in this format. You can convert minutes into seconds and then pass them to ffcast.
```
(( time=$1*60 ))
ffcast -vvs ffmpeg -f alsa -ac 2 -i pulse -r 30 -acodec pcm_s16le  -vcodec libx264 -preset ultrafast -crf 0 -threads 0 -t $time output.mkv
```

---

### Post by dralban7 on 2013-05-04
Hi Isamu715,

great... This works just fine. 

ffmpeg is recording a browser. I would like to close the browser at the end of the 60 minutes.
From command line I can open a web page for example: [FONT=Courier New]/usr/bin/firefox [www.cyberciti.biz](www.cyberciti.biz)[/FONT].
But how can I close it at the end of a recording. Or do I have to kill the browser session?

Thank you.

Greetings.
Karl

---

### Post by dralban7 on 2013-05-04
Hi,

I found some information here: [http://ubuntuforums.org/showthread.php?t=2135806](http://ubuntuforums.org/showthread.php?t=2135806).

Karl

---

