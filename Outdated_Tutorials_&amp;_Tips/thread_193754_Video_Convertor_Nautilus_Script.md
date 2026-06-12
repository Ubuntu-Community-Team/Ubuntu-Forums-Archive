---
title: "Video Convertor Nautilus Script"
date: 2006-06-10
forum: Outdated Tutorials &amp; Tips
---

### Post by crmanski on 2006-06-10
This is a Nautilus Script that I have been working on since Hoary and I thought that I would post something in the current release How-To forum. 
(The current OS(Gutsy) thread is here: [http://ubuntuforums.org/showthread.php?t=62625](http://ubuntuforums.org/showthread.php?t=62625)) 

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

An enhanced ffmpeg with xvid and aac support can be downloaded here...
[http://skulboxx.com/Ubuntu/sbx/](http://skulboxx.com/Ubuntu/sbx/)

---

### Post by chanders on 2006-06-10
Absolutely wonderful! Have been looking for something like this for a very long time...

Suggestion: Allow users to create and save custom settings... 

Again great work!

---

### Post by crmanski on 2006-06-12
That is an interesting suggestion. What types of settings would you want to create/save? I usually just edit the script and add the settings that I need, especially for the DVD encoding settings and recently as I was learning a bit about mencoder.

---

### Post by homersbrain on 2006-06-12
This is superb - worked first time! Could a progress bar possibly be implemented too? Great work!

---

### Post by crmanski on 2006-06-12
[QUOTE=homersbrain]This is superb - worked first time! Could a progress bar possibly be implemented too? Great work![/QUOTE]

This is still something that isn't working correctly.  In the old thread someone had a bit of perl that worked for the first video but not the rest. I just don't have the brains to figure it out :confused: 
If someone else more skilled were to figure it out that would be great.

---

### Post by Kung Fu Hamster on 2006-06-12
What about adding support to convert .WMV files as well?

---

### Post by art2003 on 2006-06-13
This is the script I use to convert (from terminal) all *.mpg files to .avi (xvid)
```

#!/bin/bash

for f in $(ls ./ |grep  .mpg |grep -v .avi ) ; do
xv=`echo "$f" | sed 's/\.\w*$/.avi/'` ;
ffmpeg -i $f -f avi -vcodec xvid -b 800 -g 300 -bf 2 -acodec mp2 -ab 128 $xv ;
echo $f converted to $xv ;
rm $f ;
done
```

This works for me where the script on this thread doesn't. (after selecting convert to xvid it opens the progress bar for a fraction of a second and exits)

---

### Post by crmanski on 2006-06-13
> **art2003]This is the script I use to convert (from terminal) all *.mpg files to .avi (xvid)
```

ffmpeg -i $f -f avi -vcodec xvid -b 800 -g 300 -bf 2 -acodec mp2 -ab 128 $xv  said:**
> 

That ffmpeg line will not work with the standard ffmpeg from the ubuntu repositories.  ffmpeg was only compiled with these options on my dapper install...
[QUOTE]--extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable -libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgs m --disable-debug --prefix=/usr

Did you possibly recompile it as describe in the [iPod Video convertor How-To]("http://ubuntuforums.org/showthread.php?t=114946")?
This Script has 4 options: DVD, MPEG4, SVCD and VCD. If you choose MPEG4 and you do not have mencoder installed it will fail.

If that is not the case then please try from a terminal...```

~/.gnome2/nautilus-scripts/video-convert /path/to/one/of/your/movies.mpg
```
...and post the errors.

---

### Post by OrganicPanda on 2006-06-13
wow this is amazing but it didnt work, at least i dont think it did ... a progress bar showed up for about a second and i see no outputted file, do i assume it failed?

please help , i NEED an app like this

---

### Post by art2003 on 2006-06-14
I had the same problem and fixed it now (at least for me)
Here is my revised script (tested only converting .MPG to .AVI (xvid)
```
#!/bin/bash
#
#Todo:
# -Creating a Macromedia Flash video suitable for playback in a web browser with the Macromedia Flash # #plugin: mencoder input.avi -o output.flv -of lavf -oac mp3lame -lameopts abr:br=56 -ovc lavc -lavcopts #vcodec=flv:vbitrate=500:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -srate 22050
# -MKV/OGM conversion to MPG.
# -Subtitles
# Change log...
# 10/June/2006 - crmanski
# - Changed the way .MOV files are detected. AKA... Simplfied it.
# - Code cleanup. Removed the duplicate mime type checking in the while loops, since it is now done in the file type functions.
# 6/May/2006 - crmanski
# - Changed the File type detection to work better with file types that return the same info.
# - Removed the perl code for progress and used --pulsate since it was only showing progress for the first file.
# - Fixed some typos and added some other little things.
# 29/April/2006 - crmanski
# - Changed the XVID option name to MPEG4 and after some quality checking decided to go with mencoder instead of FFMPEG.
# If mencoder was compiled with XVID or H264 support in the Ubuntu binary I would include specific options for those too.
# 9/April/2006 - Last Updated: 9/April/2006
# video-convert including to xvid.01.2
# based on:
# crmanski / http://szone.berlinwall.org
# Requirements: zenity (Comes with gnome 2.4), ffmpeg (apt-get ffmpeg), mencoder-586/mplayer-586
# This script will take multiple video files of the same type (right now: MPG, AVI, MOV) 
# and covert them into either NTSC - dvd, svcd or vcd compliant MPEG files by using
# ffmpeg (http://ffmpeg.sourceforge.net) 
# To make sure all this is installed do this at a terminal...
# (Universe Repositories should be enabled first -https://wiki.ubuntu.com/AddingRepositoriesHowto)
# sudo apt-get install ffmpeg mencoder-586 mplayer-586
### ADDED by Arturo Martinez
### OPTION TO CONVERT TO MPEG4 (.avi) 
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

#Check for AVI
is_avi ()
{
file -i "$1" | grep 'video/x-msvideo' && echo $1 | grep -i '\.avi$'
}

if (is_avi "$1")
        then
echo "File is an AVI"
video_in_type="AVI"
valid_video_type="1"

fi
#Check for QuickTime MOV
is_mov ()
{
# Simplified this below since there are different things that that file command finds depending in different cameras
echo $1 | grep -i '\.mov$'
}

if (is_mov "$1")
        then
echo "File is a MOV"
video_in_type="MOV"
valid_video_type="1"

fi
#Check for MPG
is_mpg ()
{
file -b "$1" | grep 'MPEG' && echo $1 | grep -i '\.mpg$'
}

if (is_mpg "$1")
        then
echo "File is a MPG"
video_in_type="MPG"
valid_video_type="1"

fi
#Check For ASF
is_asf ()
{
file -bi "$1" | grep 'application/octet-stream' && echo $1 | grep -i '\.asf$'
}

if (is_asf "$1")
        then
echo "File is an ASF"
video_in_type="ASF"
valid_video_type="1"

fi
#Check For MKV
is_mkv ()
{
file -b "$1" | grep 'RISC' && echo $1 | grep -i '\.mkv$'
}

if (is_mkv "$1")
        then
echo "File is a MKV"
video_in_type="MKV"
valid_video_type="1"

fi
#Check For VOB
is_vob ()
{
file -bi "$1" | grep 'video/mpeg' && echo $1 | grep -i '\.vob$'
}

if (is_vob "$1")
        then
echo "File is a VOB"
video_in_type="MPG"
valid_video_type="1"

fi


#Checking...
if [ $valid_video_type -eq "1" ]; then
valid_video_type="1"
else
zenity --error --title="Error" --text="You have not selected a valid Video Type. MimeType= $mime"
exit
fi

#Output - What kind?
#echo "This Script converts selected AVI, MOVE or MPG files to NTSC-DVD, SVCD or VCD compliant MPG files with ffmpeg"
title="What kind of Video Do you want to convert those $video_in_type files to?"
video_out_type=`zenity  --width="480" --height="380" --title="$title" --list --radiolist --column="" \
--column="Video Type" --column="Description" \
TRUE "XVID" "XVID"\
FALSE "DVD" "DVD compliant Video MPEG Stream"\
FALSE "MPEG4" "Create an AVI with MPEG4 video"\
FALSE "SVCD" "Create a NTSC/PAL SVCD"\
FALSE "VCD" "Create a NTSC/PAL VCD"\
| sed 's/ max//g' `

#user must select a target size (Check if they canceled)
if [ ! "$video_out_type" ]; then
zenity --error --title="Error" --text="You must select a Input Type"
exit
fi

# If we are making DVD there are a few options...
if [ "$video_out_type" = "DVD" ]; then
#What Size?
title="Choose which resolution the video files should be..."
dvd_res=`zenity --width="480" --height="380" --title="$title" --text="Input format: $humantype" --list --radiolist --column="" --column="Choose Video Resolution" --column "description" \
TRUE "ntsc-dvd -s 720x480" "Standard NTSC"\
FALSE "ntsc-dvd -s 720x400 -padtop 40 -padbottom 40" "Standard NTSC - Widescreen" \
FALSE "ntsc-dvd -s 704x480" "" \
FALSE "ntsc-dvd -s 704x396 -padtop 42 -padbottom 42" "Standard NTSC - Widescreen" \
FALSE "ntsc-dvd -s 352x480" "4:3 half ntsc" \
FALSE "ntsc-dvd -s 352x474 -padbottom 6" "4:3 half NTSC, with a little off the bottom" \
FALSE "ntsc-dvd -s 352x240" "4:3 vcd size" \
FALSE "ntsc-dvd -s 352x196 -padtop 22 -padbottom 22" "VCD widescreen" \
FALSE "ntsc-dvd -s 352x192 -padtop 24 -padbottom 24" "VCD widescreen" \
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
FALSE "224" \
FALSE "160" \
TRUE "128" | sed 's/ max//g' `
#user must select an audio bitrate
if [ ! "$audio_br" ]; then
zenity --error --title="Error" --text="You must select an Audio bitrate."
exit
fi
title="Choose the audio stream type your video files should have..."
audio_str=`zenity  --width="480" --height="380" --title="$title" --list --radiolist --column="" --column="Choose Audio Stream Type" TRUE "ac3" FALSE "mp2" | sed 's/ max//g' `
#user must select an audio bitrate
if [ ! "$audio_str" ]; then
zenity --error --title="Error" --text="You must select an Audio stream type."
exit
fi
fi

#XVID Options
#This is still in planning...
#Will require recompiling mencoder to support xvid.
if [ "$video_out_type" = "XVID" ]; then
title="How high should the XVID quality be?"
mpeg4_quality=`zenity  --width="480" --height="380" --title="$title" --list --radiolist --column="" \
--column="Choose Quality of Encoding..." --column="Description" \
FALSE "Very_High_Quality" "Best Quality, Long time to encode, about 6fps"\
FALSE "High_Quality" "High Quality, about 15fps"\
FALSE "Fast_Encode" "Really fast, not as good quality"\
TRUE "Three_Pass" "3 Pass VBR Encode, MP3 VBR audio, Excellent Quality"\
| sed 's/ max//g' `

fi

#MPEG4 Options
# The first three options are from http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#mencoder
# The 3 pass (My Favorite) is from here (http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#mencoder) and a few other places.
if [ "$video_out_type" = "MPEG4" ]; then
title="How high should the MPEG4 quality be?"
mpeg4_quality=`zenity  --width="480" --height="380" --title="$title" --list --radiolist --column="" \
--column="Choose Quality of Encoding..." --column="Description" \
FALSE "Very_High_Quality" "Best Quality, Long time to encode, about 6fps"\
FALSE "High_Quality" "High Quality, about 15fps"\
FALSE "Fast_Encode" "Really fast, not as good quality"\
TRUE "Three_Pass" "3 Pass Encode, MP3 VBR audio, Excellent Quality"\
| sed 's/ max//g' `
echo "mpeg4_quality: $mpeg4_quality"
title="What Resolution should the video be?"
mpeg4_resolution=`zenity  --width="480" --height="380" --title="$title" --list --radiolist --column="" \
--column="Choose Video Resolution..." --column="Description" \
FALSE "720:480" "NTSC DVD size, 720x480"\
FALSE "720:576" "PAL DVD 720x576"\
TRUE "640:480" "Standard TV size, 640x480"\
FALSE "352:576" "352x576 4:3 half pal"\
FALSE "352:240" "NTSC VCD, 352x240"\
FALSE "320:240" "NTSC VCD, 320x240"\
FALSE "352:288" "PAL VCD,352x288"\
| sed 's/ max//g' `
title="Choose the Video bitrate your MPEG4 files should have..."
mpeg4_vid_br=`zenity  --width="480" --height="380" --title="$title" --list --radiolist --column="" \
--column="Choose Audio Bitrate" \
FALSE "1500" \
FALSE "1300" \
FALSE "1100" \
TRUE "900" \
FALSE "700" \
FALSE "500" | sed 's/ max//g' `
#user must select a Video bitrate
if [ ! "$mpeg4_vid_br" ]; then
zenity --error --title="Error" --text="You must select an Video bitrate. Using the default 900 instead."
mpeg4_vid_br="900"
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
echo "Choose VCD Type"
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
mpeg4_encode ()
{
rm frameno.avi
rm divx2pass.log
if [ "$mpeg4_quality" = "Three_Pass" ]; then
echo "# Converting $movie to MPEG4 \n with 3 pass encode... \n Pass 1 of 3..." 
mencoder "$movie" -ovc frameno -oac mp3lame -lameopts vbr=3 -o frameno.avi
echo "# Converting $movie to MPEG4 \n with 3 pass encode... \n Pass 2 of 3..." 
mencoder "$movie" -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=1:vbitrate=$mpeg4_vid_br -vop scale=$mpeg4_resolution -o "$mpeg4_file"
echo "# Converting $movie to MPEG4 \n with 3 pass encode... \n Pass 3 of 3..." 
mencoder "$movie" -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=2:vbitrate=$mpeg4_vid_br -vop scale=$mpeg4_resolution -o "$mpeg4_file"
fi
if [ "$mpeg4_quality" = "Very_High_Quality" ]; then
echo "# Converting $movie to MPEG4 \n Using $mpeg4_quality setting..."
mencoder "$movie" -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=$mpeg4_vid_br:mbd=2:mv0:trell:v4mv:cbp:last_pred=3:predia=2:dia=2:vmax_b_frames=2:vb_strategy=1:precmp=2:cmp=2:subcmp=2:preme=2:qns=2 -vop scale=$mpeg4_resolution -oac mp3lame -lameopts vbr=3 -o "$mpeg4_file"
fi
if [ "$mpeg4_quality" = "High_Quality" ]; then
echo "# Converting $movie to MPEG4 \n Using $mpeg4_quality setting..."
mencoder "$movie" -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=$mpeg4_vid_br:mbd=2:trell:v4mv:last_pred=2:dia=-1:vmax_b_frames=2:vb_strategy=1:cmp=3:subcmp=3:precmp=0:vqcomp=0.6:turbo -vop scale=$mpeg4_resolution -oac mp3lame -lameopts vbr=3 -o "$mpeg4_file"
fi
if [ "$mpeg4_quality" = "Fast_Encode" ]; then
echo "# Converting $movie to MPEG4 \n Using $mpeg4_quality setting..."
mencoder "$movie" -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=$mpeg4_vid_br:mbd=2:trell:v4mv:turbo -vop scale=$mpeg4_resolution -oac mp3lame -lameopts vbr=3 -o "$mpeg4_file"
fi
}
xvid_encode ()
{
 #       /usr/bin/ffmpeg -i "$movie" -f mp4 -s 640x480 -aspect 4:3 -vcodec mpeg4 -b 900 -g 300 -bf 2 -#acodec aac -ab 128 -y "$mpeg4_file".mp4
#/usr/bin/ffmpeg -i "$movie" -f mp4 -s 640x480 -aspect 4:3 -vcodec mpeg4 -b 900 -g 300 -bf 2 -acodec mp2 #-ab 128 -y "$mpeg4_file".mp4
xvid=`echo "$movie" | sed 's/\.\w*$/.avi/'`

ffmpeg -i "$movie" -f avi -vcodec xvid -b 800 -g 300 -bf 2 -acodec mp2 -ab 128 $xvid

}
#Input Selection was AVI Video
if [ "$video_in_type" = "AVI" ]; then
Video_Count=1

while [ $# -gt 0 ]; do
movie=$1
mpg_file=`echo "$movie" | sed 's/\.\w*$/.mpg/'`
mpeg4_file=`echo "$movie" | sed 's/\.\w*$/_MPEG4.avi/'`
xvid_file=`echo "$movie" | sed 's/\.\w*$/_XVID.avi/'`
echo "# Processing AVI Video $movie \n Total: $Video_Count"
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
if [ "$video_out_type" = "MPEG4" ]; then
mpeg4_encode
fi
                        if [ "$video_out_type" = "XVID" ]; then
                                xvid_encode
                        fi
let Video_Count=Video_Count+1
shift
done |
 zenity --progress --pulsate --auto-close --title="Converting AVI Video Files"  --text="Converting AVI Video Files..."  --percentage=0
fi

#Input Selection was Quicktime Video
if [ "$video_in_type" = "MOV" ]; then
Video_Count=1

while [ $# -gt 0 ]; do
movie=$1
mpg_file=`echo "$movie" | sed 's/\.\w*$/.mpg/'`
mpeg4_file=`echo "$movie" | sed 's/\.\w*$/_MPEG4.avi/'`
xvid_file=`echo "$movie" | sed 's/\.\w*$/_XVID.avi/'`
echo "# Processing Quicktime Video $movie \n Total: $Video_Count"
echo "Movie: $movie"
echo "mpg_file: $mpg_file"
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
if [ "$video_out_type" = "MPEG4" ]; then
mpeg4_encode
fi
                        if [ "$video_out_type" = "XVID" ]; then
                                xvid_encode
                        fi
let Video_Count=Video_Count+1
shift
done |
        zenity --progress --pulsate --auto-close --title="Converting Quicktime Video Files"  --text="Converting Quicktime Video Files..."  --percentage=0

fi

#Input Selection was MPG Video
if [ "$video_in_type" = "MPG" ]; then
Video_Count=1
while [ $# -gt 0 ]; do
movie=$1
mpg_file=`echo "$movie" | sed 's/\.\w*$/_NTSC-DVD.mpg/'`
mpeg4_file=`echo "$movie" | sed 's/\.\w*$/_MPEG4.avi/'`
xvid_file=`echo "$movie" | sed 's/\.\w*$/_XVID.avi/'`
echo "# Processing MPG Video $movie \n Total: $Video_Count"
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
if [ "$video_out_type" = "MPEG4" ]; then
mpeg4_encode
fi
                        if [ "$video_out_type" = "XVID" ]; then
                                xvid_encode
                        fi
let Video_Count=Video_Count+1
shift
done|
        zenity --progress --pulsate --auto-close --title="Converting MPG Video Files"  --text="Converting MPG Video Files..."  --percentage=0
fi

#Input Selection was ASF Video
if [ "$video_in_type" = "ASF" ]; then
Video_Count=1

while [ $# -gt 0 ]; do
movie=$1
mpg_file=`echo "$movie" | sed 's/\.\w*$/_NTSC-DVD.mpg/'`
mpeg4_file=`echo "$movie" | sed 's/\.\w*$/_MPEG4.avi/'`
xvid_file=`echo "$movie" | sed 's/\.\w*$/_XVID.avi/'`
echo "# Processing ASF Video $movie \n Total: $Video_Count"
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
if [ "$video_out_type" = "MPEG4" ]; then
mpeg4_encode
fi
                        if [ "$video_out_type" = "XVID" ]; then
                                xvid_encode
                        fi
let Video_Count=Video_Count+1
shift
done |
        zenity --progress --pulsate --auto-close --title="Converting ASF Video Files"  --text="Converting ASF Video Files..."  --percentage=0
fi

```

Now, for this to work you need to have installed codecs as per automatrix AND got hold of a version of ffmpeg compiled with xvid support (not the dapper one)

this is the output of ffmpeg -formats   in my system:
```
File formats:
  E 3g2             3gp2 format
  E 3gp             3gp format
 D  4xm             4X Technologies format
 D  RoQ             Id RoQ format
 DE ac3             raw ac3
 DE alaw            pcm A law format
 DE amr             3gpp amr file format
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE audio_device    audio grab and output
 DE avi             avi format
  E crc             crc testing format
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  ea              Electronic Arts Multimedia Format
 DE ffm             ffm format
 D  film_cpk        Sega FILM/CPK format
 D  flic            FLI/FLC animation format
 DE flv             flv format
 DE gif             GIF Animation
 DE h261            raw h261
 DE h263            raw h263
 DE h264            raw H264 video format
 D  idcin           Id CIN format
 DE image           image sequence
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 DE imagepipe       piped image sequence
 D  ipmovie         Interplay MVE format
 DE m4v             raw MPEG4 video format
 D  matroska        Matroska file format
 DE mjpeg           MJPEG video
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2 QuickTime/MPEG4 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             mp4 format
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  nsv             NullSoft Video format
  E null            null video format
 DE nut             nut format
 DE ogg             Ogg Vorbis
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 DE rawvideo        raw video format
 D  redir           Redirector format
 DE rm              rm format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           pcm signed 16 bit big endian format
 DE s16le           pcm signed 16 bit little endian format
 DE s8              pcm signed 8 bit format
 D  sdp             SDP
 D  shn             raw shn
  E singlejpeg      single JPEG image
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
  E vcd             MPEG1 System format (VCD)
 D  video4linux     video grab
 D  vmd             Sierra VMD format
  E vob             MPEG2 PS format (VOB)
 DE wav             wav format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 DE yuv4mpegpipe    YUV4MPEG pipe format

Image formats (filename extensions, if any, follow):
 DE gif    gif

Codecs:
 D V    4xm
 D V D  8bps
 DEA    aac
 D V D  aasc
  EA    ac3
 DEA    adpcm_4xm
 DEA    adpcm_adx
 DEA    adpcm_ct
 DEA    adpcm_ea
 DEA    adpcm_ima_dk3
 DEA    adpcm_ima_dk4
 DEA    adpcm_ima_qt
 DEA    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 DEA    adpcm_ima_ws
 DEA    adpcm_ms
 DEA    adpcm_swf
 DEA    adpcm_xa
 D A    alac
 DEA    amr_nb
 DEA    amr_wb
 DEV D  asv1
 DEV D  asv2
 D V D  camtasia
 D V D  cinepak
 D V D  cljr
 D V D  cyuv
 D A    dts
 DEV D  dvvideo
 DEV D  ffv1
 DEVSD  ffvhuff
 D A    flac
 D V D  flic
 DEVSD  flv
 DEA    g726
 DEV D  h261
 DEVSDT h263
 D VSD  h263i
  EV    h263p
 DEV DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
  EV    ljpeg
 D V D  loco
 D A    mace3
 D A    mace6
 D V D  mdec
 DEV D  mjpeg
 D V D  mjpegb
 DEA    mp2
 DEA    mp3
 D A    mp3adu
 D A    mp3on4
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D A    mpeg4aac
 D VSDT mpegvideo
 DEVSD  msmpeg4
 DEVSD  msmpeg4v1
 DEVSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 DEA    pcm_s8
 DEA    pcm_u16be
 DEA    pcm_u16le
 DEA    pcm_u8
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D V D  qdraw
 D V D  qpeg
 D V D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 D A    roq_dpcm
 D V D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 D A    shorten
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 DEV D  svq1
 D VSD  svq3
 D V    theora
 D V D  truemotion1
 D V D  ultimotion
 D V    vc9
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V D  vqavideo
 D A    wmav1
 D A    wmav2
 DEVSD  wmv1
 DEVSD  wmv2
 D V    wmv3
 D V D  wnv1
 D A    ws_snd1
 D A    xan_dpcm
 D V D  xan_wc3
 D V D  xl
  EV    xvid
 DEV D  zlib

Supported file protocols:
 file: pipe: udp: rtp: tcp: http:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif
Motion estimation methods:
 zero(fastest) full(slowest) log phods epzs(default) x1

Note, the names of encoders and decoders dont always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported for example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats its even
worse
 
```

If your ffmpeg doesn't show   EV    xvid
then I don't see how ffmpeg is going to create xvid files for you.

---

### Post by art2003 on 2006-06-14
mencoder is installed in my system and it is the default dapper version

I tried to recompile ffmpeg as described in the thread you mention but somehow it was not compiling, it was giving permanent errors on XVID and when I disabled XVID on something else. both with gcc-3.4 and gcc-4.0 so in the end a dirty trick was to copy ffmpeg (the binary) from my old breezy backup (that's goodness for backups)
then run it, it complained of a couple of missing libraries, copyed them over as well and working fine now (I know it is not very elegant but unable to compile my own ffmpeg and spending hours trying to find a ffmpeg.deb package compiled with xvid and mp2/mp3 support it did the trick.
I did the same for mplayer as it wasn't playing most files I had around.

[QUOTE=crmanski]That ffmpeg line will not work with the standard ffmpeg from the ubuntu repositories.  ffmpeg was only compiled with these options on my dapper install...

Did you possibly recompile it as describe in the [iPod Video convertor How-To]("http://ubuntuforums.org/showthread.php?t=114946")?
This Script has 4 options: DVD, MPEG4, SVCD and VCD. If you choose MPEG4 and you do not have mencoder installed it will fail.

If that is not the case then please try from a terminal...```

~/.gnome2/nautilus-scripts/video-convert /path/to/one/of/your/movies.mpg
```
...and post the errors.[/QUOTE]

---

### Post by chanders on 2006-06-14
[QUOTE=art2003]mencoder is installed in my system and it is the default dapper version

I tried to recompile ffmpeg as described in the thread you mention but somehow it was not compiling, it was giving permanent errors on XVID and when I disabled XVID on something else. both with gcc-3.4 and gcc-4.0 so in the end a dirty trick was to copy ffmpeg (the binary) from my old breezy backup (that's goodness for backups)
then run it, it complained of a couple of missing libraries, copyed them over as well and working fine now (I know it is not very elegant but unable to compile my own ffmpeg and spending hours trying to find a ffmpeg.deb package compiled with xvid and mp2/mp3 support it did the trick.
I did the same for mplayer as it wasn't playing most files I had around.[/QUOTE]

Just download the .deb for ffmpeg from the ipod converter thread and install it... No need to recompile ffmpeg wheg it is already done!

---

### Post by crmanski on 2006-06-17
Added a few changes today...
# - Added WMV detection.
# - More code redudancy cleanup...
# - Added ffmpeg XVID support detection
# - Added iPod and PSP output. (Note, I do not own either of these and cannot test or support this. I just took the spec from the ffmpeg FAQ: [http://ffmpeg.mplayerhq.hu/faq.html#SEC16](http://ffmpeg.mplayerhq.hu/faq.html#SEC16)) This also requires a non-standard ffmpeg. I recompiled mine to test this. There is a .deb file mentioned in the ipodenc thread ([http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946) under "Encoding Video for the iPod Video")

First item, I tend to stay away from WMV files, so I did not have a lot to sample from as far as what the output of "file -b movie.wmv" would look like. On the couple I had it said "Microsoft ASF". If someone has something differnt let me know.

Third item, I added a check to see if ffmpeg has xvid support. If it does then there will be an item in the list of output formats.

---

### Post by art2003 on 2006-06-18
There is no .deb file in that thread anymore
Perhaps some kind soul who has a suitable ffmpeg.deb file can upload it
using [www.sendmefile.com](www.sendmefile.com) and post a link here for others to download?

```
The .deb Method -- Recommended for those not familiar with compiling from source

The .deb Method source has been taken offline recently. Please follow the Source Method below.

```
> There is a .deb file mentioned in the ipodenc thread ([http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946) under "Encoding Video for the iPod Video")


---

### Post by FISHERMAN on 2006-06-18
First: Many thanks for this application\\:D/ . Video Converting is the only reason why I still have a Windows partition.

Second: I have some problems with *.wmv's and *.mov's(I have w32 and other proprietary codecs installed).
When I convert the wmv's I have no video and aonly a few seconds sound.
With mov's I have no sound(though video is OK).
Is there anyway to fix this?

---

### Post by OrganicPanda on 2006-06-18
heya again i'm using the new version (with psp support etc) and for some reasoin when i right-click the file and chose video-convert i get an error messege box:

> 
You have not selected a valid video type. MimeType=
ERROR: Cannot open 'testy.avi' (No such file or directory)


but it works fine from command line and i get a nice xvid avi out the other end
eg: ~/.gnome2/nautilus-scripts/video-convert ~/Desktop/testy.avi 
gets me:

```

panda@panda-desktop:~$ ~/.gnome2/nautilus-scripts/video-convert ~/Desktop/testy.avi
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-ogm
  built on Apr 29 2006 00:14:12, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-ogm
  built on Apr 29 2006 00:14:12, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
FALSE XVID XVID
/home/panda/Desktop/testy.avi: video/x-msvideo
/home/panda/Desktop/testy.avi
File is an AVI
XVID chosen as the output type.
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-ogm
  built on Apr 29 2006 00:14:12, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Input #0, avi, from '/home/panda/Desktop/testy.avi':
  Duration: 00:00:07.2, start: 0.000000, bitrate: 29972 kb/s
  Stream #0.0: Video: dvvideo, yuv420p, 720x576, 25.00 fps
  Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, 1024 kb/s
Output #0, avi, to '/home/panda/Desktop/testy_XVID.avi':
  Stream #0.0: Video: xvid, yuv420p, 720x576, 25.00 fps, q=2-31, 800 kb/s
  Stream #0.1: Audio: mp3, 32000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=  180 q=14.0 Lsize=     941kB time=7.2 bitrate=1076.4kbits/s
video:810kB audio:114kB global headers:0kB muxing overhead 1.909441%

```

any ideas because i love this script, its very very kool

edit: after looking at the script it seems asif it is reporting in the above output 'FALSE XVID XVID' which would mean no xvid compatibility but then it encoded me an xvid video anyway.... strange

---

### Post by haani on 2006-06-18
great script nice work but i use tovid to convert files to dvd O:)

---

### Post by crmanski on 2006-06-18
[QUOTE=art2003]There is no .deb file in that thread anymore
Perhaps some kind soul who has a suitable ffmpeg.deb file can upload it
using [www.sendmefile.com](www.sendmefile.com) and post a link here for others to download?

```
The .deb Method -- Recommended for those not familiar with compiling from source

The .deb Method source has been taken offline recently. Please follow the Source Method below.

```[/QUOTE]

There is a deb. What you are quoting is referring to a deb that I believe was in the forum. Just search for  SBX on the page...
> Encoding Video for the iPod Video

Dapper Packages!!!
SBX has been kind enough to create .deb packages for ffmpeg and Vive for Dapper. You can get them [here]("http://skulboxx.com/Ubuntu/sbx/") and install them both with sudo dpkg -i packagename.deb. Thanks so much to SBX for this contribution!

---

### Post by crmanski on 2006-06-18
[QUOTE=OrganicPanda]
edit: after looking at the script it seems asif it is reporting in the above output 'FALSE XVID XVID' which would mean no xvid compatibility but then it encoded me an xvid video anyway.... strange[/QUOTE]

That is just an echo statement that I was using to debug the list item for the XVID statement. Nothing to worry about.

I am not sure about the error. In the old original thread there was one person that was unable to run it if the file was on the desktop or in the root of the home directory. If the file was anywhere else it worked fine. Sounds strange, but I would try moving the file to something line ~/Movies/ and trying the conversion.

---

### Post by crmanski on 2006-06-18
[QUOTE=FISHERMAN] I have some problems with *.wmv's and *.mov's(I have w32 and other proprietary codecs installed).
When I convert the wmv's I have no video and aonly a few seconds sound.
With mov's I have no sound(though video is OK).
Is there anyway to fix this?[/QUOTE]

I would need to see the output of something like this at a terminal...
```
~/.gnome2/nautilus-scripts/video-convert /path/to/a/movie.wmv
```

---

### Post by FISHERMAN on 2006-06-19
[QUOTE=crmanski]I would need to see the output of something like this at a terminal...
```
~/.gnome2/nautilus-scripts/video-convert /path/to/a/movie.wmv
```[/QUOTE]
-I've solved my .mov-sound problems(I just picked a higher audio bitrate)
-I get this when trying to convert a WMV 9(I've noticed it works fine with WMV 7).
```
Could not open codec.
FATAL: Cannot initialize video driver.
Could not open codec.
FATAL: Cannot initialize video driver.
Cannot find codec matching selected -vo and video format 0x33564D57.

```

---

### Post by crmanski on 2006-06-19
[QUOTE=FISHERMAN]
-I get this when trying to convert a WMV 9(I've noticed it works fine with WMV 7).
```
Could not open codec.
FATAL: Cannot initialize video driver.
Could not open codec.
FATAL: Cannot initialize video driver.
Cannot find codec matching selected -vo and video format 0x33564D57.

```[/QUOTE]

I am pretty sure that WMV9 will not work with ffmpeg. Might work with mencoder, but I personally do not have any videos in this format to test out.

---

### Post by jISh on 2006-06-30
I'd like to thank you for this script, it is very well done and useful. However, I have one gripe with it.

Whenever I convert a DivX encoded AVI to a NTSC DVD, the audio/video is out of sync at many points during the film, and dvdauthor reports out of range audio segments when I run it....

Anyone else have this problem?

---

### Post by sublime on 2006-07-01
having some problems converting an mp4 to a dvd.  heres the output running it from terminal

```
richard@dapperdesktop:~$ .gnome2/nautilus-scripts/videoconvert /home/richard/movies/worldcup06/germanyvsargentina/germanyvsargentina.mp4
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
XVID support not present in ffmeg
AAC support not present in ffmeg
video/mp4
File is a MP4
ISO Media, MPEG v4 system, version 2
DVD chosen as the output type.
# Processing MP4 Video /home/richard/movies/worldcup06/germanyvsargentina/germanyvsargentina.mp4 \n Total: 1
Total Frames:
Encoding with command: ffmpeg -i /home/richard/movies/worldcup06/germanyvsargentina/germanyvsargentina.mp4 -target ntsc-dvd -s 720x480 -sameq -r 29.97 -aspect 4:3 -ab 128 -ar 48000 -ac 2 -acodec ac3 -y /home/richard/movies/worldcup06/germanyvsargentina/germanyvsargentina.mpg
awk: $1 ~ /frame/ {if ($2*100/>1) print $2*100/; fflush();}
awk:                          ^ syntax error
awk: $1 ~ /frame/ {if ($2*100/>1) print $2*100/; fflush();}
awk:                                           ^ syntax error

```

---

### Post by sublime on 2006-07-02
anybody?  id kind of like to watch this germany argentina game. ;)

---

### Post by crmanski on 2006-07-04
[QUOTE=sublime]having some problems converting an mp4 to a dvd.  heres the output running it from terminal

```
awk: $1 ~ /frame/ {if ($2*100/>1) print $2*100/; fflush();}
awk:                          ^ syntax error
awk: $1 ~ /frame/ {if ($2*100/>1) print $2*100/; fflush();}
awk:                                           ^ syntax error

```[/QUOTE]


The problem is that tcprobe does not find the number of frames correctly. I hadn't actually tried this on a mp4 file after adding the progress bars. If you could try replacing the get_frames function with this...

```
get_frames ()
{
	#get video duration and frames
        if [ "$video_in_type" = "MP4" ]; then
                echo "File is a MP4. Using Mencoder to get frame count..."
                total_frames=`mencoder "$movie" 2>&1 | grep "MOV track #0" | awk '{print $6}'`
             else
                echo "Using tcprobe to find number of frames..."
                total_frames=`tcprobe -i "$movie" 2>&1 |grep "length:" | awk '{gsub(/,/,"");gsub(/:/,"");print $2; fflush();}'`
        fi

}
```

... and let me know if that works. If not the output of...
```
mencoder "movie.mp4"
```
would help.

---

### Post by encho on 2006-07-04
Nice script, I've been looking for this for a long time. Although I can suggest to use mencoder instead of ffmpeg for creating DVDs and other. Mencoder gives much better quality overall and you can tweak it to perfection. Also it would be nice to include x264 and mkv as well (I am converting my DVD & xvid collection to mkv'ed 264s and I can tell you that you can have 50% smaller file at the same quality!). I can give you my command line details if you're interested.

---

### Post by crmanski on 2006-07-04
[QUOTE=encho]I can suggest to use mencoder instead of ffmpeg for creating DVDs and other.  I can give you my command line details if you're interested.[/QUOTE]

Sure. I'll take them. I have been working on a mencoder or ffmpeg choice for the script. I have a separate mkv->dvd script that I am polishing up and plan on integrating into this one that uses mencoder, grabs subtitles, multi-audio, etc... So far I have a High, Med, and Low quality level of encode for DVD output. Nothing for the other things like xvid, ipod, psp...

---

### Post by sublime on 2006-07-04
alright after replacing that function and trying it i still get the same error.  however converting the mp4 to mpg using a line for mencoder worked.

---

### Post by encho on 2006-07-05
Here are few of my command line options:

**###DVDs###**
**Mencoder**
> 
mencoder -ofps 24000/1001 -mc 1 -ovc lavc -oac lavc \
-lavcopts acodec=ac3:abitrate=160:vcodec=mpeg2video:lmin=1:lmax=10:\
keyint=15:trell:vmax_b_frames=2:mbd=2:precmp=2:subcmp=2:cmp=2:dia=-10:\
predia=-10:cbp:mv0:dc=10:vstrict=-1:vrc_buf_size=1835:vbitrate=6000:\
vrc_maxrate=9800:vqscale=4 -af volume=+0dB,volnorm=2,lavcresample=48000 \
-srate 48000 -channels 2 -sws 9 -vf denoise3d=1.33:1:2,pp=hb/vb/dr/al/lb,\
scale=716:476,expand=720:480,scale=720:480,harddup -of mpeg -mpegopts \
format=dvd:vaspect=16/9:telecine:init_vpts=400:init_apts=400 \
-mc 1 -o output_file.mpg input_file.avi

Explanation:
This is NTSC encoded file with 3:2 pulldown. Means that file is encoded at 23.976 fps (24000/1001), while dvd player is tricked to think it is 29.97 (that's what 'telecine' option does in mpegopts). This way we have much smaller file with same quality. For PAL encodings use '-ofps 25' and exclude 'telecine' in mpegopts.
In lavcopts we have some settings set to achieve very high quality encodings. You can change abitrate to ie 224 if you want higher quality sound. Option vqscale sets constant quantizer (4 in this case), lower the quant, better the quality, but also bigger file. Quantizer 1 is not recomended (compatibility issues). If you want fixed size file, you should use 2-pass encoding.
Video filters ('-vf' option) sets some filters. Include 'al' (autolevels) only if your video source has washed-up look. 'scale' settings are set to give 2px border around video (giving smaller size encoding, those 2 pixels are not visible on most tvs). 
Note that those settings are tweaked for widescreen material, you should change few things (like autoaspect option in lavcopts), but I did not bother to check. Also '-of mpeg' is still in experimental stage, so output file might need to be remultiplexed (this issue might be solved in mencoder pre8 that's been released recently). Read man for more info.

**Transcode**
> 
transcode --print_status 5 --export_fps 23.976,1 -J hqdn3d=4:3:6:4:pre,pp=hb:vb:dr:al,normalize,text=string="My Cool Video":fade=2:range=150-350:font=/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf:pos=500x50:points=10 --video_max_bitrate 7500 -V -j0,-2 --export_prof dvd-ntsc --export_asr 3 -y mpeg2enc,ffmpeg -F 8,"-K kvcd" -N 0x2000 -R 3 -w 7,12,90 --pulldown -E 48000 -D 0 -b 160 -i input_file.avi -o output_file -m output_file.ac3

Recently I've discovered that transcode with mpeg2enc gives even better results than mencoder, only it can be very slow sometimes. Source is also ntsc pulled down to 29.97. Some cool options are in '-J'. First - filters used are mplayer ones, same as mecoder; do not use 'al' unless for washed-up videos. 'normalize' will normalize your sound. 'text' is the easiest way to add text to your video (range is frame start/end). '--export_asr 3' is for widescreen. '-y' tells transcode to use mpeg2enc module for video and ffmpeg for audio. You can use ffmpeg for video to get some speed, but will lose some quality. -F is for passing options to mpeg2enc module. '8' is for dvd format "-K kvcd" is for matrix (very powerfull feature; kvcd is matrix used for tweaking mpeg to produce smaller files - around 15%; other options are tmpgenc|default|hi-res - check man mpeg2enc). '-N 0x2000' is for ac3 output. '-R 3' in combination with '-w' gives constant quantizer (7 in this case, mpeg2enc related, corresponds to mencoder's q4). '12' is keyframe setting and '90' is crispness/smoothness factor. Again change '-b' option to 224 if you want higher quality sound.
Once encoding is finished, you need to multiplex video/audio files:
> 
mplex -S 4700 -f 8 -M -V -o output_file.mpg video.m2v audio.ac3

Transcode will ensure that you have very compliant dvd video with superb quality.

---

### Post by crmanski on 2006-07-05
Thanks for these. I'll compare them to the ones I already have setup. Could you do me a favor and edit the post, click advanced and then check off "Disable smilies in text"?

---

### Post by encho on 2006-07-05
Done. I haven't even noticed :-\"

---

### Post by finite9 on 2006-07-05
Hi!

I had big problems with this script!!

1. If you cut the text from this forum and paste it into Gedit, then due to word wrap being enabled, it saves the file with word wrapping in place!!  Then you get no response when running the script in Nautilus, but you get script syntax errors if run from the shell.  If you save the script in Gedit with word wrapping off (selected in Preferences) then the script works ok (no syntax errors at least.  This took days to figure out!

2. Neither transcode nor mencoder-arch exist in the repositories for Dapper Drake i386 or amd64.  To get around this, I commented out the exit command when you pop up the dialog using zenity.  Obviously, this does not affect coding if you want to convert Windows formats.

3. The quality of the SVCD conversion is very poor.  It skips frames.  I don't know if this is due to the settings you use or ffmpeg?  Weird, but the colours are really screwed up in Totem, but look fine in VLC, but both VCD and SVCD versions of the converted file hang when played in VLC.

4. You still refer to standard ffmpeg from the repos as being needed in the updated script as of 25 June, but others have already determined that this does not have support for XviD, so you cannot keep referring to the repository version of ffmpeg, without giving instructions on how to get an ffmpeg .deb with XviD enabled!  Could you please include instructions for this?

--finite9

---

### Post by crmanski on 2006-07-08
> **finite9 said:**
> Hi!

I had big problems with this script!!

1. If you cut the text from this forum and paste it into Gedit, then due to word wrap being enabled, it saves the file with word wrapping in place!!  Then you get no response when running the script in Nautilus, but you get script syntax errors if run from the shell.  If you save the script in Gedit with word wrapping off (selected in Preferences) then the script works ok (no syntax errors at least.  This took days to figure out!

2. Neither transcode nor mencoder-arch exist in the repositories for Dapper Drake i386 or amd64.  To get around this, I commented out the exit command when you pop up the dialog using zenity.  Obviously, this does not affect coding if you want to convert Windows formats.

3. The quality of the SVCD conversion is very poor.  It skips frames.  I don't know if this is due to the settings you use or ffmpeg?  Weird, but the colours are really screwed up in Totem, but look fine in VLC, but both VCD and SVCD versions of the converted file hang when played in VLC.

4. You still refer to standard ffmpeg from the repos as being needed in the updated script as of 25 June, but others have already determined that this does not have support for XviD, so you cannot keep referring to the repository version of ffmpeg, without giving instructions on how to get an ffmpeg .deb with XviD enabled!  Could you please include instructions for this?

--finite9


1. I'll attach a tar.gz of the script to the original post if I can. I always have word wrap off.

2. Yes they do...
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mencoder&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mencoder&searchon=names&subword=1&version=dapper&release=all)
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=transcode&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=transcode&searchon=names&subword=1&version=dapper&release=all)
Most likely you do not have the correct repositories (Multiverse).

3. Nothing I can do about that. Quality usually depends on source quality. I am posting a Beta of the script that will let you choose to use mencoder or ffmpeg. Mencoder is supposed to give better quality. 

4. The philosophy behind this script is basically to support only standard ubuntu packages. If someone has a recompiled ffmpeg that supports xvid, ipod or psp then those options are enabled. This is noted in the script and there is a link in this the thread that mentions where the non standard ffmpeg package is. (search forums for SBX)

---

### Post by joe343 on 2006-07-18
Hi I'm getting this error when I run this command:
sh video_convert /media/data/Videos/AmazingFootballSkill.avi
```
: command not found 79:
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
: command not found 85:
'ideo_convert: line 137: syntax error near unexpected token `
'ideo_convert: line 137: `is_asf ()
```


When I right click on a video and select the script, nothing happen.

Thanks for your help.

---

### Post by crmanski on 2006-07-19
> **joe343 said:**
> Hi I'm getting this error when I run this command:
sh video_convert /media/data/Videos/AmazingFootballSkill.avi
```
: command not found 79:
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
: command not found 85:
'ideo_convert: line 137: syntax error near unexpected token `
'ideo_convert: line 137: `is_asf ()
```


When I right click on a video and select the script, nothing happen.

Thanks for your help.

Are you having the same problem that finite9 was having a few posts above yours? When I look at this part of the error that your posted...
> 'ideo_convert: line 137: `is_asf ()
..It looks like the lines might have wrapped? Line 137 does not have is_asf() on it.

---

### Post by boywondr16 on 2006-07-22
I'm getting more and more frustrated with video encoding on Breezy, so I thought I'd float my question here to see if anyone has an answer...

It doesn't matter if I'm attempting to use Avidemux or this script to convert Xvid, I don't get the full movie encoded.  Everything just stops...

Codecs are in...The only thing I could figure is VBR audio, but beyond that, am I overlooking something else? Anyone else have this problem?

---

### Post by crmanski on 2006-07-24
> **boywondr16 said:**
> I'm getting more and more frustrated with video encoding on Breezy, so I thought I'd float my question here to see if anyone has an answer...

It doesn't matter if I'm attempting to use Avidemux or this script to convert Xvid, I don't get the full movie encoded.  Everything just stops...

Codecs are in...The only thing I could figure is VBR audio, but beyond that, am I overlooking something else? Anyone else have this problem?

Not sure. I would need more information. If you type...
```
mplayer "/path/to/MovieName.avi"
```
...in a terminal and post the output here I'll take a look.

---

### Post by ~LoKe on 2006-07-24
Not sure if I'm doing something obviously wrong...but after I choose DVD, the video resolution, audio bitrate, etc, a progress bar flashes then disappears.  

> loke@x04d:~$ ~/.gnome2/nautilus-scripts/video-convert ~/Desktop/Miscellaneous/V.For.Vendetta/V.For.Vendetta.avi
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
XVID support not present in ffmeg
AAC support not present in ffmeg
/home/loke/Desktop/Miscellaneous/Movie/Movie.avi: video/x-msvideo
/home/loke/Desktop/Miscellaneous/Movie/Movie.avi
File is an AVI
RIFF (little-endian) data, AVI, 532 x 222, 23.98 fps, video: DivX 5, audio: MPEG-1 Layer 3 (stereo, 48000 Hz)
DVD chosen as the output type.
# Processing AVI Video /home/loke/Desktop/Miscellaneous/Movie/Movie.avi \n Total: 1
Total Frames: 183061
Encoding with command: ffmpeg -i /home/loke/Desktop/Miscellaneous/Movie/Movie.avi -target ntsc-dvd -s 720x480 -sameq -r 29.97 -aspect 4:3 -ab 128 -ar 48000 -ac 2 -acodec ac3 -y /home/loke/Desktop/Miscellaneous/Movie/Movie.mpg
loke@x04d:~$

The 
> XVID support not present in ffmeg
AAC support not present in ffmeg

part seems most relevant.  How would I acquire said support?

**EDIT:** I'm trying to convert an .AVI to a suitable DVD format (Mpeg?).

---

### Post by art2003 on 2006-07-25
I use the following script to convert all .mpg files on a given folder to xvid

```
#!/bin/bash

for f in $(ls ./ |grep  .ASF |grep -v .avi ) ; do
xvid=`echo "$f" | sed 's/\.\w*$/.avi/'`
ffmpeg -i $f -f avi -vcodec xvid -b 800 -g 300 -bf 2 -acodec mp2 -ab 128 $xvid
done
```

Then use WinX2D to change the header as otherwise it comes with unknown codec in a windows pc with xvid codecs.

This is done to convert some .asf home videos taken with my video cam.
This works to the point where they play fine on my ubuntu PC but when I share  these supposely .xvid files with my windows-only relatives they get audio ok but video extremely jerky.

What can I do to generate standard xvid files with ffmpeg in the first place that will play both on ubuntu and windows?

---

### Post by vuitton on 2006-07-25
Thank you very much, this script is very useful and satifies my needs :)

---

### Post by crmanski on 2006-07-25
> **art2003 said:**
> 

What can I do to generate standard xvid files with ffmpeg in the first place that will play both on ubuntu and windows?

I have not had good luck with ffmpeg creating XVID files. The latest Avidemux seems pretty good, but it is hard to script.  I have been converting my mythtv recordings (MPG) to xvid with these commands in a similar script using mencoder. They play fine on windows. I use VLC on both platforms.

```
mencoder "$file" -oac copy -ovc xvid -ofps 24000/1001 -vf pullup,softskip,pp=md,hqdn3d=2:1:2 -xvidencopts bitrate=900:pass=1:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg -o "$current_title.avi"
mencoder "$file" -oac copy -ovc xvid -ofps 24000/1001 -vf pullup,softskip,pp=md,hqdn3d=2:1:2 -xvidencopts bitrate=900:pass=2:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg -o "$current_title.avi" 
```

Since you are not converting an interlaced video you might want to try something different and remove the "-ofps 24000/1001 " and the "pullup,softskip,pp=md" (deinterlacing) parts of the command.

---

### Post by crmanski on 2006-07-25
> **~LoKe said:**
> Encoding with command: ffmpeg -i /home/loke/Desktop/Miscellaneous/Movie/Movie.avi -target ntsc-dvd -s 720x480 -sameq -r 29.97 -aspect 4:3 -ab 128 -ar 48000 -ac 2 -acodec ac3 -y /home/loke/Desktop/Miscellaneous/Movie/Movie.mpg

Everything looks ok in what you posted. The only thing that I can even think of is that the Video is in a folder on the Desktop. I have had others say the script did not work when executed on files in this directory. I have no idea why. Try moving the files to /home/loke/Miscellaneous or something and see if it works.

ffmpeg with xvid and aac support can be downloaded here...
[http://skulboxx.com/Ubuntu/sbx/](http://skulboxx.com/Ubuntu/sbx/)

---

### Post by Hatrist on 2006-07-26
I´m using **ffmpeg**: Is there any possible way to convert a video file with 5 channels audio stream? Here is what I did:

1) I used the model:
```
ffmpeg -i /home/hatrist/Movies/Movie.avi -target ntsc-dvd -s 720x480 -sameq -r 29.97 -aspect 4:3 -ab 128 -ar 48000 -ac 2 -acodec ac3 -y /home/hatrist/Movies/Movie.mpg
```
This is right, isn´t it?

2) When I pressed ¨Return¨, it started analyzing the .avi file. And here is the error:
```
Input #0, avi, from '/home/hatrist/Movies/Movie.avi':
  Duration: 00:53:47.2, start: 0.000000, bitrate: 1821 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 736x400, 23.98 fps
  Stream #0.1: Audio: 0x2001, 48000 Hz, 5 channels, 754 kb/s
Resampling with input channels greater than 2 unsupported.Can't resample.  Aborting.
```

Any possible way to resample 5 channels?

---

### Post by crmanski on 2006-07-26
> **Hatrist said:**
> I´m using **ffmpeg**: Is there any possible way to convert a video file with 5 channels audio stream? Here is what I did:

1) I used the model:
```
ffmpeg -i /home/hatrist/Movies/Movie.avi -target ntsc-dvd -s 720x480 -sameq -r 29.97 -aspect 4:3 -ab 128 -ar 48000 -ac 2 -acodec ac3 -y /home/hatrist/Movies/Movie.mpg
```
This is right, isn´t it?

2) When I pressed ¨Return¨, it started analyzing the .avi file. And here is the error:
```
Input #0, avi, from '/home/hatrist/Movies/Movie.avi':
  Duration: 00:53:47.2, start: 0.000000, bitrate: 1821 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 736x400, 23.98 fps
  Stream #0.1: Audio: 0x2001, 48000 Hz, 5 channels, 754 kb/s
Resampling with input channels greater than 2 unsupported.Can't resample.  Aborting.
```

Any possible way to resample 5 channels?

Remove this part of the line: -ac 2
That might work. Strange that it is 5 channel and not 6.

---

### Post by Hatrist on 2006-07-26
Don´t ask me where I´ve taken it from :mrgreen: 

Thanks for the help, but there is another problem now:
[[img]http://img86.imageshack.us/img86/3144/screen001ct4.th.png[/img]](http://img86.imageshack.us/my.php?image=screen001ct4.png)

---

### Post by crmanski on 2006-07-26
> **Hatrist said:**
> Don´t ask me where I´ve taken it from :mrgreen: 

Thanks for the help, but there is another problem now:
[[img]http://img86.imageshack.us/img86/3144/screen001ct4.th.png[/img]](http://img86.imageshack.us/my.php?image=screen001ct4.png)

I would use the beta version of the script that I have on the first post and make sure that in the config options at the beginning of the script are set to use mencoder instead of ffmpeg.

---

### Post by Hatrist on 2006-07-26
Hmmm, I tried with the script and it was success... in some way.
This time it didn´t converted the whole video file. It made a 250 MB .mpg file, but that´s not the whole video. 

/I used the DVD option/

---

### Post by k420 on 2006-07-28
oh i got it

---

### Post by k420 on 2006-07-28
i can not install transcode with apt-get and when i try with synaptic it wants to remove mplayer mencoder and a bunch of other apps. the script wwill not run with out transcode what can i do

---

### Post by crmanski on 2006-07-29
> **k420 said:**
> i can not install transcode with apt-get and when i try with synaptic it wants to remove mplayer mencoder and a bunch of other apps. the script wwill not run with out transcode what can i do

When I have had these errors in the past it was because I had some odd/non-supported repositories enabled (seveas, cipherfunk to name a few). If you have something like that in your setup you could disable them, refresh your package list and try to install.

---

### Post by hardkaare on 2006-08-27
It would be realy cool if it could take dvdimages directly and an option for ipod formats :-)

---

### Post by Athanasius on 2006-09-04
What is the difference between a mpg file and a vob file?  My digital camcorder records to avi format and I don't know if mpg is as compatible with  dvd players because I know that regular dvd's are all vob files.  Is there someone "in the know" that could help me?  Thank you

---

### Post by jethro10 on 2006-09-04
> **Athanasius said:**
> What is the difference between a mpg file and a vob file?  My digital camcorder records to avi format and I don't know if mpg is as compatible with  dvd players because I know that regular dvd's are all vob files.  Is there someone "in the know" that could help me?  Thank you

A vob file is basically just an mpeg file with chapter marks and other DVD specific info embeded in it.
An mpeg therefore is akin to a 'raw' dvd image as such.

when an mpeg is converted to a dvd it just slips these little bits in and chops them up, usually, to 1Gb file sizes.

An AVI is just a container to keep a file in and the format may be one of many. However to most people an avi is an Mpeg 4 file, which is a more compresed format to normal DVD's which are actually Mpeg 2's.

Mpeg 4 is used in the newer hi Def dvd's, digital cameras and formats you may have heard of like Divx and Xvid.

A program like AviDemux can convert to and from most of these formats quite easily.
hope this helps.

---

### Post by LKRaider on 2006-09-26
Very cool script. I was going to develop my own, but this is already done!

thanks :)

---

### Post by user1397 on 2006-11-06
wait, have any of you ever heard of tovid?


it is an active project written in python, and it has very advanced video conversion tools.

i have made a guide on howto use tovid, its in my sig.

sorry to write this, but i thought people were more aware of tovid!

it uses mplayer for encoding by default, but you can set it to encode with ffmpeg too.

---

### Post by crmanski on 2006-11-07
Certianly. It was still early in development when I started this and didn't convert the files in the way I wanted at the time. I have looked at it in the last month or so and I like todisc and some of the other scripts.

---

### Post by user1397 on 2006-11-07
> **crmanski said:**
> Certianly. It was still early in development when I started this and didn't convert the files in the way I wanted at the time. I have looked at it in the last month or so and I like todisc and some of the other scripts.
wait so is your project going to die off, because of the already established power of tovid, or are you going to still develop this program?

---

### Post by dave37 on 2006-11-26
Am new to Linux video conversion and love this script, it works great for me.

---

### Post by crmanski on 2006-11-27
Other than adding support for other formats I do not plan on going much further with this project. Last update was 10/17/06.

> **erik1397 said:**
> wait so is your project going to die off, because of the already established power of tovid, or are you going to still develop this program?

---

### Post by malcolm1234 on 2006-12-22
This script is great. I've made a few modifications so that the iPod option is the default and encodes video for my phone. Now it only takes a couple of clicks to convert a video ready to take with me on the train.

Excellent work :KS 

M

---

### Post by tomski on 2007-01-06
Great script 

one question though how do i define the output directory if i dont want it to be the same location as source

---

### Post by edmondt on 2007-01-07
Is there a way to convert files to rmvb? :)

---

### Post by caplod on 2007-03-29
Great script. I added the support for flv movies.

---

### Post by crmanski on 2007-03-30
> **caplod said:**
> Great script. I added the support for flv movies.

If you post the code i'll include it in the first post.

---

### Post by fatalbert on 2007-05-19
It's failing for me and I have tried both scripts using the command line and gui. I'm trying to convert PAL to NTSC.

After running the script, I get a pop window of "You have not selected a valid video type - MimeType=application/octet-stream

Any ideas?

Thanks

$ ls -lrt
total 1482080
-rwxr--r-- 1       66096 2006-10-17 20:43 Video_Convertor_Beta
-rw-r--r-- 1      12288 2007-05-01 06:39 VIDEO_TS.BUP
-rw-r--r-- 1       36864 2007-05-01 07:52 VTS_01_0.IFO
-rw-r--r-- 1       36864 2007-05-01 07:52 VTS_01_0.BUP
-rw-r--r-- 1       12288 2007-05-01 07:52 VIDEO_TS.IFO
-rw-r--r-- 1   442236928 2007-05-01 13:18 VTS_01_2.VOB
-rw-r--r-- 1  1073709056 2007-05-01 13:25 VTS_01_1.VOB
-rwxr----- 1      25664 2007-05-19 11:03 video-convert


$ ./Video_Convertor_Beta *.*
-----------------------------------------------------------------------------
Video Converter Nautilus Script
-----------------------------------------------------------------------------
Checking for required software and capabilities...
-----------------------------------------------------------------------------
XVID support not present in ffmeg
AAC support not present in ffmeg
Checking for file type...
-----------------------------------------------------------------------------
application/octet-stream

Here's the regular script output:

$ ./video-convert *.*
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Oct  4 2006 10:57:36, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Oct  4 2006 10:57:36, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
XVID support not present in ffmeg
AAC support not present in ffmeg
application/octet-stream

---

### Post by crmanski on 2007-05-21
You use this on the command line...
```
./video-convert *.*
```
This includes the .IFO, and .BUP file which are probably giving you the application/octet-stream. You should specify the name of the file you want to convert instead of using the wildcard.

```
./videoconvert VTS_01_2.VOB
```

---

### Post by tetralis on 2007-05-23
I am trying to convert mp4-conatiners that includes MPEG4 SP and AAC to MPEG4 SP and Mp3 is this script able to do so (what are the setup for this) or should I try splitting the conatainer, coverting aac and then join them together again? 
Maybe the audio and video formats that I need (MPEG4 SP and MP3) could be joined into an AVI file (instead of MP4, whatever the difference is)?

---

### Post by mindhaq on 2007-07-05
I made the following changes to the script, so it will accept .dv and .3gp files:

```
#Check for DV
is_dv ()
{
	file -b "$1" | grep 'DIF (DV)' && echo $1 | grep -i '\.dv$'
}

if (is_dv "$1")
        then
	echo "File is a DV"
	video_in_type="DV"
	valid_video_type="1"
fi

#Check for 3GPP
is_dv ()
{
	file -b "$1" | grep '3GPP' && echo $1 | grep -i '\.3gp$'
}

if (is_dv "$1")
        then
	echo "File is a 3GPP"
	video_in_type="3GPP"
	valid_video_type="1"
fi

```

Other than that, I really like this. Very easy to use with good results so far.

---

### Post by guilherme08 on 2007-07-05
If this problem hasn't been fixed yet (I searched the thread and didn't find anything), the following code should make the script work with files in the Desktop or trash:

