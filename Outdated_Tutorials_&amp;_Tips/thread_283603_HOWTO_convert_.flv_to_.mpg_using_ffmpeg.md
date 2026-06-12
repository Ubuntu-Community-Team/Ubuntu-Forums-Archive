---
title: "HOWTO: convert .flv to .mpg using ffmpeg"
date: 2006-10-24
forum: Outdated Tutorials &amp; Tips
---

### Post by DarkN00b on 2006-10-24
I was searching for a program to convert .FLV files to .MPG files. I found an easy way to do it using the command line and ffmpeg. First, you have to make sure you have ffmpeg installed, if you don't then install it from the repositories.

Then:
1.   Save a .flv file to a folder (your home folder is fine). I'm going to assume you know how to do this. :-D 

2.   Open a terminal window and navigate to the folder where you saved the .flv.

3.   Type this in the terminal window and hit enter:

```
 ffmpeg -i video.flv -ab 56 -ar 22050 -b 500  -s 320x240 video.mpg
```

Video.flv is the file you want to convert, so the name must be the same as the source file. You can name video.mpg whatever you want as long as it has the .mpg extension.

Here's an explanation of the options used here:
-b bitrate: set the video bitrate in kbit/s (default = 200 kb/s)
-ab bitrate: set the audio bitrate in kbit/s (default = 64)
-ar sample rate: set the audio samplerate in Hz (default = 44100 Hz)
-s size: set frame size. The format is WxH (default 160x128 )

If you need help, type man ffmpeg.

I use [Keepvid]("http://keepvid.com/") to download videos from YouTube and Google video. The result is a .flv file I can't watch in Ubuntu. Mplayer does not play the video and VLC doesn't play sound. ](*,) 
NOTE:
This was taken from a blog called "The 409". This is not my own work, I just posted it here to make it Ubuntu specific. Go to [The 409]("http://asuaf.org/~jj/blog/index.php/2006/01/08/convert-google-video-flvs-into-avi-mpg-etcin-linux/") for the original article.

---

### Post by honeydew on 2007-05-11
I fouund this one laying around and thought it was a good script..

```

#!/bin/sh

# YouTube Videodownloader for those of us, 
# who has no sucking Flash in their browsers.
# If you experience any problems with this script, please
# report them to ivap on SILCNet (https://silcnet.org)
#
# $Id: hacktube.sh,v 0.1.0.9 2007/04/29 00:45:51 ivap Exp $

if [ $# -lt 1 ]; then
   echo -e 1>&2 "Usage: $0 [-f] <url or id>"
   echo -e 1>&2 "Options:\n\t-f   enable ffmpeg postprocessing"
   echo -e 1>&2 "Examples: "
   echo -e 1>&2 "\t$0 http://www.youtube.com/watch?v=injqufD1WZI"
   echo -e 1>&2 "\t$0 injqufD1WZI"
   exit 64
fi

while [ $# -ge 1 ]; do
            case "$1" in
             "-f")
                if ! `which ffmpeg >/dev/null 2>&1`; then
                   echo 1>&2 "ERROR: Install ffmpeg and try again"
                   exit 69
                fi
                with_ffmpeg="true"              
                ;;
             *youtube*)
                vid_url=$1
                ;;
             *)
                vid_url=`echo http://www.youtube.com/watch?v= $1 | sed 's/ //g'`
                ;;
            esac
            shift
done

if ! `which wget >/dev/null 2>&1`; then
   echo 1>&2 "ERROR: Install wget and try again"
   exit 69
fi

f_id=`echo $vid_url | sed 's/.*=//1'`
base_url='http://www.youtube.com/get_video?'
temp_fname=`mktemp html_data.XXXXXX`
if [ $? -ne 0 ]; then
   echo "ERROR: cannot create temp file"
   exit 69
fi

if ! wget -q -O $temp_fname $vid_url; then
   echo "ERROR: could not retrieve requested page"
   rm $temp_fname
   exit 69
fi

new_url=`cat $temp_fname | grep player2.swf | sed 's/va.*?//1' | sed 's/".*;//g'`
complete=`echo $base_url $new_url| sed 's/ //1'`
rm $temp_fname

if ! wget -O ${f_id}.flv $complete; then
    echo "ERROR: could not retrieve requested video"
    exit 69
fi

#feel free to tune ffmpeg's flags
if [ -n "$with_ffmpeg" ]; then 
   if ffmpeg -acodec mp3 -i ${f_id}.flv ${f_id}.avi; then
         rm ${f_id}.flv
         exit 0
   else
      echo "ERROR: could not convert video"
      rm -f ${f_id}.avi
      exit 69
   fi
fi

```

save this file and make it executable 

```

chmod +x hacktube.sh

