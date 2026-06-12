---
title: "How to find specific characters within directory or file name"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by deedledum on 2013-02-17
what find option do you use to find specific characters within a directory or file name?  Would need to include directory and subfolders below.

---

### Post by Doug S on 2013-02-17
Hi, and Welcome to Ubuntu forums.
 
Say I wanted to find all files containing the string "history" from my current directory and below. This would so it:```
find . -type f -name "*history*"
```
 
Edit: Actually, to include directory names, I think you would want this:```
find . -name "*history*"
```

---

### Post by deedledum on 2013-02-17
Thanks Doug S for the quick reply. Forgive my ignorance but what do the -type and -name signify? If I were looking for all files or directories containing the letter 'w'  inside Downloads and its subdirectories for instance?

---

### Post by schragge on 2013-02-17
**-type f** - only regular files
**-type d** - only directories
by default - files of all types
**-name [color=blue]pattern[/color]** - only files that match [color=blue]pattern[/color]

See [GNU Findutils Manual](http://www.gnu.org/software/findutils/manual/html_node/find_html/Finding-Files.html).

---

### Post by ajgreeny on 2013-02-17
If you want to search plaintext file content recursively within a folder which contains files you can use the command ```
grep -i -r *searchword* */path/to/folder*
```This searches al the text files line by line and outputs  the filename and the complete lines, with the searchword showing in colour.

---

### Post by deedledum on 2013-02-17
Thanks everyone, this is what I was looking for. The extra links were a great resource too.

---

