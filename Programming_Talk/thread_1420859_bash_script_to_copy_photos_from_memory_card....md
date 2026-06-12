---
title: "bash script to copy photos from memory card..."
date: 2010-03-03
forum: Programming Talk
---

### Post by blur xc on 2010-03-03
I've been studying the linux command line and bash scripting off and on ever since I started using Linux (less than a year ago) and to help myself learn I've been working on this project-

It's a script to transfer files from my camera's compact flash card to a specific folder, named by date.  Every photo manager program does things differently and none do anything the way I want (except for Lightroom, but that's still not automatic, and it's only in Windows), so I saw this as an opportunity to both learn and make something useful.

Here's the script (version 0.0.0-0001 - j/k):
```
#!/bin/bash
## Script to copy files from compact flash card
## to a specific directory

echo
echo "Preparing to transfer files..."
echo
FILEPATH=`date +%Y/%Y-%m-%d`  ## Create folder path
COPIES=0
ERRORS=0

## Check if memory card is mounted at the correct location,
## check again if destination directory exists, and if
## not, create it, then find files on memory card and 
## copy them to the specified directory.
if [ -d /media/disk/DCIM ];then
    if [ `find /media/disk/DCIM -type f | wc -l` -eq 0 ];then
        echo "Memory card appears to be empty,"
        echo "please check card and try again."; echo
        exit 0
    else
        if [ -d $FILEPATH ]; then
            echo "The directory already exists"
        else
            mkdir -pv $FILEPATH
        fi
        echo
        find /media/disk/DCIM -type f -exec cp -v '{}' $FILEPATH \;
     fi
else
    echo "Memory card not found"
    exit 0
fi

## Verify that each file copies without any errors
echo
echo "Verifying integrity of destination files..."
while read FILE; do
    COPIES=$[$COPIES+1]
    NAME=`echo $FILE | cut -f5 -d"/"`
    if ! cmp -s "$FILE" "$FILEPATH/$NAME";then
        echo "There was a problem copying $NAME"
        ERRORS=$[$ERRORS+1]
    fi
done < <(find /media/disk/DCIM -type f) 

## Report status
if [ $ERRORS -gt 0 ];then
    if [ $ERRORS -eq 1 ];then
        echo "$COPIES files copied with $ERRORS error"
    else
        echo "$COPIES files copied with $ERRORS errors"
    fi
else
    if [ $COPIES -eq 1 ];then
        echo "$COPIES file copied successfully"
    else
        echo "$COPIES files copied successfully"
    fi
fi
echo
exit 0
```

There are a lot of improvements I think I can make to the code- which I'll work on.  One is to remove all the redundant find commands and use a variable array.  I haven't don't that in bash yet.  Also, maybe use functions as well- which would help with future additions to the script.  I would like to create a function that retries the copy on any files that may have been corrupted in the transfer (almost never happens, but has happened in the past, albeit on an old XP machine and a bad usb card reader) an x number of times before faulting out if the file cannot be copied w/o errors.

I'm trying to make this script as robust as possible.  I'm still way to scared to have it erase the memory card data on it's own.  I still like to see the files in the destination folder w/ my own eyes and wipe the card on my own.  I'm just a big chicken.  I could not begin to imagine my wife's anger if I wiped 200 photos of the family on vacation because my script had a bug in it.

I've received a bit of help here and there from the forums- this is a great place to learn.

Thanks!
BM

---

### Post by DaithiF on 2010-03-03
Hi thanks for sharing.  Just a few minor suggestions
1. for the report status at the end, its quite a lot of code just to get the pluralisation of the words file & error right, a suggestion to avoid all this would something like:

```
printf "%d file%s copied with %d error%s\n" $COPIES $( [ $COPIES != 1 ] && echo "s") $ERRORS $([ $ERRORS != 1 ] && echo "s")

```

2. you repeat the path to the images a few times, better to define it once as a variable and then use that variable name in the rest of the script.  That way if you get a new camera which has a different path you only have to change one line rather than several
```
MEDIA_PATH=/media/disk/DCIM

```

3. this line: 
```
NAME=`echo $FILE | cut -f5 -d"/"`

```
depends on the path to the file being a known number of directories deep.  better to do it like:```

[CODE]NAME=${FILE##*/}
```
[/CODE]or
```
NAME=$(basename $FILE)

```

happy scripting!

---

