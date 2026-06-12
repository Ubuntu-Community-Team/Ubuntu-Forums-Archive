---
title: "Bash script for subdirectories under unknown directories"
date: 2011-07-14
forum: Programming Talk
---

### Post by madsaientist on 2011-07-14
I am not the most well versed at scripting but I am trying to write one now that needs to create a directory once a month under several other directories.  The subdirectory creation I have no problem with the problem is is that the directories I need to create the subdirectories under are not all known to me and can be created by other users without my knowledge.  Is there a way to specify, using a wildcard or something else, to create a new directory under an unknown group of directories one level deep under our top level directory?  If so could someone give me some tips.

Thanks in advance,

MS

---

### Post by Vaphell on 2011-07-14
```

top='/home/username'
new='new dir'
find "$top" -mindepth 1 -maxdepth 1 -type d | while read dir
do
  echo Dir: "$dir"
  echo New dir: "$dir"/"$new"
done

```

---

### Post by papibe on 2011-07-14
You can use the 'for' statement to run through all entries in a folder. For example, this script creates a directory called 'dir' under any directory where is run:
```
#!/bin/bash
for file in *
do
    if [ -d "$file" ]
    then
        echo "directory found: $file"
        mkdir "$file"/dir
    fi
done

```

---

