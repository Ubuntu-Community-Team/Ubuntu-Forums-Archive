---
title: "Mount script"
date: 2010-05-15
forum: Programming Talk
---

### Post by SpinningAround on 2010-05-15
I'm working on a script based on this one [http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369) but instead of only mounting iso, will it also mount img files. As an extra feature to unmount the file if it's already mounted. Problem is that TYPE = "$(file -b "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | cut -c 3-6 )" wont return anything, so I can't see what type it's.

[PHP]
#!/bin/bash
#
# nautilus-file-mounter

gksudo -u root -k /bin/echo "Enter your password for root terminal access"

# Get file type ISO or UDF
TYPE = "$(file -b "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | cut -c 3-6 )"
zenity --info --title "TEST" --text "$TYPE"
exit 0
# Check if file already mounted | not finished
if [-d /media/"$*" ]; then
	#Confirm to unmount
	if [ zenity --question --title "File Mounter" --text "Unmount $*?" ]; then
		sudo umount "$*" 
		zenity --info --text "Successfully unmounted /media/$*/"
		sudo rmdir "/media/$*/"
		exit 0
	else
		exit 1
	fi
#Try to mount
else
	#ISO
	if [ "$TYPE"==ISO ]; then
		BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`
		sudo mkdir "/media/$BASENAME"
		if [ sudo mount -o loop -t iso9660 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS "/media/$BASENAME" ]; then
			zenity --info --title "File Mounter" --text "$BASENAME Successfully Mounted."
			exit 0
		else
			sudo rmdir "/media/$BASENAME"
			zenity --error --title "File Mounter" --text "Cannot mount $BASENAME!"
			exit 1
		fi
	#UDF IMG
	elif [ "$TYPE"==UDF ]; then
		BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .img`
		sudo mkdir "/media/$BASENAME"
		if [ sudo mount -t udf -o loop $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS "/media/$BASENAME" ]; then
			zenity --info --title "File Mounter" --text "$BASENAME Successfully Mounted."
			exit 0
		else
			sudo rmdir "/media/$BASENAME"
			zenity --error --title "File Mounter" --text "Cannot mount $BASENAME!"
			exit 1
		fi
	#None of the above
	else
		zenity --error --title "File Mounter" --text "Cannot mount $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS!"
		exit 1
	fi
fi
[/PHP]

---

### Post by SpinningAround on 2010-05-16
shameless bump

---

