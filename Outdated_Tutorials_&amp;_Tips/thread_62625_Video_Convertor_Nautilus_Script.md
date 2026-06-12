---
title: "Video Convertor Nautilus Script"
date: 2005-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by crmanski on 2005-09-05
(Note: Dapper thread is here: [http://www.ubuntuforums.org/showthread.php?t=193754](http://www.ubuntuforums.org/showthread.php?t=193754))
Hello everyone,
This script will take multiple video files of the same type (right now: MPG, AVI, MOV, ASF, VOB, WMV), ask you a few questions and covert them into either NTSC/PAL - dvd, svcd or vcd compliant MPEG files by using ffmpeg and mencoder. They can then be used with DVD styler, varsha, etc. to create a dvd video disk. 

Installation:
-Requirements: zenity (Comes with gnome), ffmpeg (apt-get ffmpeg), mencoder mplayer, transcode, mkvtoolnix
```
sudo apt-get install ffmpeg mencoder mplayer transcode mkvtoolnix
```
-Download the script and place it in the Nautilus scripts folder (/home/YourUserName/.gnome2/nautilus-scripts)
-Make sure the file is executable ```
chmod 740 ~/.gnome2/nautilus-scripts/video-convert
```
-Select some video files. (This works well on the video files my digital camera makes)
-Right-Click -> Choose Scripts -> video-convert

Note: There is a Beta version of the script attached to this post and the original that I used in the Hoary/Dapper days. I use the "Beta" version on my current desktop(Gutsy). Make sure to check the "Configuration Options" near the top of the script.

An enhanced ffmpeg with xvid and aac support can be downloaded here...
[http://skulboxx.com/Ubuntu/sbx/](http://skulboxx.com/Ubuntu/sbx/)

---

### Post by Nightblade on 2005-09-05
> **crmanski]Hello everyone,
This is my first public submission of something of this nature.  Constructive criticism is welcome. This script works as I would hope except that I cannot seem to make the zenity progress do anything, but I like the dialog up versus the conversion running in the background. Other than fixing that I do not plan to do much else with this script...

This script will take multiple video files of the same type (right now: MPG, AVI, MOV), ask you a few questions. and covert them into either NTSC - dvd, svcd or vcd compliant MPEG files by using ffmpeg ([http://ffmpeg.sourceforge.net](http://ffmpeg.sourceforge.net)). This could easily be setup to convert PAL also, but I do not have the means to test the final product on an authored DVD.

Background and Credits:
I came across the very nicely done audio-convert script in the Ubuntu forums [http://ubuntuforums.org/showthread.php?t=48007](http://ubuntuforums.org/showthread.php?t=48007) and thought how nice it would be to not have to open each file I want to convert in avidemux manually or by using a script for each file(s) using ffmpeg. So after looking at [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)  and some of the scripts there:
[http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/NIS](http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/NIS) 
[http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/convert_to_jpeg](http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/convert_to_jpeg) 

I ended up working this out with various bits and pieces of the above mentioned scripts. It is not pretty but it works for me.  Have fun!

Installation:
-Requirements: zenity (Comes with gnome 2.4), ffmpeg (apt-get ffmpeg)
-Place the script in the Nautilus scripts folder (/home/YourUserName/.gnome2/nautilus-scripts)
-Make sure the file is executable (chmod 740 ~/.gnome2/nautilus-scripts)
-Select some video files. This works well on the video files my digital camera makes
-Right-Click -> Choose Scripts -> video-convert


```
#!/bin/bash
#
# video-convert .01
# crmanski / http://szone.berlinwall.org
# Requirements: zenity (Comes with gnome 2.4), ffmpeg (apt-get ffmpeg)
# This script will take multiple video files of the same type (right now: MPG, AVI, MOV) 
# and covert them into either NTSC - dvd, svcd or vcd compliant MPEG files by using
# ffmpeg (http://ffmpeg.sourceforge.net)
#
# Installation:
# Place the script in the Nautilus scripts folder (/home/YourUserName/.gnome2/nautilus-scripts)
# Make sure the file is executable
# Select some video files. This works well on the video files my digital camera makes
# Choose Scripts->video-convert
#
# Background and Credits:
# I came across the very nicely done audio-convert script in the ubuntu forums
# http://ubuntuforums.org/showthread.php?t=48007
# and thought how nice it would be to not have to open each file I want to convert in avidemux
# manually or by using a script for each file(s) using ffmpeg. So after looking at 
# http://g-scripts.sourceforge.net/ and some of the scripts there:
# http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/NIS
# http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/convert_to_jpeg
# I ended up working this out with various bits and pieces of the above mentioned scripts.
# It is not pretty but it works for me.  Have fun!
#
# License:
# This program is free software said:**
> ; then
	zenity --error --title="error" --text="You must select at least 1 file to process"
	exit 1
fi

zenity --question \
        --text="This Script converts selected AVI, MOVE or MPG files to NTSC-DVD, SVCD or VCD compliant MPG files with ffmpeg. Proceed?"

#if $? != 0, user clicked on cancel button, so exit
if [ "$?" != 0 ] ; then
	exit
fi

#Input - What Type?
# Laziness. I am not detecting video mime types.
title="Choose which type the input video files are..."
video_in_type=`zenity --title "$title"  --list --separator=" " --column="Choose Input Video Type" "AVI" "MOV" "MPG" | sed 's/ max//g' `
#user must select a target size
if [ ! "$video_in_type" ]; then
	zenity --error --title="Error" --text="You must select a Input Type"
	exit
fi

#Output - What kind?
title="What kind of Video are you making?"
video_out_type=`zenity --title "$title"  --list --separator=" " --column="Output to..." "DVD" "SVCD" "VCD" | sed 's/ max//g' `
#user must select a target size
if [ ! "$video_out_type" ]; then
	zenity --error --title="Error" --text="You must select a Input Type"
	exit
fi

# If we are making DVD there are a few options...
if [ "$video_out_type" = "DVD" ]; then
	
	#What Size?
	title="Choose which resolution the video files should be..."
	dvd_res=`zenity --width="480" --height="480" --title "$title"  --list --separator=" " --column="Choose Video Resolution" "ntsc-dvd -s 720x480" "ntsc-dvd -s 720x400 -padtop 40 -padbottom 40" "ntsc-dvd -s 704x480" "ntsc-dvd -s 704x396 -padtop 42 -padbottom 42" "ntsc-dvd -s 352x480" "ntsc-dvd -s 352x240" "ntsc-dvd -s 352x196 -padtop 22 -padbottom 22"| sed 's/ max//g' `
	#user must select a target size
	if [ ! "$dvd_res" ]; then
		zenity --error --title="Error" --text="You must select a target resolution."
		exit
	fi
	title="Choose the audio bitrate your video files should have..."
	audio_br=`zenity --title "$title"  --list --separator=" " --column="Choose Audio Bitrate" "448" "356" "224" "160" "128" | sed 's/ max//g' `
	#user must select an audio bitrate
	if [ ! "$audio_br" ]; then
		zenity --error --title="Error" --text="You must select an audio bitrate."
		exit
	fi
	title="Choose the audio stream type your video files should have..."
	audio_str=`zenity --title "$title"  --list --separator=" " --column="Choose Audio Stream Type" "ac3" "mp2" | sed 's/ max//g' `
	#user must select an audio bitrate
	if [ ! "$audio_str" ]; then
		zenity --error --title="Error" --text="You must select an audio stream type."
		exit
	fi
fi

#Video Encoding Functions...
dvd_encode ()
{
	/usr/bin/ffmpeg -i "$movie" -target $dvd_res -sameq -hq -r 29.97 -aspect 4:3 -ab $audio_br -ar 48000 -ac 2 -acodec $audio_str -y "$mpg_file"
}
svcd_encode ()
{
	/usr/bin/ffmpeg -i "$movie" -target ntsc-svcd -sameq -hq -aspect 4:3 -y "$mpg_file"
}
vcd_encode ()
{
	/usr/bin/ffmpeg -i "$movie" -target ntsc-vcd -sameq -hq -aspect 4:3 -y "$mpg_file"
}

#Input Selection was AVI Video
if [ "$video_in_type" = "AVI" ]; then
	mime=`file -bi $*`
	nb_video=`echo "$mime" | grep video/x-msvideo | wc -l`

	let "nbfiles = $nb_video"

	while [ $# -gt 0 ]; do
		movie=$1
		mpg_file=`echo "$movie" | sed 's/\.\w*$/.mpg/'`
		mime=`file -bi "$movie"`
		isvideo=`echo "$mime" | grep video/x-msvideo | wc -l`
		if [ $isvideo -eq 0 ]; then
			zenity --error --title="error" --text="$movie is not an AVI video file"
		else
			echo "# Processing AVI Video $movie ..."
			if [ "$video_out_type" = "DVD" ]; then
				dvd_encode
			fi
			if [ "$video_out_type" = "SVCD" ]; then
				svcd_encode
			fi
			if [ "$video_out_type" = "VCD" ]; then
				vcd_encode
			fi
		fi	
		
		shift
	done|
	        zenity --progress --auto-close --title="Converting AVI Video Files"  --text="Converting AVI Video Files..."  --percentage=0
fi

#Input Selection was Quicktime Video
if [ "$video_in_type" = "MOV" ]; then
	mime=`file -bi $*`
	nb_video=`echo "$mime" | grep application/octet-stream | wc -l`

	let "nbfiles = $nb_video"

	while [ $# -gt 0 ]; do
		movie=$1
		mpg_file=`echo "$movie" | sed 's/\.\w*$/.mpg/'`
		mime=`file -bi "$movie"`
		isvideo=`echo "$mime" | grep application/octet-stream | wc -l`
		if [ $isvideo -eq 0 ]; then
			zenity --error --title="error" --text="$movie is not a Quicktime video file"
		else
			echo "# Processing Quicktime Video $movie ..."
			if [ "$video_out_type" = "DVD" ]; then
				dvd_encode
			fi
			if [ "$video_out_type" = "SVCD" ]; then
				svcd_encode
			fi
			if [ "$video_out_type" = "VCD" ]; then
				vcd_encode
			fi
		fi	
		
		shift
	done|
	        zenity --progress --auto-close --title="Converting Quicktime Video Files"  --text="Converting Quicktime Video Files..."  --percentage=0
fi

#Input Selection was MPG Video
if [ "$video_in_type" = "MPG" ]; then
	mime=`file -bi $*`
	nb_video=`echo "$mime" | grep video/mpeg | wc -l`

	let "nbfiles = $nb_video"

	while [ $# -gt 0 ]; do
		movie=$1
		mpg_file=`echo "$movie" | sed 's/\.\w*$/_NTSC-DVD.mpg/'`
		mime=`file -bi "$movie"`
		isvideo=`echo "$mime" | grep video/mpeg | wc -l`
		if [ $isvideo -eq 0 ]; then
			zenity --error --title="error" --text="$movie is not a MPG video file"
		else
			echo "# Processing MPG Video $movie ..."
			if [ "$video_out_type" = "DVD" ]; then
				dvd_encode
			fi
			if [ "$video_out_type" = "SVCD" ]; then
				svcd_encode
			fi
			if [ "$video_out_type" = "VCD" ]; then
				vcd_encode
			fi
		fi	
		
		shift
	done|
	        zenity --progress --auto-close --title="Converting MPG Video Files"  --text="Converting MPG Video Files..."  --percentage=0
fi

```
 Awesome man! Trying it out right now. 

Constructive critisism:

* Maybe make the interference a bit more userfriendly, with like pre-chosen default options.
* Autodetect filetypes.
* Support more formats.


Anyway, cool idea.

---

### Post by crmanski on 2005-09-05
Thanks Nightblade.
"pre-chosen default options"
I would like that too.  My first time playing around with zenity/bash scripting was yesterday, so if someone more knowledgeable could point me in the correct direction that would be welcome.

"Support more formats"
There are a ton of things that could be added.  I just added the ones that I most commonly use. Any Specifics?

---

### Post by heart_reaver on 2005-09-10
thats a great work of urs. 

can i get command for terminal line to copy vcd directly to HDD by using ffmpeg ;-)

---

### Post by Nightblade on 2005-09-10
[QUOTE=crmanski]Thanks Nightblade.
"pre-chosen default options"
I would like that too.  My first time playing around with zenity/bash scripting was yesterday, so if someone more knowledgeable could point me in the correct direction that would be welcome.

"Support more formats"
There are a ton of things that could be added.  I just added the ones that I most commonly use. Any Specifics?[/QUOTE]
 XviD/DivX encoding, from/to wmv avi ogg. That's what I'd use ;)

---

### Post by gheorghe_pop on 2005-09-10
I'd like a pall dvd
btw great work

---

### Post by Nightblade on 2005-09-10
[QUOTE=gheorghe_pop]I'd like a pall dvd
btw great work[/QUOTE]
 Yeah PAL is really nice too.

---

### Post by crmanski on 2005-09-10
[QUOTE=heart_reaver]thats a great work of urs. 

can i get command for terminal line to copy vcd directly to HDD by using ffmpeg ;-)[/QUOTE]
 To convert a VCD to an MPG you have to extract it with vcdimager.  Once you have the MPG you can reencode it to another format.

---

### Post by crmanski on 2005-09-10
Ok,
Sometime this weekend I'll look into the possible resolutions, add them and see if it works for you...

---

### Post by crmanski on 2005-09-11
[QUOTE=gheorghe_pop]I'd like a pall dvd
btw great work[/QUOTE]
 Ok, I just updated the code in the original post with options for PAL formatted video output.

---

### Post by heart_reaver on 2005-09-11
[QUOTE=Nightblade]XviD/DivX encoding, from/to wmv avi ogg. That's what I'd use ;)[/QUOTE]
 an example will be  appreciated to convert dvd/vcd to mpeg format directly form DVD/VCD.

---

### Post by slow learner on 2005-09-18
Hi

I have made a script file (called it 'video-convert') and put it into the nautilusiscripts folder & made it excutable but everytime i try to use the script (right click-->scripts-->video-convert) i get this error message:

I am clueless to what i have done wrong.
Thanks for all help

---

### Post by crmanski on 2005-09-19
[QUOTE=slow learner]

I am clueless to what i have done wrong.
Thanks for all help[/QUOTE]

Nothing wrong. I just dont have that particular mimetype set in the script.

If you reply with this output from this command: file -bi "YourFileName.avi" 
I can see about adding it.

---

### Post by slow learner on 2005-09-19
[QUOTE=crmanski]Nothing wrong. I just dont have that particular mimetype set in the script.

If you reply with this output from this command: file -bi "YourFileName.avi" 
I can see about adding it.[/QUOTE]
 Hi,
thanks for the reply.

I am not exactly sure what you wanted me to do. I opened up a terminal and cd to a directory with an avi file (the same one that gave the error attached above) and used the command you pasted.
All that was given in the terminal window after hitting enter was:
          video/x-msvideo

If I have done something wrong could you let me know.

Thanks again

---

### Post by crmanski on 2005-09-19
From looking at the error again this evening, it seems like there is either a permission problem with the script accessing the file or nautilus is not finding the path of the selected file correctly.  I thought it might be the -- in the file name but I named an avi file the exact same name and had no errors...

---

### Post by slow learner on 2005-09-19
I tried moving the location - put it into /mnt (with the same avi) and it worked, the option windows came up. but when i started the conversion the window closed & nothing else happened. (processor usage stayed at normal idle state)
I tried all formats dvd,svcd,vcd and all with pal & ntsc.

It is unable to open up the conversion window with any other avi file I have when located on the desktop or userhome directory.

---

### Post by crmanski on 2005-09-21
I am wondering where your ffmpeg binary is located. Type this in a terminal to find out: ```
which ffmpeg
```

To really see what is going on it might be best to run the script from a terminal like so...

```
~/.gnome2/nautilus-scripts/video-convertor "/home/Username/YourMovieFile.avi"
```

...and post any error messages you see.

---

### Post by crmanski on 2005-09-21
[QUOTE=heart_reaver]an example will be  appreciated to convert dvd/vcd to mpeg format directly form DVD/VCD.[/QUOTE]

This is basically beyond the scope of my script.  There are multiple steps involved in converting VCDs or DVDs to something else. The place I learned the most about this is at: [http://www.videohelp.com/](http://www.videohelp.com/) 
Some linux stuff here: [http://www.videohelp.com/guides.php?howtoselect=1;60](http://www.videohelp.com/guides.php?howtoselect=1;60)

If you search the forums for dvdshrink you will find quite a bit of discussion about it.

---

### Post by putte30 on 2005-11-08
Possible to do a new option that will convert eg. xvid to mp4 mobile profile?

Would be very very appreciated :smile:

---

### Post by Statik on 2005-11-09
Just tried this out. Seemed to work at first, then nothing. So, I ran it in terminal and here's the output:
```

statik@ubuntu:~$ ~/.gnome2/nautilus-scripts/video-convert "/home/statik/Mythbusters3x04.avi"
/home/statik/.gnome2/nautilus-scripts/video-convert: line 69: valid_video_type: command not found
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, avi, from '/home/statik/Mythbusters3x04.avi':
  Duration: 00:43:28.4, start: 0.000000, bitrate: 1308 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 512x384, 25.00 fps
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 224 kb/s
/usr/bin/ffmpeg: unrecognized option '-hq'

```

See any reason it's failing? I chose SVCD and SVCD NSTC

Statik

---

### Post by jtpratt on 2005-12-11
I had the exact same problem on my Ubuntu 5.10 install, when I installed the script and ran it - it would just die after I answered the questions.  I looked at your error output and it said that it wouldn't take the '-hq' option, which is 'high quality'.  I had the same error.

If you open up the script you installed in /home/user/.gnome2/nautilus-scripts/video-convert
and remove all the '-hq' (without the quotes) from the file (and re-save) - it will then work.

the little windows won't show any progress, but if you have a file browser open it will show the new .mpg file growing as it converts.
For some reason, it thinks .wmv files are Quicktime - but it will convert most.  Some it gives the error "not Quicktime" and it ignores them.

If you have troubles, just run the command yourself in terminal (first line is for ntsc, and second for pal).  If you want more options just run the command 'man ffmpeg' in terminal for the manual.
ffmpeg -i myfile.avi -target ntsc-vcd -bf 2 /home/user/vcd.mpg
ffmpeg -i myfile.avi -target pal-vcd -bf 2 /home/user/vcd.mpg

---

### Post by crmanski on 2005-12-12
I updated the first post to include this change also.

---

### Post by Georges on 2006-03-05
Hi

I modified the script. What's new:

* more pal resolutions
* the resolution chooser now shows the output of file -b in the header
* the progress bars actually do some progress!

Maybe better use in next version xdialog instead of zenity, it just has much more options.
If you are ok with this, I can migrate the script over to xdialog.

The script is attached to this post (as .txt because the bloody damn forum thinks it has to check for extension type. silly!).

---

### Post by Georges on 2006-03-05
found an issue with ffmpeg.

I encode a divx5 to mpeg2 and the result has the audio getting more and more offset from the video. I then tried DeVeDe [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html) and it does not offset the audio. DeVeDe uses mencoder.
Here's the mencoder command line DeVeDe uses to encode pal at 352x288

```

/usr/bin/mencoder -srate 48000 -af lavcresample=48000 -oac lavc -ovc lavc -of mpeg \
-mpegopts format=dvd -ofps 25 -vf scale=352:288,harddup \
-lavcopts vcodec=mpeg2video:vrc_maxrate=6750:vrc_buf_size=1835:vbitrate=4500:keyint=15:acodec=ac3:abitrate=224:aspect=4/3 \
-o movie_01_01.mpg inputmovieDiVX.avi

```

As my original source is not of good quality I can't say if mencoder is doing a good job in quality. At least it's not ofsetting audio.

Georges

---

### Post by art2003 on 2006-04-09
I have edited the script provided on this thread to include to changes:

A) The possibility of encoding from mpg, vob or asf TO XVID (.avi)
This generally produces files 3 to 4 times smaller.

B) Support for movie files in .ASF format (as this is the only format my video camera records in)

```
#!/bin/bash
#
# video-convert including to xvid.01.2
# 9/April/2006 - Last Updated: 9/April/2006
# based on:
# crmanski / http://szone.berlinwall.org
# Requirements: zenity (Comes with gnome 2.4), ffmpeg (apt-get ffmpeg)
# This script will take multiple video files of the same type (right now: MPG, AVI, MOV) 
# and covert them into either NTSC - dvd, svcd or vcd compliant MPEG files by using
# ffmpeg (http://ffmpeg.sourceforge.net) 
### ADDED by Arturo Martinez
### OPTION TO CONVERT TO XVID (.avi) 
### Also added handling of .ASF files as input types.
# Installation:
# Place the script in the Nautilus scripts folder (/home/YourUserName/.gnome2/nautilus-scripts)
# Make sure the file is executable
# Select some video files. This works well on the video files my digital camera makes
# Choose Scripts->video-convert
#
# Background and Credits:
# I came across the very nicely done audio-convert script in the ubuntu forums
# http://ubuntuforums.org/showthread.php?t=48007
# and thought how nice it would be to not have to open each file I want to convert in avidemux
# manually or by using a script for each file(s) using ffmpeg. So after looking at 
# http://g-scripts.sourceforge.net/ and some of the scripts there:
# http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/NIS
# http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/convert_to_jpeg
# I ended up working this out with various bits and pieces of the above mentioned scripts.
# It is not pretty but it works for me.  Have fun!
#
# License:
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
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  
# USA

#Has a file been selected?
if [ $# -eq 0 ]; then
	zenity --error --title="error" --text="You must select at least 1 file to process"
	exit 1
fi

#Input - What Type?
#Detect Mime Type
#This will detect the first file in the bunch and base the encoding on that. Make sure you select the same types.
mime=`file -bi "$1"`
humantype=`file "$1"`
valid_video_type="0"
if [ "$mime" = "video/x-msvideo" ]; then
	video_in_type="AVI"
	valid_video_type="1"
fi
if [ "$mime" = "application/octet-stream" ]; then # this one is fishy to me, but that is all the info I could get out of the files off my camera
	video_in_type="MOV"
	valid_video_type="1"
fi
if [ "$mime" = "video/mpeg" ]; then
	video_in_type="MPG"
	valid_video_type="1"
fi
if [ "$mime" = "application/octet-stream" ]; then
	video_in_type="ASF"
	valid_video_type="1"
fi


#Checking...
if [ $valid_video_type -eq "1" ]; then
	valid_video_type = "1"
	else
	zenity --error --title="Error" --text="You have not selected a valid Video Type. MimeType= $mime"
	exit
fi

#Output - What kind?
#echo "This Script converts selected AVI, MOVE or MPG files to NTSC-DVD, SVCD or VCD compliant MPG files with ffmpeg"
title="What kind of Video Do you want to convert those $video_in_type files to?"
video_out_type=`zenity  --width="480" --height="380" --title="$title" --list --radiolist --column="" \
	--column="Video Type" \
	TRUE "XVID" \
	FALSE "DVD" \
	FALSE "SVCD" \
	FALSE "VCD" | sed 's/ max//g' `

#user must select a target size
if [ ! "$video_out_type" ]; then
	zenity --error --title="Error" --text="You must select a Input Type"
	exit
fi

# If we are making DVD there are a few options...
if [ "$video_out_type" = "DVD" ]; then
	
	#What Size?
	title="Choose which resolution the video files should be..."
	dvd_res=`zenity --width="480" --height="380" --title="$title" --text="Input format: $humantype" --list --radiolist --column="" --column="Choose Video Resolution" --column "description" \
		TRUE "ntsc-dvd -s 720x480" "standard ntsc"\
		FALSE "ntsc-dvd -s 720x400 -padtop 40 -padbottom 40" "" \
		FALSE "ntsc-dvd -s 704x480" "" \
		FALSE "ntsc-dvd -s 704x396 -padtop 42 -padbottom 42" "" \
		FALSE "ntsc-dvd -s 352x480" "4:3 half ntsc" \
		FALSE "ntsc-dvd -s 352x240" "4:3 vcd size" \
		FALSE "ntsc-dvd -s 352x196 -padtop 22 -padbottom 22" "" \
		FALSE "pal-dvd -s 720x576" "4:3 full pal" \
		FALSE "pal-dvd -s 704x576" "" \
		FALSE "pal-dvd -s 352x576" "4:3 half pal" \
		FALSE "pal-dvd -s 352x288" "4:3 vcd size" \
		| sed 's/ max//g' `

	#PAL?
	if [ "${dvd_res##pal-dvd}" != "$dvd_res" ]; then
		video_out_type="DVD_PAL"
	fi

	#user must select a target size
	if [ ! "$dvd_res" ]; then
		zenity --error --title="Error" --text="You must select a target resolution."
		exit
	fi
	title="Choose the audio bitrate your video files should have..."
	audio_br=`zenity  --width="480" --height="380" --title="$title" --list --radiolist --column="" \
	--column="Choose Audio Bitrate" \
		FALSE "448" \
		FALSE "356" \
		TRUE "224" \
		FALSE "160" \
		FALSE "128" | sed 's/ max//g' `
	#user must select an audio bitrate
	if [ ! "$audio_br" ]; then
		zenity --error --title="Error" --text="You must select an audio bitrate."
		exit
	fi
	title="Choose the audio stream type your video files should have..."
	audio_str=`zenity  --width="480" --height="380" --title="$title" --list --radiolist --column="" --column="Choose Audio Stream Type" TRUE "ac3" FALSE "mp2" | sed 's/ max//g' `
	#user must select an audio bitrate
	if [ ! "$audio_str" ]; then
		zenity --error --title="Error" --text="You must select an audio stream type."
		exit
	fi
fi

#SVCD Options
if [ "$video_out_type" = "SVCD" ]; then
	title="What type of SVCD are you making?"
	video_out_type=`zenity  --width="480" --height="380" --title="$title" --list --radiolist --column="" \
	--column="NTSC or PAL?" \
		TRUE "SVCD_NTSC" \
		FALSE "SVCD_PAL" \
		| sed 's/ max//g' `
fi

#VCD Options
if [ "$video_out_type" = "VCD" ]; then
	title="What type of VCD are you making?"
	video_out_type=`zenity  --width="480" --height="380" --title="$title" --list --radiolist --column="" \
	--column="NTSC or PAL?" \
		TRUE "VCD_NTSC" \
		FALSE "VCD_PAL" \
		| sed 's/ max//g' `
fi

#Video Encoding Functions...
dvd_encode_ntsc ()
{
	/usr/bin/ffmpeg -i "$movie" -target $dvd_res -sameq -r 29.97 -aspect 4:3 -ab $audio_br -ar 48000 -ac 2 -acodec $audio_str -y "$mpg_file"
}
dvd_encode_pal ()
{
	/usr/bin/ffmpeg -i "$movie" -target $dvd_res -sameq -r 25 -ab $audio_br -ar 48000 -ac 2 -acodec $audio_str -y "$mpg_file"

}
svcd_encode_ntsc ()
{
	/usr/bin/ffmpeg -i "$movie" -target ntsc-svcd -sameq -aspect 4:3 -y "$mpg_file"
}
svcd_encode_pal ()
{
	/usr/bin/ffmpeg -i "$movie" -target pal-svcd -sameq -aspect 4:3 -y "$mpg_file"
}
vcd_encode_ntsc ()
{
	/usr/bin/ffmpeg -i "$movie" -target ntsc-vcd -sameq -aspect 4:3 -y "$mpg_file"
}
vcd_encode_pal ()
{
	/usr/bin/ffmpeg -i "$movie" -target pal-vcd -sameq -aspect 4:3 -y "$mpg_file"
}
xvid_encode ()
{
	/usr/bin/ffmpeg -i "$movie" -f avi -vcodec mpeg4 -b 800 -g 300 -bf 2 -acodec mp2 -ab 128 -y "$avi_file"
}

#Input Selection was AVI Video
if [ "$video_in_type" = "AVI" ]; then
	mime=`file -bi "$*"`
	nb_video=`echo "$mime" | grep video/x-msvideo | wc -l`

	let "nbfiles = $nb_video"

	while [ $# -gt 0 ]; do
		movie=$1
		mpg_file=`echo "$movie" | sed 's/\.\w*$/.mpg/'`
		mime=`file -bi "$movie"`
		isvideo=`echo "$mime" | grep video/x-msvideo | wc -l`
		if [ $isvideo -eq 0 ]; then
			zenity --error --title="error" --text="$movie is not an AVI video file"
		else
			echo "# Processing AVI Video $movie ..."
			if [ "$video_out_type" = "DVD" ]; then
				dvd_encode_ntsc
			fi
			if [ "$video_out_type" = "DVD_PAL" ]; then
				dvd_encode_pal
			fi
			if [ "$video_out_type" = "SVCD_NTSC" ]; then
				svcd_encode_ntsc
			fi
			if [ "$video_out_type" = "SVCD_PAL" ]; then
				svcd_encode_pal
			fi
			if [ "$video_out_type" = "VCD_NTSC" ]; then
				vcd_encode_ntsc
			fi
			if [ "$video_out_type" = "VCD_PAL" ]; then
				vcd_encode_pal
			fi
			if [ "$video_out_type" = "XVID" ]; then
				xvid_encode
			fi
		fi	
		
		shift
	done 2>&1|
                perl -ne '$/="\r";$| = 1;if (/Duration: (\d+):(\d+):(\d+)/) { $max=($1*3600+$2*60+$3) };
                if (/time=(\d+)/) { printf "%d\n",($1/$max*100);}
                print STDERR $_;'|
	        zenity --progress --auto-close --title="Converting AVI Video Files"  --text="Converting AVI Video Files..."  --percentage=0
fi

#Input Selection was Quicktime Video
if [ "$video_in_type" = "MOV" ]; then
	mime=`file -bi "$*"`
	nb_video=`echo "$mime" | grep application/octet-stream | wc -l`

	let "nbfiles = $nb_video"

	while [ $# -gt 0 ]; do
		movie=$1
		mpg_file=`echo "$movie" | sed 's/\.\w*$/.mpg/'`
		mime=`file -bi "$movie"`
		isvideo=`echo "$mime" | grep application/octet-stream | wc -l`
		if [ $isvideo -eq 0 ]; then
			zenity --error --title="error" --text="$movie is not a Quicktime video file"
		else
			echo "# Processing Quicktime Video $movie ..."
			if [ "$video_out_type" = "DVD" ]; then
				dvd_encode_ntsc
			fi
			if [ "$video_out_type" = "DVD_PAL" ]; then
				dvd_encode_pal
			fi
			if [ "$video_out_type" = "SVCD_NTSC" ]; then
				svcd_encode_ntsc
			fi
			if [ "$video_out_type" = "SVCD_PAL" ]; then
				svcd_encode_pal
			fi
			if [ "$video_out_type" = "VCD_NTSC" ]; then
				vcd_encode_ntsc
			fi
			if [ "$video_out_type" = "VCD_PAL" ]; then
				vcd_encode_pal
			fi
			if [ "$video_out_type" = "XVID" ]; then
				xvid_encode
			fi
		fi	
		
		shift
	done 2>&1|
                perl -ne '$/="\r";$| = 1;if (/Duration: (\d+):(\d+):(\d+)/) { $max=($1*3600+$2*60+$3) };
                if (/time=(\d+)/) { printf "%d\n",($1/$max*100);}
                print STDERR $_;'|
	        zenity --progress --auto-close --title="Converting Quicktime Video Files"  --text="Converting Quicktime Video Files..."  --percentage=0
fi

#Input Selection was MPG Video
if [ "$video_in_type" = "MPG" ]; then
	mime=`file -bi "$*"`
	nb_video=`echo "$mime" | grep video/mpeg | wc -l`

	let "nbfiles = $nb_video"

	while [ $# -gt 0 ]; do
		movie=$1
		mpg_file=`echo "$movie" | sed 's/\.\w*$/_NTSC-DVD.mpg/'`
		avi_file=`echo "$movie" | sed 's/\.\w*$/_XVID.avi/'`
		mime=`file -bi "$movie"`
		isvideo=`echo "$mime" | grep video/mpeg | wc -l`
		if [ $isvideo -eq 0 ]; then
			zenity --error --title="error" --text="$movie is not a MPG video file"
		else
			echo "# Processing MPG Video $movie ..."
			if [ "$video_out_type" = "DVD" ]; then
				dvd_encode_ntsc
			fi
			if [ "$video_out_type" = "DVD_PAL" ]; then
				dvd_encode_pal
			fi
			if [ "$video_out_type" = "SVCD_NTSC" ]; then
				svcd_encode_ntsc
			fi
			if [ "$video_out_type" = "SVCD_PAL" ]; then
				svcd_encode_pal
			fi
			if [ "$video_out_type" = "VCD_NTSC" ]; then
				vcd_encode_ntsc
			fi
			if [ "$video_out_type" = "VCD_PAL" ]; then
				vcd_encode_pal
			fi
			if [ "$video_out_type" = "XVID" ]; then
				xvid_encode
			fi
		fi	
		
		shift
	done 2>&1|
                perl -ne '$/="\r";$| = 1;if (/Duration: (\d+):(\d+):(\d+)/) { $max=($1*3600+$2*60+$3) };
                if (/time=(\d+)/) { printf "%d\n",($1/$max*100);}
                print STDERR $_;'|
	        zenity --progress --auto-close --title="Converting MPG Video Files"  --text="Converting MPG Video Files..."  --percentage=0
fi

#Input Selection was MPG Video
if [ "$video_in_type" = "MPG" ]; then
	mime=`file -bi "$*"`
	nb_video=`echo "$mime" | grep video/mpeg | wc -l`

	let "nbfiles = $nb_video"

	while [ $# -gt 0 ]; do
		movie=$1
		mpg_file=`echo "$movie" | sed 's/\.\w*$/_NTSC-DVD.mpg/'`
		avi_file=`echo "$movie" | sed 's/\.\w*$/_XVID.avi/'`
		mime=`file -bi "$movie"`
		isvideo=`echo "$mime" | grep video/mpeg | wc -l`
		if [ $isvideo -eq 0 ]; then
			zenity --error --title="error" --text="$movie is not a MPG video file"
		else
			echo "# Processing MPG Video $movie ..."
			if [ "$video_out_type" = "DVD" ]; then
				dvd_encode_ntsc
			fi
			if [ "$video_out_type" = "DVD_PAL" ]; then
				dvd_encode_pal
			fi
			if [ "$video_out_type" = "SVCD_NTSC" ]; then
				svcd_encode_ntsc
			fi
			if [ "$video_out_type" = "SVCD_PAL" ]; then
				svcd_encode_pal
			fi
			if [ "$video_out_type" = "VCD_NTSC" ]; then
				vcd_encode_ntsc
			fi
			if [ "$video_out_type" = "VCD_PAL" ]; then
				vcd_encode_pal
			fi
			if [ "$video_out_type" = "XVID" ]; then
				xvid_encode
			fi
		fi	
		
		shift
	done 2>&1|
                perl -ne '$/="\r";$| = 1;if (/Duration: (\d+):(\d+):(\d+)/) { $max=($1*3600+$2*60+$3) };
                if (/time=(\d+)/) { printf "%d\n",($1/$max*100);}
                print STDERR $_;'|
	        zenity --progress --auto-close --title="Converting MPG Video Files"  --text="Converting MPG Video Files..."  --percentage=0
fi

#Input Selection was ASF Video
if [ "$video_in_type" = "ASF" ]; then
	mime=`file -bi "$*"`
	nb_video=`echo "$mime" | grep application/octet-stream | wc -l`

	let "nbfiles = $nb_video"

	while [ $# -gt 0 ]; do
		movie=$1
		mpg_file=`echo "$movie" | sed 's/\.\w*$/_NTSC-DVD.mpg/'`
		avi_file=`echo "$movie" | sed 's/\.\w*$/_XVID.avi/'`
		mime=`file -bi "$movie"`
		isvideo=`echo "$mime" | grep application/octet-stream | wc -l`
		if [ $isvideo -eq 0 ]; then
			zenity --error --title="error" --text="$movie is not a ASF video file"
		else
			echo "# Processing ASF Video $movie ..."
			if [ "$video_out_type" = "DVD" ]; then
				dvd_encode_ntsc
			fi
			if [ "$video_out_type" = "DVD_PAL" ]; then
				dvd_encode_pal
			fi
			if [ "$video_out_type" = "SVCD_NTSC" ]; then
				svcd_encode_ntsc
			fi
			if [ "$video_out_type" = "SVCD_PAL" ]; then
				svcd_encode_pal
			fi
			if [ "$video_out_type" = "VCD_NTSC" ]; then
				vcd_encode_ntsc
			fi
			if [ "$video_out_type" = "VCD_PAL" ]; then
				vcd_encode_pal
			fi
			if [ "$video_out_type" = "XVID" ]; then
				xvid_encode
			fi
		fi	
		
		shift
	done 2>&1|
                perl -ne '$/="\r";$| = 1;if (/Duration: (\d+):(\d+):(\d+)/) { $max=($1*3600+$2*60+$3) };
                if (/time=(\d+)/) { printf "%d\n",($1/$max*100);}
                print STDERR $_;'|
	        zenity --progress --auto-close --title="Converting MPG Video Files"  --text="Converting MPG Video Files..."  --percentage=0
fi



```

---

### Post by crmanski on 2006-04-10
[QUOTE=Georges]
* the progress bars actually do some progress!

Maybe better use in next version xdialog instead of zenity, it just has much more options.
If you are ok with this, I can migrate the script over to xdialog.
[/QUOTE]

Georges,
Thanks for that progress indicator. I had no clue how to do that one. I am ok with any changes that improve the script.
crmanski

---

### Post by cyrocr on 2006-04-24
Is it possible to have an option to mux a .srt or a .sub subtitle inside the converted video?? It would be a good add on to the script.

Cyro

---

### Post by cyrocr on 2006-04-24
Here is a simply code that would add subtitles support to mpeg videos to your script if merged to it:

#!/bin/bash
dir=`pwd`
zenity --info --title="Subtitle Mixer" --text="Script to add subtitles to Mpeg 1 ou 2 videos
\n
\n
Press ok to continue"

subtitle=`zenity --entry --title="Subtitle Mixer" --text="Subtitle filename:"`

video=`zenity --entry --title="Subtitle Mixer" --text="Mpeg video filename:"`

echo "<subpictures>" > /tmp/subtitle.xml
echo "  <stream>" >> /tmp/subtitle.xml
echo "    <textsub filename=\"$dir/$subtitle\" characterset=\"ISO8859-1\"" >> /tmp/subtitle.xml
echo "         fontsize=\"20.0\" font=\"Vera.ttf\" horizontal-alignment=\"center\"" >> /tmp/subtitle.xml
echo "         vertical-alignment=\"bottom\" left-margin=\"60\" right-margin=\"60\"" >> /tmp/subtitle.xml
echo "         top-margin=\"20\" bottom-margin=\"30\" subtitle-fps=\"29.97\"" >> /tmp/subtitle.xml
echo "         movie-fps=\"29.97\" movie-width=\"720\" movie-height=\"478\"/>" >> /tmp/subtitle.xml
echo "  </stream>" >> /tmp/subtitle.xml
echo "</subpictures>" >> /tmp/subtitle.xml

spumux -s0 /tmp/subtitle.xml < $dir/$video > $dir/sub_$video

rm -f /tmp/subtitle.xml


Please note that for this script to work you have to create a .spumux directory inside your home directory and copy the Vera.ttf font to it!!

Cyro

---

### Post by Zhukov on 2006-04-28
You should add the subtitiles to the main script! Great thing! :D
Just a small question... The charset, does it support caracteres like à á and so on?

---

### Post by crmanski on 2006-04-29
Hello,
Just wanted to anyone subscribed to this thread that I updated my original post and include most of the updates I have found in this thread (thanks everyone).  I also changed the MPEG4 video conversion to use mencoder instead of ffmpeg.  It seems to create better quality video when using the 3-pass VBR option.
Thanks,
Crmanski

---

### Post by jms830 on 2006-05-02
This script is great.  One thing I would love added is quick video conversion to ipod support. Theres already a script on this page that does it, is there a way to integrate the two perhaps? When this script is run one of the radio buttons could be for ipod! Just an idea...

[http://ubuntuforums.org/showthread.php?t=114946&highlight=ipodvidenc](http://ubuntuforums.org/showthread.php?t=114946&highlight=ipodvidenc)

Edit:  Also, at the end of the post theres a fix for (video will play for 15 seconds, stop, and then continue without audio) 1.1 firmware of video ipods which could also be run on videos converted to ipod format.

---

### Post by crmanski on 2006-05-02
I am sure this is doable. It was something I had in mind.

[QUOTE=jms830]One thing I would love added is quick video conversion to ipod support. [/QUOTE]

---

### Post by crmanski on 2006-05-03
Hi art,
I am thinking about adding support for OGM, and MKV and I noticed an overlap in the file type recognition...
```
if [ "$mime" = "application/octet-stream" ]; then 
	video_in_type="MOV"
	valid_video_type="1"
fi
if [ "$mime" = "application/octet-stream" ]; then
	video_in_type="ASF"
	valid_video_type="1"
fi
```

I am looking at doing something like this instead...
```
is_mkv ()
{
	file -b "$1" | grep 'RISC OS archive' || echo $1 | grep -i '\.mkv$'
}

if (is_mkv "$1")
        then
	echo "File is a MKV"
	video_in_type="MKV"
	valid_video_type="1"
fi
```

I was wondering if you could reply back with  a copy/paste of the output of...
```
file -b *.asf

```
so I can include a better file type detection in the script.
Thanks!

[QUOTE=art2003]
B) Support for movie files in .ASF format (as this is the only format my video camera records in)
[/QUOTE]

---

### Post by art2003 on 2006-05-05
I am afraid the output is: application/octet-stream

I am afraid several mime formats my be identified like this.

My approach was to ask the user to select the correct format in this case

Please select what type of file this is:
   * ASF
   * MOV
   * Other

---

### Post by crmanski on 2006-05-05
That is fine.  I will finish up the code that I mentioned above tonight so that the script will figure it out without having to ask the user which one it is.

---

### Post by f76 on 2006-05-20
wow! how is this going? this will be incredible if it includes support for even more formats! thx, now i have to try it!

---

### Post by mbeach on 2006-05-26
hi - fantastic script.  I had some mov files from a Kodak CX4300 which I could only convert if I replaced "application/octet-stream" with "video/quicktime" in three places in the relevant "mov" sections.  The first was the check in is_mov function and the others were in the if video_in_type if statement; specifically the nb_video and isvideo variables has the mime type mentioned.  I suspect its something the way Kodak is doing things or the way Dapper is recognizing the mov filetype.  I'm happy, it's converting for me - thank you.

---

### Post by crmanski on 2006-06-10
Hi mbeach,
I updated my original post with some code cleanup and a simpler .mov file type recognition. Since it seems to vary between different cameras, I made it just check that the extension is .mov.  I also removed the redundant code in the bottom half of the script (f video_in_type if statement, nb_video, etc).  Those parts where needed during the original script.  
Thanks

---

### Post by art2003 on 2006-06-11
hello
Doesn't seem to be working to convert .mpg to .avi (divx4 or xvid)

The progress box shows just for less than a second and then exits without any error messages.

Perhaps it is because I don't seem to have mencoder installed. doesn't seem to come with Dapper repositories, will try to find it.

Spent 2 hours and can't find anyway to install mencoder, mplayer is installed but without mcoder, found tens of gui's for mencoder, documentation, but no way to just download it and install it. anybody can post a link or instructions on how to get mencoder on dapper?

ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
Input #0, mpeg, from 'magic_roundabout.mpg':
  Duration: 01:59:57.8, start: 25338.624189, bitrate: 3011 kb/s
  Stream #0.0[0x1c0]: Audio: mp2, 48000 Hz, stereo, 192 kb/s
  Stream #0.1[0x1ea]: Video: mpeg2video, yuv420p, 544x576, 25.00 fps, 10000 kb/s Unknown codec 'aac'

---

### Post by crmanski on 2006-06-12
mencoder is required to convert to avi.

I just looked at [http://packages.ubuntulinux.org/dapper/allpackages](http://packages.ubuntulinux.org/dapper/allpackages)

> mencoder (2:0.99+1.0pre7try2+cvs20060117-0ubuntu8) [multiverse]
    MPlayer's Movie Encoder

Do you have the multiverse repositories enabled?

---

### Post by art2003 on 2006-06-14
yes I have mencoder installed and universe and multiverse repositories.

I believe the problem happens because the mplayer found in the ubuntu repositories has no mp2 or xvid support built-in (whereas in breezy times it used to have)

it seems impossible to find a proper mplayer.deb to download (or a repository with it) with xvid and mp2/mp3 support.

---

### Post by crmanski on 2006-06-14
[QUOTE=art2003]yes I have mencoder installed and universe and multiverse repositories.

I believe the problem happens because the mplayer found in the ubuntu repositories has no mp2 or xvid support built-in (whereas in breezy times it used to have)

it seems impossible to find a proper mplayer.deb to download (or a repository with it) with xvid and mp2/mp3 support.[/QUOTE]

The mencoder/mplayer in ubuntu reads xvid fine on mine(I also have w32codecs installed). These packages will not encode in xvid, but they should decode fine. This script does not output XVID, only MPEG4, so it should not be a problem producing the output file...

---

### Post by crmanski on 2006-06-14
> Unknown codec 'aac'

That is the problem. ffmpeg will not read aac audio in files. You would need to recompile ffmpeg with aac support. The iPod convertor script thread has instructions on this...
[http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946)

---

### Post by tomplast on 2006-07-30
It would be nice if the script could detect the resolution of the source file and preselect that resolution for the destination file :)

---

### Post by starscalling on 2006-08-18
mm
so 
once its in mpeg format what now?

---

### Post by ubuntu27 on 2006-08-18
> **starscalling said:**
> mm
so 
once its in mpeg format what now?

Then you burn it with your favorite app such as k3b. ;)

