---
title: "Move all duplicate files to another folder."
date: 2014-12-01
forum: New to Ubuntu
---

### Post by matthew31 on 2014-12-01
I've got a 60+ gig folder of backups from an old PC.

I was in a desperate situation to get these off of an infected Windows computer and it looks like I copied the same thing multiple times in multiple places and even named different things.

I have found that the "fdupes" command does exactly what I need for finding the files, but how can I move all duplicates to a new directory?

Example: folderA contains the file C.png and another file called D.png that is identical.

How can I make things end up like this after running fdupes?

```
folderA/C.png
folderB/D.png

```

---

### Post by Wtower on 2014-12-02
I had a similar issue, but instead of moving the files I needed to add a symlink. So what I did was to redirect the output of fdupes to a file, and then created a bash script to go through each line and handle the duplicates.

---

