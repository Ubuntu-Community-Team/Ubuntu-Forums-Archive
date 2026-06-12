---
title: "Video Converter"
date: 2010-11-10
forum: Philippine Team
---

### Post by JCyberinux on 2010-11-10
i need a video converter like super video converter in windows xp. is there such a thing or equivalent in ubuntu? i try winFF, but i also need a AVI to MOV. because i'm going to put it on my ipod touch video.

Thanks!

---

### Post by aljoriz on 2010-11-10
Try the featured app called Arista Transcoder from the Software Center.

---

### Post by enhu on 2010-11-10
open the .avi file in avidemux and save as .mov

---

### Post by punong_bisyonaryo on 2010-11-10
I used WinFF before to convert the whole Full Metal Alchemist for my iPod Nano. iPods can handle MPEG-4 formats (MOV and MP4 are both just containers for the MPEG-4 codecs).

Depending on which version of WinFF you're using, you just need to choose iPod or Rockbox in the Convert To dropdown box.

Post back if you need more help.:D

> **JCyberinux said:**
> i need a video converter like super video converter in windows xp. is there such a thing or equivalent in ubuntu? i try winFF, but i also need a AVI to MOV. because i'm going to put it on my ipod touch video.

Thanks!

---

### Post by pinoyskull on 2010-11-10
try handbrake 
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by Cpierce on 2010-11-10
Another vote for Handbrake

---

### Post by d3v1150m471c on 2010-11-10
ffmpeg, all the way. It's CLI but easy to learn and powerful. Converts sound and video btw.
```

# examples:
# convert an mp4 to an avi with the same quality.

ffmpeg -i input.mp4 -sameq output.avi

# extract sound from video
ffmpeg -i input.avi output.mp3

```

---

### Post by Script Warlock on 2010-11-10
what about the ibulk just beside your sig d3v1150m471c... but i'm fine with handbrake. check this out [http://www.marcus-furius.com/?page_id=200](http://www.marcus-furius.com/?page_id=200)

---

### Post by d3v1150m471c on 2010-11-11
> **Script Warlock said:**
> what about the ibulk just beside your sig d3v1150m471c... but i'm fine with handbrake. check this out [http://www.marcus-furius.com/?page_id=200](http://www.marcus-furius.com/?page_id=200)

ibulk is a frontend to ffmpeg geared for converting videos to use on ipods and iphones. I'll have to check on the requirements for the "touch's" video necessities. if the question is best video converter i vote ffmpeg. For best video converter apple products, minus the touch because I haven't researched it, i use ibulk. keep in mind ibulk needs ffmpeg and some libraries from medibuntu to convert anything with AAC encoding.

Update:

Yes, ibulk will convert videos for the ipod touch. The requirements are the same as the iphones.

---

### Post by JCyberinux on 2010-11-11
thanks for the responds guys, i'm going to try it out all of your suggestions... I'll let you know guys if what i'm using right now and which is really gives me a best bet.

---

### Post by JCyberinux on 2010-11-12
> **aljoriz said:**
> Try the featured app called Arista Transcoder from the Software Center.

I tried the arista transcoder, result were acutally good enough to covert my avi to mov...
easy to used without any configurations, speaking of configurations the only thing i worried is the customization of the video output. Let's say i want to convert it to mov will sample rate like this, frame rate like this, sound quality like this... etc... you know what i mean right.
anyway i gives the output what i need, but still hording some good features.

cheers! :popcorn:

---

### Post by seydou on 2010-11-12
As for viewing any movie on the iPod/iPhone - I use mencoder, mplayer, sox, gpac and faad to produce mp4 movies, and I gather it is the most flexible and reliable way of doing the thing. It can be wrapped up in a script, used in a batch etc. In case you interested, follow this steps:

1/ get the software (I guess everybody has mplayer/mencoder, but one never knows)

```

sudo apt-get install mencoder gpac faad mplayer sox

```

2/ Convert the video

Let's take somefile.avi example, xvid coded avi container. We need to obtain mpeg4 video stream, without audio at this stage. The simplest mencoder command would be:

```

mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=900 \
-ofps 25 -o video.avi somefile.avi

```

Note we use rather low bitrate of 900, which is good enough for small iPod's screen, and we run single pass encoding.

In case you want to render the subtitles as well, you can do this:

```

mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=900 \
-ofps 25 -sub subtitles.srt -o video.avi somefile.avi

```

