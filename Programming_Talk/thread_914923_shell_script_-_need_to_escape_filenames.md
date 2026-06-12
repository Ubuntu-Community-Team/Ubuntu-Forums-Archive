---
title: "shell script - need to escape filenames"
date: 2008-09-09
forum: Programming Talk
---

### Post by talz13 on 2008-09-09
I'm trying to write a shell script that will handle filename inputs (or a directory via output of 'ls'):

```
#! /bin/bash

if [ -e $1 ]
then
        if [ -f $1 ]
        then
                # it's a file, start processing it...
                echo "Processing a single file...";
                command="~/Downloads/encode-handheld-1.9.pl -t psp -threads 4 -f $1";
                echo $command;
        elif [ -d $1 ]
        then
                # it's a directory, list the contents and start processing them in a batch...
                echo "Processing an entire directory...";
                for i in $(ls $1 | grep -v db\$);
                do
                        `~/Downloads/encode-handheld-1.9.pl -t psp -threads 4 -f $1/$i`;
                done
        fi
fi
```

But when the filename contains spaces, brackets, or other special characters, it either drops the escape \ or doesn't receive an escape to begin with (i.e. from 'ls' output).  Is there a way to programatically escape these characters so that it can find the files?

Example: ```
jeff@server:~$ ls /home/shares/video/anime/bleach/
[DB]_Bleach_183_[07493DEF].avi  [DB]_Bleach_185_[B1B2B639].avi
[DB]_Bleach_184_[CC171141].avi  [DB]_Bleach_186_[37E46364].avi
jeff@server:~$ ./pspEncoder.sh /home/shares/video/anime/bleach/\[DB\]_Bleach_183_\[07493DEF\].avi
Processing a single file...
~/Downloads/encode-handheld-1.9.pl -t psp -threads 4 -f /home/shares/video/anime/bleach/[DB]_Bleach_183_[07493DEF].avi
jeff@server:~$
```

It completes "successfully" even though it didn't actually run (since it couldn't find a file "[DB]_Bleach_183_[07493DEF].avi", it needs to find "\[DB\]_Bleach_183_\[07493DEF\].avi" instead...)

---

### Post by ghostdog74 on 2008-09-09
try using 
```

for i in $1/*
do
  ...
done


```
instead of 
```

for i in $(ls ... )
do
...
done

```

---

### Post by mssever on 2008-09-09
> **talz13 said:**
> I'm trying to write a shell script that will handle filename inputs (or a directory via output of 'ls'): Try this (my changes are in bold):

```
#! /bin/bash

if [ -e $1 ]
then
        if [ -f $1 ]**; then**
                # it's a file, start processing it...
                echo "Processing a single file..."
                **"$HOME"**/Downloads/encode-handheld-1.9.pl -t psp -threads 4 -f **"$1"**
        elif [ -d $1 ]**; then**
                # it's a directory, list the contents and start processing them in a batch...
                echo "Processing an entire directory..."
                for i in **"$1"/*; do**
                    **"$HOME"**/Downloads/encode-handheld-1.9.pl -t psp -threads 4 -f **"$1/$i"**
                done
        fi
fi
```A few of my changes are stylistic changes to reflect the way most people format their bash scripts. Also, you don't need to end lines with a semicolon unless you're putting multiple lines on a single line.

---

