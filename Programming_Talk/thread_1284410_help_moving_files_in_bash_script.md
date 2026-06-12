---
title: "help moving files in bash script"
date: 2009-10-06
forum: Programming Talk
---

### Post by syxbit on 2009-10-06
I have Client folders with their name
John
Steve
James
etc..
Some of the files have PDFs directly in them, but others have PDFs in a subdirectory.
could someone help me on writing a script that would be run at the root (which contains client named folders) and put any file that is underneath the client folder (however deep) and puts it right in the client folder.
example.
John contains 1.pdf and a folder FILES with 2.pdf in it
I want just the folder John with all the PDFs directly in it. (1.pdf and 2.pdf)
this is easy for one client folder. I would run
cd John
mv */* .
and possibly 
mv */*/* . (if there are several layers)

but I don't know how to do this automatically for hundreds of different client folders at once.

could someone help me out?
thanks

---

### Post by syxbit on 2009-10-06
I've got this so far

```


for file in *

do
        if [ -d "$file" ]; then
                cd "$file";
                mv */* .;
                cd ..;
                continue
        fi
done


exit 0

```

This pushes everything up a directory, I get an error
cannot stat */*
but it seems to work.
I just run the code twice, and each run does one sub directory.

any ideas to improve this?

---

### Post by scragar on 2009-10-06
```
#!/bin/bash

for file in *
do
        if [ -d "$file" ]; then
                cd "$file";
                find ./* -iname "*.pdf" -exec mv {} ./ \;
                cd ..;
        fi
done
exit 0
```Maybe?

---

### Post by NoaHall on 2009-10-06
You're moving everything from root/home?

---

### Post by syxbit on 2009-10-06
by root I meant the location of the script and all the top level client name folders.

the above script gives syntax errors, so I'll just stick with mine. It's not that elegant, but it works :)

---

### Post by DaithiF on 2009-10-07
you could also do it something like this:
```
find <startdir> -type f | while read filename
do
  destdir=${filename%%/*}
  mv "$filename" "$destdir"
done


```

---