You can also specify the subtitle character encoding by '-subcp' parameter (for example '-subcp cp1250').

3/Convert the audio

The audio stream can be in whole lot of different formats, so let's strip it as a wav first, mplayer does the job nicely and quickly:

```

mplayer -ao pcm -vo null -vc dummy somefile.avi

```

After this, we will have the original sound in audiodump.wav file (mplayer default filename).

Let's examin it before we go on.

```

file audiodump.wav

```

The response could be

```

audiodump.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, mono 44100 Hz

```

As we can see, it is mono, so we might want to convert it to a stereo. The sample rate could also be different, so I recommend to treat audiodump.wav in this manner

```

sox audiodump.wav -b 16 -c 2 -r 44100 tmp.wav

```

It produces 16 bit stereo sound with 44100 Hz sample rate. You can run it without even checking the audiodump.wav, it does no harm and runs quick. Now, we need to produce AAC coded audio, as it is the one iPod requires.

```

faac -q 75 -w tmp.wav

```

And the file tmp.m4a lands in our directory.


4/ Putting things together

Now, put it all together by exactly following:

```

MP4Box my_ipod_movie.mp4 -add video.avi#video -add tmp.m4a

```

Yes, the '#' looks weird, but it should be there like this. Now, you can synchronise my_ipod_movie.mp4 with your iPod.

I have done numerous tests, and always produced decend movie with correct sync of video/audio. I have rigged up the script, which does the job for me. It features 2pass encoding, and some image enhancements options, but it does not render subtitles. Here it is for your convenience:

```

#!/bin/bash

#simple imput check
if [ $# -eq 1 ];then
:
else
echo "Wrong imput file: or none, or too many. Pass only one at the time."
exit
fi

#picture enhancement parameters
VOPT="mbd=2:keyint=132:v4mv:vqmin=3:lumi_mask=0.07:dark_mask=0.2:scplx_mask=0.1:tcplx_mask=0.1:naq"

#bitrate setting, the bigger the value, the bigger the file
#but also better quality
BR=900

#the in-file is supposed to be avi container
INFILE=$1
OUTFILE="${INFILE%.[Aa][Vv][Ii]}.mp4"

#2pass video encoding
mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4:vpass=1:vbitrate=$BR:$VOPT -ofps 25 -o /dev/null "${INFILE}" && \
mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4:vpass=2:vbitrate=$BR:$VOPT -ofps 25 -o video.avi "${INFILE}"

#strip out the original sound
mplayer -ao pcm -vo null -vc dummy "${INFILE}"

#treat it for propper format
sox audiodump.wav -b 16 -c 2 -r 48000 tmp.wav

#and create AAC coded audio
faac -q 75 -w tmp.wav

#put the streams together
MP4Box "${OUTFILE}" -add video.avi#video -add tmp.m4a

#and clean the garbage
rm -f video.avi tmp.m4a audiodump.wav tmp.wav divx2pass.log


```

---

### Post by d3v1150m471c on 2010-11-12
I created a .deb package for iBulk btw. The link's on my signature. I used to use arista, which is why I created iBulk. I like arista but it's incredibly slow.

---

### Post by JCyberinux on 2010-11-13
> **enhu said:**
> open the .avi file in avidemux and save as .mov

is choosing auto > ipod is a better option rather than customized converting? thanks!

---

### Post by JCyberinux on 2010-11-13
> **enhu said:**
> open the .avi file in avidemux and save as .mov

another question! when i try to auto > ipod > click (ok)
it prompts me "*Codec Error* *Cannot select the MPEG-4 SP codec*"
do i have to download another packages for this one? thanks!

---

### Post by JCyberinux on 2010-11-13
> **d3v1150m471c said:**
> I created a .deb package for iBulk btw. The link's on my signature. I used to use arista, which is why I created iBulk. I like arista but it's incredibly slow.

sir thank you for sharing your thoughts with us, anyway i download your iBulk software on .deb then installed it. For some reason, there was an issue encountered:

*Error: Dependency is not satisfiable: gtkdialog (>= 2.0)*

hmm.. i guess another packages to be downloaded or to be added right? i try to find it at synaptic package manager but nowhere to be found. kindly advice me sir. thank you!

---

### Post by Samhain13 on 2010-11-16
> **d3v1150m471c said:**
> ffmpeg, all the way. It's CLI but easy to learn and powerful. Converts sound and video btw.

