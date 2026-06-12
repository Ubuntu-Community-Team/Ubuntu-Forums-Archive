---
title: "is this a dash shell error?"
date: 2011-11-23
forum: Programming Talk
---

### Post by saphil on 2011-11-23
or maybe I am just confused ("What! Surely not")

This line works to copy a series of filenames to filenames including the extra string
```

ParentDir=$(echo "${PWD}" | awk -F'/' '{print $NF}')
for i in $(ls); do cp """${i}" "$ParentDir"_"${i}"""; done

```
however when I attempt to get the for loop to cd into a set of folders and do the same thing in each, the pine fails saying cannot stat the parent directory (which it properly names)
```

for i in $(ls); do cd "${i}"; ParentDir=$(echo "${PWD}" | awk -F'/' '{print $NF}'); echo "$ParentDir"; cp "${i}" ""$ParentDir"_"${i}""; cd ..; done
# The output is:
College_1913-12-26
#This is the result of the echo command
cp: cannot stat `College_1913-12-26': No such file or directory  #How is it that it cannot be found here??


```

---

### Post by Bachstelze on 2011-11-23
This will give you a better idea of what's going on:

```
for i in *; do
        cd "${i}"
        echo "changed dir to $(pwd)"

        ParentDir=$(echo "${PWD}" | awk -F'/' '{print $NF}')
        echo "ParentDir is $ParentDir"

        echo "trying to copy $i to ${ParentDir}_$i"
        if ! cp -v "${i}" ""$ParentDir"_"${i}""; then
                echo "    failed"
        else
                echo "    success"
        fi
        echo

        cd ..
        echo "changed dir to $(pwd)"
done

```

---

### Post by ofnuts on 2011-11-23
> **saphil said:**
> or maybe I am just confused ("What! Surely not")

This line works to copy a series of filenames to filenames including the extra string
```

ParentDir=$(echo "${PWD}" | awk -F'/' '{print $NF}')
for i in $(ls); do cp """${i}" "$ParentDir"_"${i}"""; done

```however when I attempt to get the for loop to cd into a set of folders and do the same thing in each, the pine fails saying cannot stat the parent directory (which it properly names)
```

for i in $(ls); do cd "${i}"; ParentDir=$(echo "${PWD}" | awk -F'/' '{print $NF}'); echo "$ParentDir"; cp "${i}" ""$ParentDir"_"${i}""; cd ..; done
# The output is:
College_1913-12-26
#This is the result of the echo command
cp: cannot stat `College_1913-12-26': No such file or directory  #How is it that it cannot be found here??


```
What is wrong with 
```
Parentdir=$(basename $PWD)
``` (assumig this is really what you want, of course)

---

### Post by ehmicky on 2011-11-23
Hi,

Is it what you're trying to do ?
```
for i in * ; do cp "$i" "$(basename "$PWD")_$i" ; done
```

---

### Post by saphil on 2011-11-23
> **Bachstelze said:**
> This will give you a better idea of what's going on:

```
for i in *; do
        cd "${i}"
        echo "changed dir to $(pwd)"

        ParentDir=$(echo "${PWD}" | awk -F'/' '{print $NF}')
        echo "ParentDir is $ParentDir"

        echo "trying to copy $i to ${ParentDir}_$i"
        if ! cp -v "${i}" ""$ParentDir"_"${i}""; then
                echo "    failed"
        else
                echo "    success"
        fi
        echo

        cd ..
        echo "changed dir to $(pwd)"
done

```

Thanks, that is helpful - I see that the cd into command is not working but the cd .. did work.  I am sure there is a better way to do this and I am reading through responses.

---

### Post by saphil on 2011-11-23
> **ofnuts said:**
> What is wrong with 
```
Parentdir=$(basename $PWD)
``` (assumig this is really what you want, of course)

I am in a directory that contains directories.  
```
Parentdir=$(basename $PWD) 
```
w[FONT=Arial]orked well to tell me where I am, and as usual, your code is slicker than mine.  However, as Bachstelze pointed out, my cd command is not working how I expected - I want to get into the sub-directories and rename their children, so I can move them out of the subfolders and package them for other processes.  Currently I have a lot of files with identical names, which would fight each other to death if I just moved them to a common folder.[B][FONT=Arial][SIZE=2][/SIZE][/FONT]

[/B][/FONT]

---

### Post by saphil on 2011-11-23
> **ehmicky said:**
> Hi,

Is it what you're trying to do ?
```
for i in * ; do cp "$i" "$(basename "$PWD")_$i" ; done
```

ehmicky - This is exactly what I was trying to do!  However I am in a directory that I want to go into the subdirectories and change the files in them to the names of their parent dir.

