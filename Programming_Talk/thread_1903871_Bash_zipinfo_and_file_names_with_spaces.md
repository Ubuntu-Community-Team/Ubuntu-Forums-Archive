---
title: "Bash: zipinfo and file names with spaces"
date: 2012-01-03
forum: Programming Talk
---

### Post by leekaiwei on 2012-01-03
Here is the code:

```
structure_array=(`zipinfo -1 "$file_name"`)
```

Basically outputting the directory into an array. Everything works fine until the directory has files names with spaces in them.

---

### Post by gnometorule on 2012-01-03
I haven't tested it, but changing the IFS should do:

IFS_OLD=$IFS
IFS=$'\n'
structure_array=(`zipinfo -1 "$file_name"`)
IFS=$IFS_OLD

---

### Post by sisco311 on 2012-01-04
See: BashFAQ 005 (link in my signature).

Bash 4:
```
mapfile -t structure_array < <(zipinfo -1 "$file_name")
```

Unfortunately, zipinfo can't print the filenames separated by a null character instead of a newline, so your script will fail with filenames with newlines.

---

### Post by sisco311 on 2012-01-04
Hmmm, you could write a python script to print the file names separated by a null character. My python skills are very limited, but the following code works to some extent. I'm sure that someone can improve it for you:
```
#!/usr/bin/env python

import sys, zipfile

file = zipfile.ZipFile(sys.argv[1], "r")

for name in file.namelist():
        print (name, end="\0")

file.close()

```
You must to pass a .zip file as an argument to the script.

With this script you can use the *[Reading NUL-delimited streams]("http://http://mywiki.wooledge.org/BashFAQ/005#Reading_NUL-delimited_streams")* method to read the file names in an array.

---

### Post by leekaiwei on 2012-01-05
> **gnometorule said:**
> I haven't tested it, but changing the IFS should do:

IFS_OLD=$IFS
IFS=$'\n'
structure_array=(`zipinfo -1 "$file_name"`)
IFS=$IFS_OLD

Thank you very much! This works perfectly.

---