+1 for FFMpeg. I can't live without it. :guitar:

---

### Post by d3v1150m471c on 2010-11-16
```
sudo apt-get install gtkdialog
```then reinstall iBulk. I originally developed it as purely CLI. I only recently added the GUI option using gtkdialog. If you don't want to install gtkdialog you can use the tar.gz package instead, as it works perfectly without the GUI. It comes with a install/uninstall script so you won't have to worry about random files on your pc you cannot find to remove, should you decide you want to uninstall it.

---

### Post by echo2knight on 2010-11-18
I use Arista, Avidemux and Handbrake for transcoding.

They perform better than the transcoder I was using in windows.

Only proves that OSS can be better than commercial softwares.

---

### Post by JCyberinux on 2010-11-20
> **d3v1150m471c said:**
> ```
sudo apt-get install gtkdialog
```then reinstall iBulk. I originally developed it as purely CLI. I only recently added the GUI option using gtkdialog. If you don't want to install gtkdialog you can use the tar.gz package instead, as it works perfectly without the GUI. It comes with a install/uninstall script so you won't have to worry about random files on your pc you cannot find to remove, should you decide you want to uninstall it.


there is no gtkdialog package.. i tried it...

*E: Couldn't find package gtkdialog*

and i also tried to search it on synaptic package manager, no results!

---

### Post by JCyberinux on 2010-11-20
> **echo2knight said:**
> I use Arista, Avidemux and Handbrake for transcoding.

They perform better than the transcoder I was using in windows.

Only proves that OSS can be better than commercial softwares.

(by the way, how to i install the handbrake...) ----> i got it!!! from via ppa! .deb

---

### Post by JCyberinux on 2010-11-20
> **seydou said:**
> As for viewing any movie on the iPod/iPhone - I use mencoder, mplayer, sox, gpac and faad to produce mp4 movies, and I gather it is the most flexible and reliable way of doing the thing. It can be wrapped up in a script, used in a batch etc. In case you interested, follow this steps:

1/ get the software (I guess everybody has mplayer/mencoder, but one never knows)

```

sudo apt-get install mencoder gpac faad mplayer sox

```2/ Convert the video

Let's take somefile.avi example, xvid coded avi container. We need to obtain mpeg4 video stream, without audio at this stage. The simplest mencoder command would be:

```

mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=900 \
-ofps 25 -o video.avi somefile.avi

```Note we use rather low bitrate of 900, which is good enough for small iPod's screen, and we run single pass encoding.

In case you want to render the subtitles as well, you can do this:

```

mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=900 \
-ofps 25 -sub subtitles.srt -o video.avi somefile.avi

```You can also specify the subtitle character encoding by '-subcp' parameter (for example '-subcp cp1250').

3/Convert the audio

The audio stream can be in whole lot of different formats, so let's strip it as a wav first, mplayer does the job nicely and quickly:

```

mplayer -ao pcm -vo null -vc dummy somefile.avi

```After this, we will have the original sound in audiodump.wav file (mplayer default filename).

Let's examin it before we go on.

```

file audiodump.wav

```The response could be

```

audiodump.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, mono 44100 Hz

```As we can see, it is mono, so we might want to convert it to a stereo. The sample rate could also be different, so I recommend to treat audiodump.wav in this manner

```

sox audiodump.wav -b 16 -c 2 -r 44100 tmp.wav

```It produces 16 bit stereo sound with 44100 Hz sample rate. You can run it without even checking the audiodump.wav, it does no harm and runs quick. Now, we need to produce AAC coded audio, as it is the one iPod requires.

```

faac -q 75 -w tmp.wav

```And the file tmp.m4a lands in our directory.


4/ Putting things together

Now, put it all together by exactly following:

```

MP4Box my_ipod_movie.mp4 -add video.avi#video -add tmp.m4a

```Yes, the '#' looks weird, but it should be there like this. Now, you can synchronise my_ipod_movie.mp4 with your iPod.

I have done numerous tests, and always produced decend movie with correct sync of video/audio. I have rigged up the script, which does the job for me. It features 2pass encoding, and some image enhancements options, but it does not render subtitles. Here it is for your convenience:

