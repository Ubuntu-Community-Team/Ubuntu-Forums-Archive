---
title: "Bash Scripting -- Rename Folders in Mass"
date: 2008-12-18
forum: Programming Talk
---

### Post by evisboy on 2008-12-18
I have to rename several folders, including in subdirectories, based on the results of find. The files should be renamed only, and not moved. All folders to be renamed contain files and folders themselves. 

So, this is what I have so far: 


find . -name 'Year 05' -exec rename -v 's/Year 05/Year 04/' '{}' \;

This works fine on my local machine, but not on the server (fedora -- although rename is installed -- or seems to be)

So, I tried this: 

for filename in `find -name "Year 05"`; do mv -fT "$filename" `echo $filename | sed -e "s/Year 05/Year 04/"`; done 

but I keep getting this error: 
mv: cannot stat `./md-1/Year': No such file or directory
mv: cannot stat `04': No such file or directory

The path should be ./md-1/Year 04


I finally got it working with this:

find ./* -name "Year 05" -fprintf rename.sh 'mv "%h/%f" "%h/Year 04"\n' 

But I want something more elegant -- for my own learning)

Anybody have any ideas?

---

### Post by ghostdog74 on 2008-12-18
use a while loop instead
```

find /path .... |while read line
do
 # do something with $line
done

```
remember to quote your variables.

---

### Post by kaibob on 2008-12-18
I had trouble writing a script that would recursively rename nested directories because the path to subdirectories changed after higher-level directories were renamed and the script would stop. A solution that worked was to pipe the find command through sort -r. 

```
#!/bin/bash
cd /directory/name
find -type d | sort -r | while read LINE ; do
DIR=$(dirname "$LINE")
FILE=$(basename "$LINE")
mv "${DIR}/${FILE}" "${DIR}/${FILE/old/new}"
done
```

I've only partially tested this script, and renaming directories in this manner can do substantial harm, so please be careful if using this script.

---

