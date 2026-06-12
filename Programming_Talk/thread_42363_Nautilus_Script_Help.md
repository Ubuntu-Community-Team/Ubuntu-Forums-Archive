---
title: "Nautilus Script Help"
date: 2005-06-17
forum: Programming Talk
---

### Post by audax321 on 2005-06-17
Hello,

I'm trying to write a nautilus script that will prompt the user to create a directory after right clicking on a file and running the script.  For example, the user selects blah.mp3 and then runs the nautilus script which prompts for the name of a directory to which he or she enters my_dir and the program creates the directory:

(some base directory already in the script)/blah.mp3/my_dir

This is what I have and it works if the script is run in gnome-terminal (after removing the "$1" entry of course). But when it is run using the scripts menu in nautilus, the script is not run in gnome-terminal so the user never gets a prompt. Is there a way to do this?

```

#!/bin/bash

BASE_PATH=~

echo "Enter name for a folder: "
read USER_PATH

mkdir "$BASE_PATH"/"$1"/"$USER_PATH"


``` 

I know this script does not seem useful, but I'll post the script when it is done and it will make more sense then :) 


Thanks...

---

### Post by audax321 on 2005-06-17
Alternatively I was think of making the nautilus-script launch a second script in gnome-terminal, but in that case I need to know how to pass the $1 variable from the nautilus-script being run to the second script.

Any ideas? I don't shell script much...  :neutral:

---

### Post by audax321 on 2005-06-17
Okay, I got the scripts working, and if anyone is interested here is what the script does. I found this program called NZBPerl to download .nzb files with and get stuff off of usenet. The problem with this program right now is that it downloads all the files to one folder and makes a mess. So, I wanted to make a script that would put each NZB file in its own folder. 


A simple way to accomplish this was to just name the new download folder the same as the .nzb file and the nautilus-script below will accomplish that:
```

#!/bin/bash

# SET PATHS
NZBPERL_BASE_DOWNLOAD_PATH=~/Downloads/NZBPerl
NZBPERL_EXE=~/Applications/nzbperl.pl

NZBPERL_FULL_DOWNLOAD_PATH="$NZBPERL_BASE_DOWNLOAD_PATH"/"$1"_FILES

# CREATE DOWNLOAD PATH
mkdir "$NZBPERL_FULL_DOWNLOAD_PATH"

# IF NO ERRORS, START DOWNLOAD
if [ "$?" = "0" ]; then
	gnome-terminal --geometry=111x41 -x perl "$NZBPERL_EXE" --dlpath="$NZBPERL_FULL_DOWNLOAD_PATH" "$1"
else
	echo "Cannot create directory!" 1>&2
	exit 1
fi

```

> 
NZBPERL_BASE_DOWNLOAD_PATH needs to be set to the directory where all downloads will go (e.g. if NZBPERL were run without a script)
NZBPERL_EXE needs to be set to where the nzbperl.pl file is kept
 


But, then I started thinking why not write a script that allows you to specify what you want to call the folder because .nzb files don't always have very descriptive names. In order to do this I needed to make two scripts. The nautilus-script (the one you would launch by right clicking on an actual .nzb file) launches the second script (which actually initiates the download after asking for the name of the directory).

This is the nautilus script (goes in ~/.gnome2/nautilus-scripts)
```

#!/bin/sh

# Nautilus script which executes another script that initiates the download of *.nzb files.

# SET PATH TO DOWNLOAD SCRIPT
NZBPERL_DOWNLOAD_SCRIPT_PATH=~/Misc.\ Items/Scripts/NZBPERL_Custom_Download_Script.sh

gnome-terminal --working-directory=pwd -x sh "$NZBPERL_DOWNLOAD_SCRIPT_PATH" "$1"

```

> 
NZBPERL_DOWNLOAD_SCRIPT_PATH needs to be set to the path of the second script (below).
 


This is the second script (goes anywhere you want, but you have to set the variable in the nautilus-script appropriately)
```

#!/bin/bash
# Script to download *.nzb files into a user-defined folder (run by another script through Nautilus).

# SET PATHS
NZBPERL_BASE_DOWNLOAD_PATH=~/Downloads/NZBPerl
NZBPERL_EXE=~/Applications/nzbperl.pl


echo "Enter a name for the folder to download files to below: " 
read NZBPERL_USER_DOWNLOAD_PATH
NZBPERL_FULL_DOWNLOAD_PATH="$NZBPERL_BASE_DOWNLOAD_PATH"/"$NZBPERL_USER_DOWNLOAD_PATH"

# CREATE DOWNLOAD PATH
mkdir "$NZBPERL_FULL_DOWNLOAD_PATH"

# IF NO ERRORS, START DOWNLOAD
if [ "$?" = "0" ]; then
	gnome-terminal --geometry=111x41 -x perl "$NZBPERL_EXE" --dlpath="$NZBPERL_FULL_DOWNLOAD_PATH" "$1"
else
	echo "Cannot create directory!" 1>&2
	exit 1
fi

```

> 
NZBPERL_BASE_DOWNLOAD_PATH needs to be set to the directory where all downloads will go (e.g. if NZBPERL were run without a script)
NZBPERL_EXE needs to be set to where the nzbperl.pl file is kept



Hopefully one of the two solutions is useful to someone else... it gets the job done for me.


NZBPERL is available here: [http://noisybox.net/computers/nzbperl/](http://noisybox.net/computers/nzbperl/)

---

### Post by audax321 on 2005-06-19
Okay, I just updated the above script to use gdialog so now the two script approach can be done with just one script. Maybe someone else here can find another application of this :)

```

#!/bin/bash

# Script to download *.nzb files into a user-defined directory.


# SET PATHS
NZBPERL_BASE_DOWNLOAD_PATH=~/Downloads/NZBPerl
NZBPERL_EXE=~/Applications/nzbperl.pl

NZBPERL_USER_DOWNLOAD_PATH=$(gdialog --title "Filename..." --inputbox "All NZB downloads will download to $NZBPERL_BASE_DOWNLOAD_PATH. Enter a name for the sub-directory to download files to below:" 200 450 "Downloads" 2>&1)
NZBPERL_FULL_DOWNLOAD_PATH="$NZBPERL_BASE_DOWNLOAD_PATH"/"$NZBPERL_USER_DOWNLOAD_PATH"

# CREATE DOWNLOAD PATH
mkdir -p "$NZBPERL_FULL_DOWNLOAD_PATH"

# IF NO ERRORS, START DOWNLOAD
if [ "$NZBPERL_USER_DOWNLOAD_PATH" != "" ]; then
	if [ "$?" = "0" ]; then
		gnome-terminal --geometry=111x41 -x perl "$NZBPERL_EXE" --dlpath="$NZBPERL_FULL_DOWNLOAD_PATH" "$1"
	else
		NZBPERL_RESPONSE=$(gdialog --title "WARNING!" --inputbox "Can't create sub-directory '$NZBPERL_USER_DOWNLOAD_PATH' or it already exists! Would you like to attempt using the directory anyway? [y/n]" 200 450 "n" 2>&1)
	
		if [ "$NZBPERL_RESPONSE" = "y" ]; then
			gnome-terminal --geometry=111x41 -x perl "$NZBPERL_EXE" --dlpath="$NZBPERL_FULL_DOWNLOAD_PATH" "$1"
		else
			exit 1
		fi
	fi
fi


```

---

