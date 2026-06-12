---
title: "Bash Split folder by size..."
date: 2013-07-17
forum: Programming Talk
---

### Post by bnsmith001 on 2013-07-17
I have a group of directories that I need to split for backup.

The directories contain less than 9 Gig of data split amongst over 100 files.

I am looking to write a script to toss into my ~/bin folder to split the directory into two directories by SIZE.
Call it DVDsplit (ie less than a dvd-5 of data).
DVDsplit will be run from the directory to split.
It will create a subdirectory named part1, and a subdirectory named part2

The following thread is closed... 
[http://ubuntuforums.org/showthread.php?t=1993087]("http://ubuntuforums.org/showthread.php?t=1993087")
so I couldn't respond there, 
but the thread provided me with a starting template for a script.

```
#!/bin/bash
#This shell script splits a large folder of files into many smaller subfolders. You can define the no. of files in a subfolder.
# Doubts: printf "format"

# Checking input...
read -p "No. of files in each folder: " nofiles
if [ -z "$1" ]; then
   echo "Please specify a directory to split, as a parameter to the script."
   exit
else
   if [ ! -d "$1" ]; then
      echo "directory $1 does not exist."
      exit
   fi
fi
# Change to the specified folder
cd $1
# getting the count of files
# assuming no hidden files are being moved
file_count=$(ls | cat | wc -l)
# no. of sub folders = total no. of files / no. of files in each folder.
dir_no=$(printf "%.0f" $(echo "scale=2; $file_count/$nofiles" | bc))
echo "$file_count files to be moved..."
# define variables
i=1
j=1
# loop 1: create sub folders and execute loop 2
(until [ "$i" -gt "$dir_no" ]
do
	mkdir `printf "%03d\t" $i`
# loop 2: fill each folder with the no. of files specified.
	ls | cat | sort -gb | while [ "$j" -le "$nofiles" ]
	do
		# Code that moves files
		read line
		mv "$line" "$i"
		let j=j+1
	done
	let i=i+1
	# percent = total files - remaining files / total files * 100	
	left_files=$(ls | cat | wc -l)
	percent=$(printf "%.0f" $(echo "scale=2; (($file_count-$left_files)/$file_count)*100" | bc))
	echo $percent
	# Use the percent variable to show a graphical progress bar using zenity
done) | zenity --progress --auto-close --title="Folder splitter"  \
               --text="Processing files..." --percentage=0
if [ "$?" == "0" ]; then
echo "$dir_no folders have been created, with $nofiles files in each"
fi
```

First thing, I'll do is rip the prompt out --
```
# Checking input...
read -p "No. of files in each folder: " nofiles
if [ -z "$1" ]; then
   echo "Please specify a directory to split, as a parameter to the script."
   exit
else
   if [ ! -d "$1" ]; then
      echo "directory $1 does not exist."
      exit
   fi
fi

```
Okay, I'm not so brash as to throw away code. ;)
I'll comment it out.
See?
```
# Checking input...
# read -p "No. of files in each folder: " nofiles
# if [ -z "$1" ]; then
   # echo "Please specify a directory to split, as a parameter to the script."
   # exit
# else
   # if [ ! -d "$1" ]; then
      # echo "directory $1 does not exist."
      # exit
   # fi
# fi
```

The next thing I want to do is move any "part1" and "part2" directory files back, in case a previous run of the script blew up.
#Merge any part1 or part2 files back into current directory.
```
if [ ! -d "./part1" ]; then
  echo "directory PART1 does not exist."
else 
  mv -f ./part1/* ./
fi

if [ ! -d "./part2" ]; then
  echo "directory PART2 does not exist."
else 
  mv -f ./part2/* ./
fi
```

The next thing I want to do is create "part1" and "part2" directories in case they don't exist.
I can merge this into the previous block of code, under the DNE (does not exist) logic.
```
#Merge any part1 or part2 files back into current directory.
#Optionally, create work directories.
if [ ! -d "./part1" ]; then
  echo "directory PART1 does not exist. create."
  mkdir part1
else 
  mv -f ./part1/* ./
fi

if [ ! -d "./part2" ]; then
  echo "directory PART2 does not exist. create"
  mkdir part2
else 
  mv -f ./part2/* ./
fi
```

Unlike the original poster, I come from a C/C++/C# background, so printf doesn't scare me. :)

Currently, the script looks like --
```
#!/bin/bash
#This shell script splits a large folder of files into two smaller subfolders.

# Checking input...
# read -p "No. of files in each folder: " nofiles
# if [ -z "$1" ]; then
   # echo "Please specify a directory to split, as a parameter to the script."
   # exit
# else
   # if [ ! -d "$1" ]; then
      # echo "directory $1 does not exist."
      # exit
   # fi
# fi

#Merge any part1 or part2 files back into current directory.
#Optionally, create work directories.
if [ ! -d "./part1" ]; then
  echo "directory PART1 does not exist. create."
  mkdir part1
else 
  mv -f ./part1/* ./
fi

if [ ! -d "./part2" ]; then
  echo "directory PART2 does not exist. create"
  mkdir part2
else 
  mv -f ./part2/* ./
fi

## Continue here - bns
# Change to the specified folder
cd $1
# getting the count of files
# assuming no hidden files are being moved
file_count=$(ls | cat | wc -l)
# no. of sub folders = total no. of files / no. of files in each folder.
dir_no=$(printf "%.0f" $(echo "scale=2; $file_count/$nofiles" | bc))
echo "$file_count files to be moved..."
# define variables
i=1
j=1
# loop 1: create sub folders and execute loop 2
(until [ "$i" -gt "$dir_no" ]
do
	mkdir `printf "%03d\t" $i`
# loop 2: fill each folder with the no. of files specified.
	ls | cat | sort -gb | while [ "$j" -le "$nofiles" ]
	do
		# Code that moves files
		read line
		mv "$line" "$i"
		let j=j+1
	done
	let i=i+1
	# percent = total files - remaining files / total files * 100	
	left_files=$(ls | cat | wc -l)
	percent=$(printf "%.0f" $(echo "scale=2; (($file_count-$left_files)/$file_count)*100" | bc))
	echo $percent
	# Use the percent variable to show a graphical progress bar using zenity
done) | zenity --progress --auto-close --title="Folder splitter"  \
               --text="Processing files..." --percentage=0
if [ "$?" == "0" ]; then
echo "$dir_no folders have been created, with $nofiles files in each"
fi
```

I fully realize that the original logic is counter-based. 
I need to research completely reworking the loop logic into a loop based upon the original filesize sum of main directory, and an inner loop approximating half for filling part2. When the part2-filling loop ends, i need to move the remaining files in main directory to part1.

Talk amongst yourselves.  Give me pointers.  I'll watch the thread. :)

---

### Post by bnsmith001 on 2013-07-17
Crud! I just found a command that is in BASH's arsenal...

**[SIZE=4]dirsplit[/SIZE]**

I guess this thread can be completely deleted!!!

Thanks!

---