```

total 68
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:19 1010
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:20 11
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:19 1212
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:20 1313
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:19 1414
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:21 1515
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:19 1616
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:21 22
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:20 33
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:21 44
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:20 55
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:21 66
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:20 77
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:21 88
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:20 99
drwxr-xr-x 2 lyrasis lyrasis 4096 2011-11-23 15:21 9999
-rw-r--r-- 1 lyrasis lyrasis    0 2011-11-08 14:40 dd.pdf
-rw-r--r-- 1 lyrasis lyrasis    0 2011-11-08 14:40 ee.pdf
-rw-r--r-- 1 lyrasis lyrasis    0 2011-11-08 14:40 gg.pdf
-rw-r--r-- 1 lyrasis lyrasis    0 2011-11-08 14:40 hh.pdf
-rw-r--r-- 1 lyrasis lyrasis    0 2011-11-08 14:40 ii.pdf
-rwxr-xr-x 1 lyrasis lyrasis  385 2011-11-10 19:26 ntest.sh

./1010:
total 0
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 dd.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 ee.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 gg.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 hh.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 ii.pdf

./11:
total 0
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:20 dd.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:20 ee.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:20 gg.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:20 hh.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:20 ii.pdf

./1212:
total 0
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 dd.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 ee.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 gg.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 hh.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 ii.pdf

./1313:
total 0
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:20 dd.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:20 ee.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:20 gg.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:20 hh.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:20 ii.pdf

./1414:
total 0
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 dd.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 ee.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 gg.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 hh.pdf
-rw-r--r-- 1 lyrasis lyrasis 0 2011-11-23 15:19 ii.pdf

# and so on 

```

I want to change ./1414/dd.pdf to ./1414/1414_dd.pdf.  However I don't want to have to manually motor into each folder, as there are hundreds that need to be so treated.

---

### Post by Vaphell on 2011-11-23
code maybe something like this?
```
for f in */*
do
  if [ -f "$f" ]
  then
    echo $f is a file 
    echo mv -v "$f" "${f%/*}/${f%/*}_${f##*/}"
  else
    echo $f is a dir
  fi
done
``` now it prints out the mv command for testing purposes

```
$ ./mass_ren.sh 
111/a.txt is a file
mv -v 111/a.txt 111/111_a.txt
111/b.txt is a file
mv -v 111/b.txt 111/111_b.txt
222/a.txt is a file
mv -v 222/a.txt 222/222_a.txt
222/b.txt is a file

```

---

### Post by saphil on 2011-11-23
Thanks Y'all
The following script appears to rename all files 2 levels down and below with the name of it's pwd prepending it. 

```

find . -depth -mindepth 2 -type d -print0 | while IFS= read -r -d ''  subdir; do    (cd "$subdir"; echo "${PWD} is where we are"; for i in * ;  do mv "$i" "$(basename "$PWD")_$i" ; done ; echo ${i} );  done
```

I broke this down as follows.  The only part I am not sure of is ```
read -r -d
```
=====================================
```
find
``` A command that lets you do a huge amount with the filesystem.  It is such an understatement to call this "find."
```
. 
```means current directory
```
-depth
``` makes it handle the lowest files and folders first, 
```
-mindepth 2
``` keeps it from changing the names of pwd and the first level of subdirectories.  
```
-type d
``` means it only searches for directories
```
-print0 
```prints the output (to a file) or to be piped to another command as input, even if the output contains a newline character.
```
|
``` sends an output to another command. 
```
while 
``` While the argument is true, continue to loop across the contained expressions
```
IFS=
``` IFS is the "Input Field Separator" environmental variable. A string treated as a list of characters that is used for field splitting and to split lines into fields with the read[]("http://pubs.opengroup.org/onlinepubs/009695399/utilities/read.html") command. If *IFS* is not set, the shell shall behave as if the value of *IFS* is <space>, <tab>, and <newline>, in this case IFS= "read -r -d '' subdir" 
```
read -r -d '' subdir 
``` means the read command is going to be fed the subdirectories and separate the subdirectories on the null character (2 single-quotes) and each glob will be called subdir on its cycle through the while loop.  When there are no more subdirs, the while loop terminates.
```
;
``` ";" is a symbol to tell bash that what follows the ";" on the line is another command.
```
do
``` starts the body of the while loop
```
(
``` inside an expression, signals the launching of a subshell or a child process.  
```
cd "$subdir"
``` changes into the directory currently filling the value of the variable subdir. The dollar sign "$" lets the shell know that it is to use the value rather than the literal name of the variable
```
;
``` The following is a subsequent command expression on the same line.  Most commands, if followed by a newline character, do not need to be delimited with a ";" but some need the ";" regardless.
```
 echo "${PWD} is where we  are"
``` This is scaffolding to help me see what the command is doing and where.  It prints the location in the file-system and a jaunty cheer.  When it is proven that the code is doing as I expect it to, I will probably remove this scaffolding.
```
 ;
``` Another command is following on this line.
```
 for i in *
``` A for loop walks through a range or array of known size.  In this case the variable "i" will be given the value of each item in the current subdirectory
```
 ;
``` The next object in the string is a new command.
```
 do
``` shows the beginning of the body of this for loop.
```
 mv "$i" "$(basename "$PWD")_$i" 
``` rename the file with the name currently filling the "i" variable with a string concatenating the parent directory, a "_" and itself.
```
"$(basename "$PWD")_$i"
``` basename [path] returns the lowest-level directory (farthest from "/" or the root of the directory system). starting a child process to ascertain the basename of the environmental variable PWD gives a clean single string conforming to the current working directory.
```
;
``` What follows is another command without a newline character
```
 done
``` Denotes the end of the body of the for loop.
```
 ;
``` Yes, it means another command is on this line.
```
 echo  ${i}
``` This is another piece of scaffolding that is supposed to print to the screen the original filename.
```
 )
``` Denotes the closing of the substring
```
;
``` Would you believe there is another command following on this line?
```
 done
``` Denotes the end of the while loop body.


