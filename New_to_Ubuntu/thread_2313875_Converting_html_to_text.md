---
title: "Converting html to text"
date: 2016-02-16
forum: New to Ubuntu
---

### Post by bwanaaa on 2016-02-16
I followed this thread:
[http://ubuntuforums.org/showthread.php?t=2042120&page=2](http://ubuntuforums.org/showthread.php?t=2042120&page=2)
and succesfully got a bash script to convert the html files residing in the directory of the script.

What is the best way to iterate down a folder hierarchy containing numerous html files in each folder.?

Also would like to cut out the first 18 lines and last 18 line of each appended text file.  Can bash manipulate text files?

---

### Post by TheFu on 2016-02-16
"best way" is highly subjective.

I would use **wget**.
Others would install a firefox addon/extension.
Others would use **curl**.

Well, bash is a glue language, not really something that opens files and manipulates them, but there are many, many, many, text processing tools on your Linux machine (or any Unix-based OS) that do manipulate text files anyway you like and these can all be called from a bash script (which is commonly done).  A few tools to lookup.
* head - tell it how many lines you want to see from the beginning of a file.
* tail  - tell it how many lines you want to see from the end of a file.
* awk - general purpose file filter.
* perl - general purpose file filter AND much more
* sed - "stream editor" - that's a little vague, but trust me - it is amazing.
* cut - cuts out specific fields in a line - you define the field delimiter. ;)
* wc - word counter (also counts lines in a file) - if you are going to manipulate files, it could be important to know how many lines that file has, right?

Converting an html file to text should just be 1 call to html2text, right? 

BTW, we frown upon telling people to read the manpages, but in this case, with what you are asking, using the local manpages on your box would be the best resource.  BTW, there are probably 1,000+ examples of bash scripts on your system today - many will use sed, cut, head, tail ... all the normal basic text processing tools on the system already.

Also, most Unix 101 books will teach these tools in the first few chapters as a primer to shell scripting.  [http://tldp.org/LDP/abs/html/textproc.html](http://tldp.org/LDP/abs/html/textproc.html) is The Linux Documentation Project's page about text processing.  Could be a good place to start and has example scripts for all those cmds I listed above.  These tools haven't changed much since ... Unix was created in the 1970s.  Actually, these tools were some of the most important tools provided on AT&T-UNIX systems back then.

---

### Post by SeijiSensei on 2016-02-16
> **bwanaaa said:**
> What is the best way to iterate down a folder hierarchy containing numerous html files in each folder.?
```

#!/bin/bash
DIRS=$(ls -1)

for d in $DIRS
do
    cd $d
    mkdir txt
    for f in *.html
    do
        NAME=$(basename -s .html $f)
        html2text -o txt/$NAME.txt $f
    done
    cd ..
done

```
Put this in a file, mark it executable with "chmod a+x /path/to/the/script", then run this in the top directory where the HTML files are located.  

I haven't used html2text myself.  I based my syntax for the html2text command using its manual page ("man html2text").  Also if the directories have spaces in their names, this won't work correctly.  I avoid using embedded spaces in directory and filenames to avoid these sorts of problems.

The "head" and "tail" commands that TheFu mentions might help with stripping the lines off the top and bottom.  For instance, "tail -n18 filename" will skip the first 18 lines of filename.  Stripping the last 18 lines is harder and is left as an exercise for the reader :D

---

