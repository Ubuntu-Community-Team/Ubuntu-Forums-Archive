---
title: "write new data to top of file"
date: 2007-10-11
forum: Programming Talk
---

### Post by springer on 2007-10-11
how do i write new data to the top of an existing file.
I've got a backup script that needs to write a success / fail line to a log file, but every simple method of cat or echo writes to the end of the file, then requiring sorting.

below are two methods an idiot like me came up with.... but there must be a better way, but i just cant find it.

any suggestions ????
-------------------------------------------------------------
#! /bin/bash

STRING1='text text strin1 '`date`
echo $STRING1
echo $STRING1 > datetmp.txt

cp master.txt date1.txt
cat datetmp.txt date1.txt >master.txt

or 


STRING1=`date`' success or fail '
echo $STRING1
echo $STRING1 >> master1
sort -nr master1 > master2

---

### Post by milosz.galazka on 2007-10-11
First method using additional file is normal and the easiest way to add things at the top of file...

keep it simple, stupid :)

For creating log files look [here]("http://ubuntuforums.org/showthread.php?t=569442")

---

### Post by ghostdog74 on 2007-10-11
```

sed -i '1i statusline' logfile

```

---

### Post by pmasiar on 2007-10-12
You mean beginning of the file? You cannot: You can only add (append) to existing file. Log adds lines to the end of the file (appends).

IMHO you have to create new file, write new part, then add original file, delete original, and rename new file to original name.

I guess sed command suggested above by ghostdog does just that. :-)

---

### Post by public_void on 2007-10-12
Appending log file messages is much easier. Use
```
tail -n
```to display the last n lines, rather than sorting the whole file.

---

### Post by pmasiar on 2007-10-12
and appending to end is much faster too - you don't need to do that allocate/copy/rename dance

---

### Post by hod139 on 2007-10-12
A google search came up with [this gem]("http://www.openaddict.com/documents/abs-guide/x15426.html"):

[COLOR=#000000]```
cat - $file <<<$title > $file.new
```[/COLOR]
where $file is the file, $title is the line to pre-pend, and $file.new is the name of the output file.

EDIT: [another option]("http://www.structure.bio.purdue.edu/support/docs/abs/assortedtips.html") is:
echo $title | cat - $file >$file.new
#"cat -" concatenates stdout to $file.

---

### Post by mjwood0 on 2007-10-12
Writing to the end of a file is so much faster.

Since you can't actually write to the beginning, at the most basic level you're writing a new file with your new data and appending (to the end) all the data in the other file.  As the file grows, this takes longer and longer.  Append to the end and use the tail command to read it.

---

