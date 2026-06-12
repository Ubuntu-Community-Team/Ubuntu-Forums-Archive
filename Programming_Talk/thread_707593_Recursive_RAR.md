---
title: "Recursive RAR"
date: 2008-02-25
forum: Programming Talk
---

### Post by jdusablon on 2008-02-25
Hi and thanks in advance to everyone for any help.

I'm trying to write a command or short script that will walk through a directory structure, find all the jpg files and roll them into rar files (actually cbr files) named after their parent directory.

If you haven't guessed it already, I've got 28 graphic novels containing 15 to 20 chapters, each of which contains about 60 jpg files. I'm trying to make nice and neat CBR files for comix. Directory structure goes like this: volume01/chapter001/blahblah001.jpg

You can imagine how much work this amounts to manually, not to mention all the human error I'll likely introduce trying to repeat the same process 500 times.

*******

What I've got so far:

The following gives a nice directory name of each file in all subdirectories:
```
find -iname *.jpg -exec dirname {} \;
```

I'm trying the following, but it keeps trying to make a single archive called .cbr that gets overwritten each time the directory changes:
```
find -iname *.jpg -exec rar a `dirname {}`.cbr {} \;
```

It seems like the dirname {} is not working where/how it is presently.

I just need a pointer, and yes, I am reading up on the subject.

---

### Post by Fbot1 on 2008-02-25
How are the jpegs named?

---

### Post by jdusablon on 2008-02-25
Like this:
Comicbooktitle v01 c001 001.jpg
Comicbooktitle v01 c001 002.jpg
Comicbooktitle v01 c001 003.jpg
etc.

---

### Post by Fbot1 on 2008-02-25
So do you put the files in a directory and it just figures it out? I think you're using the wild card wrong. *.jpg refers to a whole group of files so when you do something it doesn't do it to each member it does it to the group. Also I don't think that's how you make .cbr .

---

### Post by jdusablon on 2008-02-26
Um... cbr files are made either like that or by making rar files and renaming them all cbr. Doing it this way saves me time, and I've done it many times before.

I don't really understand the wildcard bit you said, though.

The find command recursively finds *.jpg files. Each time it finds a file, it executes whatever is in the command field of -exec {} \; This is done on a line per line basis; for each jpg found, find generates a line.

That's how it is with most linux commands.

---

### Post by jdusablon on 2008-02-29
**BUMP**
Anyone?

---

### Post by Mr. C. on 2008-02-29
Where do you want your rar archives to end up?

---

