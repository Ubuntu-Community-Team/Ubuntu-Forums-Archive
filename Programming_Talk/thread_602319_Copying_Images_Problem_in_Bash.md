---
title: "Copying Images Problem in Bash"
date: 2007-11-04
forum: Programming Talk
---

### Post by ncwilde43 on 2007-11-04
What is the best way in a bash script to copy images from randomly created source directories to a destination directory.

copy from: /sourcedir/randomdir/images.jpg
copy to: /destinationdir/images.jpg

Currently I am going into the sourcedir, using 
```

#!/bin/bash
cd sourcedir
find -maxdepth 2 -name "*.JPG" | while read x; do
INSTDIR="/destinationdir"
install -d "$INSTDIR"
INSTFILE="$INSTDIR/$x"
cp -ax "$x" "$INSTFILE"
done

```

and trying to copy the found images to the destination dir.  The images just won't seem to copy.

Any help is appreciated.

---

### Post by Martin Witte on 2007-11-04
change to someting like 

#!/bin/bash
sourcedir=/home/martin
destdir=/home/martin/destdir

if [ ! -d $sourcedir ]
then
   echo "error $sourcedir doesn't exist"
   exit 1
fi
# make sure destination directory exists
if [ ! -d $destdir ]
then
   mkdir $destdir
fi


cd $sourcedir
#linux filenames are case sensitive
find -maxdepth 2 -name "*.[Jj][Pp][Gg]" | while read pica; do
   # print to screen what we're going to copy
   destname=$destdir/`basename $pica`
   echo "copy $pica to $destname"
   cp $pica $destname
done

---

### Post by ncwilde43 on 2007-11-05
> **Martin Witte said:**
> change to someting like 

#!/bin/bash
sourcedir=/home/martin
destdir=/home/martin/destdir

if [ ! -d $sourcedir ]
then
   echo "error $sourcedir doesn't exist"
   exit 1
fi
# make sure destination directory exists
if [ ! -d $destdir ]
then
   mkdir $destdir
fi


cd $sourcedir
#linux filenames are case sensitive
find -maxdepth 2 -name "*.[Jj][Pp][Gg]" | while read pica; do
   # print to screen what we're going to copy
   destname=$destdir/`basename $pica`
   echo "copy $pica to $destname"
   cp $pica $destname
done

Thanks for the help.  I finally got it to work.  It turns out I was missing the whole `basename` command.  I'm actually running this script to automatically download the images from my SD Card once I plug it in.  I've posted the code in case anyone wants to use it.
```

#!/bin/bash

# Reads EXIF creation date from all .JPG files in the
# current directory and moves them carefully under
#
#   $BASEDIR/YYYY/YYYY-MM-DD
#
# ...where 'carefully' means that it does not overwrite
# differing files if they already exist and will not delete
# the original file if copying fails for some reason.
#
# It DOES overwrite identical files in the destination directory
# with the ones in current, however.
#
# This script was originally written and put into
# Public Domain by Jarno Elonen ; in June 2003.
# Feel free to do whatever you like with it.

BASEDIR="/media/Media/My Documents/My Pictures"

DISKDIR="/media/disk/DCIM"

cd $DISKDIR
find -maxdepth 2 -name "*.JPG" | while read x; do
DATE=`exiftags "$x"| \
	egrep "^[ t]*Image Created:"|sed -r "s/Image Created: ([0-9:]*).*/\1/"`	

if [ ! -z "$DATE" ];
then
	YEAR=`echo $DATE | sed -r "s/([0-9]*):([0-9]*):([0-9]*)/\\1/"`    
	MONTH=`echo $DATE | sed -r "s/([0-9]*):([0-9]*):([0-9]*)/\\2/"`
	DAY=`echo $DATE | sed -r "s/([0-9]*):([0-9]*):([0-9]*)/\\3/"`

    	if [ "$YEAR" -gt 0 ] & [ "$MONTH" -gt 0 ]
    	then
    		INSTDIR=${BASEDIR}/${YEAR}/${YEAR}_${MONTH}_${DAY}
    	install -d "$INSTDIR"
    		INSTFILE=$INSTDIR/`basename $x`
    		if [ -e "$INSTFILE" ] && ! cmp -s "$x" "$INSTFILE"
    		then
        		echo "WARNING: '$INSTFILE' exists already and is different from '$x'."
    		else
        		echo "Moving '$x'"
        		cp -ax "$x" "$INSTFILE"
        		if ! cmp -s "$x" "$INSTFILE"
        		then
        			echo "WARNING: copying failed somehow, will not delete original '$x'"
        		#else
        		#rm -f "$x"
        		fi
    		fi
    	else
    	echo "WARNING: '$x' doesn’t contain date."
    	fi
else
    	echo "WARNING: '$x' doesn't contain date."
fi

done

```
My next question is how do I make a progress bar with Zenity?

---

### Post by geirha on 2007-11-05
> **ncwilde43 said:**
> 
```

    	if [ "$YEAR" -gt 0 ] & [ "$MONTH" -gt 0 ]

```

You seem to have a little bug here. Single **&** will send the first command **[ "$YEAR" -gt 0 ]** to the background, and it won't get evaluated. Only $MONTH>0 will. Boolean and is **&&**, which is probably what you want here.
```

$ if [ -1 -gt 0 ] & [ 1 -gt 0 ]; then echo true; else echo false;fi
[1] 7294
true

$ if [ -1 -gt 0 ] && [ 1 -gt 0 ]; then echo true; else echo false;fi
false

```

> **ncwilde43 said:**
> 
My next question is how do I make a progress bar with Zenity?

```
man zenity
``` there's an example at the end.

---

