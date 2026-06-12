---
title: "Creating a script to zip a large number of folders individually"
date: 2011-01-14
forum: Programming Talk
---

### Post by rbishop on 2011-01-14
Hello all.   Here is what I would like to do with a script.

I have a large number of pictures in individual folders.  I would like to have a script read the contents of the main folder "My Pictures" and list all of the sub-folders.  After that I would like the script to create individual zip files of each sub-folder.

My Pictures
     Pics 1
     Pics 2
     Pics 3

I would really like to have them all labeled in the following way Pics1-01-14-11.tar.gz.  This way i know what folder is zipped and when it was created.

I know how to list the folders into a text file, but I am unclear on how to use that list as a variable to pass to the tar command.  


Here is what I have so far....
```

TD=$(date '+%m-%d-%y')

ls /My Pictures/ > picfolder.txt

tar -cvzf /My Pictures/$name-$TD.tar.gz /My Pictures/$name

```

Like I said above, I am not sure on how to use the txt file from my ls command to name the files, so any help would be greatly appreciated.

---

### Post by roccivic on 2011-01-14
You shouldn't have spaces in paths...

This works as expected on my machine:

[PHP]#/bin/bash

cd ~/Pictures                                    # Go to the target directory

TD=$(date '+%m-%d-%y')                           # Save the time
for folder in *; do                              # Process each file in the working directory
  if [ -d "$folder" ]; then                      # We are only interested in folders
    tar -cvzf "$folder-$TD.tar.gz" "$folder";    # Compress
  fi;
done[/PHP]

---

### Post by sisco311 on 2011-01-14
D'oh! roccivic beat me to it. :)

```
#!/usr/bin/env bash

_error0 ()
{
  echo "error: $0: $DIRNAME: No such directory" >&2
  echo "USAGE: $0 [ DIR ]" >&2
  exit 1
}

_error1 ()
{
  echo "error: $0: cannot create archive from $1" >&2
}

DATE="$(date +'%m-%d-%y')"
DIRNAME="$1"

#set default directory
DIRNAME="${DIRNAME:-**/home/sisco/xtmp/foo**}"

#if it's not a directory, exit
if [ ! -d "$DIRNAME" ]; then
  _error0
fi

#compress the directoies
cd "$DIRNAME"
for file in *; do
  if [ -d "$file" ]; then
    tar -cvzf "./${file}-$DATE.tar.gz" "./$file" || _error1 "$file"
  fi
done

exit 0

```


> **roccivic said:**
> You shouldn't have spaces in paths...


Why not?

---

### Post by rbishop on 2011-01-14
roccivic - Thank you so much.  That is exactly what I needed.

---

