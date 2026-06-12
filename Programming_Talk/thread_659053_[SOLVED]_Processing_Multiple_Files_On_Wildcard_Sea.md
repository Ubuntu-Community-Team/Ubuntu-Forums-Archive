---
title: "[SOLVED] Processing Multiple Files On Wildcard Search"
date: 2008-01-05
forum: Programming Talk
---

### Post by cmnorton on 2008-01-05
I have a bash shell script that looks for a file based on a wildcard:


CITATION_PRESENT=`ls /home/${user_name}/citation????*.txt 2>/dev/null`

if [ -z ${CITATION_PRESENT} ]; then
	CITATION_PRESENT=`ls /home/${user_name}/citation3.txt 2>/dev/null`

If more than one file satisfies the match, then the script fails. My question is what is a good way to get a list of files and process them?

In this case, I'm going to rename each file as I get it; process it into a database application; and then get the next file.

Thanks.
cmn

---

### Post by ghostdog74 on 2008-01-06
not sure what you really want, however to go over list of files and process them
```

ls /home/${user_name}/citation*.txt | while read file
do
  echo "do something with file"
done

```

---

### Post by stroyan on 2008-01-06
Parsing "ls" output is error prone because file names may contain whitespace.
It is also unnecessary to involve "ls".  The shell can handle file names by itself.
The default behavior when a pattern like "citation????*.txt" doesn't match any
files is to leave the original pattern.  The "shopt -s nullglob" setting changes
that behavior so patterns that don't match any file expand to null.  That can
be restored to the default setting as done in the example below if there may
be other code in a script that expects the default behavior.
[PHP]restore=$(shopt -p nullglob)  #save previous nullglob setting
shopt -s nullglob
unset f  #This is so you can test for no match and try citation3.txt below
for f in /home/${user_name}/citation????*.txt
  do
    echo handle "$f"
  done
eval $restore
unset restore
if [ -z ${f} ]; then
  echo handle "/home/${user_name}/citation3.txt"
fi
[/PHP]

---

### Post by ghostdog74 on 2008-01-06
> **stroyan said:**
> Parsing "ls" output is error prone because file names may contain whitespace.

True, but you can always use quotes like that in your for loop example
> 
It is also unnecessary to involve "ls".  The shell can handle file names by itself.

It depends on the requirement. If OP want to process more than filenames, 
such as getting the file sizes, etc into the database, he can read in the necessary fields that he wants
```

ls -l | while read a b c blah
do
 ........
done

```
A for loop can't in this case.

---

### Post by stroyan on 2008-01-06
Once you start adding a -l option parsing "ls" output gets quite a bit harder.
The number of fields actually vary for different file types.
Perhaps the test builtin and stat command would be more appropriate for finding file sizes, etc.```
for file in *
do
if [[ -f "$file" ]] 
then
  size=$(stat -c%s "$file")
  echo $file $size
fi
done
```

---

### Post by ghostdog74 on 2008-01-06
> **stroyan said:**
> Once you start adding a -l option parsing "ls" output gets quite a bit harder.
The number of fields actually vary for different file types.
Perhaps the test builtin and stat command would be more appropriate for finding file sizes, etc.```
for file in *
do
if [[ -f "$file" ]] 
then
  size=$(stat -c%s "$file")
  echo $file $size
fi
done
```
what i gave is just example. There are few situations where using OP's method of ls is more "convenient", like including hidden files in the listing  or doing recursive subdirectories listing, etc..

---

### Post by geirha on 2008-01-06
A little digression here. Is /home/${user_name}/ meant to point to the homedir of the user running the script? if so, it's much better to use $HOME or ~ 

Homedirs are usually located in /home/ but they don't have to be, and the root user has its homedir as /root/, so it wouldn't work for root.

---

### Post by cmnorton on 2008-01-07
Thank you for the replies. There are a lot of good ideas and comments.

---

