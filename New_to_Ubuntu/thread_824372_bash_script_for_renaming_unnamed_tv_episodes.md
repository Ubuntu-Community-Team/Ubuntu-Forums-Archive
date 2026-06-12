---
title: "bash script for renaming unnamed tv episodes"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by uncannybuzzard on 2008-06-10
ok, i hate it when i download a torrent of a season of a show i like and the files are all named something like "simpsons.season1.episode2.WaNKErsx.avi" and don't have the proper episode names. so i wrote a script to rename them with the episode number and proper title, i.e., "02 - USA Fun Society.avi"
there are a couple caveats though as this it pretty much a 0.1 version. you must rename the files to the episode number.extension (01.avi, 02.avi, etc.) and the titles must be in a file without an extension in a straight list, one title per line. you can grab season titles pretty easily at epguides.com, just copy them into a text editor and then vi or nano them into an extensionless file. like i said, this is still pretty alpha, i just whipped it up, so any suggestions are welcome.

```
#!/bin/bash

#VARIABLES#
read -p "Please enter the location of the file containing the episode names: " loc
eps=`ls *.* | sed 's/\(.*\)\..*$/\1/'`
num=`ls *.* | wc -l`
titlenum=`cat $loc | wc -l`
###########

if [ $num != $titlenum ]; then

	echo "The number of episodes and the number of titles do not match. Exiting."
	exit 0

fi

for X in $eps

do

        title=`head -n $X $loc | tail -n 1`
	ext=`ls $X* | sed 's/.*\(\..*$\)/\1/'`
        file=`ls $X*`
        echo "$X - $title$ext"
        mv $file "$X - $title$ext"
	ext=NULL

done

exit 0
```

the number of extensioned files in the directory must match the number of titles in the title file. you can rename most garbled torrent names to 01.avi, 02.avi format fairly easily with thunar bulk rename or any similar program.

---

