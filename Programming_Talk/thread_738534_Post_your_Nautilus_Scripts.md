---
title: "Post your Nautilus Scripts"
date: 2008-03-28
forum: Programming Talk
---

### Post by jobsonandrew on 2008-03-28
Hi all,
I recently downloaded a Nautilus script to set an image that you right-click on as the desktop background... only problem was it didnt work with all the images I have on my NAS drive (smb share) so I thought I'd make one of my own.. 
for those that are unsure, paste the code to a new file eg **SetAsWallpaper** and save in your home directory, then in terminal:
```
chmod +x SetAsWallpaper; mv SetAsWallpaper ~/.gnome2/nautilus-scripts
```
then you can right-click on an image and select **scripts -> SetAsWallpaper**

I couldn't find such a topic so I thought I would start one... Why not post the code of scripts you've written... they can be great learning tools for BASH programming.. (just dont post any stupid malicious commands)

heres the code: (please read the warning below!)
```
#!/bin/bash
#
#Set an image file as the desktop wallpaper.. works on smb shares as well
#as local dirs
#allowed extensions:
exts=( jpg JPG bmp BMP png PNG gif GIF )
#(add to this array if you know of any more)
#
#By Andrew Jobson (jobsonandrew) March 2008
#=======================================================================

#find the path of the file clicked:
source_file_path=$( echo $NAUTILUS_SCRIPT_SELECTED_URIS | sed -e 's/file:\/\///g')
#find the name of the file clicked:
source_file_name="${source_file_path##*/}"
#make sure it ends with one of the exts
source_ext=${source_file_name#*.}
supported_ext=0
for ext in ${exts[@]}
do
    if [ "$ext" = "$source_ext" ]; then
        supported_ext=1
        break
    fi
done
if [ "$supported_ext" = "0" ]; then
    zenity --error --text="Extension not recognised!"
    exit 1
fi
#generate the copy destination
#the background is stored in ~/.bg this folder is
#flushed each time the script is run, so that there
#is no build-up of image files
if [ -d "$HOME/.bg" ]; then
    cd "$HOME/.bg"
    if [ "$?" = "0" ]; then
        rm *
    else
        zenity --error --text="An Error Occured.. Aborting copy"
        exit 1 
    fi
else
    mkdir "$HOME/.bg"
fi
new_file="$HOME/.bg/$source_file_name"
#copy the file to the bg dir:
gnomevfs-copy $source_file_path $new_file
#set the newly copied file as the background:
gconftool-2 --set --type string  /desktop/gnome/background/picture_options "stretched"
gconftool-2 --set --type string  /desktop/gnome/background/picture_filename "$new_file"
exit 0
```

**Warning:**
This script creates a hidden directory in your home folder called **.bg**
Each time you set an image as a background, the entire contents of **.bg** is **deleted and replaced**
So make sure you don't put anything in there.. and make sure you don't currently have a folder called **.bg**
P.S. I know scripts like this already exist.. but i was writing it so that I can learn from it! hehe :)

---

### Post by nhandler on 2008-04-26
Just as a heads up (since you admitted that your script wasn't perfect), there is a package called "nautilus-wallpaper" that does the exact same thing. It isn't a nautilus script, but it still appears in the right click context menu.

Also, gnome-look has a small collection of user-submitted nautilus scripts:
[http://www.gnome-look.org/index.php?xcontentmode=188](http://www.gnome-look.org/index.php?xcontentmode=188)

---

