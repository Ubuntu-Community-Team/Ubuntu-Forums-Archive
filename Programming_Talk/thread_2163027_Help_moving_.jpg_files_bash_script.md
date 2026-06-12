---
title: "Help: moving .jpg files bash script"
date: 2013-07-16
forum: Programming Talk
---

### Post by vikler on 2013-07-16
Hi everyone!
Could you please help a begginer with the following bash script.

So I have a directory with a lot of .jpg files. Same directory has a lot of sub-folders. What I want is to move .jpg's to sub-dir's using the following rule:
Each of my .jpg files is named by ids, that refer to the folder. For example
First set:
SPL1234_001.jpg
SPL1234_002.jpg
SPL1234_003.jpg
Second set:
SPL1235_001.jpg
SPL1235_002.jpg

etc (you get the idea)
The folders in the same directory (empty) already exist and are named this way:
SPL1234_Some_name
SPL1235_Some_name_2
etc
there id of the directory before the first "_" and the id of the photo set are always the same, but what comes after "_" can't be tracked (Some_name and Some_named_2 are not made by any rule, they can be very diverse).

What I need in my script is basically something similar to the results of
mv SPL1235* ./SPL1235_*
mv SPL1234* ./SPL1234_*
....
etc for each set of files


I hope I've made it clear... Can someone help me since I am just a newbie, and have been trying to think of an answer for hours, but without any luck


Any help is deeply appreciated:D

---

### Post by Vaphell on 2013-07-16
assuming directories have unique ids
```
for f in ./*.jpg; do **echo **mv -t "./${f%%_*}"* "$f"; done
```
test it first on some dummy files first. **echo ** prints mv commands so it's easy to see the parameters. If you are happy with the results get rid of echo.

---

### Post by papibe on 2013-07-16
Hi vikler.

This should work:
```
#!/bin/bash
PROJECT='SPL*'

# find all directories that match PROJECT
while read -d '' -r dir; do
    base=${dir##*/} # get clean filename (basename)
    id=${base%%_*}  # get id name

    # Info message.
    echo "$dir -> ${id%%_*}"

    # find every file that starts with the id, and move it to the current directory.
    find -type f -name "$id*.jpg" -exec bash -c '**echo -e "\t"** mv -iv "$1" "$2"' _ '{}' "$dir" \;

done< <(find -mindepth 1 -type d -name "$PROJECT" -print0)

```
Note this code does not actually move the files, but echo the command (so you can test and debug it first). In order to actually move the files, remove the bold part: **echo -e "\t"**

Hope it helps. Let us know how it goes.
Regards.

---

### Post by vikler on 2013-07-17
thanks a lot, papibe! Works the way I wanted it to work. AMAZING job!!!
Thank you, Vaphell, too!
You guys are awesome

---

