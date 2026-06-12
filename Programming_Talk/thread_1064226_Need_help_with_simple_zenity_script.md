---
title: "Need help with simple zenity script"
date: 2009-02-08
forum: Programming Talk
---

### Post by theinnercityhippy on 2009-02-08
Hello,

I'm trying to write a simple script to back up all jpeg and png files from removable media in a graphical way using zenity as a bit of an exercise I've set myself.

I've reached a bit of a brick wall and can't understand the result I'm getting from a command so wsa hoping someone could help.

Cutting out superfluous stuff (like titles, text etc...) what I have in a nutshell is this;
```

#!/bin/bash
#
Medlist=`ls -1 -I cdrom0 /media | while read File; do echo "FALSE $File"; done`
#
ans1=$(zenity --list --title="Select Storage Device(s)" --text="Here is the list of removable storage devices." --checklist --multiple --separator="," --column " " --column "Removable Storage" $Medlist)
```

Now when I try to use find on the output in the next line like so;

```
ans2=`find /media/{$ans1} -name "*.jpg" -or -name "*.png"`
#
echo $ans2
```

I get an error saying find: file '/media/{disk,disk-1,etc}' not found.

If I enter the find command directly into the shell however, it works fine. I can't see why it isn't working as part of the script as the syntax in the error message seems fine.

Any ideas?

-JimDog*-

---

### Post by geirha on 2009-02-08
I believe brace expansion happens before variable expansion, so that just won't work.

Consider using find like this.
```
find /media -mindepth 1 -maxdepth 1 -type d -printf 'FALSE\0%p\0' | 
xargs -0 zenity --list --checklist --multiple --column ' ' --column 'Removable Storage'
```

Using \0 as delimiter is also very safe with regard to filenames with whitespace.

Getting an equally safe way of retrieving the directory names from zenity though, is a bit trickier, since you can't tell zenity to use \0 as separator. The next best thing would be to use \n as separator, since that is rarely used in pathnames.
```
ans1=$(find /media -mindepth 1 -maxdepth 1 -type d -printf 'FALSE\0%p\0' | 
xargs -0 zenity --list --checklist --multiple --separator=$'\n' -column ' ' --column 'Removable Storage')

# Read the selected mount-points into an array

read -d '\n' -a mountpoints <<< "$ans1"

# Find all jpegs and pngs on those mountpoints
find "${mountpoints[@]}" -iname "*.jpg" -o -iname "*.png"

```

The code above is very bash-centric, and will not work with /bin/sh. Hope this helps...

---

### Post by theinnercityhippy on 2009-02-09
> **geirha said:**
> I believe brace expansion happens before variable expansion, so that just won't work.

Consider using find like this.
```
find /media -mindepth 1 -maxdepth 1 -type d -printf 'FALSE\0%p\0' | 
xargs -0 zenity --list --checklist --multiple --column ' ' --column 'Removable Storage'
```

Using \0 as delimiter is also very safe with regard to filenames with whitespace.

Getting an equally safe way of retrieving the directory names from zenity though, is a bit trickier, since you can't tell zenity to use \0 as separator. The next best thing would be to use \n as separator, since that is rarely used in pathnames.
```
ans1=$(find /media -mindepth 1 -maxdepth 1 -type d -printf 'FALSE\0%p\0' | 
xargs -0 zenity --list --checklist --multiple --separator=$'\n' -column ' ' --column 'Removable Storage')

# Read the selected mount-points into an array

read -d '\n' -a mountpoints <<< "$ans1"

# Find all jpegs and pngs on those mountpoints
find "${mountpoints[@]}" -iname "*.jpg" -o -iname "*.png"

```

The code above is very bash-centric, and will not work with /bin/sh. Hope this helps...

Thankyou very much, this is very helpful.

Doing all this for a bit of fun really and to expad my knowledge of shell scripting. I have a working(ish) script that I'll post below thanks to a very late night and lots of caffeine, I think I'm starting to get the hang of variables a bit now.

The problem I'm working on now is the if then fi statements I need to make the program exit when cancel is pressed. Assuming that it is a case of continuing if anything that is not 0 is selected? Can I route the user back to specific parts of the script, say with a "start over" or "back" button?

I'm having a job getting zenity to open with focus as it seems to always open as the furthest window back, and even if there's no other windows on screen, it still doesn't have the focus by default. Is this a zenity thing or is there some way to rectify this?

Also, as this is just an exercise for me, would have liked to try and build a .deb package with icons and paths for saving the script. Is this possible with a simple shell script.

