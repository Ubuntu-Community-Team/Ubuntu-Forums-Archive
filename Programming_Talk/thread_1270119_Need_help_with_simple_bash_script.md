---
title: "Need help with simple bash script"
date: 2009-09-19
forum: Programming Talk
---

### Post by mishathegoat on 2009-09-19
Hey everyone,
I have a task that needs to be completed but could be done much quicker with some script I'm sure. I'm not too familiar with bash scripting so any help is appreciated. This is what I'm looking for:

1. List contents of a video folder and add the text to the .nfo file

2. Rename the .nfo folder to the parent folder name

3. There's a -lot- of directories like this

Here's an example of the directory structure..

[FONT="Courier New"]
[INDENT]**My Home Video (2003)**[/INDENT]
[INDENT][INDENT]My.Home.Video_CrazyCool[2003].avi[/INDENT][/INDENT]
[INDENT][INDENT]notes.nfo[/INDENT][/INDENT]
[INDENT]**Moving Video [Kitchen] (2007)**[/INDENT]
[INDENT][INDENT]kitchenisnogood.mkv[/INDENT][/INDENT]
[INDENT][INDENT]my_kitchen.nfo[/INDENT][/INDENT][/FONT]

Again.. any help is appreciated.. Thanks

---

### Post by scragar on 2009-09-19
```
#!/bin/bash
START_DIR="`pwd`"

for ARG in $*
do
  if [ -d "$ARG" ]; then
    cd "$ARG"
    ls >> *.nfo
    mv *.nfo "$ARG.nfo"
    cd "$START_DIR"
  fi
done
```
Example usage:
```
myscript movies/*
```

---

### Post by mishathegoat on 2009-09-19
Thanks so much for the reply! However it doesn't seem to be working.. I have a suspicion that it has something to do with the spaces in the folder names.

---

### Post by geirha on 2009-09-19
This one should be safe with regards to spaces and special characters
```
#!/bin/bash

shopt -s nullglob

for dir in */; do

  nfofiles=( "$dir"/*.nfo ) 
  newnfo="$dir/${dir%/}.nfo"  # new nfo file named the same as parent dir

  if ((${#nfofiles[@]} > 1)); then
    echo "Too many .nfo-files in $dir. Skipping"
    continue
  elif ((${#nfofiles[@]} == 1)); then
    mv "${nfofiles[0]}" "$newnfo"
  fi
  ls "$dir" >> "$newnfo"

done

```

---

