---
title: "Batch resize nautilus script"
date: 2005-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by sabmann on 2005-11-28
Hi,

To batch resize all images in a folder, I do the following:

Make a new file (not as root):

```
gedit ~/.gnome2/nautilus-scripts/batch640x480
```

Then add the following:

```
#!/bin/sh
# author: Bas Wenneker
# email: sabmann [ta] gmail [tod] com
# Use this script to batch resize all images in a folder.
# First open the folder and then use the script.

for file in `ls -l`
do
name=`echo $file | cut -f1 -d.`
  convert -geometry 640x480 -quality 65 $file ${name}_640x480.jpg
done
```

Then make it executable:

```
chmod +x ~/.gnome2/nautilus-scripts/batch640x480

```

Then you're done. Go to the folder you'd like to resize. Then rightclick and find the 'batch640x480' script. 
I use this script for resizing large amounts of photo's for a website. That's why the '-quality 65' is in the script. You can change the script to your needs. Click [here]("http://www.imagemagick.org/script/convert.php") for more convert commands.

Hope you'll find this usefull...

---

### Post by linkunderscore on 2005-11-30
Does this resize other images besides .jpgs? 

For instance .svg?

---

### Post by oxEz on 2005-11-30
[QUOTE=linkunderscore]Does this resize other images besides .jpgs? 

For instance .svg?[/QUOTE]

You cannot resize a .SVG directly.. svg files have no defined size. They're just a XML file at all !

---

### Post by oofnik on 2005-12-02
Thanks! I was looking for this. Since all the files I want to convert end in JPG, I changed 'ls -l' to 'ls | grep JPG' and it doesn't spit out a bunch of 'cannot find' things from ls. I've noticed though that the efficiency of the jpeg compressor in convert is not as good as the one gthumb uses. At quality setting 80, gthumb produces a file ~30 KB less. Oh well, it saves me a boatload of time :)

---

### Post by sabmann on 2005-12-02
>  I changed 'ls -l' to 'ls | grep JPG'

yes I tried your 'ls | grep JPG' but sometimes the extensions are different like .jpeg or   the extension is in uppercase... so that's why I use the ls -l... But you are right about the cannot find * messages... I'll add it to my first post, thanks

---

### Post by lhtown on 2006-04-14
I got this script to work on Dapper. I made a couple of changes to the script so that it would save the new pictures into a separate directory that I called "thumbnails" instead of mingling them with my other pictures and also, I adjusted the picture size and quality to suit my preference. Also, I added the -strip argument so that it would strip out my exif information. My camera adds a lot of exif information and in my case, that saved me about 25-30kb per picture, which is a major difference for the web.

```

#!/bin/sh
# author: Bas Wenneker
# email: sabmann [ta] gmail [tod] com
# Use this script to batch resize all images in a folder.
# First open the folder and then use the script.
mkdir ./thumbnails
for file in `ls -l`
do
name=`echo $file | cut -f1 -d.`
  convert -strip -geometry 800x600 -quality 80 $file ./thumbnails/${name}_800x600.jpg
done

```

---

### Post by Felix21685 on 2006-10-08
> **lhtown said:**
> I got this script to work on Dapper. I made a couple of changes to the script so that it would save the new pictures into a separate directory that I called "thumbnails" instead of mingling them with my other pictures and also, I adjusted the picture size and quality to suit my preference. Also, I added the -strip argument so that it would strip out my exif information. My camera adds a lot of exif information and in my case, that saved me about 25-30kb per picture, which is a major difference for the web.

```

#!/bin/sh
# author: Bas Wenneker
# email: sabmann [ta] gmail [tod] com
# Use this script to batch resize all images in a folder.
# First open the folder and then use the script.
mkdir ./thumbnails
for file in `ls -l`
do
name=`echo $file | cut -f1 -d.`
  convert -strip -geometry 800x600 -quality 80 $file ./thumbnails/${name}_800x600.jpg
done

```

hey thanks lhtown for the updated version with quality difference and stating that you got it to work in dapper.
haha note if you try and resize a movie file it resizes each frame. :D

---

### Post by MockY on 2006-10-25
What am I missing? I have tried this script and others as well, but in all cases, only folders are made and the picture/s is not resized at all. Nothing happens. My guess is that I'm missing something but I don't know what it is.

---

