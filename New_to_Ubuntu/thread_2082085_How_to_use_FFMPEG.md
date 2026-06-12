---
title: "How to use FFMPEG"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by Hari5g900 on 2012-11-08
Hello,
    How can I get ffmpeg to record my screen and capture system audio? I googled a lot but could only find things that would not work. I can record without sound with this command:
```
ffmpeg -r 30 -s 1280x800 -f x11grab -i :0.0 -vcodec msmpeg4v2 -qscale 1 /home/ubuntu/Videos/NewVideo.avi
```
But is there any way to get the sound too?

---

### Post by linuxorunix on 2012-11-08
Dear Hari5g900,

Maybe this forum post can help you: [http://forums.fedoraforum.org/showpost.php?p=515790&postcount=3]("http://forums.fedoraforum.org/showpost.php?p=515790&postcount=3")

For the whole topic, please see this url: [http://forums.fedoraforum.org/showthread.php?t=106888]("http://forums.fedoraforum.org/showthread.php?t=106888")

Good luck with it :)

Kind regards,
linuxorunix

---

### Post by Hari5g900 on 2012-11-08
Well, that won't work

```
ubuntu@ubuntu-linux:~$ ffmpeg -vd /dev/video0  -vcodec mpeg4  -ad /dev/dsp -ar 44100 -ab 64 -ac 2  -target vcd ~/home/ubuntu/Desktop/test.avi
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1~ppa1~lucid1, Copyright (c) 2000-2010 the Libav developers
  built on Apr  7 2011 02:04:15 with gcc 4.4.3
  configuration: --extra-version='4:0.6.2-1ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version='4:0.6.2-1ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version='4:0.6.2-1ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version='4:0.6.2-1ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version='4:0.6.2-1ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version='4:0.6.2-1ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version='4:0.6.2-1ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version='4:0.6.2-1ubuntu1~ppa1~lucid1' --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Unrecognized option 'vd'

```

---

### Post by ron999 on 2012-11-08
...

---

### Post by Hari5g900 on 2012-11-10
...??

---

### Post by HiImTye on 2012-11-10
this is the script I wrote, though I haven't tested it since I switched to 12.10. it worked with the 12.04 medibuntu ffmpeg. it needs to be run in a terminal or you have no way other than killing ffmpeg to stop it from capturing (and if you kill the script itself, it won't combine or transcode). the output is YouTube compatible webm using vorbis for audio

