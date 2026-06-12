---
title: "accessing file data (ex. permissions, size) in C?"
date: 2007-10-27
forum: Programming Talk
---

### Post by deadowl on 2007-10-27
I've never really accessed this layer of information when programming, but I have this idea I just would like to get out of me and I'd need to be able to read different file data such as date modified, date accessed, permissions, owner, group, etc.

Right now I have a program that can open a directory and read off all of the file names.

I know how to open a file and read its contents. However, I don't know how to access these other fields.

I am not recreating ls, and its source is pretty inconsistent, particularly in terms of indentation style, and therefore hard to grasp..

---

### Post by slavik on 2007-10-27
read up on open and stat :)

---