### Post by blur xc on 2010-03-03
Thanks for the suggestions!  I did realize that I was putting a lot of effort into getting the pluralization correct on my status report- when I could just cheat are wrote file(s) and error(s), but I'm anal that way I guess.  Even after all that, there is still one bug.  If I copy just one file and have an error, it will print "1 file**s** copied with 1 error"...   I don't want to nest won more if-then in there.  I'll study your code and stick it in my script.

My line with the cut command also bothered me.  I'll look forward to axing that as well.  As for the file path, the mount point can change, disk, disk-1, etc.., and I would like in the end to have the script query mounted file systems and find the correct path for the memory card.  99% of the time it mounts at /media/disk, so for the most part I think I'll manage until I get the rest figured out.

Right now I'm trying to figure out how to assign a variable to the find command, so I don't need ot rewrite it over and over again.  I thought I could use a variable array, but it seems I don't know how to assing the ouput of the find command to an array.  So far I have:
```
FILES=`find /media/disk/DCIM -type f`
for FILE in "$FILES"; do
   echo "$FILE"
done
```
and the output is good- but I don't understand why it works.  I don't like not knowing why my script works.  If I just enter "echo $FILES" I get a massive jumble of file names, not an array.  So, I don't know how the for command knows to delimit the massive string of filenames.

I am a little afraid though, how long it will take my script to verify 4gb of copied files.  right now I'm just testing it on empty files (touch file{1..100}).  

Anyway- thanks for your input.

BM

---

### Post by pickarooney on 2010-03-08
My one looks like this, for comparison's sake:
```

#!/bin/bash

changesize=$1
CAM=/media/disk
PIX=/home/pickarooney/Pictures

if [ ! -d $CAM ]
then
  echo "Cannot find a digital camera. Is it plugged in at all?"
  exit
fi

if [ -f ~/.getpixdir ]
then
  PIXDIR=`cat ~/.getpixdir`
else
  PIXDIR="."
fi

echo "Please enter a directory name for the pictures"
echo "(press ENTER to use previous: $PIXDIR )"
read NEWDIR 

if [ "$NEWDIR" == "" ]
then
  DIRPATH="$PIXDIR"
else
  DIRPATH="$NEWDIR"
fi
echo "files going into $DIRPATH"
echo "$DIRPATH" > ~/.getpixdir

mkdir -p $PIX/"$DIRPATH"/tmp
echo "Copying photos..."

mv $CAM/DCIM/*/*.* $PIX/"$DIRPATH"/tmp

cd $PIX/"$DIRPATH"/tmp
/home/pickarooney/scripts/downall

if [ "$changesize" != "" ]
then
  mogrify -resize 1024x768! $PIX/"$DIRPATH"/tmp/*.jpg
fi

echo "Please enter the theme for these pictures($DIRPATH):"
read theme
cd $PIX/"$DIRPATH"/tmp
if [ "$theme" == "" ]
then
  theme=`basename "$DIRPATH"`
fi
  
/home/pickarooney/scripts/themepix "$theme"
/home/pickarooney/scripts/themevid "$theme" 2>/dev/null

mv $PIX/"$DIRPATH"/tmp/*.* $PIX/"$DIRPATH"/

rmdir --ignore-fail-on-non-empty $PIX/"$DIRPATH"/tmp

```

No find commands, but it's not all that generic I suppose (I've tweaked it each time I changed camera which is about once every three years).

---

### Post by blur xc on 2010-03-09
> **pickarooney said:**
> My one looks like this, for comparison's sake:
```

#!/bin/bash

changesize=$1
CAM=/media/disk
PIX=/home/pickarooney/Pictures

if [ ! -d $CAM ]
then
  echo "Cannot find a digital camera. Is it plugged in at all?"
  exit
fi

if [ -f ~/.getpixdir ]
then
  PIXDIR=`cat ~/.getpixdir`
else
  PIXDIR="."
fi

echo "Please enter a directory name for the pictures"
echo "(press ENTER to use previous: $PIXDIR )"
read NEWDIR 

if [ "$NEWDIR" == "" ]
then
  DIRPATH="$PIXDIR"
else
  DIRPATH="$NEWDIR"
fi
echo "files going into $DIRPATH"
echo "$DIRPATH" > ~/.getpixdir

mkdir -p $PIX/"$DIRPATH"/tmp
echo "Copying photos..."

mv $CAM/DCIM/*/*.* $PIX/"$DIRPATH"/tmp

cd $PIX/"$DIRPATH"/tmp
/home/pickarooney/scripts/downall

if [ "$changesize" != "" ]
then
  mogrify -resize 1024x768! $PIX/"$DIRPATH"/tmp/*.jpg
fi

echo "Please enter the theme for these pictures($DIRPATH):"
read theme
cd $PIX/"$DIRPATH"/tmp
if [ "$theme" == "" ]
then
  theme=`basename "$DIRPATH"`
fi
  
/home/pickarooney/scripts/themepix "$theme"
/home/pickarooney/scripts/themevid "$theme" 2>/dev/null

mv $PIX/"$DIRPATH"/tmp/*.* $PIX/"$DIRPATH"/

rmdir --ignore-fail-on-non-empty $PIX/"$DIRPATH"/tmp

```No find commands, but it's not all that generic I suppose (I've tweaked it each time I changed camera which is about once every three years).

