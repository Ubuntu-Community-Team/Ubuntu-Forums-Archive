---
title: "[BASH] Recursion"
date: 2009-02-12
forum: Programming Talk
---

### Post by wick3dsunny on 2009-02-12
Hi guys, 

I am trying to write this script in bash which prints the stats of every file in the directory using recursion and stat command but the recursion seems to not work... Any help would be appreciated 

```
#! /usr/bin/env bash

function display(){

if test $# -eq 0; then
directory=`pwd`

elif test $# -eq 1; then
        directory=$1

        fi

for files in `ls -A $1`
do

echo $directory
cd $directory
stat -c %n,%F,%i,%s $files

if test -d $files; then
echo "{"
display $directory/$files
echo "}"

fi
done

}

display $1








```

---

### Post by ghostdog74 on 2009-02-12
recursion? 
```

# stat -c %n,%F,%i,%s  *

```
if you need to traverse directories, use the find command with options like -exec or -execdir. you do not need to reinvent the wheel.

---

### Post by Neural oD on 2009-02-12
maybe try this: for files in `ls -AR $1`

---

### Post by wick3dsunny on 2009-02-12
I would really love to use the find and ls -R command but I am not allowed to use it unfortunately :(! 

I am trying to traverse through directories but getting stuck with recursion. any help with what the problem is ?

---

### Post by lloyd_b on 2009-02-12
Well, one MAJOR problem with your code is that you're never "cd"ing back to the parent directory after recursing into a child directory...

You need to stash the parent directory somewhere, before resetting the value of "directory".  Remember, all variables are GLOBAL in a shell script, so it does NOT revert to the previous value of "directory" when the function returns (with the exception of the positional parameters ($1, $2, $#, etc).

Here's some example code.  What I've done is declared a variable ("level") to keep track of what recursion level it's at, and then used an array variable ("directory[]") to store the previous directory each time it recurses.

A few notes:
1.  I prefer the "if [ ... ]" form of the "test", rather than the longer form you used.  
2.  I prefer the terser form of the if/for/etc statements, since they use less vertical space.
3.  I *strongly* recommend indenting your code for each if/for/etc statement - it makes it a LOT easier to read and understand.

```
#! /usr/bin/env bash

function display(){

level=$((level + 1))

if [ $# -eq 0 ]; then
    directory[$level]=`pwd`
else
    directory[$level]=$1
fi

echo "entering directory ${directory[$level]}"
cd "${directory[$level]}"

for files in `ls -A $1`; do
    stat -c %n,%F,%i,%s $files

    if [ -d $files ]; then
        echo "{"
        display ${directory[$level]}/$files
        echo "}"
    fi
done

level=$((level - 1))

if [ $level -gt 0 ]; then
    cd ${directory[$level]}
    echo "returning to ${directory[level]}" 
fi

}

level=0
display $1

```

Lloyd B.

---

