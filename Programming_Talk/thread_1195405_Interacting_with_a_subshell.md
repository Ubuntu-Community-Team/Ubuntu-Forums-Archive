---
title: "Interacting with a subshell"
date: 2009-06-23
forum: Programming Talk
---

### Post by Arctic_Fox on 2009-06-23
Hi guys, I'm trying to write a script that converts flv files to mp3s with ffmpeg. I've gotten it to work but I have a few questions.

```
# Converts flv audio files to mp3s using ffmpeg
#! /bin/bash

echo $(ls | grep -e '\.[fF][lL][vV]' | \
	awk '{ gsub(/ /, "\ ") 
		newname=substr($0,0,length($0)-3)".mp3"
		print "ffmpeg -i "$0" -acodec copy "newname";"
	}') | bash
exit 0
```

My questions are two fold. First, if there is already a file with the output name, I can't interact with the prompt that asks if I want to overwrite or not, thus the file isn't converted. I assume this is because the pipe to bash means that it's running from a subshell. Is there any way to either interact with the subshell or somehow make the subshell not... sub? Second, you will probably notice that I echo the output of the awk then pipe it to bash, which seems redundant. But when I don't do this however, with multiple files only the first gets converted. I'm guessing somehow this is because awk is sending the output to bash line by line? But I don't see why that would be a problem, and I didn't think awk worked like that. Anyway, these are probably noob questions, but thanks for your help!

---

### Post by croto on 2009-06-23
Hi, I would try to avoid a subshell at all. I guess something like this may work:

```

#!/bin/bash

# A trick to avoid problems with filenames containing spaces.
# This will fail if the filename contains newlines.
OLDIFS=$IFS
IFS=$'\n'
files=($(find . -iname '*.flv'))
IFS=$OLDIFS
nfiles=${#files[@]}

# Looping over the elements of the array
for ((i=0; i<$nfiles; i++)); do
    file=${files[$i]}

    newfile=${file:0:${#file}-3}mp3
    toprocess=1

    # confirmation
    if [ -e "$newfile" ]; then
	while :; do
          read -p "File $newfile already exists. Overwrite? (Y/N): " answer
	  if [ "$answer" == "Y" ] || [ "$answer" == "y" ]; then 
	      toprocess=1; break; 
	  fi
	  if [ "$answer" == "N" ] || [ "$answer" == "n" ]; then 
	      toprocess=0; break; 
	  fi
	done
    fi

    if [ $toprocess -eq 1 ]; then
	# ok, process. Remeber to quote the $file and $newfile
	# (because of the possible spaces)
	echo ffmpeg -i "$file" -acodec copy "$newfile"
	ls "$file" "$newfile"
    fi

done

```

---

### Post by Arctic_Fox on 2009-06-23
Yes that does work, but I already had my script working. I was just wondering if what I described was possible. Thanks for the input though.

---

### Post by Arctic_Fox on 2009-06-24
I don't like to bump my own threads but I'm just too curious for an answer.

---