There must be several books written just on the find command.  Wow!

---

### Post by ehmicky on 2011-11-23
I think you can use Vaphell solution, it's full-bash and elegant. Just replace */* by "$PWD"/** if you want a recursivity of more than 2 levels, and do a "shopt -s globstar" before in order for ** to work.

---

### Post by saphil on 2011-11-23
> **ehmicky said:**
> I think you can use Vaphell solution, it's full-bash and elegant. Just replace */* by "$PWD"/** if you want a recursivity of more than 2 levels, and do a "shopt -s globstar" before in order for ** to work.

Vaphell's code worked great on one level of subdirectories.  
Thanks Vaphell
I have to go set up some more test systems to see how it looks on 2 levels deep.  :popcorn:

---

### Post by saphil on 2011-11-23
it is outputting a strange thing:
```

for f in "${PWD}"/**
do
  if [ -f "$f" ]
  then
    echo $f is a file 
    echo mv -v "$f" "${f%/*}/${f%/*}_${f##*/}"
  else
    echo $f is a dir
  fi
done
#---------------------
lyrasis@LTS-CLOUDCTL-01:~/bin/LyrasisCode/ftarget61$ bash mvmv.sh 
/home/lyrasis/bin/LyrasisCode/ftarget61/example1 is a dir
/home/lyrasis/bin/LyrasisCode/ftarget61/example2 is a dir
/home/lyrasis/bin/LyrasisCode/ftarget61/mvmv.sh is a file
mv -v /home/lyrasis/bin/LyrasisCode/ftarget61/mvmv.sh /home/lyrasis/bin/LyrasisCode/ftarget61//home/lyrasis/bin/LyrasisCode/ftarget61_mvmv.sh
/home/lyrasis/bin/LyrasisCode/ftarget61/Pig.pdf is a file
mv -v /home/lyrasis/bin/LyrasisCode/ftarget61/Pig.pdf /home/lyrasis/bin/LyrasisCode/ftarget61//home/lyrasis/bin/LyrasisCode/ftarget61_Pig.pdf
/home/lyrasis/bin/LyrasisCode/ftarget61/poke.pdf is a file
mv -v /home/lyrasis/bin/LyrasisCode/ftarget61/poke.pdf /home/lyrasis/bin/LyrasisCode/ftarget61//home/lyrasis/bin/LyrasisCode/ftarget61_poke.pdf


```
This looks like I would need to do $(basename "$PWD") to avoid adding the whole path into the filename.

---

