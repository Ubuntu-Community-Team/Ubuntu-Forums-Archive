---
title: "zenity and files names"
date: 2011-04-28
forum: Programming Talk
---

### Post by chukchuck on 2011-04-28
My start script is this:

```
DEST="$HOME/prova"
FILES=`zenity --file-selection --multiple --separator=' ' --title="Choose files"`
mv $FILES $DEST
zenity --info --text="Files $FILES have been moved correctly"
```

I want to move 2 or more files and my 2 question about zenity are:

1) in zenity --info etc ... i have a problem because it dispaly me all the path but i want to be display ONLY the files names. How can i do it?

2) if i choose files that are in a folder which name have space (example a directory called: DIR DOR) it doesn't work because "mv" doesn't recognize the path with space. How can i solve it?

Thanks a lot!

---

### Post by DaithiF on 2011-04-28
Hi,
first the code:
```
#!/bin/bash

dest="$HOME/prova"
IFS=$'\n' files=($(zenity --file-selection --multiple --separator=$'\n' --title="Choose files"))
mv "${files[@]}" "$dest"

# iterate through $files array of paths, picking out the filename 
# from each
for f in ${files[@]}
do
  name=${f##*/}
  names="$names $name"
done
zenity --info --text="Files:$names have been moved correctly"

```

second, some explanations:
1. your problem with spaces in paths is twofold:
  (a) you're asking zenity to output the files you choose using a space character as the separator between each one.  Once you've done that its impossible to know whether a space is a separator between two files or a character in a files path.  Instead ask zenity to use a character that is unlikely (or impossible) to appear in a filename.  Ideally the null character but I don't know if zenity can output that so i've chosen the newline \n character instead.
  (b) in order to move a file with spaces you need to quote it (ie. surround it with quotes).  In order to put quotes around the right parts of the string that zenity outputs you need to split that string into an array, and using the newline character as the delimiter for that array.  That is the purpose of the IFS=$'\n' files=(...) code
2. to show only names of the files rather than full paths you need to iterate through each one and strip off the path piece
3. better to use lower case variable names to avoid overwriting environment variables (which are CAPITALS)

---

### Post by chukchuck on 2011-04-28
First of all thanks for the reply! :D

Then let me ask you some explanations:

1) you have set IFS=$'\n' but what does $'\n' mean? I know that \n stay for newline and i know that IFS stay for whitespace...

2) --separator=$'\n' why? You have set "newline" as separator between path or filename??

3) "${files[@]}" i don't understand [@] (or better: i don't know why to write it)

4) i haven't understand so much clearly the for cycle...
```
for f in ${files[@]} #THIS IS OK
do                         #ALSO THIS IS OK
  name=${f##*/}            #ERRR....WHAT IS IT??
  names="$names $name"     #ERRR...???
done
```

And last....thanks thanks thanks for all of your help :)

---

### Post by DaithiF on 2011-04-28
> **chukchuck said:**
> 1) you have set IFS=$'\n' but what does $'\n' mean? I know that \n stay for newline and i know that IFS stay for whitespace...
$'\n' is a way of representing the newline character on the command line.  IFS is bash's Internal Field Separator, or what bash uses when deciding how to split something up into discrete parts ... in our case zenity spits out a big string which has newlines between each file that you chose, and by surrounding this with ( ) we are asking bash to split the string into an array, using the separator (IFS) that we have just set 
> 
2) --separator=$'\n' why? You have set "newline" as separator between path or filename??
if in the zenity dialog you choose two files ... /foo/bar and /foo/bar1, the output of zenity will be /foo/barX/foo/bar1 where X is whatever you ask for in the --separator parameter.  So in our case we would get:
/foo/bar
/foo/bar1
(ie. the two files you chose separated by a newline.  So notice that we are specifying 'use a newline as a separator' twice ... once when telling zenity what to output between each file you choose, and again telling bash how to separate that zenity output into discrete elements of the array that we create.

> 
3) "${files[@]}" i don't understand [@] (or better: i don't know why to write it)
files is a bash array.  probably worth you googling for bash arrays to understand how they work, but for example: ${files[0]} would be the first element of the array, ${files[1]} would be the 2nd, and ${files[@]} would be all elements of the array.  The other one you will see is ${files
[*]} which also means all elements of the array, but the distinction between the '@' and '*' is that when you surround the ${files[@ or *]} in  quotes, then the result is for @ is each element surround by quotes, whereas the result for * is all the elements surrounded by one set of quotes.   ie. in our example above, 
${files[@]} would expand to "/foo/bar" "/foo/bar1", 
whereas
${files
[*]} would expand to "/foo/bar /foo/bar1"

> 
4) i haven't understand so much clearly the for cycle...
```
for f in ${files[@]} #THIS IS OK
do                         #ALSO THIS IS OK
  name=${f##*/}            #ERRR....WHAT IS IT??

```
see bash parameter expansion in man bash.  this strips content from the beginning of a string, every character up to and including the last occurrence of '/'.  You will often see this method used to strip a filename from a path, or a related ${f%/*} concept to strip off a filename leaving the path of the parent directory

> 
  names="$names $name"     #ERRR...???
done> 
each time through the loop $name becomes a filename.  This line just builds a cumulative record of all the $name instances, so that by the end $names contains them all.

---

### Post by chukchuck on 2011-04-28
Many many many thanks man! :P:popcorn:

---

### Post by hakermania on 2011-04-29
Hey, leaving only the filename could be done with ```
basename
``` as well ;)
nice solution and many things I didn't know, I will bookmark it and have a look ;)

---

