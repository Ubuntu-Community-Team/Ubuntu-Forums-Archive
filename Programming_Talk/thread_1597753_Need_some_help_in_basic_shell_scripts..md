---
title: "Need some help in basic shell scripts."
date: 2010-10-15
forum: Programming Talk
---

### Post by Rushyang on 2010-10-15
Bonjour guys,

I was writing these scripts and just wanted to have tip from where to start. Cause my mind is about to explode from too many blur ideas.

1) I want to use "cd -" in my script, but I don't want to display it's changed path to previous directory on the run time.

eg.
when we use cd - (or cd "$OLDPWD") .. it shows the full path to which it changed.. I don't want to show that while using it.

2) Is there ANY way to print ONLY files from current working directory (Not subdirectories), without using 'find $PATH_HERE -maxdepth 1 -type f -print' ??

---

### Post by AlphaLexman on 2010-10-15
1) How about:
```
OLDDIR=$OLDPWD
cd $OLDDIR
```

---

### Post by shawnhcorey on 2010-10-15
Redirect the stdout to the null device:
```
cd - >/dev/null
```

---

### Post by saulgoode on 2010-10-15
> **Rushyang said:**
> 2) Is there ANY way to print ONLY files from current working directory (Not subdirectories), without using 'find $PATH_HERE -maxdepth 1 -type f -print' ??


```
ls * -dp |grep -v '/$'
```

Note that you must specify a wildcard pattern -- an asterisk for all files -- else there will be no matching files. This is because the -d option specifies that only directory names should be listed, and without any filename pattern only the current working directory's "name" is shown, not its contents (actually, the name of the CWD is not shown, but its alias "./" ; and this will be stripped by the 'grep').

Having said all that, I'd recommend using 'find'.

---

### Post by Rushyang on 2010-10-16
> **saulgoode said:**
> ```
ls * -dp |grep -v '/$'
```Note that you must specify a wildcard pattern -- an asterisk for all files -- else there will be no matching files. This is because the -d option specifies that only directory names should be listed, and without any filename pattern only the current working directory's "name" is shown, not its contents (actually, the name of the CWD is not shown, but its alias "./" ; and this will be stripped by the 'grep').

Having said all that, I'd recommend using 'find'.

That was supercool.. Thanks for the tip. 

Can you tell me how to use 'for' loop into all files of directory, without going into that directory? 

ie. I use ...
cd DIRNAME
for i in *
do
done

I want to use, that 'for loop' only in files, which are in DIRNAME.. I also don't want to cd into that directory before using 'for loop'..

---

### Post by spjackson on 2010-10-16
> **Rushyang said:**
> Can you tell me how to use 'for' loop into all files of directory, without going into that directory? 

ie. I use ...
cd DIRNAME
for i in *
do
done

I want to use, that 'for loop' only in files, which are in DIRNAME.. I also don't want to cd into that directory before using 'for loop'..
```

for i in DIRNAME/*
do
    if [ -f "$i" ] ; then
        echo "$i is a file, not a directory"
    fi
done

```

---

### Post by Rushyang on 2010-10-16
> **spjackson said:**
> ```

for i in DIRNAME/*
do
    if [ -f "$i" ] ; then
        echo "$i is a file, not a directory"
    fi
done

```

Hi spjackson,
Thanks for reply. 
That gives an error for files which have spaces.. I know about converting new line characters into null characters through option of `find . -type f -print0 | xargs -0`

I wrote..
> 
echo "Enter absolute path"
read path

if test -d $path; then
    args=`find $path -maxdepth 1 -type f -print0 | xargs -0`
    for i in $args
    do
    
            echo "$i"
    done
else
    echo "path does not exist"
fi
when I ran it..
> rushyang@Maverick_Meerkat: 1610 $ sh forexp.sh 
Enter absolute path: /home/rushyang/Experiments

/home/rushyang/Experiments/1Renamed
/home/rushyang/Experiments/cdel.sh
/home/rushyang/Experiments/case1.sh
/home/rushyang/Experiments/errors1.sh
/home/rushyang/Experiments/O'Reilly
-
SED
and
AWK.examples.rar
/home/rushyang/Experiments/pathfile
/home/rushyang/Experiments/history14102010
/home/rushyang/Experiments/sudotest.sh
/home/rushyang/Experiments/oldhostname
/home/rushyang/Experiments/loginscreenchange.sh
/home/rushyang/Experiments/script_session.sh
/home/rushyang/Experiments/Rename_Final.sh
/home/rushyang/Experiments/chessboard.sh
/home/rushyang/Experiments/.bashrc
/home/rushyang/Experiments/error.sh
/home/rushyang/Experiments/temp2.lst
/home/rushyang/Experiments/ext_change.sh
/home/rushyang/Experiments/sources.listObserve 'Oreilly SED And AWK.examples.rar' file display.

My motive: All I want is -  to use 'for loop' without going into a directory and have all files names (including names which have spaces) Absolute path with usage of both 'find' and 'ls'  Spaces are BIG Problem in filenames.

Thank you for your kind suggestions so far! :)

---

### Post by spjackson on 2010-10-16
> **Rushyang said:**
> 
That gives an error for files which have spaces.. 
Did you try my code exactly as given or did you change it to something else? You will not get an error with filenames that contain spaces provided that you surround the variable with double-quotes, e.g. "$i" as I showed you. If you remove the quoting then you will get precisely the problems you describe.

If you generate the list of items for you for loop in a completely different way, e.g. using find in back-ticks as per the code you posted, then that is a different situation. I don't understand why you are using find when you have specifically said that you don't want to do so.

