---
title: "Select n random music files from a given directory"
date: 2014-12-17
forum: Programming Talk
---

### Post by Erik1984 on 2014-12-17
This is my current bash script to write a given number of randomly selected music files to an output text file. This text file is used by a Python application I wrote.

```

#!/bin/bash

# defaults
let max_tries=100
let found_tracks=0
let tries=0

output_file="/home/erik/randomsongs.txt"
if [ -e $output_file ]; then
    rm $output_file
fi

if [ $# -ne 2 ]; then
    exit 1
fi
# First argument should be number of random tracks to select.
required_tracks=$1
# Second argument should be the music directory with added slash.
musicdir="$2/"

while [[ $found_tracks -lt $required_tracks && $tries -lt $max_tries ]]
do
    randfile=$(find "$musicdir" -type f | shuf -n1)
    mimetext=$(mimetype -b "$randfile")
    echo $mimetext
    # Selects .ogg .mp3 and .flac
    if [ $mimetext == "audio/x-vorbis+ogg" -o $mimetext == "audio/mpeg" -o $mimetext == "audio/flac" ]; then
        echo "$randfile" >> $output_file
        let found_tracks++
    fi
    let tries++
done

if [ $found_tracks -eq $required_tracks ]; then
    exit 0
fi
exit 1

```

The max_tries is just an arbitrary number set to prevent an endless loop (could otherwise happen if there are no music files in the given directory). I'm looking for a better method than what I have now, this loop structure feels clunky. Another fault of my current script is that it can select the same file multiple times. Ideally the randomly selected files should be distinct. I could keep an array of generated files and see if a newly picked song is already in there but that seems inefficient.

---

### Post by steeldriver on 2014-12-17
Have you looked at the shuf command? e.g. to return 5 results from a random permutation of all the mp3 files in a directory (provided the number of files doesn't exceed ARG_MAX I guess) you should just be able to do something like

```

shuf -n 5 *.mp3

```

---

### Post by Erik1984 on 2014-12-17
Thanks steeldriver. shuf gives an error when I add *.mp3 but you did point me in the right direction. I noticed that the find command has a file name filter. That can also be used for multiple extensions [http://unix.stackexchange.com/questions/15308/how-to-use-find-command-to-search-for-multiple-extensions](http://unix.stackexchange.com/questions/15308/how-to-use-find-command-to-search-for-multiple-extensions). Then I can use the -n parameter of shuf to control the number of randomly selected files.

The script is much shorter now
```

#!/bin/bash

output_file="/home/erik/randomsongs.txt"

if [ $# -ne 2 ]; then
    exit 1
fi
# First argument should be number of random tracks to select.
required_tracks=$1
# Second argument should be the music directory with added slash.
musicdir="$2/"

find "$musicdir" -type f \( -name \*.mp3 -o -name \*.ogg  -o -name \*.flac \) | shuf -n $required_tracks > $output_file

```

---

### Post by Vaphell on 2014-12-17
you could also modernize your script a bit if you are using bash. 

```
while [[ $found_tracks -lt $required_tracks && $tries -lt $max_tries ]]
```

integer math parens where < > == != work just fine, notice that $ are superfluous here in case of variable names.
```
while (( found_tracks < required_tracks && tries < max_tries ))
```

```
let tries++

(( tres++ ))
```

something like this
```
[ $mimetext == "audio/x-vorbis+ogg" -o $mimetext == "audio/mpeg" -o $mimetext == "audio/flac" ]
```
can be reduced to 
```
[[ $mimetext =~ ^audio/(x-vorbis\+ogg|mpeg|flac)$ ]]
```

generally [[ ]] and (( )) are superior and there is no reason to use [ ] in bash


in your newer version
```
find "$musicdir" -type f \( -name \*.mp3 -o -name \*.ogg  -o -name \*.flac \)
```

again using regex is arguably a bit more convenient than ORing possibilities
```
-regextype posix-extended -iregex '.*\.(mp3|ogg|flac)$'
```

---

### Post by ofnuts on 2014-12-17
```

ls *.mp3 | sort -R | head -5

```

Or am I missing something?

---

### Post by Erik1984 on 2014-12-17
I missed something, didn't know sort had a random mode. Would that be faster than find | shuf ?

@Vaphell
Thanks for the feedback. The different brackets and parentheses in bash can be confusing but that's a good explanation.

---

### Post by ofnuts on 2014-12-17
Did some benchmarking(*) and shuf is definitely faster than sort -R

(*) I have an extensive collection of server logs that comes very handy for this

---

### Post by Vaphell on 2014-12-17
> Thanks for the feedback. The different brackets and parentheses in bash can be confusing but that's a good explanation. 

tl;dr:
integer math/comparisons: (( ))
else: [[ ]]

;-)

---