Anyway, here's what I've got so far for the community to have a gander at. Hopefully it might be useful to someone when it's finished too.

I've cut out the waffle at the top which is the description and contact details etc for now as it isn't finished.

Many thanks again for all your help

-JimDog*-


```
#!/bin/bash


# set the initial media folders to be used in the script. 

Medlist=`ls -1 -I cdrom0 /media |\
	
	 while read File;
 	do echo "TRUE $File"; 
	done`

# now to try and start the thing up, giving a brief welcome screen with an icon
# using a stock Ubuntu picture for now

zenity --info --window-icon=/usr/share/pixmaps/ubuntu-screensaver.svg\
 --title="REMOVABUBBLE v0.2"\
 --text="Hello $USER, this script\
 will let you easily copy files from several removable media\
 sources to a folder of your choice, ready for uploading to the\
 internet"

# First choose the correct Flash Disk to use for the upload

ans1=$(zenity --list\
 --window-icon=/usr/share/pixmaps/ubuntu-screensaver.svg\
 --title="Select Storage Device(s)"\
 --text="Here is the list of\
 removable storage devices. \nI have detected on your computer.\
\n\nChoose the Storage Devices you would like to \nimport pictures\
 from.\n\nNote: You may Select more than one if you wish."\
 --checklist\
 --multiple\
 --separator=" \n"\
 --column " "\
 --column "Removable Storage" $Medlist)

# Ok, now we now what disk(s) to use, time to scan the media and choose
# The files we want to use and sort them into a format readable by our
# Checklist

ans2=`echo -e "$ans1" |\

	while read file;\
	do find /media/${file} -name "*.png" -or -name "*.jpg" -or -name "*.gif" ;\
 	done |\

	 while read file2;\
 	do echo -e "TRUE ${file2} \n" ;\
	done`

# Now to choose the files we want from the media that was detected

ans3=$(zenity --list\
 --title="Choose Media Files"\
 --window-icon=/usr/share/pixmaps/ubuntu-screensaver.svg\
 --text="Right then, I've found the following list of pictures on the devices you selected.\
 \n\nChoose the files you wish to import by making sure the box for each is ticked.
 \n\nThen on the next screen we will be choosing (or creating) a target directory where\
 \nwe would like our files to be saved to"\
 --checklist\
 --multiple\
 --separator=" "\
 --column " "\
 --column "Detected Media Files" $ans2)

# Finally we just need to select the target directory where we want
# our files to be saved

TargetDir=$(zenity --file-selection\
 --directory\
 --save\
 --window-icon=/usr/share/pixmaps/ubuntu-screensaver.svg\
 --title="Where would you like to save your files?")

# Now to get on with the transfer, we just need the user to confirm
# their choices. will add a back button and a chance to review at a 
# later date

YN=$(zenity --question\
 --window-icon=/usr/share/pixmaps/ubuntu-screensaver.svg\
 --text="Pressing OK now will copy the files you\
 selected to \n\n${TargetDir} \n\nIs this correct?\
 If not press Cancel to exit\
 \nwithout saving them to your computer")

# Now to get on with the donkey work and do the transfer, closing 
# on completion and (hopefully) giving us a nice progress bar

cp $ans3 $TargetDir | zenity --progress --text="Copying your files to ${TargetDir}"\
 --percentage=0 --auto-kill --auto-close

# Then just a final confirm and a chance to say thanks

zenity --info\
 --window-icon=/usr/share/pixmaps/ubuntu-screensaver.svg\
 --text="All files have been successfully copied to\
 \n\n\ ${TargetDir}\
 \n\n\Thanks for using Removabubble.
 \n\n\Have a great day :-)"

```

---

### Post by marc41 on 2009-11-13
As for zenity popping up without focus (and underneath):

I have a script on gnome-look.org which fixes this (actually the script has a different purpose, but fixes zenity during initial setup).  Though, I've heard that Ubuntu 9.10 may have the configuration file renamed or in a different place - checking in to that now (I use Fedora 11 and it works fine, and have had only 2 complaints about Ubuntu out of thousands of downloads, so maybe it's just fine).  

In any case...

If you download this script, after the first use you will find a script /tmp/zenity.fix which was used to edit /usr/share/zenity/zenity.glade.  It will have preserved the original as zenity.glade.orig and also created zenity.glade.popover and zenity.glade.popunder

This ought to get you started!

Go here:
[http://www.gnome-look.org/content/show.php/Audio%2BVideo+Convert?content=92533](http://www.gnome-look.org/content/show.php/Audio%2BVideo+Convert?content=92533)

-- Marc

---

