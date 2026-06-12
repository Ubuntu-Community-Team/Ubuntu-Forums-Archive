---
title: "Moving files but not their containing directories"
date: 2006-07-21
forum: Programming Talk
---

### Post by Clouseau__ on 2006-07-21
Hi everyone,

I have a whole bunch of files neatly organized inside containing sub-directories and need to copy them into a single directory source without their parent sub-directories. BTW, no two files have the same name.

I've googled for a solution but so far I haven't found one that suits my need, although i'd tend to think it's probably simple once you know the right command (and flags) to use. manually copying/pasting is just not an option as there are just too many files (and directories containing them).

Any light on the subject would be greatly appreciated.

thanks in advance,

Clouseau__

---

### Post by theconley on 2006-07-21
```
cp dir1/*/* dir2/
```

If you are new to UNIX, "*" is a wildcard.

~Conley

---

### Post by scxtt on 2006-07-21
if you're working directory is /home/clouseau/move_files and you've got the setup you're describing, try this:

find . -type f -exec mv {} /path_to/new_dir \;

replace mv w/ cp if you just want to copy ...

---

### Post by Clouseau__ on 2006-07-21
> **scxtt said:**
> find . -type f -exec mv {} /path_to/new_dir

scxtt,

thanks a million, worked like a charm. Just had to add \; at the end. I did not know about the mighty -exec flag. It rocks!

Thanks a lot to you and theconley.

Clouseau__

---

### Post by scxtt on 2006-07-21
yeah, i meant to edit that, but that's about when the "showing the database some love" message showed up :p

---

### Post by theconley on 2006-07-22
No prob.

---

