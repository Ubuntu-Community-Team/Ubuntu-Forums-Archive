---
title: "Need a little help with a BASH script."
date: 2012-11-08
forum: Programming Talk
---

### Post by PinkFloyd102489 on 2012-11-08
Here's the basic rundown.

I need to be able to make a list of folders and then read those folders into the mogrify command to resize pictures inside those folders. I've already got this code set up. The problem is: I also need a way to individually read and reset the timestamp of the image file once the image has been mogrified, since mogrify systematically writes the timestamp instead of preserving the original.

This is what I have now: 
```
#Creat the dump file
touch dump

#Read the file list and drop it into the dump file
ls --ignore="*.zip" --ignore="dump" --ignore="*.sh" > dump
cat dump

#This is the magic. Read the dump file line by line, mogrify, and zip.
while read line; do
        mogrify -monitor $line/*.JPG -resize 640x430 -quality 85 $line/*.JPG
        zip -r $line.zip $line/
done < dump

#Clean the dump file
rm dump
```

This is the code to read and reset the timestamp:
```
# Record the time stamp to the nearest second.
TIMESTAMP="$( ls -l --time-style='+%Y%m%d%H%M.%S' "${FILENAME}" | cut  --delimiter=' ' --fields=6 )"

# Mogrify the file.

#  ==================================================================================================
# Insert the parameters to mogrify on the line below 'mogrify'. Be sure  to end the line with a
# single backslash.
#  ==================================================================================================
mogrify    \
    \
    "${FILENAME}"    # Change the line above this one.
#  ==================================================================================================

RETURNCODE=${?}

# Reset the timestamp.
touch -t ${TIMESTAMP} "${FILENAME}"
```


The only way I can see the timestamp part working (which I pulled from another forum post) is doing a "while within a while" loop. Set it up so that the folder name is read and cd into that folder, read the timestamp, mogrify the image, then touch the original timestamp. This process repeats for each individual file in each folder.


Apologies if this does not make sense, I'm having a hard time sorting it out in my head also. :P

---

### Post by ofnuts on 2012-11-09
Mogrify does the right thing... it changes the file contents, so the file modification timestamp changes.

if you want to do individual processing on each file you can't avoid using a loop on the files in each directory. While you are at it put mogrify in that loop and make it process one file at a time. That won't slow things down noticeably.

There is a much simpler way to copy the time stamp:
```

# copy time stamp to arbitrary file
touch -r imagefile.jpg /var/tmp/$$.timestamp
mogrify .... imagefile.jpg
# copy back time stamp from arbitrary file
touch -r /var/tmp/$$.timestamp imagefile.jpg

```

---

### Post by PinkFloyd102489 on 2012-11-09
I've got the timestamp and mogrify working fine by themselves, it's the looping that I'm having problems with. I can't get the first loop to segue into the second loop like it should and then exit properly. Just need help setting up the loop.

The only reason Im doing this is I take the pictures in a certain order so that it's easier to upload them to the site I work on, without having to rearrange them in the uploader. Otherwise, I wouldn't bother.

Thanks.

---

### Post by drmrgd on 2012-11-09
I think you can iterate over those files a little more cleanly (and without using ls) if you do it this way:

```
#!/bin/bash

# Create a dump file
dump="dumpfile.txt"

# Read file list and drop it into the dump file
for f in *.{JPG,jpg}; do
        echo "$f" >> "$dump"
done

for line in $(cat "$dump"); do
        #echo -e "$line"
        eval "mogrify -monitor \"$line/*.JPG\" -resize 640x430 -quality 85 \"$line/*.JPG\""
        zip -r "$line.zip" "$line" > /dev/null 2>&1 #quiet the output a bit
done

# Clean up
rm "$dump"
```

Then I think using ofnuts' bit in that script should give you what you want.  This isn't quite right yet, but should give you a good start.

EDIT:  I'm also assuming here that you're only working with .jpg files.  You can modify things a bit to include other kinds of picture formats if need be.

---

### Post by ofnuts on 2012-11-09
> **PinkFloyd102489 said:**
> I've got the timestamp and mogrify working fine by themselves, it's the looping that I'm having problems with. I can't get the first loop to segue into the second loop like it should and then exit properly. Just need help setting up the loop.

The only reason Im doing this is I take the pictures in a certain order so that it's easier to upload them to the site I work on, without having to rearrange them in the uploader. Otherwise, I wouldn't bother.

Thanks.
With the current program structure, you can't. You need something like:
```

#Read the file list and drop it into the dump file
ls --ignore="*.zip" --ignore="dump" --ignore="*.sh" > dump
cat dump

#This is the magic. Read the dump file line by line, mogrify, and zip.
while read line; do
    for file in $line/*.JPG
    do
        # Record the time stamp to the nearest second.
        TIMESTAMP="$( ls -l --time-style='+%Y%m%d%H%M.%S' "${FILENAME}" | cut  --delimiter=' ' --fields=6 )"
        # Mogrify the files one by one
        mogrify $file -resize 640x430 -quality 85 $file
        RETURNCODE=${?}
        # should do something here if <>0
        # Reset the timestamp.
        touch -t ${TIMESTAMP} "${FILENAME}"
    done
    zip -r $line.zip $line/
done < dump

#Clean the dump file
rm dump

```Warning;: syntax not checked, and behavior of "for" loop with spaces in file names can be erratic.

Btw, while we are at it, contrary to popular belief, the construct isn't "while read line" but "while read <bunch of variables to receive the line contents>", so your code would be more readable using "while read directory" or some such.

---

### Post by PinkFloyd102489 on 2012-11-15
```
total 1580
-rw-r--r-- 1 brandon brandon  99623 Nov 14 17:18 DSC_1587.JPG
-rw-r--r-- 1 brandon brandon 136498 Nov 14 17:18 DSC_1588.JPG
-rw-r--r-- 1 brandon brandon 132603 Nov 14 17:19 DSC_1589.JPG
-rw-r--r-- 1 brandon brandon 117732 Nov 14 17:19 DSC_1590.JPG
-rw-r--r-- 1 brandon brandon 126546 Nov 14 17:19 DSC_1591.JPG
-rw-r--r-- 1 brandon brandon 123899 Nov 14 17:19 DSC_1592.JPG
-rw-r--r-- 1 brandon brandon 133428 Nov 14 17:21 DSC_1593.JPG
-rw-r--r-- 1 brandon brandon 117439 Nov 14 17:21 DSC_1594.JPG
-rw-r--r-- 1 brandon brandon 132385 Nov 14 17:21 DSC_1595.JPG
-rw-r--r-- 1 brandon brandon 139822 Nov 14 17:22 DSC_1596.JPG
-rw-r--r-- 1 brandon brandon 112526 Nov 14 17:22 DSC_1597.JPG
-rw-r--r-- 1 brandon brandon 113267 Nov 14 17:22 DSC_1598.JPG
-rw-r--r-- 1 brandon brandon 103568 Nov 14 17:22 DSC_1599.JPG
```

These pictures were written to the memory card yesterday and copied out to the Desktop today. I mogrified them with the script and they still retained yesterday's timestamp.

That script worked. It's still uploading out of order, which eliminates the script. Time to point fingers elsewhere!

Thanks for all of your help!

---

