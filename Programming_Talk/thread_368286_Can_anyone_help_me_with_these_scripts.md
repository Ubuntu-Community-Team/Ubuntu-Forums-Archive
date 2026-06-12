---
title: "Can anyone help me with these scripts?"
date: 2007-02-23
forum: Programming Talk
---

### Post by cewan on 2007-02-23
Hi, I'd like to have some scripts perform the following tasks for me:

1. usage: ```
collectfiles <sourcefolder> <destfolder> <extensionlist>
```
This script would walk through all folders in <sourcefolder> and whenever it finds a file with an extension matching any extension in <extensionlist>, the file will be moved to <destfolder>
example: ```
collectfiles . myMovies avi,mov
```

2. usage: ```
spacify <sourcefolder>
```
This script would walk through all folders in <sourcefolder> and whenever it finds a file or directory having a name that contains underscore ('_') it will be replaced with a space (' ').

3 usage: ```
capitalize <sourcefolder>
```
This script would walk through all folders in <sourcefolder> and for every folder and file each word in it's name will be capitalized, i.e. the first letter of the word will be changed to upper case.
example: ```
capitalize my\ folder
```
will result in the folder changing name to 'My Folder'.

Anyone have any hints, complete solutions or guidance? Is it even possible to write such scripts?
BR,

---

### Post by yabbadabbadont on 2007-02-23
1:> This script would walk through all folders in <sourcefolder> and whenever it finds a file with an extension matching any extension in <extensionlist>, the file will be moved to <destfolder>
example:
Code:

collectfiles . myMovies avi,mov
find . -type f \( -name "*.avi" -o -name "*.mov" \) -exec mv {} /full/path/to/myMovies \;

Edit: Do your own homework.  :D

---

### Post by cewan on 2007-02-23
Oh, that's a nice one! Thanks alot :) 

1 down, 2 to go

It is hard to know where to search for these kinds of stuff. I guess it comes by experience, right? I am a real newbie to Linux, wasted all my life with Windows and just discovered Linux like a month ago. Now I use Linux both at work and at home =)

Would be grateful for help on the other scripts as well!

---

### Post by yabbadabbadont on 2007-02-23
```
/home/bubba/temp $ ls -lR another\ folder test_folder
another folder:
total 20
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 04:05 folder1
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 04:05 folder 2
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 04:05 folder_3
-rw-r--r-- 1 bubba bubba    3 2007-02-23 04:05 test_file_with_lots_of_underscores
-rw-r--r-- 1 bubba bubba    3 2007-02-23 04:05 test_file_with_lots_of_underscores and spaces

another folder/folder1:
total 0

another folder/folder 2:
total 8
-rw-r--r-- 1 bubba bubba 3 2007-02-23 04:05 test_file_with_lots_of_underscores
-rw-r--r-- 1 bubba bubba 3 2007-02-23 04:05 test_file_with_lots_of_underscores and spaces

another folder/folder_3:
total 0

test_folder:
total 20
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 03:59 folder1
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 03:59 folder 2
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 03:59 folder_3
-rw-r--r-- 1 bubba bubba    3 2007-02-23 03:59 test_file_with_lots_of_underscores
-rw-r--r-- 1 bubba bubba    3 2007-02-23 03:59 test_file_with_lots_of_underscores and spaces

test_folder/folder1:
total 0

test_folder/folder 2:
total 8
-rw-r--r-- 1 bubba bubba 3 2007-02-23 03:59 test_file_with_lots_of_underscores
-rw-r--r-- 1 bubba bubba 3 2007-02-23 03:59 test_file_with_lots_of_underscores and spaces

test_folder/folder_3:
total 0
/home/bubba/temp $ ./go.sh another\ folder test_folder
/home/bubba/temp $ ls -lR another\ folder test\ folder
another folder:
total 20
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 04:05 folder1
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 04:05 folder 2
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 04:05 folder 3
-rw-r--r-- 1 bubba bubba    3 2007-02-23 04:05 test file with lots of underscores
-rw-r--r-- 1 bubba bubba    3 2007-02-23 04:05 test file with lots of underscores and spaces

another folder/folder1:
total 0

another folder/folder 2:
total 8
-rw-r--r-- 1 bubba bubba 3 2007-02-23 04:05 test file with lots of underscores
-rw-r--r-- 1 bubba bubba 3 2007-02-23 04:05 test file with lots of underscores and spaces

another folder/folder 3:
total 0

test folder:
total 20
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 03:59 folder1
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 04:05 folder 2
drwxr-xr-x 2 bubba bubba 4096 2007-02-23 03:59 folder 3
-rw-r--r-- 1 bubba bubba    3 2007-02-23 03:59 test file with lots of underscores
-rw-r--r-- 1 bubba bubba    3 2007-02-23 03:59 test file with lots of underscores and spaces

test folder/folder1:
total 0

test folder/folder 2:
total 8
-rw-r--r-- 1 bubba bubba 3 2007-02-23 03:59 test file with lots of underscores
-rw-r--r-- 1 bubba bubba 3 2007-02-23 03:59 test file with lots of underscores and spaces

test folder/folder 3:
total 0

```
**go.sh:**```
/home/bubba/temp $ cat go.sh
#!/bin/bash

# for simplicity, process files first, then directories

find "$@" -type f -name "*_*" > tmpMatches

while read current
do
        filename=$(basename "$current")
        pathname=$(dirname "$current")
        newfilename=$(echo $filename | sed "s/_/ /g")
        mv "$pathname/$filename" "$pathname/$newfilename"
done < tmpMatches

rm tmpMatches

find "$@" -depth -type d -name "*_*" > tmpMatches

while read current
do
        curdirname=$(basename "$current")
        pathname=$(dirname "$current")
        newdirname=$(echo $curdirname | sed "s/_/ /g")
        mv "$pathname/$curdirname" "$pathname/$newdirname"
done < tmpMatches

rm tmpMatches
```

---

### Post by cewan on 2007-02-23
Haha, I am really impressed, you know your scripting!

2 down! Is the third too hard? ;-)

---

### Post by yabbadabbadont on 2007-02-23
The last isn't very hard either.  However, as most professors would say, "the rest is left as an exercise for the student."  :D

Hint:
man sed
man tr

(in addition to the programs I used previously)

---

### Post by cewan on 2007-02-23
That's a good reply! :-)
Now I know what I will spend my weekend on :-k 

/Soon-to-be-a-scripting-guru-like-Yabbadabbadont

---

### Post by yabbadabbadont on 2007-02-23
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

That looks like a decent place to start.  I didn't read through too much of it, but it looked decent.

---

