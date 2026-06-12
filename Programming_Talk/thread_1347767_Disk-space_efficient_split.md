---
title: "Disk-space efficient split"
date: 2009-12-06
forum: Programming Talk
---

### Post by silentrebel on 2009-12-06
I'm trying to split a big file into smaller pieces by number of bytes:
```
split file -b 650 m
```

However, I do not have enough disk space to accommodate the original file and the split version.  I was wondering if there exists an option or another utility that directly splits the original file such that you do not have to have file.size*2 bytes free for the operation...  

It would be acceptable if it copied one slice to a new file and then deleted that section in the original file before proceeding.  

In fact, any process that yields the same end result without requiring file.size*2 bytes would be appreciated.

---

### Post by Arndt on 2009-12-06
> **silentrebel said:**
> I'm trying to split a big file into smaller pieces by number of bytes:
```
split file -b 650 m
```

However, I do not have enough disk space to accommodate the original file and the split version.  I was wondering if there exists an option or another utility that directly splits the original file such that you do not have to have file.size*2 bytes free for the operation...  

It would be acceptable if it copied one slice to a new file and then deleted that section in the original file before proceeding.  

In fact, any process that yields the same end result without requiring file.size*2 bytes would be appreciated.

I think I would write a program to do it. But what will happen to the pieces once you have split the big file up? Are they to be sent to another computer, or input to a program which doesn't support more than a certain size of input?

---

### Post by silentrebel on 2009-12-06
I need to burn the file to CDs...  I also have another project that will need to often split large files and disk-space usage could eventually be a problem with the above-mentioned split command.

Does anyone know where to start to write such a program?

---

### Post by The Cog on 2009-12-07
There is a file truncate feature. It is supported by the C libraries and by python, so I guess most languages will support it. I would therefore start by making copies of the end of the file, and truncating it after each copy has been made so the original file slowly gets shorter. This way, you should only need disk space to hold the original file plus one piece. Due to familiarity, I would probably do it in python, but any language you are familiar with should do.

---

### Post by silentrebel on 2009-12-07
Thank you very much for your post.  That's very helpful..
In fact, I already started coding using that truncate function in C++... I should have made a note of it here...  
I'll let you know how it goes...
I have to say that I am tempted to switch over to Python...  There seem to be some C++ binary I/O flags that are messed up with GNU g++... Undoubtedly, Python would not present this problem...

---

### Post by The Cog on 2009-12-07
I imagine you will be repeatedly call seek(offset) and read(size) and truncate(size) to read the end part of the file and then shorten it.

As for binary I/O flags, I'm not sure. Python allows opening files with a "r" or "w" flag for read/write, and "rb"/"wb" for binary, but I thought the binary flag was only relevant on Windows, where in non-binary mode it does some messing with line endings.

---