```

and then  type ./hacktube.sh  [http://youtube.com/url](http://youtube.com/url)....  

enjoy =]

---

### Post by captgadget on 2007-05-15
whenever I try this I get this error message: Big-Fish.flv: I/O error occured
Usually that means that input file is truncated and/or corrupted.

---

### Post by khalidaziz on 2008-04-23
That means you haven't navigated to the file. Do that by typing

```
cd /home/khalid/Desktop
```

replace "/home/khalid/Desktop" with whatever address the folder containing the file has.

---

### Post by ctyc on 2008-04-23
Very nice ffmpeg trick thanks.
:)

---

### Post by therabbt on 2008-04-27
I can't get this working on Hardy.  It worked great on Gutsy though.
Here's what I get.  I'm not really sure how to get ffmpeg to work...
```

spencer@manbearnix:~/Desktop$ ffmpeg -i punched.flv -b 500 -s 320x240 out.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
punched.flv: Unknown format
```

---

### Post by Hells_Dark on 2008-04-27
Nice :)
Even if i play the flv format with mplayer.. no problem at all..

---

### Post by Egeste on 2008-05-15
> **therabbt said:**
> I can't get this working on Hardy.  It worked great on Gutsy though.
Here's what I get.  I'm not really sure how to get ffmpeg to work...
```

spencer@manbearnix:~/Desktop$ ffmpeg -i punched.flv -b 500 -s 320x240 out.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
punched.flv: Unknown format
```

```
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
sw_attack.flv: Unknown format
```

---

### Post by ffmpegfailure on 2008-06-24
Sorry, im new to ffmpeg. I tried your command line and this happened. Also, will the same script work for converting to mp4?

> username:~$ ffmpeg  video.flv -ab 56 -ar 22050 -b 500 -s 320x240 convertedvideo.mpg 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
File video.flv' already exists. Overwrite ? [y/N] y
Cannot open video device /dev/video : No such file or directory
Could not find video grab device
username:~$ 


---

### Post by iqpilot on 2009-08-16
I got the : Incorrect frame size , but the frame size is apps correct :(

hrvoje@localhost:~/Videos/Music$ ffmpeg -i CarlCox#118.flv -ab 56 -ar 22050 -b 500 -s 320×240 CarlCox#118.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 12.50 (25/2)
Input #0, flv, from 'CarlCox#118.flv':
  Duration: 01:00:41.8, start: 0.000000, bitrate: 128 kb/s
  Stream #0.0: Video: vp6f, yuv420p, 640x360, 12.50 fps(r)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Incorrect frame size

---

### Post by Nyken on 2009-11-06
Have Karmic Koala now, but Darkn00b's instruction is currently correct. Had no problems using it.

---

### Post by tomski on 2009-11-17
hi peep's
 i use the following:

```

ffmpeg -i input.flv -target ntsc-dvd -s 648x364 -padleft 36 -padright 36 -padtop 58 -padbottom 58  output.mpg

```

i would love if some of you guy's out there could create a nautilus/sh script that would allow me to 'bulk' convert an entire folder full of flv files, keep the original filename & output to the input folder as i have approx 10Gb of flv files which i need to convert to mpg to play them on my d-link dsm520 & im getting fed up with doing it manually

i have tried various apps but they just complicate things further and do not want to learn their way lol
i know what i got
i know what i need

and the above code just works for me
thanks

---

### Post by FakeOutdoorsman on 2009-11-17
> **tomski said:**
> hi peep's
 i use the following:

```

ffmpeg -i input.flv -target ntsc-dvd -s 648x364 -padleft 36 -padright 36 -padtop 58 -padbottom 58  output.mpg

