---
title: "subversion: listing unsubmitted local files that are not in repository"
date: 2008-03-10
forum: Programming Talk
---

### Post by idn on 2008-03-10
Hi, I have a subversion repository and want to delete my local copy, but before I do I want to see what local files I might not have added to the repository by mistake - I just found one. 

I don't want to svn add all the files recursively because there are binary and hidden files that I do not want to add. Does anyone know a way to do this? Just want to make sure I do not loose any files! There are a lot of directories so doing it manually is not fun :)

Cheers

---

### Post by WW on 2008-03-10
Try the command **svn status**.  Any file with a question mark in front of it is not in the repository.  For more information, use **svn help status**

---

### Post by idn on 2008-03-28
great, thanks!

---

