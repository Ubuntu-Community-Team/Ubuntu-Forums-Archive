---
title: "Nautilus Script to Upload Image to Picasa using GoogleCL"
date: 2010-06-20
forum: Programming Talk
---

### Post by ncwilde43 on 2010-06-20
Since Google released the [GoogleCL]("http://google-opensource.blogspot.com/2010/06/introducing-google-command-line-tool.html") package, I decided to create a Nautilus script that quickly uploads an image to my Drop Box album in Picasaweb.

**Note:** The zenity progress bar does not work and is used only to show that the script is running.

[SIZE=5]**Instructions for installation:**[/SIZE]
[LIST=1]
[*]Save the code to your ~/.gnome2/nautilus-scripts directory
[*]Make the script executable.```
chmod +x ~/.gnome2/nautilus-scripts/Upload-Image
```
[*]Restart Nautilus```
nautilus -q
```
[/LIST]
For those of you that haven't linked your GoogleCL library and Google account, open up the Terminal and enter the following command:
```
google picasa list title --title "Drop Box"
```Follow the link given to authenticate GoogleCL.

Save the following code to ~/.gnome2/nautilus-scripts/Image-Upload
```
#!/bin/bash

FILENAME=$*
FULLPATH=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

## ---Check to see if GoogleCL is installed
if [ $(which google | wc -l) -eq 0 ] ; then
    zenity --error --title "Picasa Uploader" --text "GoogleCL is not installed!"
    exit 1
fi

## ---Upload image - Zenity progress bar does not work properly.
google picasa post --title "Drop Box" $FULLPATH | zenity --progress --pulsate --auto-close --auto-kill --percentage=50 --title "Upload" --text "Uploading $FILENAME . . ." --width 350 --height 25

## ---Check to see if image uploaded successfully and show notification
if [ $(google picasa list title --title "Drop Box" | grep $FILENAME | wc -l) -eq 1 ] ; then
    zenity --info --title "Complete" --text "Upload of $FILENAME complete!" --height 15
else
    zenity --error --title "Error" --text "Upload of $FILENAME failed!" --height 15
fi
```If anyone can figure out how to get the zenity progress bar to work, that would be great!

---

### Post by Vicolaships on 2013-01-08
Hey, this script doesn't work for me, I have googlecl_0.9.14-2_all version of GoogleCL.

Here is my script (modified from others found on the Internet)

```
#!/bin/bash

# Folder in your picasa account, the folder must exist !
folder="Fichiers transférés"
# Allow to show the filename in notification
filename=$(basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS)

# Check if GoogleCL is installed
if [ $(which google | wc -l) -eq 0 ] ; then
notify-send -i "process-stop" "Picasa upload" "`printf "Please do :\n sudo apt-get install -y googlecl"`"
    exit 1
fi

# Upload image
notify-send -i "gtk-go-up" "Picasa upload" "`printf "$filename is being uploaded"`"
google picasa post "Fichiers transférés" $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

# Check if upload is successfull and show notification
if [ "$?" -ne "0" ]; then
notify-send -i "process-stop" "Picasa upload" "`printf " Your upload failed \n Error: $?"`"
else
notify-send -i "gtk-ok" "Picasa upload" "`printf "$filename is online"`"
fi

```I tried this to test my script :
```
nautilus -q
nautilus --no-desktop
```I can use the script and upload pictures successfully.

The terminal show this for example :
```
$ nautilus --no-desktop
Initializing nautilus-gdu extension
Loading file /home/victor/Téléchargements/Portrait.jpg to album Fichiers transférés

```


But when I use it in a normal situation (launching Nautilus from the dash) the upload fails and I get an error 0 (it is not supposed to be an error !)

Any help would be appreciated :)

---

### Post by Vicolaships on 2013-02-10
Do someone have a working script ?
Please help !

---