```

#!/bin/bash

#simple imput check
if [ $# -eq 1 ];then
:
else
echo "Wrong imput file: or none, or too many. Pass only one at the time."
exit
fi

#picture enhancement parameters
VOPT="mbd=2:keyint=132:v4mv:vqmin=3:lumi_mask=0.07:dark_mask=0.2:scplx_mask=0.1:tcplx_mask=0.1:naq"

#bitrate setting, the bigger the value, the bigger the file
#but also better quality
BR=900

#the in-file is supposed to be avi container
INFILE=$1
OUTFILE="${INFILE%.[Aa][Vv][Ii]}.mp4"

#2pass video encoding
mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4:vpass=1:vbitrate=$BR:$VOPT -ofps 25 -o /dev/null "${INFILE}" && \
mencoder -nosound -ovc lavc -lavcopts vcodec=mpeg4:vpass=2:vbitrate=$BR:$VOPT -ofps 25 -o video.avi "${INFILE}"

#strip out the original sound
mplayer -ao pcm -vo null -vc dummy "${INFILE}"

#treat it for propper format
sox audiodump.wav -b 16 -c 2 -r 48000 tmp.wav

#and create AAC coded audio
faac -q 75 -w tmp.wav

#put the streams together
MP4Box "${OUTFILE}" -add video.avi#video -add tmp.m4a

#and clean the garbage
rm -f video.avi tmp.m4a audiodump.wav tmp.wav divx2pass.log


```

too many things to do, but for some reasons the m4a doesn't work on my ipod touch... i dont know why... maybe i miss something.

---

### Post by TimEnid on 2010-12-09
i currently use handbrake to convert movies for my droid, by using the itouch preset. for some reason, there is no droid preset. so i downloaded Arista, and converted a 4gb movie, not only did it take 2 hours to conver (handbrake takes about 20 minutes), the size of the converted file was about 3gb. and it wouldnt even play on my droid. i sent the company an email asking them about this. maybe i did something wrong. but i selected the droid preset and then chose droid x. i wish dvd catalyst was available for ubuntu. it wont work in my virtual box.

---

### Post by ragadanga63 on 2010-12-16
Mobile Media Converter.  Here's an article which also has the download link:

[http://www.chinwong.com/index.php?/site/comments/cool_media_converter/](http://www.chinwong.com/index.php?/site/comments/cool_media_converter/)

Works fine and fast in 10.10.

---

### Post by QwUo173Hy on 2010-12-16
> **ragadanga63 said:**
> Mobile Media Converter.  Here's an article which also has the download link:

[http://www.chinwong.com/index.php?/site/comments/cool_media_converter/](http://www.chinwong.com/index.php?/site/comments/cool_media_converter/)

Works fine and fast in 10.10.

I've just tried it, and it's the best in terms of ease of use. But when converting an 850MB avi file for the ipod (mp4), the output file is over 400MB. Should it not be a LOT smaller than that?

---

### Post by pinoyskull on 2010-12-16
> **jarlath said:**
> I've just tried it, and it's the best in terms of ease of use. But when converting an 850MB avi file for the ipod (mp4), the output file is over 400MB. Should it not be a LOT smaller than that?
that is still big for an IPOD video, unless its super high quality mp4

---

### Post by QwUo173Hy on 2010-12-17
> **pinoyskull said:**
> that is still big for an IPOD video, unless its super high quality mp4

I just used the 3gp instead, and they are one tenth of the size. The picture quality is poor, but I am watching lectures and it's quite fine for that.

---

### Post by ragadanga63 on 2010-12-18
At the lower right side of the MMC, there's a drop down menu for the video quality and even a button for advanced options.  Have you tried using the "low" setting?

---

### Post by QwUo173Hy on 2010-12-18
> **ragadanga63 said:**
> At the lower right side of the MMC, there's a drop down menu for the video quality and even a button for advanced options.  Have you tried using the "low" setting?

I hadn't spotted that ragadanga63, thanks. I'll give it a shot when I'm encoding the next lot. 

Cheers!

---

### Post by TimEnid on 2011-01-01
> **jarlath said:**
> I've just tried it, and it's the best in terms of ease of use. But when converting an 850MB avi file for the ipod (mp4), the output file is over 400MB. Should it not be a LOT smaller than that?

i downloaded the deb file, but it wont install.

---

### Post by Script Warlock on 2011-01-01
@TimEnid,if you mean MMC  try to install with sudo dpkg -i file.deb sa terminal.... then check sa applications>sound and video. during the days of Gdebi kahit na tapos mo na install ang mmc "install" pa din ang nakadisplay.

---

