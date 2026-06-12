---
title: "bash script or command to compare directory contents?"
date: 2010-07-07
forum: Programming Talk
---

### Post by tarahmarie on 2010-07-07
Hi!

I have a directory A containing multiple folders, each with zillions of files. I have another copy of that directory--call it B--with similarly named folders and fewer files, but possibly different files as A.  

If in A, I have a folder xyx that contains six files, and in B, I have the same folder xyz that contains four files, here is what I need:

I want to compare each subdirectory in B to the similarly named one in A. If there are four files in xyz, I want to check that the same four files exist as part of the six files in the xyz directory in A.  If they do not, or if only some of them do, I want to copy over the files that do NOT already exist into the directory in A.  

I'm trying to do this in bash, since I'm trying to learn it. I don't know where to start, though. Is this a simple command I can run in my shell or do I need to write a more complicated script to check for identical files?

---

### Post by kaibob on 2010-07-07
I think you can do that with the cp command with the recursive and no-clobber options. If the A and B directories are in your home directory:

```
cp -r -n /home/kaibob/B/* /home/kaibob/A
```

It should be noted that this command will copy any subdirectories in directory B that do not have corresponding subdirectories in directory A. You state that all subdirectories in B have corresponding subdirectories in A, so this shouldn't be an issue.

---

### Post by tarahmarie on 2010-07-07
> **kaibob said:**
> I think you can do that with the cp command with the recursive and no-clobber options. If the A and B directories are in your home directory:

```
cp -r -n /home/kaibob/B/* /home/kaibob/A
```

It should be noted that this command will copy any subdirectories in directory B that do not have corresponding subdirectories in directory A. You state that all subdirectories in B have corresponding subdirectories in A, so this shouldn't be an issue.

Holy CRAP you just saved me a lot of work. Thank you VERY much. Didn't know about the no-clobber opt.

---

