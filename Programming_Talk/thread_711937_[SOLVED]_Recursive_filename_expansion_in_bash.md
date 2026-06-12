---
title: "[SOLVED] Recursive filename expansion in bash"
date: 2008-03-01
forum: Programming Talk
---

### Post by flightless bird on 2008-03-01
I would like to work out how to recursively expand filenames in bash, so instead of expanding ```
some_directory/*
``` to ```
some_directory/sub-directory1 
some_directory/sub-directory2
some_directory/some_file1
some_directory/some_file2
``` I could expand it to ```
some_directory/sub-directory1/some_file1
some_directory/sub-directory1/some_file2
some_directory/sub-directory2/some_file1
some_directory/sub-directory2/some_file2
some_directory/some_file1
some_directory/some_file2
```As far as I know, bash doesn't do this itself, I'm not sure how tioget ls to do it neatly, and while I am aware that ksh does it, I would prefer to stay with bash, all things being equal. Any ideas?

---

### Post by lloyd_b on 2008-03-01
I don't know of ANY way to get bash to do this on it's own.

However, you can easily get such recursive expansion from the "find" command:
```
find . -type f -print
```
will give you a list of all files in the "." (current) directory, as well as all files in all subdirectories (but not the subdirectories themselves).

There are MANY variations on the "find" command - "man find" in a terminal window for more info.

Lloyd B.

---

### Post by flightless bird on 2008-03-01
Thanks lloyd_b - works a treat.

f-b

---

