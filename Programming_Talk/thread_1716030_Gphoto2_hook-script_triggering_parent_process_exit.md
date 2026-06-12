---
title: "Gphoto2 hook-script triggering parent process exit?"
date: 2011-03-27
forum: Programming Talk
---

### Post by cardmaverick on 2011-03-27
I've been working for days on a great little script that uses gphoto2 and a number of image viewers to capture and display shots from my Nikon D700. One of the last big hurdles I'm having is getting the parent process to kill itself when I close down the viewer program that the gphoto2 hook-script triggers. Currently I need to type ctrl-c in order to kill the terminal (it also kills the viewer program if its still open). 

What I want is to be able to close my viewer and have the terminal and gphoto2 stop running. Most of my work so far has been the result of searching and reading around... 

I'm also using Zenity to make the script more user friendly.

My "tethering" script is below, followed by one of the "hook-scripts" I'm using for viewing:

[PHP]
#!/bin/sh

zenity --info --text="Welcome to Linux Capture Pro!\n\n Please connect your camera before\n continuing!\n\nSelect a capture viewing mode\n in the next dialog that pops up.\n\n In the second dialog, select or\n create a new directory to\n capture your files too.\n\n If in doubt, read the dialog box\n titles before proceeding."

gvfs-mount --unmount-scheme gphoto2

cd /home/chris/Pictures/advanced_capture/capture_modes

VIEWER=$(zenity --file-selection --title="Select a CAPTURE MODE file.")

if [ ! $VIEWER ]; then
	
	zenity --error --text="ABORTING"
	exit
else	

cd /home

CAPTURE=$(zenity --file-selection --directory --title="Select a Capture Location");cd "$CAPTURE"

if [ ! $CAPTURE ]; then
	zenity --error --text="ABORTING"
	exit

else 

CAMERA_FOLDER=/store_00010001


zenity --info --text="You can now begin capturing!\n\n To close out, open the\n terminal and enter CTRL+C."

while [ 1==1 ]
do	

	
	gphoto2 --folder="$CAMERA_FOLDER" --capture-tethered --hook-script="$VIEWER"

	gphoto2 --recurse
		
	sleep 1
	

done

exit;

fi
fi
fi
[/PHP]

Hook-script:

[PHP]
#!/bin/sh

case "$ACTION" in
	init)
		# Called just after gphoto2 starts
		# Return non-zero exit code to abort
		;;

	start)
		# Called just before gphoto2 executes requested commands
		;;

	stop)
		# Called just before gphoto2 ends
		;;

	download)
		# Called just after a file has been downloaded to the computer
		geeqie --remote --tools-show --last "$ARGUMENT" &
		;;
esac

[/PHP]

Any help would be immensely appreciated!

---