```

i would love if some of you guy's out there could create a nautilus/sh script that would allow me to 'bulk' convert an entire folder full of flv files, keep the original filename & output to the input folder as i have approx 10Gb of flv files which i need to convert to mpg to play them on my d-link dsm520 & im getting fed up with doing it manually

i have tried various apps but they just complicate things further and do not want to learn their way lol
i know what i got
i know what i need

and the above code just works for me
thanks

You could use FFmpeg with the find command to bulk convert your files.  See andrew.46's excellent guide for details and examples:

[Linux Basics: A gentle introduction to 'find'](http://ubuntuforums.org/showthread.php?t=1128937)

---

### Post by tomski on 2009-11-19
thnx for the tip fakeoutdoorsman but i have no scripting experience and have no idea where to begin on implementing your advice!

i guess my post was more of a plea/request to readers to create it
my time is filled by trying to get my ubuntu to work correctly since the koala upgrade, perhaps once this is finished i will attempt to learn bash programming

---

### Post by mc4man on 2009-11-19
For the moment here is a batch convert *command* that will do as you asked, same filename, same dir. ( using your parameters in blue

```
for f in *.flv; do ffmpeg -i "$f" [COLOR="Blue"]-target ntsc-dvd -s 648x364 -padleft 36 -padright 36 -padtop 58 -padbottom 58[/COLOR] "${f%.flv}.mpg"; done
```

assumes your flash has a .flv ext. ( if no ext. then add

You just cd to the dir. containing files to be converted and run.

As far as a script, I've got to run but you could do it a few different ways, you'd probably want it executed in a visible terminal. (either by starting a terminal at the wanted dir. prompt as above for the command or having that part of the script.

---

### Post by Sotiri on 2010-12-02
for better quality use this!  ffmpeg -i existingvideo.format -ab 56 -ar 44100 -b 1000 outgoingvideo.format that .format is if you want to convert frome anny type op video codec.

---

### Post by FakeOutdoorsman on 2010-12-02
> **Sotiri said:**
> for better quality use this!  ffmpeg -i existingvideo.format -ab 56 -ar 44100 -b 1000 outgoingvideo.format that .format is if you want to convert frome anny type op video codec.

That won't work. FFmpeg takes bitrate values in bits/s, and your command will tell the encoder to use 56 bits/s for the audio.  Add a "k" to your bitrate values.

---

### Post by Sotiri on 2010-12-05
It works for me!


[IMG]http://gamingmedia.be/images/originalphotos/62/4/eeb559ff9ce1c599cde06a09.png[/IMG]

---

### Post by FakeOutdoorsman on 2010-12-05
> **Sotiri said:**
> It works for me!
Let's try some tests. H.264 / AAC audio in MKV:
```
$ ffmpeg -i IronMan.mkv -ab 56 -ar 44100 -b 1000 -y out.mkv
...
Seems stream 0 codec frame rate differs from container frame rate: 47.95 (10000000/208541) -> 24.00 (24/1)
Input #0, matroska,webm, from 'IronMan.mkv':
  Duration: 00:01:48.50, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 1280x720, PAR 115:87 DAR 1840:783, 23.98 fps, 24 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16
**WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s**
[buffer @ 0x1e76fe0] w:1280 h:720 pixfmt:yuv420p
Output #0, matroska, to 'out.mkv':
  Metadata:
    encoder         : Lavf52.88.0
    Stream #0.0: Video: mpeg4, yuv420p, 1280x720 [PAR 115:87 DAR 1840:783], q=2-31, 1 kb/s, 1k tbn, 24 tbc
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, s16, **0 kb/s**
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 2600 fps= 86 q=31.0 Lsize=   21587kB time=108.46 bitrate=1630.5kbits/s    
video:21491kB audio:45kB global headers:0kB muxing overhead 0.240341%
```
Result: Output contains an invalid audio stream and no audio plays back with ffplay or mplayer. The audio stream is 45 KB in file size for a 108 second input.

Another format. H.263 / MP3 in FLV:
```
ffmpeg -i in.flv -ab 56 -ar 44100 -b 1000 out.flv
```
Result: It plays. The output of this 60 second input contains an audio stream that is 117 KB in file size. This means that FFmpeg is ignoring your **-ab** and using the default value of 64k.

Conclusion: FFmpeg will output a warning telling you that the bitrate parameter is set too low and, depending on the encoder, the output file may either create a non-playable file or will revert to the default of **-ab 64k**.

---

### Post by Sotiri on 2010-12-08
so why did it work for me then?

---

### Post by ron999 on 2010-12-08
> **Sotiri said:**
> so why did it work for me then?
Probably because you are using an old version of ffmpeg.
Enter:-
```
**[FONT="Courier New"]ffmpeg[/FONT]**
```
to find out when your ffmpeg was compiled.
Like so:-
> ron@ubuntu:~$ ffmpeg
FFmpeg version SVN-r25751, Copyright (c) 2000-2010 the FFmpeg developers
  built on Nov 14 2010 13:43:35 with gcc 4.4.1


---

### Post by FakeOutdoorsman on 2010-12-08
> **Sotiri said:**
> so why did it work for me then?

It probably didn't use your *-ab* value, and so didn't work as expected. Divide the size of the audio stream by the duration to find your bitrate. It will probably be around 64 **k**bits/s and not 56 bits/s.

---

### Post by Sotiri on 2010-12-13
> **ron999 said:**
> Probably because you are using an old version of ffmpeg.
Enter:-
```
**[FONT=Courier New]ffmpeg[/FONT]**
```to find out when your ffmpeg was compiled.
Like so:-


I have an output  like this!


FFmpeg version SVN-r25846, Copyright (c) 2000-2010 the FFmpeg developers
  built on Nov 29 2010 20:40:21 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.33. 0 / 50.33. 0
  libavcore      0.14. 0 /  0.14. 0
  libavcodec    52.97. 2 / 52.97. 2
  libavformat   52.87. 1 / 52.87. 1
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.65. 0 /  1.65. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

---

