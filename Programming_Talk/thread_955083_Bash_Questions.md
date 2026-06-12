---
title: "Bash Questions"
date: 2008-10-21
forum: Programming Talk
---

### Post by essention on 2008-10-21
Basically I have two directories one full of files and one which will be a backup for those files.

I currently have a little script that simple copies all those files into a sub-directory with the current date.

What I would like to do is have the files only copy if they dont exist within the root backup directory or any of the date named sub-directories.
So there would only be one copy of that file with in any of the directories. 

And basically i know how to do a simple find command but have no clue in how I would only copy files to the new directory if that file didnt exist within any other subdirectory.

Any help with this would be greatly appreciated.

---

### Post by ghostdog74 on 2008-10-21
to check for file exist
```

if [ -e "$filename" ];then
 ...
fi

```
see my sig for learning bash.

---

