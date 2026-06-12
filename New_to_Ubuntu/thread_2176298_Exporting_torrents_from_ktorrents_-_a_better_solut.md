---
title: "Exporting torrents from ktorrents - a better solution"
date: 2013-09-23
forum: New to Ubuntu
---

### Post by parazythum on 2013-09-23
Hello,

I wanted to extract the .torrents from ktorrent, which are stored in a temp directory, each torXXX directory containing a file named "torrent", which is a backup of the original .torrent file.

If found a solution in this (closed) thread : [http://ubuntuforums.org/showthread.php?t=1248292](http://ubuntuforums.org/showthread.php?t=1248292)

BUT all the saved files were named TORXXX.torrent - whoops, what if I have a hundred torrents stored ? How can I know which is which ?

So I wrote a script, taking what was good from the other solution, to extract the display name of the torrent, and if none was found extract it from the file map, which contains the directory where the downloaded files are stored (hopefully named accordingly to the torrent description).

Here we go :
```

#!/bin/sh

#You can find the information below in the directory options in ktorrent
#This is where the temp files are stored
INPUT_DIR=/media/DataCo2/Downloads/Torrent
#This is where we will save the exported .torrent
DEST_DIR=/media/DataCo2/Downloads/Torrent.backup
#This is where the downloaded file are stored
DOWNLOAD_DIR=/media/DataCo2/Downloads/Incoming/

#Delete all files in the dest dir - uncomment this line if needed
#rm $DEST_DIR/*

#If a dest dir is specified in the command line
if [ "$#" -ge "2" ]
then DEST_DIR="$1"
fi

#Create the dest dir if it doesn't exist
if ! [ -e "$DEST_DIR" ]
then mkdir -p "$DEST_DIR"
fi

#Working dir
cd $INPUT_DIR

#Create torrent list
TORRENT_LIST=

if [ -e tor0 ]
then TORRENT_LIST="$TORRENT_LIST tor?"
fi

if [ -e tor10 ]
then TORRENT_LIST="$TORRENT_LIST tor??"
fi

if [ -e tor100 ]
then TORRENT_LIST="$TORRENT_LIST tor???"
fi

#Extract the name of each torrent and copy the file
for  i in $TORRENT_LIST ; do
  #Find the name in "stats"
  torrent_name=$(cat $i/stats |grep "DISPLAY_NAME=")
  torrent_name=$(echo ${torrent_name#DISPLAY_NAME=})
  #If the display name is null, we can find the original torrent name in the files list (in "file_map")
  if [ -z "${torrent_name}" ]; then
    line=$(head -n 1 $i/file_map)
    line=$(echo ${line#$DOWNLOAD_DIR})
    line=$(echo ${line%%/*})
    torrent_name=$line	
  fi
  
  #Treat duplicate file names
  if [ -e  "$DEST_DIR/$torrent_name.torrent" ]; then
    while [ -e  "$DEST_DIR/$torrent_name.torrent" ];
      do
        #Add a "-" character to the file name as much as needed
        torrent_name=$torrent_name-
        echo "file exists"
    done   
  fi 

  echo $torrent_name
  #Copy the torrent file
  cp -vRTpu $i/torrent "$DEST_DIR/$torrent_name.torrent"
done

```

Enjoy !

---

