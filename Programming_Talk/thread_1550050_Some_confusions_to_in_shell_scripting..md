---
title: "Some confusions to in shell scripting."
date: 2010-08-10
forum: Programming Talk
---

### Post by Rushyang on 2010-08-10
1) I'm making a script, which will prompt all 0 BYTE (EMPTY) files (from specific directory to it's all subdirectories).. and then will ask to whether to delete a file or not.. one by one..

in which I was successful to find all empty files by command..

>  $find . -empty But I am not able to figure out how to pipe those outcomes with rm command. 
if to make a temp file and then store those outcomes into it.. but how to point out (traverse) a variable from file?

3) If I do below...

> 
$img=myimage.jpg
$echo ${img/.jpg/}
myimage  (OUTPUT)
So it will trim .jpg extension from backward...

what if I want to trim my selected words or specific positions? (I don't if **trim** is correct word to explain what I want to do..)

---

### Post by MadCow108 on 2010-08-10
1)
use xargs:
find . -empty -print0 | xargs -0 rm
print0 and -0 are for handling spaces in filenames.

I don't quite understand what you mean in 3)
But probably regular expressions are an answer.
use e.g. sed to trim the front of the filename (assuming only one . in the name):
echo "img.jpg" | sed -e "s/^[^\.]*\.//"

---

### Post by ghostdog74 on 2010-08-11
```

find /path -type f -size 0 -exec rm -i "{}" +;

```

---

