---
title: "Bash script to convert files using ffmpeg"
date: 2006-08-01
forum: Programming Talk
---

### Post by Lunar_Lamp on 2006-08-01
Hi I'm tryihg to write a bash script that will help me when i have downloaded flv files from youtube etc.  The idea is to have a script that will do three things (initially, and be expanded to be more complex later perhaps):

 - Convert a file from flv to mpg
 - Delete the flv file (if requested)
 - Allow user to rename the mpg file to whatever they want (I know this could be done using a $2 variable, but I would prefer not to).

I'd appreciate it if people would look over it and let me know how to make this into a working script, as I am very new to bash and have just thrown together some thoughts based upon what I already know.

```
#!/bin/bash
#
# script written to convert flvs from places like youtube and googlevideos to mpg files.
#
# note to self: $1 = 'flv filename'
#
#   todo:
# - sort the rename function out
# - combine the functions
# - make te script able to deal with multiple files
# - enable input variable to be the url, and make the script find the correct url to download and then convert

####################
# Convert Function #
####################
#this coverts the flv file specified ($1) to mpg

function convert {
	ffmpeg -i $1 -ab 56 -ar 22050 -b 500  -s 320x240 $name
}  

# -ab = averate bitrate of music (default=64)
# -ar = averate sampling rate
# -b  = 
# -s  = resize

###################
# Rename Function #
###################
#this function asks what you want to call the new file created, and acts accordingly.

function rename {
echo "By default the file will be named $1.mpg - do you want to change this?"
if [ "$rename_answer" = "y" ];
	then echo "What do you want to call it?"
	read name
	echo "Converting flv file to $name"
elif [ "$rename_answer" = "n" ];
	name=$1.mpg
	echo "Converting file to $1.mpg"
fi
}

#####################
# Deletion Function #
#####################
#this function asks if you want to delete the original file and acts accordingly.

function flvdelete {

	echo "Do you want to delete original flv file? (Y/N)"

	read reply

	if [ "$reply" = "y" ];
 		then rm $1
		echo "File deleted: $1"

	elif [ "$reply" = "n" ];
 		then echo "Leaving file intact: $1"

	fi
}

###############
# Main Script #
###############

$rename ;
$convert ;
$flvdelete 

exit
```

---

### Post by Lunar_Lamp on 2006-08-02
I have written the script now, but am unsure how to go about enabling it to have more than one target file (i.e. do a batch of files).

```
#!/bin/bash
#
# script written to convert flvs from places like youtube and googlevideos to mpg files.
#
# note to self: $1 = 'flv filename'
#
#   todo:
# - make the script able to deal with multiple files
# - enable input variable to be the url, and make the script find the correct url to download and then convert?

flv_file=$1

####################
# Convert Function #
####################
#this coverts the flv file specified ($1) to mpg

function convert {
	ffmpeg -i $flv_file -ab 56 -ar 22050 -b 500 -s 320x240 $name.mpg
}  

# Variables declared in above line (brackets are defaults used if option is omitted) 
#
# -ab = averate bitrate of music in kbit/s (default = 64)
# -ar = audio sampling frequency (default = 44100 Hz)
# -b  = video bitrate in kbit/s (default = 200 kb/s)
# -s  = set frame size (wxh) (default = 160x128)

###################
# Rename Function #
###################
#this function asks what you want to call the new file created, and acts accordingly.

rename ()
{
echo "By default the file will be named $flv_file.mpg - do you want to change this? (Y/N)"
read rename_answer
	if [ "$rename_answer" = "y" ];
		then echo "What do you want to call it? (.mpg will automatically be appended to the filename)"
		read name
		echo "Converting flv file to $name.mpg"

	else [ "$rename_answer" = "n" ];
		name=$flv_file.mpg
		echo "Converting file to $name"

	fi
}


#####################
# Deletion Function #
#####################
#this function asks if you want to delete the original file and acts accordingly.

function flvdelete {

	echo "Do you want to delete the original flv file? (Y/N)"

	read reply

	if [ "$reply" = "y" ];
 		then rm $flv_file
		echo "File deleted: $flv_file"  #should I build in some kind of detection of 'need to be root to delete'?

	elif [ "$reply" = "n" ];
 		then echo "Leaving file alone: $flv_file"

	fi
}

###############
# Main Script #
###############

rename ;
convert ;
flvdelete 

exit
```

---

### Post by Eric DANE on 2007-02-14
after $ sudo apt-get install ffmpeg, it work fine !!

Thanx.

PS : anyfirefox plugin or deb package to come ?

---

