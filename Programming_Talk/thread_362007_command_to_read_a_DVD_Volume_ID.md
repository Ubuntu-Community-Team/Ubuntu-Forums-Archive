---
title: "command to read a DVD Volume ID"
date: 2007-02-15
forum: Programming Talk
---

### Post by pozitron969 on 2007-02-15
Hello,

I am writing a shell script to catalog files that I have written to DVD.  My question is how do I read what the volume ID is from a disc that I have in my machine from a command line.  

The DVD's were created with GnomeBaker and were labelled like music_01 or video_02, which is also the same text that I wrote on the exterior of the discs.  I am trying to produce a list so that I can pop a dvd in the drive, run a shell script, and append the file listing as output to a file.  The format of the file would be very simple such as

volume_ID:pathname/filename
music_01:/rock/song.mp3
music_01:/rock/ballad.mp3
video_02:/birthday/presents.mpg
video_02:/birthday/cake.mpg

I can get the file listing how I want it but reading the volume_id has me stumped.  And I plan on grep'ing the file to get the data out that I want, so there is no need for a fancy interface.

Any suggestions would be helpful.  Thank you.

---

### Post by gcobbum on 2008-09-03
I haven't found a command for this, but a practical workaround, for Hardy at least, is this:

```
#!/bin/bash

#	Get volume label of last CD/DVD mounted.

VLABEL=$( cat /var/log/debug | grep -E 'devices/volume_label_' | tail --lines 1 )
VLABEL=${VLABEL#*devices/volume_label_}
VLABEL=${VLABEL%\'*}
echo $VLABEL

#	List all files on CD/DVD with volume label and full path.
#	Separate volume label with tab so can sort by file when merged into catalog file.

find /media/cdrom/ -name "*" -type f -printf "$VLABEL\t%p\n" | sed 's/\/media\/cdrom\///' >dvd_list

#	Visual check of listing.

gedit dvd_list

```

---

### Post by ghostdog74 on 2008-09-03
```

label=$(isoinfo -d -i /dev/cdrom | awk -F": " '/Volume id/{print $2}')

```

---

### Post by gcobbum on 2008-09-04
Thanks for the command, but it doesn't work if the disk was written without iso9660. :(

---

