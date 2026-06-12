---
title: "Need help creating a script."
date: 2013-04-13
forum: Programming Talk
---

### Post by jacox on 2013-04-13
Hello.

I am trying to create a script that does the following.
[LIST]
[*]Scans a folder '/home/jack/Downloads/complete/Music/' for .flac files.
[*]Converts these .flac files to .alac files for my iPod.
[*]Deletes the original .flac files only after successfully converting them.
[*]Then moves the .flac files (along with directory they are in) to '~/media/D3/Music/'
[/LIST]

Is this possible? I am new to ubuntu and would really like this process automated as i have a very large .flac music collection.
I need the folder structure to look like this '/Music/'Artist'/'Album'/

Can anyone get me started on the right track?

Jack.

---

### Post by prodigy_ on 2013-04-13
```
#!/bin/bash

source_root="/home/jack/Downloads/complete/Music"
target_root="~/media/D3/Music"

mkdir -p "$target_root"

find "$source_root" -type f -print0 | \
	while read -r -d $'\0' full_path; do
		if file "$full_path" | grep 'FLAC audio bitstream data'; then
			full_path_alac="${full_path%\.*}.m4a"
			ffmpeg -y -i "$full_path" -acodec alac "$full_path_alac"
			[ $? -eq 0 ] && rm "$full_path"
			dir_name=$(dirname "$full_path")
			mkdir -p "${target_root}"/"${dir_name#$source_root}"
			mv "$full_path_alac" "$target_root"/"${full_path_alac#$source_root}"
		fi
	done
```

---

### Post by Vaphell on 2013-04-13
this should be enough to find and convert
```
while read -rd $'\0' f
do
  echo flac: $f
  ffmpeg -i "$f" -acodec alac "${f%.[fF][lL][aA][cC]}.m4a"
done < <( find /home/jack/Downloads/complete/Music/ '-iname '*.flac' -print0 )
```

music/artist/album should be pulled from tags?

either way here is an interesting thread
[http://ubuntuforums.org/showthread.php?t=889700](http://ubuntuforums.org/showthread.php?t=889700)

---

### Post by jacox on 2013-04-14
> **prodigy_ said:**
> ```
#!/bin/bash

source_root="/home/jack/Downloads/complete/Music"
target_root="~/media/D3/Music"

mkdir -p "$target_root"

find "$source_root" -type f -print0 | \
    while read -r -d $'\0' full_path; do
        if file "$full_path" | grep 'FLAC audio bitstream data'; then
            full_path_alac="${full_path%\.*}.m4a"
            ffmpeg -y -i "$full_path" -acodec alac "$full_path_alac"
            [ $? -eq 0 ] && rm "$full_path"
            dir_name=$(dirname "$full_path")
            mkdir -p "${target_root}"/"${dir_name#$source_root}"
            mv "$full_path_alac" "$target_root"/"${full_path_alac#$source_root}"
        fi
    done
```


This script appears to convert the files to the appropriate format, but i'm not sure where it is moving the newly converted files to? It is however deleting the originals.. I have checked the '~/media/D3/Music' folder and it remains empty.

---

### Post by jacox on 2013-04-14
After searching for one of the converted directory names i found this. It seems that the script has done its job, but has not copied the newly created files and directory to where it's supposed to go '~/media/D3/Music/'

I'm not sure how to achieve this?


 [IMG]http://i.imgur.com/ZCMvdzC.png[/IMG]

---

### Post by prodigy_ on 2013-04-14
> **jacox said:**
> After searching for one of the converted directory names i found this. It seems that the script has done its job, but has not copied the newly created files and directory to where it's supposed to go '~/media/D3/Music/'
Apparently '~' was not expanded and that's why it's always better to use absolute paths in scripts. Fix (assuming that '~' is '/home/jack'): ```
#!/bin/bash

source_root="/home/jack/Downloads/complete/Music/~/media/D3/Music"
target_root="/home/jack/media/D3/Music"

find "$source_root" -type f -iname '*\.m4a' -print0 | \
	while read -r -d $'\0' full_path; do
		dir_name=$(dirname "$full_path")
		mkdir -p "${target_root}"/"${dir_name#$source_root}"
		mv "$full_path" "$target_root"/"${full_path#$source_root}"
	done
```

---

### Post by Vaphell on 2013-04-14
~ works only when it's unprotected by "", just like * and other key symbols

```
$ echo ~
/home/me
$ echo "~"
~
```

use $HOME istead, eg "$HOME/Downloads/complete/Music"

---

### Post by jacox on 2013-04-15
I have the script working now. It is converting the flac files to the correct format and creating the new flac files with the corresponding directory in the new directory on the correct drive. What i want to happen now though is for the folders that have been left behind to be deleted.

Is this possible? 

I'm using the script provided by prodigy_

---

### Post by Bucky Ball on 2013-04-15
*Thread moved to **Programming Talk**.*

---

