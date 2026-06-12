---
title: "[SOLVED] Change last modified date and time of all files in a directory?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by gn2 on 2008-09-04
I have a problem with an mp3 car stereo that can only play files in the order they were last modified.

Unfortunately the last modified dates/times of files in my music folders don't always follow the filenames, so When ordered by last modified date/time the tracks are not in order.

What I've been trying to find is a command that will alter the last modified date and time of all files in a folder to match the file names, so that when ordered by last modified date/time the files/tracks are in the correct order.

I found info on the web about the "touch" command and I've looked at the help, but I can't figure out how to batch change the last modified date/time of a bunch of files by name order inside a directory. 

All help gratefully received by a clueless CLI-phobe.

---

### Post by Pro-reason on 2008-09-04
Go to where your music files are (using the *cd* command).

Type ```

nano reorder.sh

```

Paste the following into the window (using the middle mouse button):

```
[B]#!/bin/bash
LIST="$(ls)"
 
for file in $LIST; do

 if [ ! -e $file ]; then
  echo "The file \"$file\" doesn't seem to exist."
  echo "It probably has a space in it."
 else
  echo "Updating \"$file\"."
  touch '$file'
 fi

done

exit[/B]


```

Press &#8220;Ctrl-X&#8221; to exit.  &#8220;Y&#8221; to save.  &#8220;Enter&#8221; to confirm the file name.

Type this on the command line:

```

chmod +x reorder.sh
./reorder.sh

```

Your files will be put in the right order.

This won't work on files with spaces or other special characters in the name.

---

### Post by Pro-reason on 2008-09-04
Here is a better version of the script.  It will work with spaces in the filenames.

```
[B]
#!/bin/bash

echo "Your files are currently in this order:"

ls -Ghlct

echo -en "\nUpdating "

ls -1 | while read FILE
do
 echo  -n "\"$FILE\", "
#sleep 1s
 touch -c "$FILE"
done

echo -e "\n\nHere is your new listing:"

ls -Ghlct

exit[/B]

```

This will run through the files and set their timestamps in alphabetical order.  There will only be a difference of a few milliseconds between each one.  If this is not enough for your device, uncomment (by removing the hash sign) the &#8220;sleep 1s&#8221; line.

Edit:

Here's a less fancy, bare-bones, one-line version, that doesn't necessitate the creation of a script, or give you any feedback:

```

ls -1 | while read FILE; do touch -c "$FILE"; done

```

Just input that on the command line.

---

### Post by gn2 on 2008-09-05
Excellent! You're a star Pro-reason!

The second script you created works perfectly, the reorder executable does *exactly* what I needed and is a very handy little tool indeed.

You've made me a very happy chappy! :D

---

### Post by almalaci on 2010-10-19
Thanks a lot Pro-reason, 

This solves my exact same problem with my car stereo, almost.
I have my albums (a lot of them) in separate folders so I needed the command to work for all the subfolders too.
So even though no-one asked for it, here's another tweaked version of the script that does it recursively. Someone else might find it useful.


```
[B]#!/bin/bash

echo "Your files are currently in this order:"

ls -Ghlct

echo -en "\nUpdating "

ls -1 | while read FILE
do
 echo  -n "\"$FILE\", "
#sleep 1s
 find . -print0 | xargs -0 touch -c "$FILE"
done

echo -e "\n\nHere is your new listing:"

ls -Ghlct

exit[/B]
```

---

