---
title: "identifying and rolling back a CVS committ locally"
date: 2014-11-25
forum: Programming Talk
---

### Post by Lars Noodén on 2014-11-25
I've checked out a module in Gnu CVS and identified one file that I want to roll back.  Aside from using the diff to unpatch, is there another way?

Further, that one file depends on definitions in at least one other file changed during the same commit.  How do I find the other files that were changed in the same commit?

---

### Post by ofnuts on 2014-11-25
My CVS is a bit rusty, and I've been using it mostly through the Eclipse plugin lately...

If you have set a tag on the commit, then checkout -r {tag} will retrieve the file with that version. Checkout -D {date} will also gives you the file contents as it was in the repository at the given date. At that point CVS makes the files read-only and remember somewhere that this isn't the latest version, but there is some way to make it the current version again. 

To find the files changed on the same day, I have no better idea than running a cvs status on them and checking for the dates, unless you have been very specific when tagging them (but this is normally not a good way to use tags, that are best used across a whole project.).

---

### Post by Lars Noodén on 2014-11-25
Ok, thanks.  I'll look at dates a bit.  However, it is likely that many files are changed on any given day, seeing as the module has about 65,000 regular files in all.  If there is a way to identify a specific commit and the files it affects, that would be the best, I think.

---

### Post by spjackson on 2014-11-25
> **Lars Noodén said:**
> Ok, thanks.  I'll look at dates a bit.  However, it is likely that many files are changed on any given day, seeing as the module has about 65,000 regular files in all.  If there is a way to identify a specific commit and the files it affects, that would be the best, I think.
My CVS is also very rusty and maybe this will help, but maybe this will help.
```

cvs -q diff --brief -r1.344 -r1.345  | grep Index

```
I think this lists files change in revision 1.345, but I'm not sure how additions/deletions are handled.

---

### Post by ofnuts on 2014-11-25
But when you commit several files, each gets its ow version number, depending on its history?

---

### Post by Lars Noodén on 2014-11-25
Yes, each file has its own, different version number.

---

### Post by spjackson on 2014-11-25
> **ofnuts said:**
> But when you commit several files, each gets its ow version number, depending on its history?
True, my mistake. I really have been away from it too long.

---

