---
title: "Is there any good desktop recorder in ubuntu"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by rpupa on 2012-04-16
I download a program called Desktop recorder. It never record a video smoothly, can't understand if the problem is with the software of the os(ubuntu). Is there any good desktop recorder...

---

### Post by mastablasta on 2012-04-17
there are a coupple of them. and there is even a Wink but a bit older version.

---

### Post by Jagoly on 2012-04-17
Unfortuanatily most screen recording tools in ubuntu are pretty pathetic. My favorite however is kazam: [https://launchpad.net/kazam](https://launchpad.net/kazam)

It isn't available in the normal repos at the moment, so you need to use the PPA.

Also, a few weeks ago, I needed to do some screencasts of minecraft, which I've found that the only recorder that really stays smooth at high loads is ffmpeg. So, I wrote a basic (and probably very nooby) script to record the desktop as well as a basic GUI to offer some configuration.

```
#!/bin/bash

# Zenity frontend to using ffmpeg as a screencasting tool

CRES=$(xdpyinfo | grep dimensions | awk '{print $2}')
let DTHREADS=$(lscpu | grep CPU\(\s\): | head -1 | awk '{print $2}')/2

FPS=$(zenity --title=FFScreenCast --entry --text='Enter Desired Framerate:' --entry-text=30)
THREADS=$(zenity --title=FFScreenCast --entry --text='Enter Number of Threads to Use:' --entry-text=$DTHREADS)

DEST=$(zenity --title=FFScreenCast --file-selection --save --confirm-overwrite --filename=recording.mkv)

ffmpeg -loglevel quiet -y -f alsa -ac 2 -i pulse -f x11grab -r $FPS -s $CRES -i :0.0 -vcodec libx264 -vpre lossless_ultrafast -crf 22 -acodec libmp3lame -ar 44100 -ab 126k -threads $THREADS "$DEST" &

RECPID=$!
zenity --title="FFScreenCast - Recording..." --info --text="Recording to $DEST\nRecording at $FPS Frames Per Second\nUsing $THREADS threads for ffmpeg\nPress OK to finish recording..."

kill $RECPID
```

just save that to something like record.sh on the desktop, then go to properties->permisions and check the box "mark as executable" then just double click it and choose run.

But, unless you are recording gameplay, kazam is great.

---

### Post by morhin on 2012-04-17
Might help if we knew what you were trying to record? DVD's, youtube, or what. 
I noticed someone mentioned gaming and I can't speak to that. But for normal stuff I've had great luck with
Firefox Download Helper, Thoggen DVD Ripper, VLC player and so on. 

Morhin

;)

---

### Post by rpupa on 2012-04-17
ok, thanks guys, i appreciate your help, i will try them.

---

