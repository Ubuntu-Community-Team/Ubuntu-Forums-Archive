---
title: "Bash randomly copy file from find search"
date: 2010-03-03
forum: Programming Talk
---

### Post by synking on 2010-03-03
Hey guys i need help i know that this script will copy all files with the .mp3 extenstion.

```
find ./ -name \*.mp3 -exec cp {} random/ \;
```

what i want to do is have it copy random files that it finds to the random folder.  I tried using the $RANDOM command but i would only grab number.mp3 files.

How do i make it copy random files to a certain amount to that folder i am not very versed in Bash but any help will be good pointers of sites that may have the answer. 

Thanks for the help

---

### Post by kaibob on 2010-03-03
You could pipe the results of the find command through the sort utility with the random option. You would have to rewrite your command, but that is pretty simple. Limiting the number of files copied could be a bit more complicated depending on how you set the limit.

---

### Post by synking on 2010-03-03
Thanks for the reply and i did not think of doing it that way. but the sort command will not actually sort a select amount of files (that i know of) and if i can how would i cp what was sorted to a new directory sort does not have an -exec command to excecute a program after it stops running.

---

### Post by kaibob on 2010-03-04
There are a number of ways to do what you want, and the approach taken depends in part on how you want to limit the files copied. For example, the following copies 10  files then stops. 

```
#!/bin/bash

counter=0
stop=10

find /source/directory -name "*.mp3" | sort -R | while read file ; do
   [ "$counter" -eq "$stop" ] && exit 0
   cp "$file" "/target/directory"
   counter=$((counter + 1))
done
```

I suspect that you want to set the limit by the file size of all files copied. That's not difficult but does require a bit more work.

---

### Post by synking on 2010-03-04
Yes that is correct but with this as a heads up i may be able to get what i want.  Thank you for the info so far i'll tweak this and see if i can't get it to stop after a certain size. Thank you.

---

### Post by kaibob on 2010-03-05
I like to play around with simple shell scripts and decided to change my above script to work with file size rather than number of files. In this script, maximum total file size is input as a command-line parameter in KB. Large files that would cause the script to exceed the maximum total file size are skipped and the script continues to process the file list to see if smaller files are available. This is done to maximize the files copied without exceeding the maximum total file size. 

```
#!/bin/bash

[ "$1" = "" ] && echo "You forgot the maximum total file size." && exit 1

used=0
max=$((${1} * 1024))

source="/source/directory"
target="/target/directory"

while read file ; do
   size=$(stat -c %s "$file")
   free=$((max - used))
   [ "$size" -gt "$free" ] && continue
   cp "$file" "$target"
   used=$((used + size))
done < <(find "$source" -name "*.mp3" 2> /dev/null | sort -R)

echo "$((used / 1024)) KB of files copied."
```

---

### Post by synking on 2010-03-05
sweet i was trying to do it an if size statemnt and using du to check didn't think of using stat. thanks for all the help.

---

