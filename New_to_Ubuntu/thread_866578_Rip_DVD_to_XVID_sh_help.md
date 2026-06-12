---
title: "Rip DVD to XVID sh help"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by garok89 on 2008-07-21
iv only switched to ubuntu less than a month ago and decided to have a go at writing a script as no matter wat program i used to rip dvds, it would not work or take an excessive amount of time

after searching i came across a script [here]("http://quadpoint.org/projects/simplerip"):

[http://quadpoint.org/projects/simplerip](http://quadpoint.org/projects/simplerip)


and modified it to ask for settings etc....
being my 1st attempt at writing in sh, i was unsure how to include the option to specify deinterlacing and PAL or NTSC standards. this wasnt helped by how vague the section on this was....

and advice would be greatly appreciated (even the option to specify output directory or different codecs).

thanks
```
#!/bin/bash

#This script is for ripping DVD-Videos to Xvid

#Asks User for name of file
echo "Please type the name of the movie you would like to rip (no spaces)"
read MovieTitle

#Makes directory for output
mkdir ~/Desktop/RippedDVDs/
mkdir ~/Desktop/RippedDVDs/$MovieTitle
cd ~/Desktop/RippedDVDs/$MovieTitle

#Asks User for audio bitrate and gain
echo "Please enter audio bitrate (recommended 128)"
read AudioBitrate
echo "Please enter audio gain -10 to +10 (recommended 0)"
read AudioGain

#Asks User for video bitrate and crop details
echo "Please enter video bitrate (recommended 1024)"
read VideoBitrate
echo "Please enter crop (run 'mplayer dvd://1 -vf cropdetect' in seperate terminal and wait for stable output in the form xxx:xxx:xx:x)"
read VideoCrop


#Asks User how many passes
echo "How many passes?
1: faster encoding
2: better quality"
read Passes

# remove conflicting files
rm -f divx2pass.log frameno.avi

# rip audio track (bitrate: $AudioBitrate, gain: $AudioGain)
nice -n 3 mencoder -oac mp3lame -lameopts mode=2:cbr:br=$AudioBitrate:vol=$AudioGain \
 -ovc frameno -o frameno.avi  dvd://1

if [ "$Passes" = "1" ]
then

# video track (pass: 1, bitrate: $)
nice -n 3 mencoder -sws 2 -oac copy -ovc lavc \
 -lavcopts vcodec=mpeg4:vbitrate=$VideoBitrate:vhq \
 -ffourcc XVID -vf crop=$VideoCrop  dvd://1 -o "$MovieTitle.avi"

else

# video track (pass: 1, bitrate: $VideoBitrate)
nice -n 3 mencoder -sws 2 -oac copy -ovc lavc \
 -lavcopts vcodec=mpeg4:vbitrate=$VideoBitrate:vhq:vpass=1 \
 -ffourcc XVID -vf crop=$VideoCrop  dvd://1 -o "$MovieTitle.avi"

# video track (pass: 2, bitrate: $VideoBitrate)
nice -n 3 mencoder -sws 2 -oac copy -ovc lavc \
 -lavcopts vcodec=mpeg4:vbitrate=$VideoBitrate:vhq:vpass=2 \
 -ffourcc XVID -vf crop=$VideoCrop  dvd://1 -o "$MovieTitle.avi"

fi

echo "Process complete. Thank You. Please press Enter to exit"
read End

#done
```

ps. did i put this in the wrong section???

---

### Post by LowSky on 2008-07-23
I dont see anything in your coding for cropping the video

[http://quadpoint.org/projects/simplerip](http://quadpoint.org/projects/simplerip)

> ```
Crop and scale settings
Cropping is necessary to remove the black borders at the top and bottom of widescreen-format DVDs, and scaling will resize the output video to a smaller pixel by pixel area, resulting in increased quality. 

Mplayer can automatically detect the crop settings. To determine the appropriate settings for your video (they will likely change per movie), open a terminal and execute: 

mplayer dvd://1 -vf cropdetectwhere dvd://1 is your source. Play for about 20 seconds and wait until the output is stable. You should see something like: 

-vf crop=704:464:10:8being repeated over and over again. In this case, the &#8221;704:464:10:8&#8221; is the important part. Here is the format for crop, from the mencoder manpage: 

crop[=w:h:x:y]
Crops  the  given  part of the image and discards the rest.  Useful to remove
black bands from widescreen movies.
  w,h  Cropped width and height, defaults to original width and height.
  x,y  Position of the cropped picture, defaults to center.For determining the scale, decide if the movie widescreen (16:9 ratio) or fullscreen (4:3). 

Widescreen: use scale &#8221;704:304&#8221; (see below) Fullscreen: use scale &#8221;640:480&#8221; (see below) 

Excerpt on scaling from the mencoder manpage: 

scale[=w:h[:interlaced[:chr_drop[:param[:param2[:presize]]]]]]
 Scales the image with the software scaler (slow) and performs a 
 YUV<->RGB colorspace con-version.
  <w>,<h>
   scaled width/height (default: original width/height)
   NOTE: If -zoom is used, and underlying filters (including libvo) are  inca-
   pable of scaling, it defaults to d_width/d_height!
       0:   scaled d_width/d_height
      -1:   original width/height
      -2:    Calculate  w/h using the other dimension and the prescaled aspect
      ratio.
      -3:   Calculate w/h using the other dimension and  the  original  aspect
      ratio.
  <interlaced>
   Toggle interlaced scaling.
      0: off (default)
      1: on
  <presize>
   Scale to preset sizes.
      qntsc:   352x240 (NTSC quarter screen)
      qpal:    352x288 (PAL quarter screen)
      ntsc:    720x480 (standard NTSC)
      pal:     720x576 (standard PAL)
      sntsc:   640x480 (square pixel NTSC)
      spal:    768x576 (square pixel PAL)
```

---

### Post by garok89 on 2008-07-23
i believe the line 

-vf crop=$VideoCrop

(where VideoCrop is entered earlier) is what you are looking for

it does work on any dvds iv ripped....its really just deinterlacing (which i can just do with vlc whilst playing) and scaling to PAL or NTSC that i cant get to work.

is there a way to get it to autodetect to crop or must it be done manualy every time?

---

### Post by garok89 on 2008-07-23
After looking at the original code i realized how easy it would have been to get the scaling and interlacing options to work if i hadnt tried to do so at 5am:lolflag:

The code now asks for a directory and all options work correctly...but no codec options... i feel its better just to leave it as xvid and convert to any other codec later

Here is the final code for anyone who wants it

```

#!/bin/bash

#This script is for ripping DVD-Videos to Xvid

#Asks User for name of file ad location
echo "Please enter the name of the movie you would like to rip (no spaces)"
read MovieTitle
echo "Please enter the directory which you would like to rip to"
read RipLocation

#Makes directory for output
mkdir $RipLocation
mkdir $RipLocation/$MovieTitle
cd $RipLocation/$MovieTitle

#Asks User for audio bitrate and gain
echo "Please enter audio bitrate (recommended 128)"
read AudioBitrate
echo "Please enter audio gain -10 to +10 (recommended 0)"
read AudioGain

#Asks User for video bitrate, crop and scaling details
echo "Please enter video bitrate (recommended 1024)"
read VideoBitrate
echo "Please enter crop (run 'mplayer dvd://1 -vf cropdetect' in seperate terminal and wait for stable output in the form xxx:xxx:xx:xx)"
read VideoCrop
echo "Please enter interlacing options
0: No Deinterlacing
1: Deinterlacing"
read VideoInterlacing
echo "Please select scaling options
 0:   Scaled d_width/d_height
-1:   Original width/height
-2:   Calculate  w/h using the other dimension and the prescaled aspect ratio.
-3:   Calculate w/h using the other dimension and  the  original  aspect ratio."
read VideoScale
echo "Please enter prescaling options
qntsc:   352x240 (NTSC quarter screen)
qpal:    352x288 (PAL quarter screen)
ntsc:    720x480 (standard NTSC)
pal:     720x576 (standard PAL)
sntsc:   640x480 (square pixel NTSC)
spal:    768x576 (square pixel PAL)"
read VideoPrescaling

#Asks User how many passes
echo "How many passes?
1: faster encoding
2: better quality"
read Passes

# remove conflicting files
rm -f divx2pass.log frameno.avi

# rip audio track (bitrate: $AudioBitrate, gain: $AudioGain)
nice -n 3 mencoder -oac mp3lame -lameopts mode=2:cbr:br=$AudioBitrate:vol=$AudioGain \
 -ovc frameno -o frameno.avi  dvd://1

if [ "$Passes" = "1" ]
then

# video track (pass: 1, bitrate: $)
nice -n 3 mencoder -sws 2 -oac copy -ovc lavc \
 -lavcopts vcodec=mpeg4:vbitrate=$VideoBitrate:vhq \
 -ffourcc XVID -vf crop=$VideoCrop,scale=$VideoScale  $VideoInterlacing  $VideoPrescaling  dvd://1 -o "$MovieTitle.avi"

else

# video track (pass: 1, bitrate: $VideoBitrate)
nice -n 3 mencoder -sws 2 -oac copy -ovc lavc \
 -lavcopts vcodec=mpeg4:vbitrate=$VideoBitrate:vhq:vpass=1 \
 -ffourcc XVID -vf crop=$VideoCrop,scale=$VideoScale  $VideoInterlacing  $VideoPrescaling  dvd://1 -o "$MovieTitle.avi"

# video track (pass: 2, bitrate: $VideoBitrate)
nice -n 3 mencoder -sws 2 -oac copy -ovc lavc \
 -lavcopts vcodec=mpeg4:vbitrate=$VideoBitrate:vhq:vpass=2 \
 -ffourcc XVID -vf crop=$VideoCrop,scale=$VideoScale  $VideoInterlacing  $VideoPrescaling  dvd://1 -o "$MovieTitle.avi"

fi

echo "Process complete. Thank You. Please press Enter to exit"
read End

#done
```

---

