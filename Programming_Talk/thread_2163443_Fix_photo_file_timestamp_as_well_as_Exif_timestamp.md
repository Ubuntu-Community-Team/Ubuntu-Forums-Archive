---
title: "Fix photo file timestamp as well as Exif timestamp"
date: 2013-07-18
forum: Programming Talk
---

### Post by hartz on 2013-07-18
Hello.

I have a number of photos from my digital camera which were taken with the camera set to the wrong date.  This happened in January of 2012.  I suppose I was still in 2011 mode because I set my then brand new camera date to 2011.

The rest is correct (month, day, hour, minute, second) or near enough so as to not matter.

I would like a script which does the following

for PHOTO in $PHOTO_LIST
do
   OLDDATE=$(get_date_from $PHOTO)
   NEWDATE=$(substitute 2012 for 2011 in $OLDDATE)
   set_exif_date $NEWDATE $PHOTO
   set_file_date $NEWDATE $PHOTO
done

I am looking for a ready solution (so as to not re-invent the wheel), otherwise I will roll my own shiny new wheel and post it here.


Thanx,
  _Johan

---

### Post by alan9800 on 2013-07-18
you might try [exiftool](http://owl.phy.queensu.ca/~phil/exiftool/#filename).

---

### Post by Vaphell on 2013-07-18
```
#!/bin/bash

path="./samples/"

while read -rd $'\0' f
do
  for tag in 0x9003 0x9004   # date_original, date_digitized
  do
    exif_date=$( exif -t "$tag" "$f" 2>/dev/null | grep -oP '\d{4}.\d{2}.\d{2} \d{2}.\d{2}.\d{2}' )
    [ "${exif_date:0:4}" = '2011' ] || continue
    exif --ifd=EXIF -t "$tag" --set-value="${exif_date/#2011/2012}" -o "$f" "$f"
  done
done < <( find "$path" -type f -iname '*.jpg' -print0 )
```

test it first on some duplicates just in case. Requires **exif**
path points to where pics are supposed to be. Not knowing the dir structure I opted for potentially recursive solution with *find*

---

### Post by Vaphell on 2013-07-18
i noticed that my test pics had another date field in another area of exif structure (ifd) so here is a slightly modified version

```
#!/bin/bash

path="./samples/"
declare -A tags
tags=( [0x0132]=0 [0x9003]=EXIF [0x9004]=EXIF )

while read -rd $'\0' f
do
  for tag in "${!tags[@]}" 
  do
    exif_date=$( exif -t "$tag" "$f" 2>/dev/null | grep -oP '\d{4}.\d{2}.\d{2} \d{2}.\d{2}.\d{2}' )
    [ ${exif_date:0:4} = '2011' ] || continue
    exif --ifd="${tags[$tag]}" -t "$tag" --set-value="${exif_date/#2011/2012}" -o "$f" "$f"
  done
done < <( find "$path" -type f -iname '*.jpg' -print0 )
```

---

### Post by hartz on 2013-07-18
Awsome solution.

I particularly like "${exif_date/#2011/2012}"

I am going to have to try it out in bits so as to understand it fully.  I won't do a find as part of a script like this.  I prefer my "tools" to work on the files they have been specified to work on by an external program.  There are two common ways:  a list of items on standard input to specify the files to use, or a list of files on the command line.

Since I habitually avoid problematic characters in file names and since I write my tools mostly for myself and want to keep them simple and because my use case is simple, I will opt for the second method, ie specify the files to operate on as arguments.

But again, Awsome solution!

---

### Post by ofnuts on 2013-07-18
Since no one mentioned it yet, the command to set the file date is "touch".

---

### Post by Vaphell on 2013-07-18
[QUOTE=hartz;12736238]Since I habitually avoid problematic characters in file names and since I write my tools mostly for myself and want to keep them simple and because my use case is simple, I will opt for the second method, ie specify the files to operate on as arguments.[QUOTE]

as in **for f; do ....; done** (**in "$@"** is implicitly assumed if nothing is provided)? whatever floats your boat ;-)


I don't know what you mean exactly by saying 'keeping it simple' but imo it's better not to do shortcuts based on rosy assumptions. Usually savings from the shortcut are miniscule (few bytes), sticking to 1 or 2 established rock solid programming patterns is not a rocket science and you never know what you get when you process files from external source or when your own script produces garbage files with weirdo names by mistake and you have to clean it up :)

Awesomeness in file processing goes like this: 1. shell globs 2. find with null delimiter + while read. Everything else is iffy and dirty hacks based on parsing ls and/or IFS are a big no-no :)

---

