---
title: "Strip first line from the results of the ls command"
date: 2011-07-25
forum: Programming Talk
---

### Post by Shpongle on 2011-07-25
Hi all , I have a directory which will be updated at each startup and I will need to access the most recent file to compare against the new one. I can access the most recent file using 

ls -t

The problem is there are several files in this directory, and ls returns the list of the whole lot. I cant use regex's as all the files will use the date of creation as their names.


I need to be able to take the first result from the ls command and store it in a variable. 


Any suggestions on what would be the best way to approach this

cut ? or sed or awk maybe ?


Regards 

Shpongle

---

### Post by AlphaLexman on 2011-07-25
Try this...
```
VARIABLE=$(ls -[COLOR="Red"]1[/COLOR]t | head -n 1)
echo $VARIABLE
```
I added the '[COLOR="red"]1[/COLOR]'
(a number one, NOT a lowercase 'L')

---

### Post by Shpongle on 2011-07-25
Cheers, that did the trick. I'll be posting the result when I'm done . I'm sure some people will find it useful.

---

### Post by sisco311 on 2011-07-25
Please check out:
[http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)
and
[http://mywiki.wooledge.org/BashFAQ/099](http://mywiki.wooledge.org/BashFAQ/099)

ls lists the files in human readable format, so you shouldn't use it for anything else, but listing files... ;)

If the modification time is in the filenames, then the glob order is also the mtime order. You can read the filenames in an array. The first element will be the oldest and the last the newest:
```
shopt -s nullglob
files=(*)
echo "oldest file: ${files[0]}"
echo "most recent: ${files[${#files[@]}-1]}"

```

---

