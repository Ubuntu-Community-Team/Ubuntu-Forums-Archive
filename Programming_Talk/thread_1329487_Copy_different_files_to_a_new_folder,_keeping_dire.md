---
title: "Copy different files to a new folder, keeping directory structure"
date: 2009-11-17
forum: Programming Talk
---

### Post by durand on 2009-11-17
Hi,

Is there an easy way to diff two directories recursively and then copy the files that are either non existent or different to a new directory while keeping the original structure the same? I think I can do this with a python script but I'd rather not.

Thanks.

---

### Post by 0cton on 2009-11-17
it seems pretty straightforward to me, and rather easy thanks to function recursivity, and python seems a good languages suited for this kind of task especially since you seem to know it.
If you are asking if there are already knows programs that do that it could be possible but I don't know any

---

### Post by dwhitney67 on 2009-11-17
'rsync' can do this; I use it at home to back up my data from one system to another.  Surely it can be used to back up one folder to another.

---

### Post by durand on 2009-11-17
I've been using rsync to update a folder. Maybe it has an option to just copy changes to a new folder.

---

### Post by durand on 2009-11-17
> **0cton said:**
> it seems pretty straightforward to me, and rather easy thanks to function recursivity, and python seems a good languages suited for this kind of task especially since you seem to know it.
If you are asking if there are already knows programs that do that it could be possible but I don't know any

Yeah, I was just hoping for a program since I'm quite lazy right now :P

---

### Post by dwhitney67 on 2009-11-17
> **durand said:**
> I've been using rsync to update a folder. Maybe it has an option to just copy changes to a new folder.

It does.  The following should suffice:
```

rsync -a srcdir/ destdir

```
Of course, make a back-up of your source-folder before you try.

---

### Post by durand on 2009-11-17
What does the archive mode do? I'm not sure you understand what I'm trying to do.

Basically, I have two folders. One is the original, the other is an update. I need to compare the two and for any files that are different in the original, I need to copy the updated files to a *new* folder while still retaining the directory structure.

---

### Post by delfick on 2009-11-17
Here's a nice usage

rsync -r --del --force -C --progress

and, with the -n switch, it's a dry run

:)

(look at rsync --help for more info)

---

### Post by durand on 2009-11-17
Thanks everyone for the responses. I just used Meld to view the differences and manually copied files. I didn't have too many anyway :/

---

### Post by dwhitney67 on 2009-11-17
> **durand said:**
> What does the archive mode do?
Read the manpage for 'rsync'.  And the -a option does more than just archive.

---