---

### Post by Medaluk on 2006-08-19
Hello

Iam new to all this script writing etc, i have done as you have said at the begining of your post and i can write click and select script, but nothing happens:( , please can you help me get things right. cheers and thanks for taking the time to write the script in the first place.


Medaluk

---

### Post by crmanski on 2006-08-20
> **Medaluk said:**
> Hello

Iam new to all this script writing etc, i have done as you have said at the begining of your post and i can write click and select script, but nothing happens:( , please can you help me get things right. cheers and thanks for taking the time to write the script in the first place.


Medaluk

Hi,
This is the old thread. Did you try the newer version?
[http://www.ubuntuforums.org/showthread.php?t=193754](http://www.ubuntuforums.org/showthread.php?t=193754)

---

### Post by ozp on 2007-01-04
I could not convert .VOB files from a DVD ISO mounted
Can it convert to xvid? 

Can it convert avi to SVCD or DVD with subtitles?

regards

---

### Post by ozp on 2007-01-04
I was able to start the process with a .avi located in a Cdrom
but nothing happend (I wonder if it try to overrite the same file with the new one)
I copied to my HD and now it cannot process the same file

says I have not selected a valid video type

---

### Post by dannyboy79 on 2007-01-04
have you installed all the programs and codec's that all ththreads mention? (win32codecs, ffmpeg, mencoder, etc etc)? 

also, this program will only convert to vcd, svcd or dvd, he states that in the very first post so you can't convert a vob file to anything else since it's already in the dvd structure and you can't convert to a xvid, you could use devede for that or avidemux I think.

---

### Post by dannyboy79 on 2007-01-04
> **Medaluk said:**
> Hello

Iam new to all this script writing etc, i have done as you have said at the begining of your post and i can write click and select script, but nothing happens:( , please can you help me get things right. cheers and thanks for taking the time to write the script in the first place.


Medaluk
did you make the script executable?
sudo chmod +x /locationofscript/locationofscript/scriptnamehere

---

### Post by ozp on 2007-01-04
> **dannyboy79 said:**
> have you installed all the programs and codec's that all ththreads mention? (win32codecs, ffmpeg, mencoder, etc etc)? 

also, this program will only convert to vcd, svcd or dvd, he states that in the very first post so you can't convert a vob file to anything else since it's already in the dvd structure and you can't convert to a xvid, you could use devede for that or avidemux I think.

I think I have installed everthing that is required (Ive installed just about all the convert/enconde stuff that is out there)

the question is why the same file on the CD goes ok, but on the HD it cannot be processed

My main demands are:
clone DVDs (I use to do with dvdshrink on windows)
convert AVI with SRT to SVCD with subtitles (to see the avi on a DVD that cant display sub titles)

---

### Post by trippinnik on 2007-02-13
Wow, cool script.  I was trying to get devede and qdvdauthor, but they kept failing to complete.  Then i remembered i had the audio convert script so a video one should be easy too.  this is basically why i can't go mac, no right click.. ctrl click doesn't cut it.  

As to the above post about cloning DVDs, try dvd::rip or acid rip.  those should put the dvd on the pc and then you can convert it to whatever you like.  I dunno really anything about that second part though.  Do you have a DVD burner?

---

### Post by kaede on 2007-05-03
are this script works on feisty too?

---

### Post by crmanski on 2007-05-03
It might, I have not updated the machine I use this on to Feisty. I am running mythtv and decided to stick with dapper to have the LTS. It should, give it a shot...

---

### Post by hawk88 on 2007-05-03
Yes it works with feisty, at least it works for me :) 

I want to ask you if you could add 3gp support, i know that ffmpeg supports that. Al the movies I make with my cellphone are 3gp but to upload it to my site the have to be flv. Currently im first using a script to convert them to .avi and afther I'm using your script to convert them to .flv. So it would be great if you could add 3gp support to it

---

### Post by vishna on 2007-07-05
Being an owner of PSP, I made a few handy modifications to the original script 

```
encode_psp ()
{
	qscale_param=$(zenity --scale --text "Chose quality 1 (best) - 31 (worst)" --min-value=1 --max-value=31 --value=5 --step 1);
	ffmpeg -i "$movie" -f psp -qscale $qscale_param -ar 24000 -ab 64 -s 320x240 "$movie"_M4V00001.MP4
	ffmpeg -y -i "$movie" -f image2 -ss 5 -vframes 1 -s 160x120 -an "$movie"_M4V00001.THM
	mkdir "$movie"_100MNV01
	mv "$movie"_M4V00001.MP4 "$movie"_100MNV01
	mv "$movie"_M4V00001.THM "$movie"_100MNV01
}
```

Well... the perfect script would detect if PSP is connected and then automatically copied necessary files and named them properly, checked if there is enough space etc. - this can be done but I'm too lazy so i added these M4V00001 suffixes so that I knew what the psp naming syntax looks like :P .THM is for a thumbinal.

If you seem to be unable to get ffmpeg and psp working consider this link
[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/)

:popcorn:

---

### Post by NikoK on 2007-08-05
so I exectuted the script, and it goes through the four options, but then I dont see any progress screen or anything, so I dont really know if its just converting it into another folder unknowingly or something is wrong, :S

---

### Post by bhohe on 2007-08-05
really nice would be an option to convert to 3gp for symbian mobile phones like the nokia n73 and others :)

---

### Post by biomedtech on 2007-09-04
i answered my own question, can't figure out how to delete this thing

---

### Post by dysonsphere23 on 2007-09-07
Sorry if this is a real noob question:

How can I get the mpeg file (converted from avi) to be small enough to fit on a cd to burn in K3b?  I have an avi file that is 698MB it converts to 1.1G when the script is run to make vcd.  

Thanks

---

### Post by mattdee on 2007-11-16
I'm hoping to get some help with this...

The script worked GREAT with Edgy and Fawn but ever since I upgraded to Gutsy, it craps out on me...

Here's what I do...
Right click the file and choose scripts 'video-convert', I run through the options (ie DVD, screen size, etc...)
It starts to convert and then bam...nothing...I'm left with an empty mpg file...

This only happens when I choose DVD...anyone have any ideas...?

Cheers,
Matt

---

### Post by crmanski on 2007-11-22
Try changing the top line to read this...
#!/bin/bash
instead of 
#!/bin/sh

---

### Post by havchr on 2007-12-04
excellent script!
Very usefull. :)

---

### Post by RedNikon on 2007-12-21
Any chance of getting mkv support?

---

### Post by fly3rman on 2007-12-23
Wow tried it so far, it works (tried some quicktime->* covertion)
Will try more later. Just wanted to say: Bit thanks and good work.

---

### Post by crmanski on 2008-01-10
> **mattdee said:**
> I'm hoping to get some help with this...

The script worked GREAT with Edgy and Fawn but ever since I upgraded to Gutsy, it craps out on me...


Matt,
The latest version that I am using on Gutsy is now in the original post.
Craig

---

### Post by crmanski on 2008-01-10
> **RedNikon said:**
> Any chance of getting mkv support?

There is MKV support in the "beta"  version. MKV's with h264/acc in them can be troublesome though. Usually the Audio/Video are out of sync.

---

### Post by nicolasdiogo on 2008-01-28
hI,

THANKS for the script.
but i am not able to convert existing mpg files into any other format as it does not recognise these formats.

is there any other library that should install to make it possible?
error message is:

You have not selected a valid Video Type. MimeType= video/mpeg

many thanks

---

### Post by QwUo173Hy on 2008-02-07
I have a similar problem in Gutsy where trying to use the script on a VOB file gives me the error;

You have not selected a valid Video Type. MimeType= video/mp2p. This happens with both scripts.

Thanks

---

### Post by gary4gar on 2008-03-18
Very nice idea, please do not let it die.
Please improve it a bit more

---

### Post by mocha on 2008-03-19
I love this script but I was wondering how folks deal with the resolution problem that it seems to have when encoding mpeg2 DVD files?  For example, if you have a file that has an aspect ratio like 1.85:1 and you want to convert it to a 4:3 DVD format, you have to go into the script and add an entry to the resolution choices otherwise the script produces files with screwed up aspect ratios.

I searched this thread and there doesn't seem to be anyone else posing this issue.  Is this not a problem for anyone else?

---

### Post by milan_cortana on 2008-07-06
hi all.
j installed video converter as it was told.
then right clik on video and j choose asf to avi etc.
text log came out in folder of my video saying that
progress is on.
but j want to se progress in terminal 
or any other way.
can anyone help.
thanks

---

### Post by cariboo on 2008-07-06
milan_cortana, I just ran the video convertor in a terminal, it did as advertised, it a good thing I use a transparent terminal or I won't have seen the other windows that popped up. There was a window asking what I'd like to convert my file to and then one for resolution, and finally a window with a progress bar showing the progress of the process. For some reason all the windows are popping up under existing windows.

Jim

---

### Post by jrz on 2009-04-20
You've probably already resolved your problem, but just in case I thought I'd mention that acidrip does a very good job of creating an AVI from a DVD or VOB files in a directory.

---