Thanks for posting your script.  It's very interesting to see another method to get the job done.

I'm assuming themepix is another script?

I never thought of doing "mv $CAM/DCIM/*/*.* $PIX/"$DIRPATH"/tmp".  I didn't think you could use a wild-card in the middle of a path like that to search all possible sub-directories.  

My only comment would bet that I don't think you need the *.*'s all over the place.  A simple * would do the trick- as Linux doesn't pay attention for file extensions, unless of course you are intentionally not moving files that do not have a . in the middle somewhere.

BM

---

### Post by GrouchyGaijin on 2013-04-22
As long as we are sharing camera scripts, I thought I'd throw mine into the mix.
Mine is no where nearly advanced as yours.

```

#!/bin/bash 
echo "Unload_camera version 3: This script will remove images and videos from your camera."
echo "Basic script by GrouchyGaijin. Heavy lifting by schragge. Additional modifications by cortman, steeldriver, and ofnuts"
echo "Run this script from the camera"  
now=$(date +"%d-%b-%Y-%T")
mkdir /path/to/where/you want/the/pictures/put/$now 
echo "Making directory to hold the photos."


dir="/path/to/clips/directory"
read -p "Press Enter to check if the clips directory is empty"
if [ "$(ls -A $dir)" ]; then
     echo "Clips is not empty. Did you forget to empty it last time? Type yes to empty the directory"
fi 
echo "If files had been found, you would have seen a message saying so."
read x
if [ "$x" = "yes" ]
then
rm -f "$dir"/* 
else
echo "OK, Leaving the directory as is."
fi 
                 
pics_dir="/path/to/$now"
clips_dir="/path/to/clips"


process_image() {
  echo "Moving $1 to $pics_dir"
  mv "$1" "$pics_dir"
  echo "Resizing $1"
  gm mogrify -resize 720x720 "$pics_dir/$1"
}
process_video() {
  echo Moving "$1" to $clips_dir
  mv "$1" "$clips_dir"
}


process_thumbnail() {
  echo Removing "$1" from the camera
  rm "$1"
}


unload() {
  case $1 in
    image) pattern='*.jpg *.JPG *.png *.PNG *.GIF *.gif';;
    video) pattern='*.MOV *.mov *.mpg *.MPG *.mpeg *.mp4';;
    thumbnail) pattern='*.THM';;
    *) echo Unknown file type, aborting...; exit 1;;
  esac
  echo Press Enter to search for $1 files; read start


  unset found
  for i in $pattern; do
    if [[ -f $i ]]; then
      [[ -v found ]] || echo ${1^}s found.
      : ${found:-set}
      process_$1 "$i"
    else
      echo Skipping $i: not a regular file
    fi
  done
  [[ -v found ]] || echo No or no additional ${1}s found.
}
shopt -s nullglob
unload image
unload video
unload thumbnail
```

---

### Post by ofnuts on 2013-04-22
I use a different approach, move everything on the card to a local directory using the file manager (Ctrl-A and drag). I trust the file manager to do the right thing is there is a problem (at least I trust it more than my code, because it hass been tested a lot more thoroughly).

Then I have several scripts to run locally to distribute files around (like putting the raw files in their subdirectory). I do a first manual sorting on the JPEG to split the pictures over several directories by subject and delete the obvious misses. Then I have another script to erase the raw files matching the deleted JPEG, and another one to move raw files next to their JPEG.

---

### Post by wildmanne39 on 2013-04-22
Thread closed. Please do not post in old threads.

---

