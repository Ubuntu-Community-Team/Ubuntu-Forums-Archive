---
title: "Output Directory Contents (BASH)"
date: 2008-10-05
forum: Programming Talk
---

### Post by blendmaster on 2008-10-05
Hello!

Well, I'm learning how to Shell Script in BASH (in part to work on a simple project to make my life a little easier, and also to have a go at the language).

I have a directory, I'll call it Unprocessed/, and basically I want to write a text file in Unprocessed/ that contains the names of all the subdirectories within Unprocessed/ (with each name on a new line).

Thus, I tried:

```
#!/bin/bash
cd ~/Unprocessed/
dir > Directory_List.txt
```

However, that produces (in the text file):

> Directory_List.txt  Example_Directory  Example_Directory2

in the text file. I A) don't want the file name there and B) don't want the files on the same line.

Any help?
Thank you!

---

### Post by mssever on 2008-10-05
```
#in Unprocessed's parent directory
ls -1d Unprocessed > Unprocessed/directory_list
```

EDIT: Or, from within Unprocessed: ```
ls -1d | grep -v directory_list > directory_list
```

---

### Post by ghantoos on 2008-10-05
You can do:
```

find Unprocessed/ -maxdepth 1 -type d > Unprocessed/Directory_List.txt

```Cheers,

---

### Post by blendmaster on 2008-10-05
Thanks guys!

Managed to get it to work with both methods.

Thanks again!

---

### Post by geirha on 2008-10-05
You allready got good suggestions, but here's one using only shell builtins:
[php]
#!/bin/bash

cd ~/Unprocessed/
for file in *; do
  [ -d "$file" ] && echo "$file"
done > Directory_List.txt
[/php]

Also, for learning bash, check out the beginner and advanced bash scripting guides at [http://tldp.org](http://tldp.org)  they use alot of examples.

---