Do you want us to correct your code using find or do you want working code that doesn't use find?

---

### Post by Rushyang on 2010-10-16
> **spjackson said:**
> Did you try my code exactly as given or did you change it to something else? 

Hello again spjackson,

Yes, I did do changes and as you said, I didn't put "" around $i. I amaze why "" are important now. Thanks man. 

I want to make same code but using 'find'.. Do you have any idea how we'll do the same thing with 'find' ? I'm confused because I don't have any option without using 'xargs'..

> echo "Enter Absolute Path"
read path

if test -d $path; then
args=`find $path -maxdepth 1 -type f -print0 | xargs -0`
    for i in $args
    do    
        echo "$i"
    done
else
    echo "Path does not exist"
fi

Above code gives me that space error.. Please advise.

---

### Post by geirha on 2010-10-16
1. Run the cd in a subshell (using parenthesis). That way, it will not affect the current shell, and you won't have to cd back. See what this outputs:
```
(cd /tmp && echo "Current directory is now $PWD"); echo "Current directory is now "$PWD"
```

2. Don't ever ever ever do «for i in `ls`» or «for i in `find`» or any other such madness. See [http://mywiki.wooledge.org/BashFAQ/020](http://mywiki.wooledge.org/BashFAQ/020) on how to iterate find output safely.

I recommend using spjackson's approach rather than find; you tried to combine the two and broke it.

Some more tips in the comments; I'm assuming you are using bash.
```

#!/usr/bin/env bash

path=""

# Infinite loop
while true; do

  # -e enables readline, which means you can use tab-completion.
  # Run ''help read'' for more options.
  # The ''|| exit'' makes the script exit if read returns false, which it
  # will if the user hits Ctrl+C amongst other.
  read -e -p "Enter absolute path: " path || exit
  
  # if path contains an existing directory, break out of this 
  # infinite loop
  [[ -d $path ]] && break
  
  echo "Invalid path, try again..."
done
# If we've reached this point, path contains an existing directory

# Do NOT omit the quotes around $dir, they ARE important
for file in "$dir"/*; do

  # file contains an existing, regular file, or skip to 
  # the next one
  [[ -f $file ]] || continue

  echo "$file"
done

```

To learn bash the right way, read [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by Rushyang on 2010-10-17
Hello Geirha,

I am super impressed from your bash scripting advanced skills. My confusion is..

1) I am not getting what I want from that script.. You wrote "$dir"  instead of "$path" in for loop by mistake. Not a big deal. Though It's super cool of you to point out "read -e -p" techniques. 
2) Why did you write path="" at the start of the script? I mean, we'll though get the same output.. right? I just want to know your concept behind this. 
3) I am not getting why 'find' and 'ls' should not be used in the for loop. because I've been trying to teach my self that. Would you little elaborate on that please?

Again, I'm so much appreciated and I will sure learn bash scripts again from your given link. Thanks for your beyond awesome suggestion. :D

---

### Post by Rushyang on 2010-10-17
& Here is another problem..
by correcting $dir to $path,
here is the output..
> 
rushyang@Maverick_Meerkat: 1710 $ bash new.sh 
Enter absolute path: /home/rushyang/Experiments/
/home/rushyang/Experiments//1Renamed
/home/rushyang/Experiments//case1.sh
/home/rushyang/Experiments//cdel.sh
/home/rushyang/Experiments//chessboard.sh
/home/rushyang/Experiments//errors1.sh
/home/rushyang/Experiments//error.sh
/home/rushyang/Experiments//ext_change.sh
/home/rushyang/Experiments//GTU16.sh
/home/rushyang/Experiments//GTU3.sh
/home/rushyang/Experiments//GTU5.sh
/home/rushyang/Experiments//history14102010
/home/rushyang/Experiments//oldhostname
/home/rushyang/Experiments//O'Reilly - SED and AWK.examples.rar
/home/rushyang/Experiments//pathfile
/home/rushyang/Experiments//script_session.sh
/home/rushyang/Experiments//sources.list
/home/rushyang/Experiments//sudotest.sh
/home/rushyang/Experiments//temp2.lst
/home/rushyang/Experiments//Testt.sh


Observe the '//' before last filename.. Can we neglect this even user has entered '/' at the end of the path?

---

### Post by geirha on 2010-10-17
1. Indeed I did use dir instead of path. Not sure how I managed that. 

The point of the script is to show how to safely iterate files using a *for*-loop. *for* iterates words, and a glob, like *"$path"/** will be expanded, by the shell, to each file inside *"$path"*, one word per file, regardless of what characters the file may contain. If you use `ls` or `find` instead, it will not know which whitespaces belong to filenames, and which don't, so it will split the output on all whitespace.

2. I first wrote the while loop as *while [[ ! -d $path ]]; do ...*, then figured it was easier to put that test inside the loop. So setting *path* to an empty string was just a left-over from that, and it's not needed.

3. This explains that in detail: [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

4. */foo/bar* and */foo//////////////////bar* is the exact same path. They look different, but the consecutive slashes will simply be ignored and treated as one path separator. You can safely pass those pathnames to another command without getting in trouble. If it matters to you, you could strip a / off from the end (if any) of the *path* variable.
```
path=${path%/}
```
See [http://mywiki.wooledge.org/BashFAQ/100](http://mywiki.wooledge.org/BashFAQ/100)

---

### Post by Rushyang on 2010-10-17
Sorry If I'm replying this late. I'm continuously reading your given links and I get it now, why we shouldn't parse output of ls. Reading other pages now. 

Thanks again.

---

