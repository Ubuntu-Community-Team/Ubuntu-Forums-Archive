---
title: "Script programming (Zenity)"
date: 2007-07-25
forum: Programming Talk
---

### Post by huzzak on 2007-07-25
So, I don't know hardly anything at all about script programming.  I just endeavored to try and puzzle it out today, and so I am requesting suggestions on this bit of code that somebody else wrote and I have (somewhat unsuccessfully modified).

The problem is that if you choose cancel in the image quality selection section, the script will create a new directory anyway even though it doesn't resize any of the images.  I'll try to highlight where it is:

```
#!/bin/bash
# Original (NIS) author : Mathieu Vilaplana <mathieu@creationgif.com> 
# Modified by: Radagast <rhosgobel2@gmail.com>
# Date : 02/19/2007
#depends: imagemagick, zenity, rename
# thanks to coffe
#version 0.4
#	- check mime type
#since v 0.4, solve bug with filename spaces
#version 0.6
#     - correct bug in filename with spaces
#     - create a subdirectory to create images
#version 0.7
#     - changed name from NIS to Resize_images for ease of menu selection
#     - changed list to contain solely the max dimension
#     - added more size options
#     - made directory name nicer ("resized_to_xxx")
#     - appended image size to file name for jpgs and gifs ("file.jpg" becomes "file_xxx.jpg")
#     - created user-friendly dialog text
#version 0.75
#     - specified bash for Edgy compatibility, based on 0.8 of NIS (http://www.creationgif.com/debian/nis/); 
#     - added PNG to list of file types that is renamed.

#test if a file has been selected
if [ $# -eq 0 ]; then
	zenity --error --title="error" --text="You must select at least 1 file to process"
	exit 1
fi

#=========================
#       SELECT SIZE DIALOG
# Add or remove (or resort) items from (in) the following list 
#   to customize the sizes available and the order in which they appear.
#   It would be nice to make this list easier to edit (make it a variable?  A file in user's home directory?)
title="Resize images"
dialogtext="Select the maximum dimension length (in pixels) \nto which you want the image(s) resized. \n\n*Script designed to work on jpgs and gifs.*"
maximgsize=`zenity --title "$title" --text="$dialogtext" --list --separator=" " --column="size (px)" "100" "150" "160" "200" "300" "320" "400" "500" "600" "640" "800" "1024" `

#if $? != 0, user click on cancel button, so exit
if [ "$?" != 0 ] ; then
	exit
fi

#user must select a target size
maximgsize=`echo $maximgsize | sed 's/ max//g'`
if [ ! "$maximgsize" ]; then
	zenity --error --title="error" --text="select a target size"
	exit
fi

#Assign max dimensions to variables for later.
imgsize="${maximgsize}x${maximgsize}" # used for the resize command
niceimgsize="$maximgsize" # used to append to file name
imgsizedir="resized_to_$maximgsize" # name of the directory that will be created

#       END SELECT SIZE DIALOG
#=========================

[B]#=========================
# Dialog for selecting the quality of the image.

dialogtext="Select the image quality of the resized images."
qual=$(zenity --scale --title "$title" --text="$dialogtext" --min-value="10" --max-value="100" --value="80" --step 1); echo qual

#if $? != 0, user click on cancel button, so exit
if [ "$?" != 0 ] ; then
	exit
fi

#  End quality select dialog
#=========================
[/B]
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

#create directory if not exist and at least one image to process
if [ ! -d $imgsizedir  ] && [ "$nb_images" -gt "0" ];then
		mkdir $imgsizedir
fi

#iterate through selected images, resize, and rename
n=$nb_images
let "n=n-1"
(for i in `seq 0 $n`;do
	picture=${selection[$i]}
	let "compteur += 1"
	echo "# Processing image $compteur / $nb_images $picture ..."
	convert -quality $qual -resize $imgsize "$picture" $imgsizedir/"$picture"
        # rename the created file - there's got to be an easier way to handle all cases.
        rename s/.JPG$/_$niceimgsize.JPG/ $imgsizedir/"$picture"
        rename s/.jpg$/_$niceimgsize.jpg/ $imgsizedir/"$picture"
        rename s/.JPEG$/_$niceimgsize.JPEG/ $imgsizedir/"$picture"
        rename s/.jpeg$/_$niceimgsize.jpeg/ $imgsizedir/"$picture"
        rename s/.GIF$/_$niceimgsize.GIF/ $imgsizedir/"$picture"
        rename s/.gif$/_$niceimgsize.gif/ $imgsizedir/"$picture"
        rename s/.PNG$/_$niceimgsize.PNG/ $imgsizedir/"$picture"
        rename s/.png$/_$niceimgsize.png/ $imgsizedir/"$picture"
	let "progress = compteur*100/nb_images"
	echo $progress
done
) |
        zenity --progress --auto-close --title="Scaling images"  --text="Processing images ..."  
--percentage=0


# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# A copy of the GNU General Public License is available at http://www.gnu.org/copyleft/gpl.html
# or can be obtained by writing Free Software Foundation, Inc.,
# 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
```

The selection in bold is the part that I added.  Another question that I have is whether or not the two dialogs could be combined in zenity.

---

### Post by cwaldbieser on 2007-07-25
```

qual=$(zenity --scale --title "$title" --text="$dialogtext" --min-value="10" --max-value="100" --value="80" --step 1)**; echo qual**

#if $? != 0, user click on cancel button, so exit
if [ "$?" != 0 ] ; then
	exit
fi

```
The part in bold is your problem.  The "echo qual" command is going to have an exit value of 0.  That sets $? to 0 and obliterates the previous exit value.  The "if" statement that follows will always skip over the nested "exit" statement.

Also, "echo qual" will always print the literal text "qual".  If it was meant as a debugging statement, it probably ought to have been something like "echo $qual".

---

### Post by huzzak on 2007-07-25
Thanks.  The website where I read about the different dialogs seemed to imply that "echo qual" was part of the zenity idea.  It doesn't make sense now that I think about it though.  Any word on whether or not one can combine two or more zenity dialogs?

My suspicion and research indicate no, but it doesn't hurt to ask.

---

### Post by cwaldbieser on 2007-07-25
> **huzzak said:**
> Thanks.  The website where I read about the different dialogs seemed to imply that "echo qual" was part of the zenity idea.  It doesn't make sense now that I think about it though.  Any word on whether or not one can combine two or more zenity dialogs?

My suspicion and research indicate no, but it doesn't hurt to ask.

If I try to give multiple dialog type options (e.g. ---calendar and --entry), zenity returns an error.  I think zenity is just supposed to make creating stock dialogs from a shell script easier.

If you want to get fancy, you could try creating your own custom dialogs that work in a similar fashion.  tcl/tk, python and Tkinter, etc. make this fairly simple.

---

### Post by huzzak on 2007-07-25
I'll look into those.  Thanks for the lead.

---