### Post by lhtown on 2006-10-25
> **MockY said:**
> What am I missing? I have tried this script and others as well, but in all cases, only folders are made and the picture/s is not resized at all. Nothing happens. My guess is that I'm missing something but I don't know what it is.

Make sure you have imagemagick installed. The convert command that you see in the script is part of the imagemagick package.

You can install imagemagick easily using Synaptic or from the command line if you prefer using something like the following:

apt-get install imagemagick

---

### Post by MockY on 2006-10-25
I made sure I had it installed before I posted, which is why I think this is weird. Any other ideas?

EDIT: Just to be sure, I installed it using apt-get and it was successful. The reason why I didn't do that earlier was that Synaptic listed it as intalled.

---

### Post by lhtown on 2006-10-26
Are you using Edgy? I have just upgraded to Edgy and I am having a similar problem to what you described.

If that is the case, I hope to have some sort of answer for you in the next day or so, but no promises. :-)

---

### Post by imon9 on 2007-01-15
yah, there seems to be some problem with edgy processing the script

well, i did some modification to the NIS script and now it works... HOWEVER with a catch!!!

PLEASE USE IN FULL CAUTION AND KNOWING THAT THIS SCRIPT DOES NOT BACKUP FOR YOU
IT SIMPLY RESIZE THE IMAGE ITSELF

SO, COPY/DUPLICATE THE IMAGE YOU WANTED TO RESIZE TO ANOTHER FOLDER BEFORE USING

use it as u please... i will paste it here

> 
#!/bin/sh
# Author : Mathieu Vilaplana <mathieu@creationgif.com>
# Date : 09/03/2005
#depends: imagemagick, zenity
# thanks to coffe
#version 0.4
#	- check mime type
#since v 0.4, solve bug with filename spaces
#version 0.6
#	- correct bug in filename with spaces
#     - create a subdirectory to create images

