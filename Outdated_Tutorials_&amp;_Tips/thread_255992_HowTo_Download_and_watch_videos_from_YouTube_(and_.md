---
title: "HowTo: Download and watch videos from YouTube (and similar)"
date: 2006-09-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Lunar_Lamp on 2006-09-12
Basically, this is just to gather, and update, the script I put [HERE]("http://ubuntuforums.org/showthread.php?t=113251&page=3&highlight=flvconvert").  I was prompted to make this How-To after receiving an email from a user who wanted me to make a GUI for it, so I did.

YouTube can be a hassle to use for some linux users, but it is still possible to watch the videos.

Step 1: Enter the URL of the YouTube (or other site) where the video you want to watch is at [http://keepvid.com/](http://keepvid.com/) (no affiliation to me, just the best one I've found).

Step 2: Wait for it to give you a download link and download the file.

Step 3: Either watch the flv file in something like Mplayer, or you can use my script to convert it to an mpeg file.  

This script needs to be located in ~/.gnome2/nautilus-scripts - just open up gedit, paste this script in, and save it in that folder as "FLVconvert" or whatever you want.  Then "chmod +x FILENAME".  To use it, just right-click on a file and select scripts>flvconvert, and follow the instructions.  It allows you to rename the file (as often they are named gobbledegook), and delete the original.  If you want it to do something else, just ask and I shall see what I can do.

```
#!/bin/bash
#
# script written by Ed to convert flvs from places like youtube and googlevideos to mpg files.
#
#   todo:
# #	- what happens when filename chosen is the same as a file already specified.
# - make the script able to deal with multiple files
# - enable input variable to be the url, and make the script find the correct url to download and then convert - NO IDEA HOW


####################################################################################################
# declaration of variable $1 to be referred to as $flv_file for the rest of the script for clarity #
####################################################################################################

flv_file=$1


####################
# Convert Function #
####################
#this coverts the flv file specified ($1) to mpg

function convert {
	ffmpeg -i "$flv_file" -ab 56 -ar 22050 -b 500 -s 320x240 "$OutputFilename".mpg | zenity --progress --auto-close 
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
RenameAnswer=$(zenity --question --text="By default the file will be named $flv_file.mpg.  If you want to change this click OK, otherwise click cancel.")

	if $RenameAnswer 
		then OutputFilename=$(zenity --entry --text="What do you want to call it? (.mpg will automatically be appended to the filename)" --title="FLVconvert")
		zenity --info --text="Press OK to convert flv file to $OutputFilename.mpg which will be found in $PWD.  This may take a while depending on how large the original flv file is.  Please be patient."

	else 
		OutputFilename=$flv_file
		zenity --info --text="Press OK to convert file to $OutputFilename which will be found in $PWD"

	fi
}

#####################
# Deletion Function #
#####################
#this function asks if you want to delete the original file and acts accordingly.



function flvdelete {
if $(zenity --question --text="Do you want to remove the original FLV file?  Press OK to delete and Cancel to keep the original flv file.")
  then rm $flv_file
  zenity --info --text="$flv_file deleted.  FLVconvert is finished."
else 
  zenity --info --text="$flv_file not deleted.  FLVconvert is finished."
fi
}


###############
# Main Script #
###############

rename ;
convert ;
flvdelete ;

exit

```

---

### Post by Anonii on 2006-10-11
> **Lunar_Lamp said:**
> Basically, this is just to gather, and update, the script I put [HERE]("http://ubuntuforums.org/showthread.php?t=113251&page=3&highlight=flvconvert").  I was prompted to make this How-To after receiving an email from a user who wanted me to make a GUI for it, so I did.

YouTube can be a hassle to use for some linux users, but it is still possible to watch the videos.

Step 1: Enter the URL of the YouTube (or other site) where the video you want to watch is at [http://keepvid.com/](http://keepvid.com/) (no affiliation to me, just the best one I've found).

Step 2: Wait for it to give you a download link and download the file.

Step 3: Either watch the flv file in something like Mplayer, or you can use my script to convert it to an mpeg file.  

This script needs to be located in ~/.gnome2/nautilus-scripts - just open up gedit, paste this script in, and save it in that folder as "FLVconvert" or whatever you want.  Then "chmod +x FILENAME".  To use it, just right-click on a file and select scripts>flvconvert, and follow the instructions.  It allows you to rename the file (as often they are named gobbledegook), and delete the original.  If you want it to do something else, just ask and I shall see what I can do.

```
#!/bin/bash
#
# script written by Ed to convert flvs from places like youtube and googlevideos to mpg files.
#
#   todo:
# #	- what happens when filename chosen is the same as a file already specified.
# - make the script able to deal with multiple files
# - enable input variable to be the url, and make the script find the correct url to download and then convert - NO IDEA HOW


####################################################################################################
# declaration of variable $1 to be referred to as $flv_file for the rest of the script for clarity #
####################################################################################################

flv_file=$1


####################
# Convert Function #
####################
#this coverts the flv file specified ($1) to mpg

function convert {
	ffmpeg -i "$flv_file" -ab 56 -ar 22050 -b 500 -s 320x240 "$OutputFilename".mpg | zenity --progress --auto-close 
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
RenameAnswer=$(zenity --question --text="By default the file will be named $flv_file.mpg.  If you want to change this click OK, otherwise click cancel.")

	if $RenameAnswer 
		then OutputFilename=$(zenity --entry --text="What do you want to call it? (.mpg will automatically be appended to the filename)" --title="FLVconvert")
		zenity --info --text="Press OK to convert flv file to $OutputFilename.mpg which will be found in $PWD.  This may take a while depending on how large the original flv file is.  Please be patient."

	else 
		OutputFilename=$flv_file
		zenity --info --text="Press OK to convert file to $OutputFilename which will be found in $PWD"

	fi
}

#####################
# Deletion Function #
#####################
#this function asks if you want to delete the original file and acts accordingly.



function flvdelete {
if $(zenity --question --text="Do you want to remove the original FLV file?  Press OK to delete and Cancel to keep the original flv file.")
  then rm $flv_file
  zenity --info --text="$flv_file deleted.  FLVconvert is finished."
else 
  zenity --info --text="$flv_file not deleted.  FLVconvert is finished."
fi
}


###############
# Main Script #
###############

rename ;
convert ;
flvdelete ;

exit

```
Thread gravedigging,
but this is great. Thanks!

---

### Post by cvmostert on 2006-10-16
Thank you... it worked for me... and then i got a problem with ffmpeg... but now it workes again after reinstalling ffmpeg again... 

I am talking about converting flv to mpg... wierd because flv to avi worked all the time... only mpg had a problem... still dunno what happened...

ciao

---

### Post by theicyj on 2006-11-07
Nice script.  GUI is a nice touch.  Thanks for sharing!

---

### Post by maka on 2006-11-07
thanks for the nice script

---

### Post by lizzard on 2006-11-07
If you use firefox you can install the "VideoDownloader" extension to download the videos.

---

### Post by ftmichael on 2007-02-19
I just use [youtube-dl]("http://www.arrakis.es/~rggi3/youtube-dl/").  Works great.  Sound and audio both play in VLC with the downloaded .flv file, or I can convert with ffmpeg.

Michael

---

### Post by ubu-for on 2007-02-26
> **Lunar_Lamp said:**
> Step 1: Enter the URL of the YouTube (or other site) where the video you want to watch is at [http://keepvid.com/](http://keepvid.com/) (no affiliation to me, just the best one I've found).

If you want to save a flash file from Firefox, just go to "/home/.../.mozilla/firefox/...default/Cache". Works with [Veoh](http://www.veoh.com/browse/videos.html?order=mp&range=w), too! :mrgreen: 

P.S. Your cache size should be big enough.

---

### Post by lukew on 2007-03-06
[http://www.ubuntuforums.org/showthread.php?t=328347](http://www.ubuntuforums.org/showthread.php?t=328347)

I combined the two to get a avi and mp3 from one URL without extra web site / mozilla application etc.

BTW I could not get mpg conversion to work; only avi.

Luke

---

### Post by Lunar_Lamp on 2007-04-02
Yeah, this script was written at a time when it was pretty hard to find any way of getting this videos, now flash is available for x86 linux though, so it's pretty redundant for me.  Truth be told, I'd forgotten I'd ever written this until I found it when looking for something else.  Glad that some people found it useful though!

---

### Post by dumskeet on 2007-04-09
Does anyone know if it’s possible to remove/delete a video from YouTube that another person has uploaded?

---

### Post by lukew on 2007-04-10
> **dumskeet said:**
> Does anyone know if it’s possible to remove/delete a video from YouTube that another person has uploaded?

Are you a UK School teacher? I hear they are going to be taking them down anyway ;)

I would imagine the only way is to complain to youtube. 

Remember if it is embarrassing don't do it; or don't film yourself doing it :)

---

### Post by dumskeet on 2007-04-15
No, I'm not a school teacher mate, thank f**k!:wink: 

"I hear they are going to be taking them down anyway"

Do you mean YouTube in general?

---

### Post by _atle_ on 2007-04-20
Thank you for this. It was needed on my end.

Atle.

---

### Post by Francewhoa on 2009-07-03
There's an easier way since then. You can watch full Veoh videos with the 'Illimitux' plug-in for Firefox. Read more at [http://ubuntuforums.org/showthread.php?p=7554700#post7554700](http://ubuntuforums.org/showthread.php?p=7554700#post7554700)

---

