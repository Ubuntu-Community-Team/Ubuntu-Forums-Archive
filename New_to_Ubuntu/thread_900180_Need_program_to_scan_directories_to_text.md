---
title: "Need program to scan directories to text"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Warren North on 2008-08-25
Need program that can scan my drive in ubuntu and list them in a text file sort of like a database for the filenames and other info it can get.
Not sure even if there is a dos like command line that I can use to do this

Thanks for any help

---

### Post by ahmatti on 2008-08-25
Execute this in your terminal:

```
find / *.* > files.txt
```

It will list all your files and directories into "files.txt" text file.

---

### Post by porchrat on 2008-08-25
Maybe you could try a ls command something like this:

```
ls -lhR / > name_of_text_file
```

that would print out all names, sizes, permissions and ownership details of all files and directories.  It would take a while though and you would probably need to use xargs as well because I don't believe ls could handle that much information.

---

### Post by Warren North on 2008-08-25
Thanks I will try it out.

---

