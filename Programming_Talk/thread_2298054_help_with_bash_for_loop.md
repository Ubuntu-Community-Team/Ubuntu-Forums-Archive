---
title: "help with bash for loop"
date: 2015-10-08
forum: Programming Talk
---

### Post by mike371 on 2015-10-08
I have been slowly converting my .flac media to V0 for mobile use.  I am using the following loop in a bash script to convert multi-disc albums but it is not functioning properly.  For some reason it will convert disc 1 of the album but not disc 2. The multi-disc albums are formatted with the parent directory being the album name with disc 1 and disc 2 being sub directories inside of it.  Obviously the the disc 1 and 2 directories each contain a number of .flacs. The script is being run from the directory containing the albums.  I'm sure I am overlooking something simple but I can not figure out what it is.  Any help or suggestions would be appreciated.  Thank you.


```
for i in  */*/
do
  cd "$i" && cp cover.jpg /home/path/to/v0/"$i"
for f in *.flac ; do avconv -i "$f" -aq 0 /home/path/to/v0/"$i"/"${f%.flac}.mp3"  ; done
  cd ..
done

```

---

### Post by Vaphell on 2015-10-08
you go down 2 levels (*/*/) with cd but go up only 1 (..)
That said personally i prefer to avoid cd-ing over the directory tree, i just transform paths

```
#!/bin/bash

dest=$HOME/test/crap/v0

for f in */*/*.flac
do
    dir=${f%/*}
    destpath=$dest/${f%.*}.mp3
    # mkdir -p "${destpath%/*}"
    echo "from: '$f'"
    echo "to: '$destpath'"
done

for f in */*/cover.jpg
do
    destpath=$dest/$f
    echo cp "$f" "$destpath"
done
```

---

### Post by mike371 on 2015-10-08
Thanks a lot for the help.  The issue was definitely not going back enough levels.  Although that was just a dumb mistake, bash is still fairly new to me.  I am curious as to what you meant by transforming paths.  In your example it seems like you meant to assign variables to the paths and use those instead of cd.  Also, what did the dir variable accomplish in your example?  I see that it has a value of ${f%/*} but I don't see it used anywhere else.  Thanks again for the help, it solved my problem and helped me to learn a bit.

---

### Post by Vaphell on 2015-10-09
dir is indeed superfluous, i thought i will need it, but then i didn't and forgot to remove it
 
> I am curious as to what you meant by transforming paths.

I mean string operations on paths to get a rock solid transformation from src_path to dest_path so you can perform the desired operation in an unambiguous way, not caring about your current position in the dir tree. Why jump (which can fail BTW and then you are not where you think you are) if you can simply calculate destination path?
For example cd-ing up and down becomes a massive PITA in case you are trying to do something like "find all files in X subtree and then do something with them exporting them to Y in a way that mirrors the initial layout" because you now have to track how deep you are.
But if your problem can be described as "given paths like these
/A/B/C/some/stuff.txt
/A/B/C/test1.txt
/A/B/C/1/2/3/4/5/music.mp3
replace /A/B/C with /D/E/F while preserving the structure" you can easily do something like

```
src_dir=/A/B/C
dest_dir=/D/E/F
f=/A/B/C/1/2/3/4/5/music.mp3      
echo "${f/#$src_dir/$dest_dir}"    # replace $src with $dest but only if it starts the string
/D/E/F/1/2/3/4/5/music.mp3


shopt -s globstar

for f in "$src_dir"/**/*.*              # **=any depth, requires shopt -s globstar
do
   dest_f=${f/#$src_dir/$dest_dir}
done

# or with find
while read f
do
    dest_f=${f/#$src_dir/$dest_dir}
done < <(find "$src_dir" -type f)
```

(note that in case of while read used to read lists of files, null delimiter should be used because reasons, *while read -rd $'\0' f* +* find -print0)*

---

### Post by mike371 on 2015-10-09
Thank you so much for taking the time to write such a detailed explanation.  It has helped me to understand things quite a bit.

---

