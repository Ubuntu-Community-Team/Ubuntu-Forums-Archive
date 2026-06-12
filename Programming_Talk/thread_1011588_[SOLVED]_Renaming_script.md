---
title: "[SOLVED] Renaming script"
date: 2008-12-14
forum: Programming Talk
---

### Post by king vash on 2008-12-14
I want a script that runs through a directory and all the sub directories capitalizing specified words and lowercasing all others


I started writing the script but I am having troubles. My script is posted below, any help would be appreciated

I am think that a sed 'y!tag!Tag! or something would work


right now I have this as a basic idea


```
#!/bin/sh
#given directory will change all files and folders to a constant capitilizastion scheme
#scheme is
#folders = first letter capitalised
#files = first letter capitalised


clear

change_directory() {
if [ -d "$1" ]; then
	rename -v -n 'y/A-Z/a-z/'
fi
}

change_file() {
if [ -f "$1" ]; then
	rename -v -n 'y/A-Z/a-z/'
fi
}

if [ $# = 1 ]; then
	if [ -d "$1" ]; then
		cd "$1"
#		find -maxdepth 4 -type d  | while read name
#		do 
#			if [ -d "$name" ]; then 
#				echo "test ""$name"
#				change_directory "$name"
#				echo ""
#			fi
#		done
		find -maxdepth 6 -type f  | while read name
		do 
			if [ -f "$name" ]; then
				echo "test ""$name"
				change_file "$name"
				echo ""
			fi
		done
	else
		echo "parameter one must be a directory"
	fi
else
	echo "need one parameters : directory to change, files or folders"
fi
```

---

### Post by mssever on 2008-12-14
What isn't working? I noticed that you're specifying the maxdepth option to find, which could easily artificially limit your script.

Your basic approach is probably OK, but I would prefer a recursive approach myself. Something like this: ```
function renamer {
  local directory="$1"
  local file=
  for file in "$directory"/*; do
    [ -d "$file" ] && renamer "$file"
    # Code to rename file here
  done
}

renamer "$1"
```

---

### Post by geirha on 2008-12-14
rename needs to know which file to rename, so add "$1" to the renames.

And, in your find loop, there's no need to double check if $name is a file when you've already told find to only list files (-type f). 

The script you have now could also be run on one line
```
find -maxdepth 6 -type f -exec rename -v -n 'y/A-Z/a-z/' {} \;
# or
find -maxdepth 6 -type f -print0 | xargs -0 -- rename -v -n 'y/A-Z/a-z/'
```

---

### Post by king vash on 2008-12-17
Thanks so much for all your help

I ended up with this which works fine if you do not have have files that overlap (file and File)

```
#!/bin/sh
#given directory will change all files and folders to a constant capitilization scheme
#scheme is
  #folders = first letter capitalised
  #files = first letter capitalised




renamer() {
	directory="$1"
	for file in "$directory"/*; do
		if [ -f "$file" ]; then
			basefolder=`dirname "$file"`
			filename=`basename "$file"`
			testfilename=`echo "$filename" | sed 's!^.!\l&!' `
			echo "  old file : $filename"
			if [ "$filename" != "$testfilename" ]; then
				echo "    RENAMING FILE"
				echo "    new file : $testfilename"
				mv "$basefolder"/"$filename" "$basefolder"/"$testfilename"
			fi
		fi
		if [ -d "$file" ]; then
			basefolder=`dirname $file`
			dirname=`basename "$file"`
			testdirname=`echo "$dirname" | sed 's!^.!\l&!' `
			echo "dir : $dirname"
			if [ "$dirname" != "$testdirname" ]; then
				echo "RENAMING DIRECTORY"
				echo "  dir : $basefolder/$dirname --> $basefolder/$testdirname"
				mv "$basefolder"/"$dirname" "$basefolder"/"$testdirname"
			fi
			renamer "$file"
		fi
  	done
}



clear

if [ $# = 1 ]; then
	if [ -d "$1" ]; then
		renamer "$1"
	else
		echo "parameter one must be a directory"
	fi
else
	echo "need one parameters : directory to change"
fi

```

---

