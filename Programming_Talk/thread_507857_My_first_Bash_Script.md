---
title: "My first Bash Script"
date: 2007-07-23
forum: Programming Talk
---

### Post by bobbocanfly on 2007-07-23
Today i decided to give bash scripting a go. I already know C# (.NET unfortunately), PHP and a *tiny* bit of C++ so i figured it shouldnt be too hard.

I noticed that there isnt an easy way to create a file, give it some basic text and apply permissions in one simple command, so i decided to make one.

Can anyone find anything wrong with it? or any suggestions?

Usage:

```
nf fileName "file contents" file permissions

nf hello.txt "Hello World!" a+w
```

The code:

```

#!/bin/bash
#nf : New File creation script 
#Copyright (C) Bobbocanfly 2007

if [ -n "$1" ]
then
	if [ -e "$1" ]
	then
		rm $1
	fi
touch $1
else
	echo "Too few arguments : no file name specified"
exit
fi
if [ -n " $2" ]
then
	echo $2 >> $1
fi
if [ -n "$3" ]
then
	chmod $3 $1
fi
```

---

### Post by jyba on 2007-07-23
```
#! /bin/bash
ERROR="Too few arguments : no file name specified"
[[ $# -eq 0 ]] && echo $ERROR && exit                 # no args? ... print error and exit
[[ -e $1 ]] && rm $1 && touch $1                      # remove and recreate file $1
[[ -n $2 ]] && echo $2 >> $1                          # append arg $2 to file $1
[[ -n $3 ]] && chmod $3 $1                            # change mode of $1
```:)

---

### Post by Nekiruhs on 2007-07-23
> **jyba said:**
> ```
#! /bin/bash
ERROR="Too few arguments : no file name specified"
[[ $# -eq 0 ]] && echo $ERROR && exit                 # no args? ... print error and exit
[[ -e $1 ]] && rm $1 && touch $1                      # remove and recreate file $1
[[ -n $2 ]] && echo $2 >> $1                          # append arg $2 to file $1
[[ -n $3 ]] && chmod $3 $1                            # change mode of $1
```:)
Dang... You're good. I had no Idea you could do that w/o if statements.  Where did you learn this side of BASH scripting.

---

### Post by Mr. C. on 2007-07-23
These are some things you pick up over time.

Here's an online course I used to teach:

[http://cis68b1.mikecappella.com](http://cis68b1.mikecappella.com)

Read the coursework notes, and try some of the homework.  Don't peek at the answers until you've worked on the problems!

MrC

---

### Post by #Reistlehr- on 2007-07-23
no means to hijack but that link helped me tons going back with my bash programming =D

---