```

if ! [[ -e $1 ]]
then
 if [[ $NAUTILUS_SCRIPT_CURRENT_URI == trash: ]]
 then 
 cd -- ~/.Trash
 elif [[ $NAUTILUS_SCRIPT_CURRENT_URI == file://$HOME/Desktop ]]
 then
 cd  -- "$HOME"/Desktop/
 else
 zenity --error --title="error" --text="Unable to find input file."
 exit 1 
 fi
fi

```

I placed it after the part that tests if a file was selected.

---

### Post by reformedgeek on 2007-08-27
Hi I'm trying to use this awesome script on a few VOB files but I keep getting the following error
```

You have not selected a valid Video Type. MimeType= video/mp2p

```

Is it to do with the way it was ripped originally from the DVD?

---

### Post by QwUo173Hy on 2007-10-09
My encoded files are only 16 minutes long even though the movie is over one hour long at least.

> ja@ja-desktop:/mnt/Disk/Video$ ~/.gnome2/nautilus-scripts/video-convert Teen\ Wolf.avi 
-----------------------------------------------------------------------------
Video Converter Nautilus Script
-----------------------------------------------------------------------------
Checking for required software and capabilities...
-----------------------------------------------------------------------------
XVID support is present in ffmeg
AAC support is present in ffmeg
Checking for file type...
-----------------------------------------------------------------------------
Teen Wolf.avi: video/x-msvideo
Teen Wolf.avi
File is an AVI
ls: Teen Wolf.srt: No such file or directory
ls: Teen Wolf.sub: No such file or directory
RIFF (little-endian) data, AVI, 592 x 320, ~30 fps, video: DivX 5, audio: MPEG-1 Layer 3 (stereo, 48000 Hz)
File is a MPG
ls: Teen Wolf.srt: No such file or directory
ls: Teen Wolf.sub: No such file or directory
rm: cannot remove `test.avi': No such file or directory
VCD chosen as the output type.
No Subs detected...
rm: cannot remove `test.avi': No such file or directory
Choose VCD Type
# Processing MPG Video Teen Wolf.avi \n Total: 1
rm: cannot remove `framemo.avi': No such file or directory
Using tcprobe to find number of frames...
Total Frames: 165359


I've tried this with many avi files all with the same result. I'm using the Beta script.

---

### Post by bouncingmolar on 2007-10-22
how do i install this on Kubuntu?

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

### Post by diskotek on 2007-12-09
hi there, 
i followed the instructions (i installed mplayer-skins instaead of mplayer-686, since there is no available package for it).

but when i click on something.vob file, i received an error: 
> You have not selected a valid Video Type. MimeType= video/mp2p
what do you think about it?

---

### Post by crmanski on 2007-12-12
> **diskotek said:**
> hi there, 
i followed the instructions (i installed mplayer-skins instaead of mplayer-686, since there is no available package for it).

but when i click on something.vob file, i received an error: 

what do you think about it?

You could try changing the part that says...
```
#Check For VOB
is_vob ()
{
	file -bi "$1" | grep 'video/mpeg' && echo $1 | grep -i '\.vob$'
}

