---
title: "renaming files in directory using a shell script"
date: 2013-03-08
forum: Programming Talk
---

### Post by jamesbon on 2013-03-08
I am having a lot of .JPG files 
> DSCN2350.JPG  DSCN2354.JPG  DSCN2358.JPG  DSCN2362.JPG  DSCN2366.JPG
DSCN2351.JPG  DSCN2355.JPG  DSCN2359.JPG  DSCN2363.JPG
DSCN2352.JPG  DSCN2356.JPG  DSCN2360.JPG  DSCN2364.JPG




I want to rename them d1.jpg d2.jpg d3.jpg and so on so I wrote a shell script 

```
#/bin/bash
p=0
for i in *.JPG;
do
mv "$i" "d$p.JPG"
((p+1))  ;
done



```

but what happened is among a lot of files when I run the above script as an output rest of the JPG files get deleted 
and I am left with only one file
d0.jpg
what is the error happening here ?

---

### Post by Mr. Shannon on 2013-03-09
The problem is in the line:
```
((p+1))
```
you are computing the value p+1, but you are not storing it anywhere.  Use
```
((p++))
```
which will increment p.

So in total your code should be:
```

#!/bin/bash

p=0
for i in *.jpg;
do
  mv "$i" "d$p.JPG"
  ((p++))
done

exit 0

```

---

### Post by spanishu on 2013-06-20
This looks good but... I am looking for something slightly more sophisticated.

**Dream:**
I have a folder called /to be moved
in this folder there are subfolders of movies which in turn will have either .mp4 or .avi files but in multiple parts
plexapp.com supports multi-file movies but they need to be named /movie abc pt1.avi /movie abc pt2.avi etc

the best would be that I could run the script from the folder /to be moved and that it would take each sub-dir take the name of the subdir and do the rename of the files according to what I stated above. Once finished move all the subdirs to /updated

[B]Good Enough:
[/B]have the script do the renaming mentioned above in each subdir (just take the name of the Directory and apply to the underlying files. 

Any suggestion ?

---

### Post by ofnuts on 2013-06-20
"good_enough" is something like

```

#! /bin/bash

# takes the directory where the files are as an argument
dir=$1
rootname=$(basename $dir)
partseq=1
for f in "$1/"*.avi
do
   mv "$f" "$dir/$rootname-part$partseq.avi
   ((partseq++))
done

```

and "dream" is

```

#! /bin/bash

#execute good_enough in all directories below the root dir passed as a parameter:
find $1 -type d -exec good_enough {} \;

```

Completely untested...

---

### Post by spanishu on 2013-06-21
Many thanks for this. I would like to test this but now the Linux noclue question is:
- I have the "Master Directory". there I placed the "good enough" how do I run it in order to make it run on a directory called movie a ?
Sorry for a lame question but really close to 0 skills!
Thanks

---

### Post by Lars Noodén on 2013-06-21
If you want to continue writing your own script for learning purposes, then go for it.  There's nothing like having a concrete problem to solve to focus learning.  However, if you are only trying to bulk rename some files and need to get that done to move on to something else, then look at rename.  (There's no manual page online for me to link to but you can find it in your own terminal.)

```

rename -n '$a++;s/^.*.jpeg$/d$a.jpeg/' *.jpeg

```

The -n makes it do just a dry run without actually changing the names.  Remove it once you see the results you want.

Edit:  You could also add leading zeros so that the result sorts better.  Change the sprintf statement to increase the number of zeros.

```

rename -n '$a++;$a=sprintf("%02d",$a);s/^.*.jpeg$/d$a.jpeg/' *.jpeg

```

---

