---
title: "HOWTO : 2 clicks resizing pictures with Nautilus"
date: 2005-05-16
forum: Outdated Tutorials &amp; Tips
---

### Post by freeflight on 2005-05-16
Just a small howto to let you resize a directory full of big pictures (typically from cameras) in a few click with zenity and nautilus. 

Put this script (you may also need to adapt to your needs) in your nautilus script directory ~/.gnome2/nautilus-scripts/ with the name of your choice (in this example Create_thumbs) :

```
#! /bin/sh

# Dialog box to choose thumb's size
SIZE=`zenity --list --title="Choose the thumbnail's size" --radiolist           --column="Check" --column="Size" "" "320x240" "" "640x480" "" "800x600" "" "1024x768"`

if [ $SIZE -eq ""]; then    
zenity --error --text="Size not defined by user.
Please choose a size to use. "
exit 1
fi


# How many files to make the progress bar
PROGRESS=0
NUMBER_OF_FILES=`find -iname "*.jpg" -maxdepth 1 | wc`
let "INCREMENT=100/$NUMBER_OF_FILES"

mkdir -p thumbnails

# Creating thumbnails. Specific work on picture should be add there as convert's option
(for i in *.jpg *.JPG; do
echo "$PROGRESS";
echo "# Resizing $i";
convert -resize $SIZE  -bordercolor black -border 10x10 -quality 50 $i thumbnails/$i
let "PROGRESS+=$INCREMENT"
done
) | zenity  --progress --title "$Creating thumbnails..." --percentage=0
```

