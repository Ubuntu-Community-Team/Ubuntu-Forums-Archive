---
title: "How can I remove a file from svn without deleting the file?"
date: 2009-03-17
forum: Programming Talk
---

### Post by kerryhall on 2009-03-17
How can I remove a file, or in this case, a huge tree of files and folders from svn, without actually deleting the files?

I checked out a bunch of files from one repo, now I need to get rid of their "svn" status so that I can put them into another repo. How do I do this?

I was thinking that I have to delete the ".svn" folder in every directory. Anyone want to give me a bash script that does this?

Thanks!

---

### Post by myrtle1908 on 2009-03-17
> **kerryhall said:**
> I was thinking that I have to delete the ".svn" folder in every directory. Anyone want to give me a bash script that does this?

This should work.  Run it from the root of your project.

```
rm -rf `find . -type d -name .svn`
```

---

### Post by shadow_code on 2009-03-17
An easier way might be to simply "svn export" that path to another location.

---

### Post by spupy on 2009-03-17
Say you want to remove a folder named lalala.

```
svn export lalala /new/path/where/you/want/it
svn rm lalala
```

Then delete the folder lalala by hand and commit.

---

### Post by kerryhall on 2009-04-02
Thank you all, this was extremely helpful!

---

