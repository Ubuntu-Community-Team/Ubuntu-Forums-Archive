---
title: "read -d...unknown option?"
date: 2008-08-27
forum: Programming Talk
---

### Post by kevin1162 on 2008-08-27
Hi,

I made a shell script that basically syncs one directory to another (one way only).

I tested it on my Ubuntu server and it worked fine, but it was intended to run on a server running Caldera Open Linux.

This is basically what my script is:
```
#!/bin/bash

dir1="/directory_1/"
dir2="/directory_2/"

cd "$dir1"
find . -print0 | while read -d $'\0' file; do
  [ -e "$dir2/$file" ] || echo "$file" | xargs rm -rfv
done

cp -rupv /directory_2/* /directory_1/
```

But i get this output when it executes
```
read: unknown option: -d 
read: usage: read [-r] [name ...] 
```

Which is really confusing me since read is a bash built-in and -d is an allowed option

My knowledge of Linux/Unix is limited so i don't know what to look at. I can't find any support forums related to Caldera OpenLinux so that's why i'm posting here.

If anyone has some knowledge about this i would appreciate the help.

Thanks

---

### Post by mssever on 2008-08-27
Two things:


[LIST=1]
[*]Make sure that your script is actually getting run by bash
[*]Check Caldera's bash version. Maybe it's older than Ubuntu's.
[/LIST]

---

### Post by ghostdog74 on 2008-08-27
@OP, you can just use -print instead of -print0.

---

