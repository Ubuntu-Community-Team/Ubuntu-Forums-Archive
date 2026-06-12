---
title: "moving specific file type to new location--maintain directory structure?"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by Jmob on 2012-09-11
Hey, I've got a big move of data I want to do, big enough that I don't want to screw it up.  I've got my music organized into a directory heirarchy (genre/artist/album/music.files), but the .mp3 and .flac files from encoding are in the same folders.  I'd like to create a new identical directory tree with just one or the other of these filetypes.  How do I approach such a problem?

I know a bit about regex, not enough to do it myself yet, but enough to figure out what I'm inputting if it involves that.  I'm comfortable with basic commandline work, and a novice at scripting.

---

### Post by steeldriver on 2012-09-11
one way that comes to mind would be to create a 'tar' archive with

```
--exclude='*.flac'
```or

```
--exclude='*.mp3'
```and then extract it into the new location... there may be better ways though

---

### Post by sisco311 on 2012-09-11
I'd try something like:
```

#!/bin/bash

# source and destination directories:
source="$HOME/foo"
dest="$HOME/bar"

# cd to the source directory or exit
cd "$source" || exit 1
# create the dest directory
mkdir -p "$dest" || exit 2

shopt -s globstar nocaseglob

for file in **/*.mp3
do
    # get the name (relative path) of the directory where the .mp3 file is
    dir="${file%/*}"
    # create the destination dir
    **echo** mkdir -p  "$dest/$dir" &&
    # cp the file to dest; you can replace cp with mv to move the files
    **echo** cp -- "$file" "$dest/$dir"
done

```

This script will only print the mkdir and cp commands. If everything looks fine, delete the **echo** commands to actually cp/mv the files.

---

### Post by Jmob on 2012-09-12
Thanks, I'll look at these.   It'll be a good learning experience, too.

---

