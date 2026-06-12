---
title: "Bash Script to unpack scene image packs"
date: 2011-03-28
forum: Programming Talk
---

### Post by worldroll on 2011-03-28
This is my first script, which I freely admitting to assembling via cut and pasting from various google searches.   

Basically I wanted a script to unpack scene image packs from  the form of 

> 
something.com_11.02.01.blah/blah00.zip 
something.com_11.02.01.blah/blah01.zip 
something.com_11.02.01.blah/blah02.zip  
where each zip is of the form  
> 
blah00.zip/file_id.diz 
blah00.zip/blah.nfo
blah00.zip/blah.rar
to
> 
something.com/something.com_11.02.01.blah/aa01.jpg 
something.com/something.com_11.02.01.blah/aa02.jpg 
something.com/something.com_11.02.01.blah/aa03.jpg 
something.com/something.com_11.02.01.blah/aa04.jpg  
What I have done seems to be working so far when the files are fine and the file nameing is as expected. What I would like to do is the make it a bit more robust, so that it gives error messages yet, so any feedback on how to make it better are more then welcome :D

[php]
#! /bin/bash
#Script to unpack sceen releases
#unzip all zip files
for i in `find . -name "*.zip"`; do unzip -o -d `dirname $i` $i;done;
#delete all zip files
for i in `find . -name "*.zip"`; do rm $i;done;
#unrar recusively
find ./* -type f -name '*.rar' -execdir unrar x {} \;
#remove rar
for i in `find . -name "*.r??"`; do rm $i;done;
#remove sample folder
for i in `find . -name "Sample"`; do rm -r $i;done;
#print list of all folders
ls -d */ > dirlist.txt
#keep just the site name
sed 's/_.*//g' dirlist.txt > dirlist2.txt
#remove duplicate entries
cat dirlist2.txt|uniq > dirlist3.txt
#make directories
for d in $(cat dirlist3.txt); do mkdir $d; done
#move directors
for d in $(cat dirlist3.txt); do mv $d?* $d; done
[/php]

---

### Post by paxxus on 2011-03-28
I always use the -e switch for my bash scripts. It causes the script to break on the first error instead of mindlessly continuing possibly with catastrophic consequences. You would put this at the top of your script:

```
#! /bin/bash -e
```But you can also turn the switch on and off in the script itself.

```
# Turn on error check.
set -e

# Turn off error check.
set +e
```I basically regard the -e switch as mandatory for robustness in bash scripts.

---

