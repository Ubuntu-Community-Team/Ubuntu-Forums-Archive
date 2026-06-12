---
title: "Bash script with zenity just exits after it checks if a directory exists or not"
date: 2011-03-29
forum: Programming Talk
---

### Post by LarsKongo on 2011-03-29
I'm a creating a small bash script that will install one of my GTK themes with some GUI dialogs from zenity. I'm pretty new at this so I've run into my first trouble:

```
#!/bin/bash 
#

# Finds the user installing the theme
user=`who am I | awk '{print $1}'`

# Starting the gui dialogs

zenity --question --text="Are you sure you want to install this theme?"
if [ $? -eq 0 ] ; then
	# Checks if the theme is already installed
	if [ ! -d "/home/$user/.themes/Simpleton" ]; then
		zenity --warning --text "The theme seems to be installed already. Aborting."
		exit
	else
		# This is where it will install the theme
	fi	
else
	zenity --error --text "Theme installation aborted."
fi
```
It's the part where it checks if the theme is already installed. The message: *"The theme seems to be installed already. Aborting."*
It just ignores that dialog and exits.

If I don't use zenity and use echo instead I can get it to work. So I'm not sure what's wrong. Any help appreciated. :)

**EDIT:**
NVM. :) Figured it out by doing this instead:

```
zenity --question --text="Are you sure you want to install this theme?"
if [ $? -eq 0 ] ; then
	# Checks if the theme is already installed
	if [ -d $HOME/.themes/Simpleton ]; then
		zenity --warning --text="The theme seems to be installed already. Aborting."
		exit 0
	else
		zenity --info --text="Test."
	fi	
else
	zenity --error --text="Theme installation aborted."
fi
```

---

### Post by Cheesehead on 2011-03-29
Try a non-user-dependent test, like creating a tempfile, to see if the logic is working.

Unless Zenity is launched from a user's tty, it may need to know which display to show the message to. Often just knowing the username isn't enough.
```
DISPLAY=:0 zenity --error --text "Theme installation aborted."

```

---

