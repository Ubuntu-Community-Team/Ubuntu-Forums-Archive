---
title: "How do I 'search' for files ?"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by L Campbell on 2013-02-06
I am using 12.04 on my PC and do not seem to be able to search for files in the way that I did when I was using 11.04.

Your help will be appreciated.

---

### Post by iMac71 on 2013-02-06
What was the way you used for searching files when you were using Natty Narwhal?
And why don't you use the "find" command in a Terminal window for your searches?

---

### Post by CaptainMark on 2013-02-06
The gui way: In the file browser (assuming you're using the default) Press ctrl+f and type a file name

The terminal way:```
find -name "file name"
```to search down from the current directory, use -iname instead to remove case sensitivity or see "man find" for more search options the * character acts as a wildcard for unknown characters

---

### Post by L Campbell on 2013-02-06
> **CaptainMark said:**
> The gui way: In the file browser (assuming you're using the default) Press ctrl+f and type a file name

The terminal way:```
find -name "file name"
```to search down from the current directory, use -iname instead to remove case sensitivity or see "man find" for more search options the * character acts as a wildcard for unknown characters

OK, I guess I could have explained myself a little better.

What I am trying to find is my .dwg files, and they seem to have become scattered.

TIA.

---

### Post by CaptainMark on 2013-02-06
in the terminal use this ```
find ~/ -iname *.dwg
```if you wan't to gather them back together use this ```
mkdir lost_files
find ~/ -iname *.dwg -exec mv {} lost_files/ \;
```This will pull all the files ending in .dwg and place them into a folder named lost_files,

I'm assuming all the dwg files are within your home directory, is this okay?

---

