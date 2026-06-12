---
title: "new to command line. change file modified date"
date: 2016-09-10
forum: New to Ubuntu
---

### Post by eric68 on 2016-09-10
I need to change the "modified-date" for all files in "new-directory."

The identical file exists in "old-directory." I just need to find it and assign its date to file from "new-directory."

I don't know how to read a file's date or how to assign it a new value.

I dont know how to execute a statement conditionally, depending on whether the two files are duplicates.

"diff" returns a code indicating identical files, but how is it used for conditional execution?

Otherwise, I just need a nested loop cycling through both directories.

Thank you much.

---

### Post by uRock on 2016-09-10
The touch command will change the time stamp on a file.
Open a terminal and run the following to each file,```
touch filename
```You will have to use the **cd** command to get to the directory containing the files first.

---

### Post by ajgreeny on 2016-09-10
You can change to a specific date, either in the past, or even in the future if you need to, with command ```
touch -d "2016-09-10 21:01:00" /path/to/file
``` which would change the date to today's at 9:01pm (local time)
The command touch filename will change the date and time to that at which you run the command, ie right now, if you see what I mean.

---

### Post by sisco311 on 2016-09-10
> **eric68 said:**
> I need to change the "modified-date" for all files in "new-directory."

You can use the `touch' command with its -d flag. See: `man touch' ;)
```
touch -d 'now' filename
```

> **eric68 said:**
> 
The identical file exists in "old-directory." I just need to find it and assign its date to file from "new-directory."

I don't know how to read a file's date or how to assign it a new value.


To get the file's mtime you can use `stat'. stat also has a man page. ;)

```
stat --format='%y' file
```

And here is an example of combining touch and stat:
```
touch -d "$(stat --format='%y' old)" new
```


> **eric68 said:**
> 
I dont know how to execute a statement conditionally, depending on whether the two files are duplicates.

"diff" returns a code indicating identical files, but how is it used for conditional execution?


Like this:
```
if diff new-file old-file > /dev/null 2>&1
 then
    printf  '%s\n' "same"
else
    printf '%s\n' "different"
fi

```
   
> **eric68 said:**
> 
Otherwise, I just need a nested loop cycling through both directories.


Something like (pseudocode in bash-ish language)
```

for new-file in /path/to/new/files/*
do
    for old-file in /path/to/old/files/*
        do
            if diff "$new-file" "$old-file" > /dev/null 2>&1
            then
                touch ...
            fi
         done
done

```

> **eric68 said:**
> 
Thank you much.

Hope this helps.

---

### Post by steeldriver on 2016-09-10
Modern versions of the `touch` command have a `-r` option that allow you to use one file as a reference to set the timestamp of another - that saves all the hassle of having to read / parse / set human readable date strings

For example, given
```

$ tree -D .
.
&#9500;&#9472;&#9472; [Sep  5 15:48]  sub1
&#9474;   &#9500;&#9472;&#9472; [Sep  5 15:44]  file1.csv
&#9474;   &#9500;&#9472;&#9472; [Sep  5 15:44]  file2.csv
&#9474;   &#9500;&#9472;&#9472; [Sep  5 15:44]  file4.csv
&#9474;   &#9492;&#9472;&#9472; [Sep  5 15:48]  file6.csv
&#9492;&#9472;&#9472; [Sep  5 15:44]  sub2
    &#9500;&#9472;&#9472; [Sep  5 15:44]  file1.csv
    &#9500;&#9472;&#9472; [Sep 10 16:20]  file2.csv
    &#9500;&#9472;&#9472; [Sep 10 16:20]  file3.csv
    &#9500;&#9472;&#9472; [Sep  5 15:44]  file4.csv
    &#9492;&#9472;&#9472; [Sep 10 16:20]  file5.csv

2 directories, 9 files

```
then
```

$ for f in sub2/*; do g="sub1/${f##*/}"; [ -f "$g" ] && touch -m -r "$f" "$g"; done

```

results in

```

$ tree -D .
.
&#9500;&#9472;&#9472; [Sep  5 15:48]  sub1
&#9474;   &#9500;&#9472;&#9472; [Sep  5 15:44]  file1.csv
&#9474;   &#9500;&#9472;&#9472; [Sep 10 16:20]  file2.csv
&#9474;   &#9500;&#9472;&#9472; [Sep  5 15:44]  file4.csv
&#9474;   &#9492;&#9472;&#9472; [Sep  5 15:48]  file6.csv
&#9492;&#9472;&#9472; [Sep  5 15:44]  sub2
    &#9500;&#9472;&#9472; [Sep  5 15:44]  file1.csv
    &#9500;&#9472;&#9472; [Sep 10 16:20]  file2.csv
    &#9500;&#9472;&#9472; [Sep 10 16:20]  file3.csv
    &#9500;&#9472;&#9472; [Sep  5 15:44]  file4.csv
    &#9492;&#9472;&#9472; [Sep 10 16:20]  file5.csv

2 directories, 9 files

```

---

### Post by sisco311 on 2016-09-11
Thanks, steeldriver!

I didn't know about this option. Maybe I should take my own advice and read the man pages.  :)

---

### Post by ajgreeny on 2016-09-11
> **sisco311 said:**
> Thanks, steeldriver!

I didn't know about this option. Maybe I should take my own advice and read the man pages.  :)
Same here.
Thanks for the info.

---

