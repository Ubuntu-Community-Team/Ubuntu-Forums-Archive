---
title: "Bash script to split a large folder, please optimize."
date: 2012-06-01
forum: Programming Talk
---

### Post by melrokz on 2012-06-01
Here is my first Bash script, used to split a big folder containing thousands of files into many subfolders. You may specify the no. of files per folder.

Usage: ./script.sh folder_name

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

Here is another script to create empty files to test the first script:

Usage: ./script.sh folder_name

```
#!/bin/bash
# Script to create empty files in the specified folder.
if [ -z "$1" ]; then
	echo "Enter the destination folder as a parameter."
	exit
elif [ ! -d "$1" ]; then
	echo "No such folder."
	exit
fi

# Change folder and discard output and errors
cd $1 1> /dev/null 2>&1
read -p "Enter the no. of empty files: " fileno
echo "Creating empty files..."
for ((i=1; i<=fileno; i++))
do
	touch f$i
done
```

Please optimize or point out errors if any...

---

### Post by Vaphell on 2012-06-01
```
cd $1
```
missing quotes

```
file_count=$(ls | cat | wc -l)
```
what is this... i don't even... ;-)
newline is a legit character in filenames, so don't count on ls printing as many lines as there are files/dirs. Ls should not be used for anything except visual feedback. Use built-in globs with loops or find instead, eg:
[I]for f in *; do if [ -f "$f" ]; then (( fc++ )); fi; done
find -mindepth 1 -maxdepth 1 -type f -printf "x" | wc -c[/I]

```
mkdir `printf "%03d\t" $i`
```
backticks are deprecated and $() should be used

```
percent=$(printf "%.0f" $(echo "scale=2; (($file_count-$left_files)/$file_count)*100" | bc))
```
*percent=$(( 100*(file_count-left_files)/file_count ))*

---

### Post by sisco311 on 2012-06-02
Even if $1 is a directory cd will fail if you don't have execute permission for it:
```

[sisco@acme xtmp]$ mkdir foo
[sisco@acme xtmp]$ chmod -x foo
[sisco@acme xtmp]$ cd foo
bash: cd: foo: Permission denied

```

In this case your code will run in the current working directory. 


I'd do something like:
```

if (( $# != 1 ))
then
    # errors and warnings shall be redirected to stderr:
    printf '%s\n' "Enter the destination folder as a parameter." >&2
    exit 1
fi

# exit if the cd command fails
cd "$1" || exit 1

```

cd will print an appropriate error massage if it fails, but if you wish, you can print a custom one:
```
cd "$1" > /dev/null 2>&1 || { printf '%s\n' "$0: I don't want to change the current directory to $1"; exit 1; } >&2
```

---

### Post by melrokz on 2012-06-02
> 
```
percent=$(printf "%.0f" $(echo "scale=2; (($file_count-$left_files)/$file_count)*100" | bc))
```
*percent=$(( 100*(file_count-left_files)/file_count ))*

Thanks a lot :) Greatly helps me learn. 

For Zenity to show a progress bar, percent variable needs to be 1 to 100 and not floating point. So I first calculate in float, round it up to get 1 more folder to put the remaining files into. Hence the 'printf' format. And I don't need to $ reference variables here?

Also, I'd like to know how to go about copying files instead of moving, everything else being the same. Maybe a few hints on how to proceed? :)

---

### Post by melrokz on 2012-06-02
what does this do? Didn't understand the format.

```
printf "%03d\t"
```

---

### Post by codemaniac on 2012-06-02
> **melrokz said:**
> what does this do? Didn't understand the format.

```
printf "%03d\t"
```
The printf command provides a method to print preformatted text similar to the printf() system interface (C function). It's meant as successor for echo and has far more features and possibilities. 

The format string interpretion is derived from the C printf() function family. 
To print a literal % (percent-sign), use %% in the format string. 

%d prints the associated argument as **signed decimal**  number                                                                                                                                                                   .

---

### Post by Vaphell on 2012-06-02
percent=$(( 100*(file_count-left_files)/file_count ))

in 'integer mode' marked by (( )) you are guaranteed to get only integers, divisions lose their fraction part. You should go to other sources only if you need floating point math.
Order of operations is important though
```
$ file_count=33333; left_files=4321
$ echo $(( 100*(file_count-left_files)/file_count ))
87
$ echo $(( (file_count-left_files)/file_count*100 ))
0
```
in 2nd case (file_count-left_files)/file_count is in 0-1 range, which means it will be 0 for anything except 1. No amount of multiplication can change that broken result later therefore divisions should be calculated last.

text inside (()) is automatically treated as a variable name (what else could that be, hm?), so no need for $ sign. The difference between a+b and $a+$b is that in former case values are substituted during the calculation itself, while in the latter the values are substituted before and math fairy sees 1+2. Little to no difference in outcomes :)

---

