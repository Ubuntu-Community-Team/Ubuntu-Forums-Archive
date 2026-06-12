---
title: "Bash search files and folders sed replace"
date: 2010-04-02
forum: Programming Talk
---

### Post by whitethorn on 2010-04-02
I'm trying to write a bash script which will search through a folder (/home) and replace certain characters with another in file names and folder names.  Here's what I've written so far.

So far I have to run two scripts, the first one replaces all spaces with an underscore.  Here I also run into the same problem as in the second script.  

```

#!/bin/bash

#Script to replace spaces with _  Run before Script SpecialCharacters

find . -name "* *"|while read file
do
        echo "$file"
    mv "$file" "`echo "$file"| awk ' BEGIN {OFS="_"} $1=$1 '`"
done

```

So the problem is, "find" prints out a list, of all filenames/directories with a space in them. Let's say I have the following 

> 
"/home/test a directory/another space/"

When I run the script it'll find both but can only rename the first directory
> 
"/home/test_a_directory/another space/"


It can't rename the second directory because the path has changed (rename on the first folder from test a directory to test_a_directory).

So what I want to achieve is for this script to first look into a directory find a space move the folder to _ and then to enter the directory and continue the search.  Instead of first finding all the spaces and then trying to rename them, because I have to run the above script a number of times until all spaces are then replaced.  Anybody have an idea how to get this done?

---

### Post by geirha on 2010-04-02
Why do you want to replace all spaces with underscores?

Anyway, you can use find and prename like this (check the man-page of prename to see what the -n does):

```
find . -depth -name "* *" -execdir prename -n 'y/ /_/' {} +
```

Also see [http://mywiki.wooledge.org/BashFAQ/030](http://mywiki.wooledge.org/BashFAQ/030)

---