### Post by saphil on 2011-11-23
My test directory structure
```

.
&#9500;&#9472;&#9472; example1
&#9474;   &#9500;&#9472;&#9472; dd.pdf
&#9474;   &#9500;&#9472;&#9472; ee.pdf
&#9474;   &#9500;&#9472;&#9472; example11
&#9474;   &#9474;   &#9500;&#9472;&#9472; dd.pdf
&#9474;   &#9474;   &#9500;&#9472;&#9472; ee.pdf
&#9474;   &#9474;   &#9500;&#9472;&#9472; gg.pdf
&#9474;   &#9474;   &#9500;&#9472;&#9472; hh.pdf
&#9474;   &#9474;   &#9500;&#9472;&#9472; ii.pdf
&#9474;   &#9474;   &#9492;&#9472;&#9472; pd.pdf
&#9474;   &#9500;&#9472;&#9472; gg.pdf
&#9474;   &#9500;&#9472;&#9472; hh.pdf
&#9474;   &#9492;&#9472;&#9472; ii.pdf
&#9500;&#9472;&#9472; example2
&#9474;   &#9500;&#9472;&#9472; dd.pdf
&#9474;   &#9500;&#9472;&#9472; ee.pdf
&#9474;   &#9500;&#9472;&#9472; example21
&#9474;   &#9474;   &#9500;&#9472;&#9472; ee.pdf
&#9474;   &#9474;   &#9500;&#9472;&#9472; example211
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; dd.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; ee.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; example2111
&#9474;   &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; dd.pdf
&#9474;   &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; ee.pdf
&#9474;   &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; gg.pdf
&#9474;   &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; hh.pdf
&#9474;   &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; ii.pdf
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; pd.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; gg.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; hh.pdf
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ii.pdf
&#9474;   &#9474;   &#9500;&#9472;&#9472; example212
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; dd.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; ee.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; gg.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; ii.pdf
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; pd.pdf
&#9474;   &#9474;   &#9500;&#9472;&#9472; gg.pdf
&#9474;   &#9474;   &#9492;&#9472;&#9472; ii.pdf
&#9474;   &#9500;&#9472;&#9472; example22
&#9474;   &#9474;   &#9500;&#9472;&#9472; ee.pdf
&#9474;   &#9474;   &#9500;&#9472;&#9472; example221
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; dd.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; ee.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; example2211
&#9474;   &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; dd.pdf
&#9474;   &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; ee.pdf
&#9474;   &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; gg.pdf
&#9474;   &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; hh.pdf
&#9474;   &#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; ii.pdf
&#9474;   &#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; pd.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; gg.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; hh.pdf
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; ii.pdf
&#9474;   &#9474;   &#9500;&#9472;&#9472; example222
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; dd.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; ee.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; gg.pdf
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; ii.pdf
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; pd.pdf
&#9474;   &#9474;   &#9500;&#9472;&#9472; gg.pdf
&#9474;   &#9474;   &#9492;&#9472;&#9472; ii.pdf
&#9474;   &#9500;&#9472;&#9472; gg.pdf
&#9474;   &#9500;&#9472;&#9472; hh.pdf
&#9474;   &#9500;&#9472;&#9472; ii.pdf
&#9474;   &#9492;&#9472;&#9472; pd.pdf
&#9500;&#9472;&#9472; mvmv.sh
&#9500;&#9472;&#9472; Pig.pdf
&#9492;&#9472;&#9472; poke.pdf

11 directories, 58 files


```
lots of places for replacements here.

---

### Post by Vaphell on 2011-11-23
try this
```
#!/bin/bash

shopt -s globstar

for f in $PWD/*/**
do
  if [ -f "$f" ]
  then 
    echo $f is a file
    d="${f%/*}"; d="${d##*/}"
    echo mv -v "$f" "${f%/*}/${d}_${f##*/}"
  else  
    echo $f is a dir
  fi
done
```

with fixed length path i could make certain assumptions that break with paths of varying length. i introduced additional variable to sort this out.

/some/long/path[COLOR="Blue"]/file.txt[/COLOR]
[COLOR="Blue"]${f%/*}[/COLOR] drops the shortest string matching /* pattern = file name part
[COLOR="Green"]/some/long/[/COLOR]path
[COLOR="Green"]d=${d##*/}[/COLOR] takes the result and removes longest string matching */ pattern
voila! d stores the name of the last dir in the path.

---

### Post by saphil on 2011-11-23
> **Vaphell said:**
> try this
```
#!/bin/bash

shopt -s globstar

for f in $PWD/*/**
do
  if [ -f "$f" ]
  then 
    echo $f is a file
    d="${f%/*}"; d="${d##*/}"
    echo mv -v "$f" "${f%/*}/${d}_${f##*/}"
  else  
    echo $f is a dir
  fi
done
```with fixed length path i could make certain assumptions that break with paths of varying length. i introduced additional variable to sort this out.

/some/long/path[COLOR=Blue]/file.txt[/COLOR]
[COLOR=Blue]${f%/*}[/COLOR] drops the shortest string matching /* pattern = file name part
[COLOR=Green]/some/long/[/COLOR]path
[COLOR=Green]d=${d##*/}[/COLOR] takes the result and removes longest string matching */ pattern
voila! d stores the name of the last dir in the path.


I may be beginning to understand this stuff.  Thanks for the clarification and the update.

---

