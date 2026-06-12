---
title: "Bash Sed Command - Import Photos from Media"
date: 2007-11-02
forum: Programming Talk
---

### Post by ncwilde43 on 2007-11-02
I'm trying to write my first bash script that takes the photos from my SD card and downloads them to the computer.

This is what I want the script to do:
-grab Image Created exif data from photo
-check to see if directory exists on computer in format /YYYY/YYYY_MM_DD
-create directory if not exists
-copy photos from camera to dir

Here is my problem.  The photos on my SD Card are located at /media/disk/DCIM so I change to that directory and search for all JPGs.  The problem arises when the camera automatically makes directories (ie. 124CANON, 125CANON) in the DCIM folder.

Problem: when running the script, the directories are created in the BASEDIR, but the photos are not copied from the SD card to the directories.  I'm assuming it has to do with the fact that image names are stored as  "./124CANON/image.JPG" and not just ./image.JPG.  Is there any way I can do a "sed" function on the image ("x")?

Also, is there a way that I can find both upper and lowercase (ie JPG & jpg) image extensions?

FYI: I'm a novice programmer

[REF LINK]("http://pario.no/2007/05/15/199/") 
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

BASEDIR="/home/wilde"

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
    		INSTFILE="$INSTDIR/$x"
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
    	echo "WARNING: '$x' doesn&#8217;t contain date."
    	fi
else
    	echo "WARNING: '$x' doesn't contain date."
fi

done

```

I'm also looking to do create a progress bar for the download.

Any help would be appreciated!

---

### Post by arsenic23 on 2007-11-02
To find .jpg files without worrying about the case of the extention, just use:
```
find -maxdepth 2 -iname "*.jpg"
```
or
```
find -maxdepth 2 -name "*.[jJ][pP][gG]"
```

---

### Post by ncwilde43 on 2007-11-02
> **arsenic23 said:**
> To find .jpg files without worrying about the case of the extention, just use:
```
find -maxdepth 2 -iname "*.jpg"
```
or
```
find -maxdepth 2 -name "*.[jJ][pP][gG]"
```

Thanks!

---