1. Choose a directory and launch the script by right-clicking > scripts > Create_thumbs
2. Choose the size your wish to use :
[[IMG]http://img24.imagevenue.com/loc144/th_517_Capture_Choose_the_thumbnail_s_size.jpg[/IMG]](http://img24.imagevenue.com/img.php?loc=loc144&image=517_Capture_Choose_the_thumbnail_s_size.jpg)

3. See the script in action  \\:D/ :
 [img]http://img12.imagevenue.com/loc108/th_8f9_Capture_thumbnails.jpg[/img]

4. A new directory appeared :
[[IMG]http://img23.imagevenue.com/loc282/th_eee_Capture_Londres.jpg[/IMG]](http://img23.imagevenue.com/img.php?loc=loc282&image=eee_Capture_Londres.jpg)

As i said, this script should be adapt to your needs. Any improvments are welcome!

Seb

---

### Post by Sniffer on 2005-05-16
Good very good. :) 

thks for all your work.

---

### Post by ow50 on 2005-05-16
Thanks. I used to have a much simpler (and worse) script for this.

I used an entry dialog for size input:
```
SIZE=`zenity --entry --title "Create thumbnails" --text "Biggest thumbnail dimension (pixels)"`
```

Suggestions:
- Add more image filetypes or just try to resize all files. As far as I know, convert doesn't crash trying to resize non-image files, they will just be skipped.
- Close the progress window on completion with "--auto-close"

---

### Post by risager on 2005-05-16
This is great. For you script-writing people I have a suggestion for something I needed a few times. I often want to email a picture to someone, but want to rescale it first. This script is most helpful in doing so. But it would be even more cool (IMO) to have, in addition, a script that does exactly what this script does, except that it should attach the files to an email instead of writing it to a new folder.  Does anyone know how to do that?

---

### Post by 23meg on 2005-05-16
this script could be combined with the email script found on [this page](http://www.ubuntulinux.org/wiki/NautilusScriptsHowto) to do what you want. there are other useful scripts on this page as well.

---

### Post by Sniffer on 2005-05-16
Problem: When enter one of my directory's with jpeg files, i press the create thumbs script, i choose the size but then....

The progress bar appears as full with the last jpeg bellow, i press ok, i enter the thumbs folder automatic generated....BUT NO Jpeg files inside!!!!! Odd :???:

---

### Post by freeflight on 2005-05-16
[QUOTE=Sniffer]Problem: When enter one of my directory's with jpeg files, i press the create thumbs script, i choose the size but then....

The progress bar appears as full with the last jpeg bellow, i press ok, i enter the thumbs folder automatic generated....BUT NO Jpeg files inside!!!!! Odd :???:[/QUOTE]

Well, that's right. As it, the script only work with *.jpg and *.JPG. If your files are named *.jpeg, it wont work, sorry.

I'll modify the script and follow above advises to improve it...
 :wink:

---

### Post by infinito on 2005-05-18
I've made some little changes on original script, just to avoid some bash scripting errors. Here's the code:

```
#! /bin/sh

# Dialog box to choose thumb's size
SIZE=`zenity --list --title="Choose the thumbnail's size" --radiolist --column="Check" --column="Size" "" "320x240" "" "640x480" "" "800x600" "" "1024x768"`

if [ "${SIZE}" == "" ]; then    
zenity --error --text="Size not defined by user.
Please choose a size to use. "
exit 1
fi

# How many files to make the progress bar
PROGRESS=0
NUMBER_OF_FILES=`find -iname "*.jpg" -maxdepth 1 | wc -l`
let "INCREMENT=100/$NUMBER_OF_FILES"

mkdir -p thumbnails

# Creating thumbnails. Specific work on picture should be add there as convert's option
(for i in *.jpg *.JPG; do
echo "$PROGRESS";
echo "# Resizing $i";
convert -resize "${SIZE}"  -bordercolor black -border 10x10 -quality 50 "${i}" thumbnails/"${i}"
let "PROGRESS+=$INCREMENT"
done
) | zenity  --progress --title "$Creating thumbnails..." --percentage=0

```

Thanks for the script and idea!!

---

### Post by GeirG on 2005-05-18
freeflight: Nice script, thanks for shareing.

Infinito: Nice details, although it seems you missed a " after thumbnails/"${i} , and the entire last line.

Regards,

---

### Post by Sniffer on 2005-05-18
[QUOTE=freeflight]Well, that's right. As it, the script only work with *.jpg and *.JPG. If your files are named *.jpeg, it wont work, sorry.

I'll modify the script and follow above advises to improve it...
 :wink:[/QUOTE]

Nope, as you can see on the screenshot 1 my files are named as jpg or JPG, a launch the script, choose the size, press ok, the progress bar automatic go to the end...i press ok and nothing inside thumbnail folder!!!!!!!!!

Just see the screenshots.

---

### Post by hesee on 2005-05-19
I have the same problem than Sniffer... :(

---

### Post by ola on 2005-05-19
Do you have the convert (imagemagick) program installed?

It might be a stupid question.. But worth asking..

---

### Post by hesee on 2005-05-19
Well, stupid questions for stupid people :) No, i don't have one, i guess i should have?

Edit:installed imegemagick, now i can resize by going into the directory(not one level up) and choosing one of the pictures, script then resizes all the pictures in the directory, is it supposed to work like that?

---

### Post by Sniffer on 2005-05-19
[QUOTE=hesee]Well, stupid questions for stupid people :) No, i don't have one, i guess i should have?

Edit:installed imegemagick, now i can resize by going into the directory(not one level up) and choosing one of the pictures, script then resizes all the pictures in the directory, is it supposed to work like that?[/QUOTE]

SH*****TTTT sometimes i can solve difficult problems...and just can't see the easy ones... ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,) 

Yep..imagemagick...Missing..Dummy myself sometimes.

Thks.

Update: Yep it convert any photo (file supported) that is on that directory.

---

### Post by Haegin on 2005-10-31
Hi,

This script is great but how do I alter it to work with all image files?

Thanks

---

### Post by joselin on 2005-11-16
Awesome script. But i what i want is to resize nautilus selected images on a folder, is there a way for doing it?

Regards.

---

### Post by belda on 2007-04-08
if u care, i have modified version of the script, this one **takes** not all in the directory, but **just** the ones, that are **selected,** it takes **all image formats** image-magick handles (im not testing it, cause if it doesnt support the format, it does nothing to the file) and u can **specify custom size**. it uses image-magick size format, so in here it resizes just the ones, that are in any direction bigger than the desired size (the > sign)
```
#!/bin/bash

# Dialog box to choose thumb's size
SIZE=`zenity --list --title="Choose the thumbnail's size" --radiolist --column="Check" --column="Size" "" "custom" "" ">140" "" ">x90" "" ">640x480" "" ">800x600" "" ">1280x1024"`
# Dialog box to choose custom size
if [ "${SIZE}" == "custom" ]; then
    SIZE=`zenity --entry --text "Enter size parameter"`
fi

if [ "${SIZE}" == "" ]; then    
    zenity --error --text="Size not defined by user.
                           Please choose a size to use. "
    exit 1
fi
# $# is the argument count
PROGRESS=0
let "INCREMENT=100/$#"

#Do the stuff with all the selected files ($@
(for arg in "$@"; do 
    echo "$PROGRESS";
    echo "# Resizing $arg";
    mogrify -resize "$SIZE" $arg; 
    let "PROGRESS+=$INCREMENT";
done ) | zenity  --progress --auto-close --title "$Resizing" --percentage=0
```

and also here are 2 also usefull scripts, for rotating pictures from nautilus left or right

rotate_left
```
#!/bin/bash
PROGRESS=0
let "INCREMENT=100/$#"

(for arg in "$@"; do 
    echo "$PROGRESS";
    echo "# Rotating $arg";
    mogrify -rotate 270 $arg; 
    let "PROGRESS+=$INCREMENT";
done ) | zenity  --progress --auto-close --title "$Rotating" --percentage=0

```

and rotate_right
```
#!/bin/bash
PROGRESS=0
let "INCREMENT=100/$#"

(for arg in "$@"; do 
    echo "$PROGRESS";
    echo "# Rotating $arg";
    mogrify -rotate 90 $arg; 
    let "PROGRESS+=$INCREMENT";
done ) | zenity  --progress --auto-close --title "$Rotating" --percentage=0

```

---

### Post by H.E. Pennypacker on 2007-05-26
Belda, I believe your script works with PNGs, but not with JPEGs.

The OP's script did nothing.

---

### Post by enine on 2007-09-07
Found this in a search, maybe you guys can help me out.  I want to batch resize all images in multiple folders and copy the folder name/structure to another location with the copies.

What I'm trying to do is I have a Pictures folder and under that are subfolders

/home/enine/Pictures/2007 04 19 Trip to Gatlinburg TN/
/home/enine/Pictures/2007 03 31 Shirley's 30th Birthday Party/
etc

each folder has several pictures in it

I want a script that can make:
/mnt/minisd/Pictures/2007 04 19 Trip to Gatlinburg TN/
/mnt/minisd/Pictures/2007 03 31 Shirley's 30th Birthday Party/

and tell imagemagick to put 320x240 copies in the destination folder structure.

I have a smartphone which can take minisd cards so I bought a big minisd card and want to copy pics in their folders to the minisd so I can display them on the phone.  To save space and make them display faster I downsizing them to the screen size of the phone.

---

