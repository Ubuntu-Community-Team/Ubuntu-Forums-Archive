---
title: "Shell Redirection?"
date: 2010-02-01
forum: Programming Talk
---

### Post by huangyingw on 2010-02-01
Hello,
     I had following script, named back.sh, as bellow:
```
#! /bin/bash

lv_file=/root/myproject/git/linux/shell/fundamental/log.txt
lvdisplay | grep -o "/dev.*" > $lv_file

cat $lv_file | while read file ; do
	echo "$file" | sed 's/dev/media/' |	mkdir -p '{}'
	#echo "$file" | sed 's/dev/media/'
	#mkdir -p 'echo "$file" | sed 's/dev/media/''
done

```
     I would like the "mkdir -p" command to use the output of "echo "$file" | sed 's/dev/media/'", but it does not work.
     BTW, another question:
     How to use sed to replace directly from a string, instead of a file.
     For example, I know ```
sed 's/dev/media/' < $file
```, in which file contains the string I would like to replace.
    While, I am expecting a direct form like bellow:```
sed 's/dev/media/' $mystring
```. But I don't know how to realize this.

---

### Post by Sporkman on 2010-02-01
Try:

myval=`echo "$file" | sed 's/dev/media/'`
mkdir -p "$myval"

---

### Post by huangyingw on 2010-02-01
> **Sporkman said:**
> Try:

myval=`echo "$file" | sed 's/dev/media/'`
mkdir -p "$myval"
yes, thank you. This is indeed a simple and useful solution.
My head is stuck at that time.:(

---

### Post by Sporkman on 2010-02-01
> **huangyingw said:**
> 
My head is stuck at that time.:(

That happens to us all. :)

---

### Post by geirha on 2010-02-02
The shell can also do that substitution itself.
```

while read -r file; do
    mp="/media${file#/dev}"
    mkdir -pv "$mp"
done < <(lvdisplay | grep -o "/dev.*")

```

---

### Post by huangyingw on 2010-02-03
> **geirha said:**
> The shell can also do that substitution itself.
```

while read -r file; do
    mp="/media${file#/dev}"
    mkdir -pv "$mp"
done < <(lvdisplay | grep -o "/dev.*")

```
Great, thank you.

---

