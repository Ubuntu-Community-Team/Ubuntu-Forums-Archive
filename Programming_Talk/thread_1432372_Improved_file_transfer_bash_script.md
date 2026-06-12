---
title: "Improved file transfer bash script"
date: 2010-03-17
forum: Programming Talk
---

### Post by blur xc on 2010-03-17
I'm a total bash beginner and I've been working on this off and on, for months now, and I think I've finally got it (almost).  It's quite an exercise in overkill- but the primary purpose was for my own education in bash scripting, and secondary to that was to make transferring files from my memory cards to the computer easier.

I posted an earlier version a while ago- and here's the updated script.  What it does is check to see if an appropriate memory card is mounted, and find the directory to where it is mounted.  Then, it checks to see if there are any files on the memory card.  If there are, then it checks to see of the destination directory already exists, and if not, create it.  Then it proceeds to copy the files to the destination directory, and verifies that each file copied transfered successfully.  If there is a problem, it will try to copy the same file three more times before giving up, and recording the filename into errors.txt.  It keeps a status of what files are left to copy in recovery.txt.  If for whatever reason the transfer is interrupted (camera battery dies, usb cable is accidentally yanked out of the computer, power outage and my UPS fails, whatever), the script halts.  I've only simulated this, I've yet to actually try pulling the cf card out of the computer while it's running.  Then, if you remount the media and run the script again, it will attempt to resume where it left off until all files are copied, and then it displays a status message.  

It could probably use a bit of cleaning up but feel free to comment on it-

I've gotten a lot of help from forum members on this- 
```
#!/bin/bash

COUNT=0
ERRORS=0
DESTINATION=`date +%Y/%Y-%m-%d`
SRCPATH=`find /media/disk* -name dcim -type d 2> /dev/null`
RETRY=0

## Copy files and verify integrity of copied file
function copy {
    cp -v "$1" $DESTINATION
    NAME=`basename "$1"`
    #corrupt "$NAME" $RETRY # Corrupt a file or two for testing
    if cmp -s "$1" "$DESTINATION/$NAME"; then
        sed -i "/$NAME/d" recovery.txt
    else
        RETRY=$[$RETRY+1]
        if [ $RETRY -le 3 ]; then
            copy "$1"
        else
            echo "File $NAME contains errors" >> errors.txt
            ERRORS=$[$ERRORS+1]
        fi
    fi
    RETRY=0    
}

## This function is to corrupt a file for debugging purposes
function corrupt {
if [ "$1" = "file 000.txt" ] || [ "$1" = "file 001.txt" ]; then
        if [ $2 -lt 2 ]; then
            echo "Corrupted File" > "$DESTINATION/$NAME"
        fi
    fi
}


## MAIN part of program starts here
echo
echo "Preparing to transfer files..."
echo

##  Check for source files, and if found
##  sends their paths to a temporary file
if [ -z $SRCPATH ]; then
    echo "Cannot find source directory" >&2
    exit 0
elif [ -s recovery.txt ]; then
    echo "Recovering failed previous transfer"
    cp -f recovery.txt tmp.txt 
else
    find $SRCPATH -type f | sort > tmp.txt
    cp tmp.txt recovery.txt
    FILES=`wc -l < tmp.txt`
    if [ $FILES -eq 0 ]; then
        echo "No files found.  Check media and try again" >&2
        exit 0
    else 
        echo "$FILES files found on $SRCPATH/"
    fi
fi

echo

## Check for destination directory and 
## create if needed
if [ -d $DESTINATION ]; then
    echo "Destination directory already exists"
else
    mkdir -pv $DESTINATION
fi

echo

## Read file paths from temporary file
while read FILE; do
    if [ -d $SRCPATH ];then
        copy "$FILE"
        COUNT=$[$COUNT+1]
        #if [ $COUNT -eq 5 ];then
        #   mv ~/bin/media/disk ~/bin/media/disk_1
        #fi
    else
        echo "Source path could not be found.  Check media and try again"
        exit
    fi
done < tmp.txt

## Status report
echo "$COUNT file(s) copied with $ERRORS error(s)." > logfile.txt
if [ -f errors.txt ]; then
    cat errors.txt >> logfile.txt
fi
echo >> logfile.txt
echo && cat logfile.txt 

cat tmp.txt >> logfile.txt
rm tmp.txt -f
rm errors.txt -f 
```

The logging system needs improvement, and I'll probably have it use ~/tmp to store the temp files, and maybe date code the logfiles.  I just realized I don't have any code that removes the recovery.txt file either...  Also, last night when I transfered photos, I found that when the card mounted, all the directory and filenames were lower case.  Normally, for the past tens of thousands of photos, they've been all uppercase- so my next deal will be to make it case insensitive when it searches for the source path- I know there's a way- seen it somewhere.  I'll have to look that one up.

Either way, it's been a fun project.

Just for kicks- here's the original script I was using before I got all carried away:

```
#!/bin/bash
# Script to make folder for photos
FOLDER=`date +%Y/%Y-%m-%d`

# Check if folder already exists and make one if it doesn't
if [ -d ./$FOLDER ]
then 
    echo "Folder ./$FOLDER already exists"
else
    mkdir -vp $FOLDER
fi

find /media/disk/DCIM -type f -exec cp -v '{}' ./$FOLDER \;

exit 0
```

Thanks,
BM

---

