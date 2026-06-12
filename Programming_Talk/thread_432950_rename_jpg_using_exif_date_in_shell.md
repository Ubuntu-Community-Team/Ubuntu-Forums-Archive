---
title: "rename jpg using exif date in shell"
date: 2007-05-04
forum: Programming Talk
---

### Post by koho on 2007-05-04
Hi, I have a lot of pics taken with different cameras and want to put them in cronological order.
I found a program that rename them according to exif date, but I don't want the files to be **2007-05-02 12:20:44.jpg**
I just want **pic1.jpg pic2.jpg**
Is there a way to make shell list jpegs in order of date and time (EXIF, not creation or modify date)?
If I find that I can write a bash script to rename them progressively.

Thank you
koho

---

### Post by lloyd_b on 2007-05-04
> **koho said:**
> Hi, I have a lot of pics taken with different cameras and want to put them in cronological order.
I found a program that rename them according to exif date, but I don't want the files to be **2007-05-02 12:20:44.jpg**
I just want **pic1.jpg pic2.jpg**
Is there a way to make shell list jpegs in order of date and time (EXIF, not creation or modify date)?
If I find that I can write a bash script to rename them progressively.

Thank you
koho

Here's a script I put together that does pretty much what you ask for.  First off, it requires that you have the "exif" package installed (it uses it to extract the date/time).  Second issue is that if by some chance two files have the same date/time stamp (unlikely, but possible), then one of them won't be processed.

Give it a try (but I recommend backing up the files first - this script has not been extensively tested):
```
#!/bin/bash

# Get a list of all jpeg files files in the current directory.  Assumes extensions of 
# ".jpg" or ".JPG"
LIST1=`ls *.jpg *.JPG`

# Loop through the list, renaming each to a date/time based name
for CURFILE in $LIST1; do
        EXIFDATE=`exif $CURFILE | grep "Date" | grep -v "(" | cut -d '|' -f 2 | tr ' ' '_'`
        mv -u $CURFILE $EXIFDATE.jpg
done

# Get the list of files, which by default will be in sorted order
LIST2=`ls *.jpg`

# Set up a counter for the file names
COUNTER=1

# Loop through list2, renaming as "pic###.jpg"
for CURFILE in $LIST2; do
        NEWNAME="pic$COUNTER.jpg"
        mv $CURFILE $NEWNAME

        # Increment COUNTER
        COUNTER=$((COUNTER + 1))
done
```

Lloyd B.

---

### Post by koho on 2007-05-04
thank you for your answer.
I modified your script to add these features:
-auto-convert spaces in underscore (your script crashed with spaces in filename)
-numbering with 3 leading zeros for avoiding pic20.jpg showing near pic2.jpg in alphabetical order
-$PATH argument on script call with existence check
-$RADICE desired prefix (img, pic, etc..)

I took away the ls *.jpg because it was giving me an error, and I suppose to launch the script in a dir containing only jpgs. Feel free to add this check if you want!
I wrote very few code, it has been mainly a copy-paste from other scripts on the net.

Give it a try and tell me what you think.
I can't understand why I had to put expicit /usr/bin/command.
Am I the only one with the need of merging pics from different cameras?   ;-)

Thank you a lot for your help!
Have a nice day
koho

```

#!/bin/bash
#
# Automatic rename of jpg files in exif date order
# Useful for merging pics of the same event from different cameras

if [ -z "$1" ]; then 
  echo "usage:"
  echo "$0 [directory to check] [prefix]"
  exit
fi

PATH=$1      # dir to check
RADICE=$2    # prefix of files

# check if the path has been specified with or without ending slash
slash=${PATH:(-1):1}
if [ $slash != '/' ]; then
  PATH=$PATH/
fi
if [ -d "$PATH" ];then

#Convert spaces in underscores
for FILE in $PATH*
  do
  FILE="${FILE#./*}"
  FILE="${FILE##*/}"
    NEW_NAME=`echo $FILE | /usr/bin/tr [:blank:] "_"`
    if [ "$FILE" != "$NEW_NAME" ]
         then
         /bin/mv -v "$PATH""$FILE" "$PATH""$NEW_NAME"
    fi
done

# Get a list of all files in the current directory.  
#Assumes extensions of ".jpg" or ".JPG"
LIST1=`/bin/ls $PATH`

# Loop through the list, renaming each to a date/time based name
for CURFILE in $LIST1; do
        EXIFDATE=`/usr/bin/exif $PATH$CURFILE | /bin/grep "Date" | /bin/grep -v "(" | /usr/bin/cut -d '|' -f 2 | /usr/bin/tr ' ' '_' | /usr/bin/tr ':' '=' | /usr/bin/cut -c -19`
        /bin/mv -u $PATH$CURFILE $PATH$EXIFDATE.jpg
done

# Get the list of files, which by default will be in sorted order
LIST2=`/bin/ls $PATH`

# Set up a counter for the file names
TEMP1=1

# Loop through list2, renaming as "$RADICE###.jpg"
for CURFILE in $LIST2; do

        # Increment COUNTER with 3 leading zeros
        COUNTER=$(/usr/bin/seq -f '%03g' $TEMP1 $TEMP1)
        TEMP1=$((TEMP1 + 1))

        NEWNAME="$RADICE$COUNTER.jpg"
        /bin/mv $PATH$CURFILE $PATH$NEWNAME

done
else
  echo "directory '$PATH' doesn't exist!"
fi
# end

```

---

### Post by lloyd_b on 2007-05-05
> I can't understand why I had to put expicit /usr/bin/command.
Because of the variable PATH.  PATH is a standard shell variable that specifies which directories to search for an executable file.  When you replace it with the directory to be processed, the shell can no longer find those executables.

Try changing it to MYPATH or something (anything but PATH) and you should be able to get rid of the "/usr/bin/" prefix on those commands.

Lloyd B.

---

### Post by koho on 2007-05-05
that's the mistery! thank you
Actually I have no problems leaving /usr/bin, it was just a matter of curiosity.

see you
koho

---

### Post by ak4good on 2010-08-30
I realize this is an old thread, but just in case someone finds it through a search engine..

I've also rolled custom shell scripts to do this sort of thing, then found exiv2, which can do this out of the box:


exiv2 [COLOR=#660033]-r[/COLOR] [COLOR=#FF0000]'%Y-%m-%d_%H%M%S_:basename:'[/COLOR] rename myfile.jpgwould rename myfile.jpg to exif date e.g. 2010-05-01_154566_myfile.jpg

It's in Debian/Ubuntu repos, apt-get it. For more see "man exiv2"

[http://giantdorks.org/alain/rename-jpeg-files-with-exif-date-using-exiv2/](http://giantdorks.org/alain/rename-jpeg-files-with-exif-date-using-exiv2/)

---

### Post by Mujaheiden on 2011-08-21
so its

> exiv2 -r '%Y-%m-%d_%H%M%S_:basename:' rename *.JPG

---

