---
title: "Borkage on Names with Spaces in them (Bash Scripting)"
date: 2008-10-25
forum: Programming Talk
---

### Post by beowulf62381 on 2008-10-25
Ok I have no Idea What I'm doing where scripting is concerned. So advice with an explanation is very much appreciated,If you have the time.

I am working on a script that will transcode videos to a size/format that will play on my gp2x, as well as split a multi page pdf into jpges.
As it sits right now it will take a single file or a directory as input and process it just fine so long as there are no spaces in the name.

Could one of you help me tweak this script so it will work regardless of spaces in the name or not.

```
#/bin/sh
###Start of Personal Settings###
#Set the output directory you want your finshed files in.
BASEDIR="/home/$USER/Desktop/GP2X"

#Set bitrate in kb/s
VBTR="100" #Video
ABTR="32" #Audio
###End of Personal Settings###

#Check to see if you have given us files to work with.
if [ -z "$1" ]; then
		echo "Usage: $0 file_or_directory_2_convert"
		echo "    Directory names end with /"
		echo "    i.e. /home/my_home/"
		echo "Usage: $0 -pdf file.pdf Will make one file-#.jpg for each page in the pdf"
		exit 1
fi

### List of internal functions ###
function CHKDIR {
		if [ -d $DIR ]; then
		echo "$DIR exists - using for output"
	else
		echo "$DIR not found - creating and using for output"
		mkdir -p "$DIR"
 fi
}

function GP2X {
        OPTS="-vf scale=320:240 -ovc xvid -oac mp3lame -lameopts abr:br=$ABTR -xvidencopts bitrate=$VBTR:quant_type=h265:vhq=4:bvhq=1:hq_ac:chroma_opt"
        mencoder $INPUT $OPTS:pass=1:turbo -o /dev/null
        mencoder $INPUT $OPTS:pass=2 -o $OUTPUT
        rm divx2pass.log
}

function TEST {
	echo "Input is $INPUT"
	echo "Output is $OUTPUT"
}

### End List ###

#Check to see if we have an output directory and create one if we do not
DIR=$BASEDIR
CHKDIR

#Check to see if any swiches where used
if [ "$1" != "-pdf" ]; then
		for INPUT in `find "$1" -name *.???`
		do
		OUTPUT="$BASEDIR/`basename "${INPUT/%.???/.avi}"`"
		GP2X
		done
	else
                for INPUT in `find "$2" -name *.[pP][dD][fF]`
                do
                DIR="$BASEDIR/`basename "${INPUT/%.[pP][dD][fF]}"`"
		CHKDIR
                OUTPUT="$DIR/`basename "${INPUT/%.[pP][dD][fF]/.jpg}"`"
		echo "Just a sec"
		echo "Processing $INPUT"
		convert -quality 75 $INPUT $OUTPUT
                done
fi
```

Thanks

p.s.
This script will not take *.mpeg as input since it only searchs for *.???
Is there a clean way to make it look for *.mpg,*.mpeg,*.avi, etc..

---

### Post by sisco311 on 2008-10-25
You can get the script to not treat spaces in file names as special by setting the IFS variable near the top of your script:

```

IFS=$'\t\n'

```

---

### Post by ghostdog74 on 2008-10-25
without changing IFS unnecessarily, use a while read loop instead of a for loop
```

find "$1" -name *.??? | while read INPUT
do
 ...
done

```
always make it a habit to  use quotes around your $variables.

---

### Post by beowulf62381 on 2008-10-25
Thank you ghostdog I made the recommended adjustments, and the script now works with spaces.

I did not understand what the IFS settings where so I chose not to adjust them, sisco but thank you for the reply perhaps if you have the time you could give a brief explanation?

---

### Post by ghostdog74 on 2008-10-25
read the bash reference or the one in my sig. Or do a man bash in your terminal, then type: /IFS

---

