---
title: "BASH Script using Rar"
date: 2009-08-28
forum: Programming Talk
---

### Post by smc18 on 2009-08-28
Hey hey,

I want to list the contents of a folder and compress each file separately.

For example.

ls -1 /home/test

Output:
test1
test2
test3

I would the script to go to line 1 and compress test1 to test1.rar and then go to line 2 and compress test2 to test2.rar, etc.

I have a long list of media files that I would like to compress on my home machine.

Any suggestions?

EDIT:

This is how I ended up writing the script

```
#!/bin/bash
#compress2gz.sh
#Author:me
#This script will go to a folder and compress each file within the folder.


echo "The files contained within '"$1"' will be compressed."
echo "Do you want to continue? [y][n] "
read answer
echo
if [ "$answer" == "Y" ] || [ "$answer" == "y" ] ;

then

  #echo "You chose to continue!!"
  cd $1
  for myfile in *;
    do gzip -v "$myfile";
    #I ommited rar compression so I could use gzip instead.
    #rar a -m3 "$myfile.rar" "$myfile";
  done

#echo ""
#echo ""
#echo "The following files have been compressed."
#ls -1 *.*
else
echo
echo "Now closing..."
fi

```

---