YouTubeTranscode.sh
```
#!/bin/bash

# put your videos folder here. it's usually $HOME/Videos but if you use a
 # different one, you can change it
basevideosfolder="$HOME/Videos"
# the video preset we are going to use for capture. different presets will give captures of different quality
videopreset="ultrafast"

# the folder we're going to use
videosfolder="$basevideosfolder/YouTube"
if [ ! -d "$videosfolder" ]; then
 mkdir $videosfolder
fi

# the base name of our capture files
capturefile=$videosfolder/.capture

# Start Log
rm -f $capturefile.mkv $capturefile.wav $capturefile.log ffmpeg2pass*.log
echo Start of Process > $capturefile.log

# Variables
TEXT="Resolution"
OPTION1="$(xrandr --current|sed -n 's/.*current[ ]\([0-9]*\) x \([0-9]*\),.*/\1x\2/p')"
DIMENSIONS="$(zenity --list --radiolist --text $TEXT --column "" --column "Choose" TRUE $OPTION1 FALSE "Other")"
if [ "$DIMENSIONS" = "Other" ]; then
 DIMENSIONS=$(zenity --entry --text $TEXT)
elif [ "$DIMENSIONS" = "" ]; then
 clear
 echo Cancelled By User Input at: $TEXT >> $capturefile.log
 sleep 1
 exit
fi
echo $TEXT=$DIMENSIONS >> $capturefile.log
TEXT="Audiosink"
OPTION1="pulse"
OPTION2="hw:0,0"
AUDIOSINK="$(zenity --list --radiolist --text $TEXT --column "" --column "Choose" TRUE $OPTION1 FALSE $OPTION2 FALSE "Other")"
if [ "$AUDIOSINK" = "Other" ]; then
 AUDIOSINK=$(zenity --entry --text $TEXT)
elif [ "$AUDIOSINK" = "" ]; then
 clear
 echo Cancelled By User Input at: $TEXT >> $capturefile.log
 sleep 1
 exit
fi
echo $TEXT=$AUDIOSINK >> $capturefile.log
TEXT="Framerate"
FRAMERATE=$(zenity --scale --text $TEXT --min-value=1 --max-value=30 --value=15 --step 2)
if [ "$FRAMERATE" = "" ]; then
 clear
 echo Cancelled By User Input at: $TEXT >> $capturefile.log
 sleep 1
 exit
else
 echo $TEXT=$FRAMERATE >> $capturefile.log
fi

# Capture
echo Capture >> $capturefile.log
ffmpeg -f alsa -ac 2 -i $AUDIOSINK -f x11grab -r $FRAMERATE -s $DIMENSIONS -i $DISPLAY -vcodec libx264 -preset $videopreset -crf 0 -threads 0 $capturefile.mkv -acodec pcm_s16le $capturefile.wav
echo Status = $? >> $capturefile.log
if ! zenity --question --text="keep?"; then
 echo Cancelled, Removing Files
 rm -f $capturefile.wav $capturefile.mkv $capturefile.log ffmpeg2pass*.log
 exit
fi
# Filename
tempfilename=$(zenity --entry --text "What should we call the file?" --entry-text "YouTube")
# strip the .webm extension from it, if it exists
if echo "$tempfilename" | grep .webm; then
 eval tempfilename='$(echo "$tempfilename" | sed "s|.webm||")'
fi
# Offer to change the name of our video if our name is already used
if [ -f "$videosfolder/"$tempfilename".webm" ]; then
 echo duplicate file found, prompting user >> $capturefile.log
 dupefilename="$tempfilename"
 dupereference="$tempfilename"
 while :
 do
   # see if we have a number at the end of our filename like so: filename.number
   if echo "$dupefilename" | grep -E '\.[0-9]+$'; then
     # if so, make it our new count
     count=$(echo "$dupefilename" | sed 's|.*\.\([0-9]*\)$|\1|')
     eval dupefilename=$(echo "$dupefilename" | sed 's|\(.*\)\.[0-9]*$|\1|')
   else
     # if not, create it
     count=0
   fi
   # add 1 to our number
   count=$(expr $count + 1)
   # ask the user what to rename our video to
   dupefilename=$(zenity --entry --text "Duplicate exists, what should we call our new one?\nnote: cancel deletes the old file." --entry-text '"$dupefilename".$count')
   # strip the .webm extension from it, if it exists
   if echo "$dupefilename" | grep .webm; then
     eval dupefilename='$(echo "$dupefilename" | sed "s|.webm||")'
   fi
   #if our new filename is different than our old one, reset our count
   if [ ! "$dupefilename" = "$dupereference" ]; then
     count=0
   fi
   # exit the loop if we're not renaming the file
   if [ "$dupefilename" = "" ]; then
     break
   # exit the loop if the file doesn't exist
   elif [ ! -f "$videosfolder/"$dupefilename".webm" ]; then
     break
   fi
   dupereference="$dupefilename"
 done
 if [ "$dupefilename" = "" ]; then
   echo "deleting old file" >> $capturefile.log
   rm -f $videosfolder/"$tempfilename".webm
 else
   # fix our file name
   echo "our new file name" >> $capturefile.log
   # change our filename
   tempfilename="$dupefilename"
 fi
fi
# add our videos folder to our filename, to make it cleaner
filename=$videosfolder/."$tempfilename"
shownfilename=$videosfolder/"$tempfilename"
# Remove any old temporary files, to be sure
echo removing existing temp files starting with ."$tempfilename" >> $capturefile.log
rm -f "$filename".log "$filename".mkv "$filename".temp.mkv "$filename".wav
# Rename to allow a simultaneous capture while we convert
echo renaming current temp files >> $capturefile.log
mv -v $capturefile.mkv "$filename".mkv >> $capturefile.log
mv -v $capturefile.wav "$filename".wav >> $capturefile.log
# we have to echo here as the output isn't redirected after it's moved so the
 # move just overwrites the output
mv $capturefile.log "$filename".log ; echo "Log file renamed:" >> "$filename".log; echo "'$capturefile.log' -> '"$filename".log'" >> "$filename".log
# Combine
echo Combine >> "$filename".log
ffmpeg -i "$filename".mkv -i "$filename".wav -vcodec copy -acodec copy "$filename".temp.mkv
echo Status = $? >> "$filename".log
# Conversion
echo Conversion Pass 1 >> "$filename".log
ffmpeg -i "$filename".temp.mkv -preset libvpx-720p -b 3900k -pass 1 -an -f webm -y "$shownfilename".webm
echo Status = $? >> "$filename".log
echo Conversion Pass 2 >> "$filename".log
ffmpeg -i "$filename".temp.mkv -preset libvpx-720p -b 3900k -pass 2 -acodec libvorbis -ab 100k -f webm -y "$filename".temp.mkv
echo Status = $? >> "$filename".log

echo Finished
echo End of Process >> "$filename".log
# Finalization
if zenity --question --text="clean up?"; then
 echo Removing Temporary Files
 rm -f "$filename".mkv "$filename".temp.mkv "$filename".wav "$filename".log ffmpeg2pass*.log
else
 echo Skipped Removal of Temp Files
fi

sleep 1
exit
```

---

### Post by Hari5g900 on 2012-11-12
Honestly, I didn't understand anything you just typed.
But I figured out a way myself. I combined two codes I got and now I can capture screen with audio with ffmpeg.
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x800 -i :0.0 -acodec pcm_s16le -vcodec msmpeg4v2 -qscale 1 /home/ubuntu/Desktop/Output.avi
```

---

### Post by Hari5g900 on 2012-12-07
Is there any way to record audio (with microphone) and capture system audio with FFMPEG?

---

### Post by RottNKorpse on 2013-01-03
Yes, set your pulse default to be your internal audio then use Audacity separately to record your microphone.

---

### Post by dannyboy79 on 2013-01-03
if you want to do it all in one ffmpeg command, you need to create some loopback devices using modules and pulseaudio. search these forums for streaming to twitch.tv. it shows how to create the loopbacks and stream to twitch but instead of streaming to twitch you could just save it to a file instead.

so to answer your question, yes, you can capture your desktop, your system sound, and your microphone all in one command

you could check out kazam screencaster, it's awesome as well!

---

### Post by sdowney717 on 2013-01-03
Kazaam works the best, imo.
I think it makes webm video files.

---

