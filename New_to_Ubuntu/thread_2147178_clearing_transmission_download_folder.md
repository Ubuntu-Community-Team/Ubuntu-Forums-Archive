---
title: "clearing transmission download folder"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by mike551345 on 2013-05-21
I recently set up my server to be used as a torrent server. Im using transmission as my torrnet client but i need help on clearing the objects that where downloaded. My server has a small hard drive so i need to clear it in order to do more stuff with my server. im using a server with a command line just and fyi. also i cant delete the contents from a ssh folder connection.

---

### Post by asensio on 2013-06-03
Hi, mike551345

I believe this script [[shared at the Transmission Foruns]("https://forum.transmissionbt.com/viewtopic.php?f=1&t=13427")] is what you need. It deletes the torrent from transmission queue and the downloaded data after X days. The default is 10 days but you can change it. You also need to set your TARGET (path to download folder), USERNAME and PASSWORD to Transmission.

I never used this script because I need it to search recursively inside TARGET. Does anyone know how to do this?

```
#!/bin/sh

# Automatically remove a torrent and delete its data after a specified period of
# time (in seconds).

TARGET=This is where you put your completed torrents.
USER=Username
PASS=Password
BIN="/usr/bin/transmission-remote"

# The default is 10 days (in seconds).
CUTOFF=`expr 86400 \* 10`

##############################################
### You shouldn't need to edit below here. ###
##############################################

# Tokenise over newlines instead of spaces.
OLDIFS=$IFS
IFS="
"

for ENTRY in `$BIN -n $USER:$PASS -l | grep 100%.*Done.*Finished`; do

    # Pull the ID out of the listing.
    ID=`echo $ENTRY | sed "s/^ *//g" | sed "s/ *100%.*//g"`

    # Determine the name of the downloaded file/folder.
    NAME=`$BIN -n $USER:$PASS -t $ID -f | head -1 |\
         sed "s/ ([0-9]\+ files)://g"`

    # If it's a folder, find the last modified file and its modification time.
    if [ -d "$TARGET/$NAME" ]; then
        LASTMODIFIED=0
        for FILE in `find $TARGET/$NAME`; do
             AGE=`stat "$FILE" -c%Y`
             if [ $AGE -gt $LASTMODIFIED ]; then
                 LASTMODIFIED=$AGE
             fi
        done

    # Otherwise, just get the modified time.
    else
        LASTMODIFIED=`stat "$TARGET/$NAME" -c%Y`
    fi

    TIME=`date +%s`
    DIFF=`expr $TIME - $LASTMODIFIED`

    # Remove the torrent if its older than the CUTOFF.
    if [ $DIFF -gt $CUTOFF ]; then
        date
        echo "Removing $NAME with ID:$ID"
        $BIN -n $USER:$PASS -t $ID --remove-and-delete
    fi

done

IFS=$OLDIFS
```


Hope it helps,
Cheers
**asensio**

---

### Post by Cheesehead on 2013-06-03
You seem to be discussing two actions:
1) Copy a file from your torrent server to somewhere else
2) After copy, delete the torrent and file

Here is an example of one way to do it.
Let's say you have a desktop and a server, and you just finished downloading the Foo torrent.

- On the desktop, install the sshfs package. That mounts the server files so they appear in your normal desktop file manager. Simply drag-and-drop /media/server/downloaded/Foo to /home/you/Foo. You could also use scp or wget or lots of other tools.

- On the server, enable the web client. On the desktop, open a browser to http://<server_ip>:9091/transmission/web/ . Use the web client connection to the server to delete torrents and data after the copying is complete.

It's possible to make things simpler or much more complex, depending upon your desire. For example, transmission sends a dbus signal when a torrent download is complete and another when a torrent upload is finished. You could have a script on the server captures that signal, scp the data to your desktop, delete the torrent, and send you an e-mail (or other notification to the desktop). You'll need to do a bit of time-consuming research and python hacking and experimentation to make that all work,  of course.

---

