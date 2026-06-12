---
title: "Not so easy renaming problem (bash)"
date: 2009-10-20
forum: Programming Talk
---

### Post by Dalekk on 2009-10-20
Hi there

I am in a situation where I have to rename a lot of files, and naturally I don't want to do this manually. Actually I have already solved the problem (partially), but I feel that my approach is somewhat naive.

I have two groups of files. The first group is about 200 .mp3 files and the second group is about 100.000 files with lyrics from all sorts of music, including lyrics for the 200 .mp3 files. I want to make a third group containing the 200 .mp3 files and the 200 corresponding lyrics-files. The problem is that the naming of the .mp3 files follow different standards, with some being TRACK NUMBER - ARTIST - ALBUM - TITLE, some being TRACK NUMBER  - TITLE and other combinations as well. The lyrics files are all ARTIST - ALBUM - TITLE.

Example:
I have the .mp3 file "01 - Dungen - Panda.mp3" and want to find the lyrics file
Dungen-Ta Det Lungt-2004-Panda.txt after which I want to rename the mp3 to Dungen-Ta Det Lungt-2004-Panda.mp3.

I have done this by first using sed to reform the .mp3 name to a string that can be used with find, and then use the string to search the lyrics directory.

My code:

```
#!/bin/bash
find -iname "*.mp3" | while read n; do 
    echo $n | sed 's/.wav././' | sed 's/[0-9]*\ //' | sed 's/-//' | sed 's/\ -\ /*/' | sed 's/.mp3//' | sed 's/.\///' | while read k; do 
        find ../emotions/ -iname "*$k*" | sed 's/..\/emotions\///' | sed 's/.txt/.mp3/' | while read j; do 
            m=`echo $n | sed 's/.\///'`
            echo "Renaming" $m "to" $j
            cp "$m" "$j"
        done; 
    done; 
done;
```First of all, I would like the user to be able to confirm the renaming of each individual file (e.g. y/n keyboard input). I tried to use read for this, but for some reason nothing happens. Secondly, I find the implementation with three while loops clumsy. 

Instead of using "while read" to snatch the output of the multi-piped sed command (I don't know what to call it), is it possible to assign the output of the last sed command to a variable? 

```
j=`echo $n | sed 's/.wav././' | sed 's/[0-9]*\ //' | sed 's/-//' | sed 's/\ -\ /*/' | sed 's/.mp3//' | sed 's/.\///'`
```does not work..

I'm sorry for the long post. Thank you if you managed to read this far! :)

---

