---
title: "Is there an easy-to-use program for converting MP4 to MP3?"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by HunterDX77M on 2012-02-17
I just got that video downloader extension for Firefox, and was wondering if there way an easy way to convert the downloaded MP4's to MP3's?  The extension says I need a program called ffmpeg, which I installed, but the in-extension conversions still fail. I appreciate any help!

---

### Post by Jose Catre-Vandis on 2012-02-17
This little bash script will convert the audio in an mp4 file to mp3. It will run on all mp4s in a directory

```
#!/bin/bash

#convert mp4 to mp3

FILES="*.mp4"

for F in $FILES

do
newname=`basename "$F" .mp4`
echo $newname
ffmpeg -i "$F" -vn -acodec libmp3lame -ac 2 -ab 128k -ar 44100 "$newname.mp3"

done
```

You can edit the file extension to handle other file types and adjust the parameters in the ffmpeg command line

---

### Post by yetiman64 on 2012-02-17
For a graphical interface you could try audacity, open audacity, drag and drop a mp4 onto the interface, select file > export, set to mp3 and set options, then name and save, add tag details if needed.

---

### Post by Matt__ on 2012-02-17
you could try [Mobile media converter](http://www.miksoft.net/mobileMediaConverterDown.htm).
It has an easy to use GUI - drag and drop and uses mencoder and ffmpeg.

[IMG]http://img813.imageshack.us/img813/2223/captureybj.png[/IMG]

---

### Post by clive littlewood on 2012-02-17
Hi

A nice easy online converter is RIP     [http://www.listentoyoutube.com/](http://www.listentoyoutube.com/)

You enter the youtube url and it then rips the audio and downloads to your PC.

Hope that helps

Clive

---

### Post by HunterDX77M on 2012-02-17
Thanks for all the suggestions guys! :D:D

I tried Audacity and it worked perfectly. I still want to try the others (particularly the command line solution) for the sake of my curiosity.

---

### Post by andrew.46 on 2012-02-17
> **HunterDX77M said:**
> I still want to try the others (particularly the command line solution) for the sake of my curiosity.

If you are keen to try FFmpeg first bulk up the Ubuntu FFmpeg by following this guide:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then run the following command against one of your downloaded mp4 files:

```
ffmpeg -i *input.mp4*
```

Substitute *input.mp4* with the actual name and correct path to your own file and then post the command and full terminal output here. It will be easy enough to then suggest a suitable commandline for you.

---

