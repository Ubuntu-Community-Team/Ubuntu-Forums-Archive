---
title: "[SOLVED] Bash: walking directory tree"
date: 2008-08-31
forum: Programming Talk
---

### Post by Nonno Bassotto on 2008-08-31
I am by no means expert of bash programming. I've been struggling with the following simple problem.

I'd like to recursively walk from a given path and find all directories containing a subdirectory called CD1. Whenever one of these is found I should create an empty file called fake.mp3 (inside the parent directory, not inside CD1).

To walk recursively I tried using a command like
```

for i in "$(ls -R mypath)"; do somethingInvolving$i; done

```
but the problem is that $i doesn't contain the full path. For example I'd like to check if $i is a directory with
```

for i in "$(ls -R mypath)"; do if [ -d $i ]; then echo $i; fi; done

```
but this doesn't work.
Similarly
```

for i in "$(ls -R mypath)"; do if [ ls $i | grep CD1 ]; then echo $i; fi; done

```
doesn't list all the directories having a subdirectory called CD1.

What is the right sintax to do what I need?

---

### Post by ghostdog74 on 2008-08-31
use the find command
```

find . -type d -name "images" -printf "%h\n" | xargs -i cp myfilepath "{}" 

```

---

### Post by Yannick Le Saint kyncani on 2008-08-31
This would work, assuming you don't have spaces in directory names :

```
find . -type d -name CD1 | sed 's#/[^/]*$#/fake.mp3#' | xargs touch
```

---

### Post by mssever on 2008-08-31
Note also that you shouldn't try to parse the output of ls. It's impossible to do so reliably. While the find command is the ideal way to do this, if you ever do need to run a for loop over a directory, the proper way is: ```
for i in *; do blah; done
```

---

### Post by Nonno Bassotto on 2008-08-31
Thank you all. The first command works. :)

---

### Post by stylishpants on 2008-08-31
You don't need the pipe.

The -execdir flag of find lets you execute one command in the directory containing the matched file / dir.  


```
find . -type d -name CD1 -execdir touch fake.mp3 \; 
```

This neatly sidesteps the issue of having to pass filenames that may or may not contain spaces through a pipe, and deal with it on the other side.

---