#test if a file has been selected
if [ $# -eq 0 ]; then
	zenity --error --title="error" --text="You must select at least 1 file to process"
	exit 1
fi


#Select only images
nb_images=0;
selection="";


while [ $# -gt 0 ]; do
	isimage=`file -bi "$1" | grep image | wc -l` 
	if [ $isimage -eq 1 ]; then
		selection[$nb_images]=$1
		let "nb_images++"
	fi
	shift
done

#if user choose files but no images, print an error and exit
if [ $nb_images -eq 0 ]; then
	zenity --error --title="error" --text="You must select at least 1 image to process"
	exit 1
fi


#CHECK IMAGE MAGICK ==================
convert_path=`which convert`
if [ ! "$convert_path" ] || [ ! -x "$convert_path" ] ;then
	zenity --error --title="error" --text="Cannot find \"convert\" executable.\nPlease install image magick package."
fi
#================================

#=========================
#       SELECT SIZE DIALOG
title="Choose which sizes to scale to"
imgsize=`zenity --title "$title"  --list --separator=" " --column="size" "160x120" "320x240" "640x480" "800x600" "1024x768" `

#if $? != 0, user click on cancel button, so exit
if [ "$?" != 0 ] ; then
	exit
fi

#user must select a target size
imgsize=`echo $imgsize | sed 's/ max//g'`
if [ ! "$imgsize" ]; then
	zenity --error --title="error" --text="select a target size"
	exit
fi

#transform 640x480 en 640x640 for convert to respect proportions
himgsize=$imgsize
val1=`echo "$imgsize" | awk -F'x' '{ print $1  }'`
imgsize="${val1}x${val1}"

#       END SELECT SIZE DIALOG
#=========================

#Process
#=============================================


picture=${selection[$i]}
convert -scale $imgsize "$picture" "$picture"
done



the bug seems to not be able to process output picture string other than plain $picture
i tried modifying the script furthur to make it able to backup, but i am new to this, so if i have one solution, i will share it

tell me if it works for u

---

### Post by mmuzzy on 2007-02-19
Thanks for this great tip, this is exactly what I've been looking for. Alot easier than doing it one at a time in GIMP!

-Mike

---

### Post by svas on 2007-03-05
For me it says "You must select at least 1 image to process" when I right click an image and choose Scripts->batch800x600 (that what I named it). The file has the name P3052725.JPG and I can open it in any other program. I have tried to rename the file to not capital letters in the file extention. I have also tried to choose a whole dir to change all of the picturefiles at the same time. What am I doing wrong?

---

### Post by svas on 2007-03-05
Sorry: Double posting.

---

### Post by Andrej_BB on 2007-03-28
I get the same error as svas - "You must select at least 1 image to process"

What should i do ?

---

### Post by svas on 2007-03-28
> **Andrej_BB said:**
> I get the same error as svas - "You must select at least 1 image to process"

What should i do ?


I have resolved this by now. I came over a solution here:
[http://rhosgobel.blogspot.com/2006/07/bulk-resizing-and-renaming-images-in.html](http://rhosgobel.blogspot.com/2006/07/bulk-resizing-and-renaming-images-in.html)

Then, right-clicking has become a totally new experience. :)

I have removed the old script and replaced by this:
[http://home.comcast.net/%7Erhosgobel/scripts/Resize_images](http://home.comcast.net/%7Erhosgobel/scripts/Resize_images)

I think the problem was the Ubuntu-version...

---

### Post by saracen on 2007-04-29
> **svas said:**
> I have resolved this by now. I came over a solution here:
[http://rhosgobel.blogspot.com/2006/07/bulk-resizing-and-renaming-images-in.html](http://rhosgobel.blogspot.com/2006/07/bulk-resizing-and-renaming-images-in.html)

Then, right-clicking has become a totally new experience. :)

I have removed the old script and replaced by this:
[http://home.comcast.net/%7Erhosgobel/scripts/Resize_images](http://home.comcast.net/%7Erhosgobel/scripts/Resize_images)

I think the problem was the Ubuntu-version...

Does anyone have a copy of this script?  The URL isn't valid anymore.

I also tried using gThumb to batch resize but when I have more than one image opened the resize option is greyed out.  All of the image manipulation options are.  It's only when I have one image open that I can resize...

---

### Post by zedlander on 2007-05-06
Hi guys,
The best solution I have found for quickly resizing images is NIS.  It lets you choose the size you want.
Get it here: [http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/NIS]("http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/NIS")
If you're using Edgy or Fiesty, change the first line from #!/bin/sh to #!/bin/bash.
Then, put the script in the your /home/username/.gnome2/nautilus-scripts folder.

---

### Post by 9387 on 2007-10-19
I have address this problem and created a step by step guide.

[http://xenon-money.blogspot.com/2007/10/mass-picture-resizing-in-ubuntu-feisty.html](http://xenon-money.blogspot.com/2007/10/mass-picture-resizing-in-ubuntu-feisty.html)

---

### Post by Bokonon on 2007-10-22
I usually just use find.  BE CAREFUL, find is powerful and you can wipeout data easily.

That said, install imagemagick (to get mogrify)
[URL="http://www.imagemagick.org/script/mogrify.php"]
mogrify info[/URL]
[URL="http://unixhelp.ed.ac.uk/CGI/man-cgi?find"]
man find[/URL]

```

sudo aptitude install imagemagick
```

```
find . -name '*.jpg' -exec mogrify {} -resize 800x600 \;
```

Again, BE CAREFUL and read the man pages for find and mogrify.  I lost a lot of photos when I accidentally renamed all the files to the same name.  I STRONGLY suggest backing up your data and making a few test runs to make sure any command/script you make does what you want it to before using it.

For example, the above command might not do what you want.  Portrait layout photos *won't* be the size you probably want (600x800) and will be ###x600 (if ### is < 800).

---

### Post by stani on 2007-11-02
I just developed Phatch (photo & batch) to make this all easier. Also you can drop shadows, add rounded corners or watermarks with it. There is a deb ubuntu installer (look for "free download" below):
[http://pythonide.stani.be](http://pythonide.stani.be)

See also:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

### Post by vibe666 on 2008-03-01
f-spot does the tric for me, there's a batch resize tool in it.  you just select all your images and then export to a folder and it does the rest.

---

### Post by lover_of_sc on 2008-03-10
I have address this problem and created a step by step guide.

[http://xenon-money.blogspot.com/2007...tu-feisty.html](http://xenon-money.blogspot.com/2007...tu-feisty.html)
__________________

I have gone trough the step-by-step guide, and i problebly have the most stuid question in this forum so far. How do I execute the script when I have selected the pictures? I don't get a 'run script' when I right click?

---

