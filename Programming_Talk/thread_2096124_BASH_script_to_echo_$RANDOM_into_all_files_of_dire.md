---
title: "BASH script to echo $RANDOM into all files of directory"
date: 2012-12-19
forum: Programming Talk
---

### Post by HypervisedEd on 2012-12-19
Hey guys, 
   First I apologize if this is in the wrong section, I am new to the ubuntuforums but I do believe this can go here.  I am trying to write a script that echos a random number into each file of a directory.  

This script does work well for me, however the issue I'm having an issue whereas when the script has completed and I list all the files of the directory it was performed on I notice that a new file name appears: $filename 

Clearly $filename is a by-product of this script.  What makes this even more bizarre is that I did not have this issue with this script until this week.  I did have to re-install Ubuntu on the remote machine I am running this on (for other reasons) & I had copied the script into the new install from my local machine so I do know that the script itself is untouched, however I'm wondering if something went wrong my bash alias of alias: hashchanger='bash /etc/hashchanger.sh' 

The permissions of /etc/hashchanger.sh are 
-rwxr-xr-x 1 root  root   

I am running this script as both root as well as a user that is not part of the root group.  Here is the script itself:

#! /bin/bash
# Echos a random number into all files of a directory except for the script itself to change the checksum of the files.

for filename in *
do
  if [ '$filename' != '$0' ]
  then
    echo '$RANDOM' >> '$filename'
  fi
done

---

### Post by HypervisedEd on 2012-12-19
Resolved!  The end result was that I needed to remove the single quote marks around $filename as such:

#! /bin/bash
# Echos a random number into all files of a directory except for the script itself to change the checksum of the files.

for filename in *
do
  if [ '$filename' != '$0' ]
  then
    echo '$RANDOM' >> $filename
  fi
done

---

### Post by ofnuts on 2012-12-19
> **HypervisedEd said:**
> Resolved!  The end result was that I needed to remove the single quote marks around $filename as such:

#! /bin/bash
# Echos a random number into all files of a directory except for the script itself to change the checksum of the files.

for filename in *
do
  if [ '$filename' != '$0' ]
  then
    echo '$RANDOM' >> $filename
  fi
done

Single quotes protect their contents from being substituted. If your filename can contains spaces you may want to enclose it in double quotes: "$filename" (the contents of double quotes are passed as a single parameter to commands)

Another way of getting a file with random contents is to use "dd" to copy bytes from the /dev/random pseudo-device:
```

dd if=/dev/random count=1 >randomized.file

```

---

### Post by rnerwein on 2012-12-19
> **HypervisedEd said:**
> Resolved!  The end result was that I needed to remove the single quote marks around $filename as such:

#! /bin/bash
# Echos a random number into all files of a directory except for the script itself to change the checksum of the files.

for filename in *
do
  if [ '$filename' != '$0' ]
  then
    echo '$RANDOM' >> $filename
  fi
done
hi
you have to remove the single quote every where or you will find in your file and on all other files on the end of the file the line: $RANDOM and not the random nunber.
to be on the saver side use: ${filename} or "$RANDOM"
even watch out if you start your script with: ./my_script this don't match with $filename !
cheers

---

