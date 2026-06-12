---
title: "Nice little script to batch convert images"
date: 2007-04-06
forum: Outdated Tutorials &amp; Tips
---

### Post by darrenm on 2007-04-06
Didn't know the best place to put this but thought I may as well post it on here because if you need to convert lots of images at once by resizing and/or compressing them this will trawl through every directory starting at the current one and convert any JPG to PNG (easily changeable) using the default of 800x600 75% quality. You can pass 2 command line parameters to it, --resize= and --quality= where you can change these settings.

It will put the PNG files in the same location as the original files. Its fine with spaces too as it sets IFS.

If anyone wants it to behave differently but doesn't know how to change it let me know.

```
#!/bin/bash

#
## Simple little script by Darren (darren@vcoc.co.uk) 
## Should be self explanatory what it does :)
#

# Parse the command line params if they are there.
param1command=`echo $1 | awk -F= '{print $1}'`
param2command=`echo $2 | awk -F= '{print $1}'`
param1value=`echo $1 | awk -F= '{print $2}'`
param2value=`echo $2 | awk -F= '{print $2}'`


if [ "$1" = "" ]
then 
   params="defaults" # Use sensible defaults of 800x600 75% quality if there are no params passed

# Test for only 1 command line param. 
elif [ "$param1command" = "--resize" ]
then
   if [ "$2" = "" ] # If there is no 2nd param we only want to resize.
   then 
      params="resize"
      size=`echo $param1value`
   
   elif [ "$param2command" = "--quality" ] # But if we do have a 2nd param passed it has to be quality.
   then 
      params="resizequality" # So the order is resize then quality.
      size=`echo $param1value` # Assign size the first param
      quality=`echo $param2value` # and quality the 2nd param
   fi
# Otherwise the user must be passing quality as the 1st param
elif [ "$param1command" = "--quality" ]
then
   if [ "$2" = "" ] # If there is no 2nd param we only want to change the quality
   then 
      params="quality"
      quality=`echo $param1value` # assign quality the value passed from the command line

   elif [ "$param2command" = "--resize" ] # Otherwise the 2nd param has to be resize
   then 
      params="qualityresize" # and then the order is quality then resize
      size=`echo $param2value`
      quality=`echo $param1value`
   fi
else
	echo -e "\nPhotocrawler. A simple BASH script to look through dirs starting at the current"
	echo -e "one. When it finds a JPG it will convert it to PNG with the defaults of"
	echo -e "a 800x600 75% PNG file. You can override these settings by passing"
	echo -e "command line params e.g. :\n"
	echo -e "photocrawler --quality=50% --resize=640x480\n"
	echo -e "using whichever quality and resize you need. (Order is not important)\n"
	exit 1
fi 

# Set IFS to only see newlines as field separators.
IFS=$'\n'

for source_filename in $(find -type f -iname '*jpg') # Use find to find anything ending in JPG or jpg
do
   dest_filename=`echo ${source_filename%.*}` # Strip the .jpg or .JPG off the end

   if [ ! -e "${dest_filename}.png" ] # If the file doesn't already exist...
   then
      echo "converting ${source_filename} to ${dest_filename}.png"
      if [ "$params" == "defaults" ]
      then
         convert "${source_filename}" -resize 800x600 -quality 75% "${dest_filename}.png"
      elif [ "$params" == "resize" ]
      then
         convert "${source_filename}" -resize $size "${dest_filename}.png"
      elif [ "$params" == "quality" ]
      then
         convert "${source_filename}" -quality $quality "${dest_filename}.png"
      elif [ "$params" == "resizequality" ] || [ "$params" == "qualityresize" ]
      then
         convert "${source_filename}" -resize $size -quality $quality "${dest_filename}.png"
      fi
   fi
done
```

---

### Post by darrenm on 2007-04-07
Some extra info:

This will accept standard Imagemagick parameters so if you want to maintain the aspect ratio then just use 
```
photocrawler.sh --resize=50%
``` which will resize down 50% maintaining the ratio. If you pass any command line parameters to it in this way it will not change the other one. e.g.
```
photocrawler.sh --quality=50%
``` will just compress the images but not resize them
```
photocrawler.sh --resize=640x480
``` will just resize the images but not compress them.
```
photocrawler.sh
``` will resize the images to 800x600 and compress them 75%
This script won't change any of your original files, it will just create a new PNG image in the dir as the original leaving it up to you to remove the old files if you want.

To install, just do ```
sudo gedit /bin/photocrawler.sh
``` copy and paste the above script into the gedit window, save and exit gedit then ```
sudo chmod a+x /bin/photocrawler.sh
```

---

### Post by aysiu on 2007-04-07
> **darrenm said:**
> Didn't know the best place to put this but thought I may as well post it on here I've put it in Tutorials & Tips.

---

### Post by kerry_s on 2007-04-07
Okay i'm guessing you need Imagemagick installed?

---

### Post by darrenm on 2007-04-07
> **kerry_s said:**
> Okay i'm guessing you need Imagemagick installed?

oops yes sorry.

---

### Post by kerry_s on 2007-04-07
Yeah, i got it, but i went a different way. I just needed something to resize a image so i just use mogrify. see pic->

---

### Post by topgun_tapan on 2009-09-09
I need to batch convert png images to grayscale without affecting their quality. Any help ?

---

### Post by SaintDanBert on 2010-01-07
I have a pile of images with all sorts of characteristics and formats.
I want a second pile of images that have characteristics extremely similar
to:
[list]
[*]one specific file
[*]this specific group of files
[/list]

One application of my requirementsis to create "icon" (web page buttons &c) images from "clip art" or simple photo or other jpeg images.

Thanks,
~~~ 0;-Dan

---