```

to this...
```
#Check For VOB
is_vob ()
{
	echo $1 | grep -i '\.vob$'
}

```

---

### Post by crmanski on 2007-12-12
> **bouncingmolar said:**
> how do i install this on Kubuntu?

For a while I had kubuntu-desktop and the regular ubuntu-desktop both installed. When I was logged into a KDE session I would open a terminal and run...
```
nautilus --no-desktop
```

Then you can browse to files with nautilus, right-click, etc.

---

### Post by feistybird on 2007-12-24
Thanks for your excellent script,

I've tried the latest version: "Video_Convertor_Beta_20071210.tar.gz"

It's really so easy to use, and works great in most cases, however, I found it can only convert the "title videos" (introduction) from some .avi files, (first 10~20 secs. ), and ignore the rest parts of the video.

Does anyone knows how to fix it please?

Thanks!

---

### Post by gary4gar on 2008-03-18
Thank You!
Worked liked a charm:)

---

### Post by mocha on 2008-03-19
I love this script but I was wondering how folks deal with the resolution problem that it seems to have when encoding mpeg2 DVD files?  For example, if you have a file that has an aspect ratio like 1.85:1 and you want to convert it to a 4:3 DVD format, you have to go into the script and add an entry to the resolution choices otherwise the script produces files with screwed up aspect ratios.

I searched this thread and there doesn't seem to be anyone else posing this issue.  Is this not a problem for anyone else?

---

### Post by Svendus on 2008-09-27
> **Kung Fu Hamster said:**
> What about adding support to convert .WMV files as well?

Is it possible to convert .ogg files captured with gtk-recordMyDesktop to AVI with this Script ?
We are using  ```
#!/bin/bash
#

mencoder -idx /home/USERNAME/out.ogg -ovc lavc -oac mp3lame -o /home/USERNAME/out.avi
```
It makes low quality AVI but we want high quality AVI 
Regards Svendus

---

### Post by Devil_Gilgamesh on 2008-10-04
Excellent.

If it had a cancel button it would be even better, and a progress bar...

Just a suggestion.

Thanks for the script.

---

### Post by abclemons on 2008-11-13
Excellent script! Just what I was looking for and worked the first time.

---

### Post by lad3391 on 2008-12-27
a tip for any1 feeling stupid (like i did) and not being able to find the .gnome2 folder... ctrl+h (while viewing the home folder) will reveal the folders that are hidden ;)

---

### Post by dialynas on 2009-03-09
after converting avi to mpg how to burn to dvd to watch it in dvdplayer?

---

### Post by nauman_30 on 2009-08-19
Great script !!

---

### Post by Abstract_Fish on 2009-11-08
2 things:
Where does the script place the converted file(s)?
and is there .MKV file support?

-thank you

---

### Post by ultraboo on 2009-11-27
Dont work with files .VOB

---

### Post by LintonHanes on 2010-01-27
thank you heaps!

---

