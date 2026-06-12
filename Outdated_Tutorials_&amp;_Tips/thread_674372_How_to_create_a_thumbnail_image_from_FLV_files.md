---
title: "How to create a thumbnail image from FLV files"
date: 2008-01-21
forum: Outdated Tutorials &amp; Tips
---

### Post by mohtasham1983 on 2008-01-21
I have been using an open source web based flash player for a while on my website without using any thumbnails on it, because I was expecting the player makes it for me. Finally, I found a way to create such thumbnails images using ffmpeg. 

After playing around with the command I created a small shell script that creates such image by specifying the file name and the time you want to make the image from. 

The first thing you need to create the image is ffmpeg with codecs. I have been running my ubuntu for long time so I don't remember exactly what codecs you have to install for that. A quick search on google should give you the corresponding result.

What I did was to create a very simple bash script which receives two arguments. First argument is the flv file name and the second one is the time which you want to extract the image from in the video.

Place the following code on your text file and name it as generate_thumbnail.sh .

```

#!/bin/bash
# this script creates a a thumbnail from a flv file

if [ $#  = '2' ]; then
	destfile=`basename $1`
	destfile=`echo ${destfile%%.*}`
	ffmpeg -i $1 -an -ss $2 -an -r 1 -vframes 1 -y -f mjpeg $destfile.jpg
else
	echo you have to provied 2 parameters Video Name and The Image Time 00.00.00 format
fi

```

I would like to mention that this script doesn't do any error handling, because I wrote this initially for my use and then decided to post it here, in case some other people may need it. 

The generated image will have exact same name as the original flv file. The only difference is that the flv extension is replaced by jpg. 

You can call this bash script as following:
```

 sh /yourpath/generate_thumbnail.sh /yourpath/video.flv 00:00:08

```

The following command will create a file called video.jpg from the 8 seconds of the video.flv in the current directory.

In my case I had a bunch of flv files, so making such images by executing the command for each flv video was a waste of time. I used the following command to create the image from all flv files:

```

for file in video/*.flv; do sh /yourpath/generate_thumbnail.sh $file 00:00:08; done

```

This command create an image from the 8th second of every flv video. Just make sure that all your videos last more than 8 seconds, otherwise I believe it will create a black jpg picture, although I haven't checked it yet.

Please feel free to add new features to this script. I'm not that good in bash scripting and I know that there are still many features that can be added to my script.

---

### Post by PhrankDaChickenGeek on 2008-01-26
To make things a little eaiser for single flash videos, you can create a file called "Generate Thumbnail"
in the folder ```
/home/USER/.gnome2/nautilus-scripts
``` and paste the following text into it

```

#!/bin/sh

TIME=8
FILE=$(echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | sed q)
ffmpeg -i "$FILE" -an -y -f mjpeg -ss $TIME -vframes 1 "$FILE".jpg

```
Make the file executable by right clicking it, selecting "Properties", "Permissions" tab, then check the box next to "Execute"

Then all you have to do is right-click the FLV file in Gnome, choose "Scripts" and then "Generate Thumbnail", and it will place the thumbnail in the same directory as the video

---

