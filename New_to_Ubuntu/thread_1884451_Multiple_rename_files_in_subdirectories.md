---
title: "Multiple rename files in subdirectories"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by Zimrie on 2011-11-21
I've got some cd where all files ends with ;1
for example readme.txt;1
All files in subdirectories are like it (with added ;1)
How to rename them, delete that ;1

Tnx

---

### Post by Zimrie on 2011-11-21
In one single directory I know how to do it, but in subdirectories?

---

### Post by kaspar_silas on 2011-11-21
There's a few ways the easiest is to use find and rename in a for loop:

for i in `find . -name "*;1"`; do mv "$i" "${i/;1}" ;done



this translates:
find all files ending in pattern ;1 
and rename them the same name - ;1

Note: As pointed out below this will fail if the folders' names have spaces in them.

---

### Post by Zimrie on 2011-11-21
> **kaspar_silas said:**
> There's a few ways the easiest is to use find and rename in a for loop:

for i in `find . -name "*;1"`; do mv "$i" "${i/;1}" ;done



this translates:
find all files matching ending in pattern ;1 
and rename them the same name - ;1

YES! That works.
Thank you very much!!!

---

### Post by Paddy Landau on 2011-11-21
You can also install and use [pyRenamer]("apt:pyrenamer"), which allows you to preview your changes before deciding to commit them.

The option to include files recursively are hidden under an icon in the top right-hand corner of the screen.

---

### Post by sisco311 on 2011-11-21
> **kaspar_silas said:**
> There's a few ways the easiest is to use find and rename in a for loop:

for i in `find . -name "*;1"`; do mv "$i" "${i/;1}" ;done



this translates:
find all files ending in pattern ;1 
and rename them the same name - ;1

Check out BashPitfalls 001 and BashFAQ 020 (link in my signature).

I'd try something like:
```
find ./ -depth -iname '*;1' -exec dash -c '**echo** mv -i -- "$1" "${1%;1}"' _ '{}' \;
```

---

### Post by kaspar_silas on 2011-11-21
Yeah fair point. 

Out of habit I never have spaces in file names so it never occurs to me. If I had to work with filenames that possibly contain spaces 
I would probably use mmv.

mmv -r ';*\;1' '#2'

---

