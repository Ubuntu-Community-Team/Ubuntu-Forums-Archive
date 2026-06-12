---
title: "Bash: help handling spaces in script"
date: 2009-07-15
forum: Programming Talk
---

### Post by roccivic on 2009-07-15
Gedit leaves backup files every time it's used and once in a while I'd like to get rid of all. I thought I'd make a quick script for removing all gedit backup files from the home directory of anyone running said script.

All nice until I realized I don't know how to deal with spaces in paths and filenames in bash, because they are the separators for lists. Here's the script I made:

```
#! /bin/bash
list=$(find ~ -name "*~")
echo "Found following garbage:"
echo
for file in $list; do
   echo $file
done
echo -e "\nPress ENTER to proceed deleting above files, CTRL+C to cancel."
read
for file in $list; do
   rm $file
done
echo "Finished, have a nice day."
```

And here the output, obviously "add post form~" is one file, not 3:
```
roccivic@roccivic-pc:~$ '/home/roccivic/Desktop/clean_gedit' 
find: /home/roccivic/.dbus: Permission denied
Found following garbage:

/home/roccivic/Desktop/clean_gedit~
/home/roccivic/Desktop/openDNS~
/home/roccivic/Software/dst/archive/add
post
form~
/home/roccivic/Software/dst/clear.html~
/home/roccivic/Software/dst/report.js~
/home/roccivic/Software/dst/CHANGELOG~

Press ENTER to proceed deleting above files, CTRL+C to cancel.

rm: cannot remove `/home/roccivic/Software/dst/archive/add': No such file or directory
rm: cannot remove `post': No such file or directory
rm: cannot remove `form~': No such file or directory
Finished, have a nice day.

```

Many thanks for any help with this in advance.
Rouslan

---

### Post by roccivic on 2009-07-15
Just in case:
```
roccivic@roccivic-pc:~$ bash --version
GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu)
Copyright (C) 2007 Free Software Foundation, Inc.
roccivic@roccivic-pc:~$ uname -r
2.6.24-23-generic
```

---

### Post by mcduck on 2009-07-15
Just put quotes around the filename, or in this case around the variable that contains the filename.

By the way, the backup copies can be disabled from Gedit's preferences.. ;)

---

### Post by roccivic on 2009-07-15
> **mcduck said:**
> Just put quotes around the filename, or in this case around the variable that contains the filename.

By the way, the backup copies can be disabled from Gedit's preferences.. ;)

That won't work, in the "for" loop the list is separated by spaces, so the variable (filename) already comes out broken into 3 piece on the other side.

Yeah, I know I can disable backups, but sometimes (when I screw something up) they do come in handy :)

---

### Post by roccivic on 2009-07-15
Formatted and modified code:
```
#!/bin/bash
DIR="$1" # failsafe - fall back to current directory
[ "$DIR" == "" ] && DIR="." # save and change
IFSOLDIFS=$IFSIFS=$'\n' # read all file name into an array
fileArray=($(find $DIR -name "*~")) # restore it
IFS=$OLDIFS # get length of an array
tLen=${#fileArray[@]} # use for loop read all filenames
for (( i=0; i<${tLen}; i++ ));do
   echo "${fileArray[$i]}"
done
```
Output:
```
roccivic@roccivic-pc:~$ '/home/roccivic/Desktop/clean_gedit-2' 
find: ./.dbus: Permission denied
./Desktop/clean_gedit~
./Desktop/clean_gedit-2~
./Software/dst/archive/add
post
form~
roccivic@roccivic-pc:~$ 
```

---

### Post by sisco311 on 2009-07-15
```
#!/bin/bash

find ~ -name "*~" | tee /tmp/files

echo -e "\nPress ENTER to proceed deleting above files, CTRL+C to cancel."
read

cat /tmp/delfiles | xargs -d "\n" rm
rm /tmp/files


```

---

### Post by ghostdog74 on 2009-07-15
to take care of spaces, you can use while read loop together with your find command
```

find .... | while read line
do
 .....
done

```

---

### Post by roccivic on 2009-07-15
> **sisco311 said:**
> ```
#!/bin/bash

find ~ -name "*~" | tee /tmp/files

echo -e "\nPress ENTER to proceed deleting above files, CTRL+C to cancel."
read

cat /tmp/files | xargs -d "\n" rm
rm /tmp/files


```

Worked perfect, thanks

---

### Post by roccivic on 2009-07-15
> **ghostdog74 said:**
> to take care of spaces, you can use while read loop together with your find command
```

find .... | while read line
do
 .....
done

```

Doesn't work, or well, maybe it's just that I can't get it to work.

---

### Post by sisco311 on 2009-07-15
> **roccivic said:**
> Doesn't work, or well, maybe it's just that I can't get it to work.

it should work, but in your case you have to use the find command twice:
```

find ~ -iname "*~"

echo -e "\nPress ENTER to proceed deleting above files, CTRL+C to cancel."
read

find ~ -iname "*~" | while read file; do
  rm "$file"
done

#or

find ~ -iname "*~" -print0 | xargs -0 rm

#or

find ~ -iname "*~" -delete

```

---

### Post by mcduck on 2009-07-15
> **roccivic said:**
> That won't work, in the "for" loop the list is separated by spaces, so the variable (filename) already comes out broken into 3 piece on the other side.

Yeah, I know I can disable backups, but sometimes (when I screw something up) they do come in handy :)

You don't even need the list in the first place..

```
#! /bin/bash

echo "Found following garbage:"
echo
for file in *~; do
   echo "$file"
done

echo -e "\nPress ENTER to proceed deleting above files, CTRL+C to cancel."
read
for file in *~; do
   rm "$file"
done
echo "Finished, have a nice day."
```

---

### Post by kaibob on 2009-07-15
I got your script to work with an array after changing the internal field separator. I also had to double-quote a few variables. 

```
#! /bin/bash

IFSBAK=$IFS
IFS=$'\n'
list=( $(find ~ -name "*~" -type f) )
IFS=$IFSBAK

echo "Found following garbage:"
echo
for file in "${list[@]}" ; do
   echo "$file"
done

echo -e "\nPress ENTER to proceed deleting above files, CTRL+C to cancel."
read
for file in "${list[@]}" ; do
   rm "$file"
done

echo "Finished, have a nice day."
```

---

