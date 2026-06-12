---
title: "delete file older then 2 days"
date: 2012-12-08
forum: Programming Talk
---

### Post by cazz on 2012-12-08
Hi

I have found this code

```
find /var/www/folder* -mtime +2 -exec rm {} \;
```

I like to delete old JPG file.

It say no error but the folder still have all old JPG file?

---

### Post by TheFu on 2012-12-08
That code looks scary. If it didn't delete every file over 2 days old, then you are lucky - really lucky.
To learn how to use the **find** command in detail, use **man find**.  I think you are missing the **-name** or **-iname **specification to match just on "JPG" files.

I think that everyone trying to do what you are trying to accomplish has made a mistake and completely wiped out directories and files that they didn't mean.  Always start with a plain **find** command - no **-exec rm **part - validate that what you are finding is only what you intend **AND NOTHING MORE.**  I once deleted an entire operating system because I wasn't careful and didn't check it.

I think this is what you want:
```
find /var/www/folder -mtime +2 -iname \*jpg
```
Notice that the filename specification is different from the folder specification.  The -iname will match case insensitive filenames. That is probably what you want, if not, use -name. That part could also be written with double quotes as 
```
-iname "*jpg"
```

---

### Post by cazz on 2012-12-08
hmm ok

Now it list the file that I want to delete but how do I delete them?

I did try to add "rm" before the string but nothing happend.

---

### Post by Herbon on 2012-12-08
> **cazz said:**
> hmm ok

Now it list the file that I want to delete but how do I delete them?

I did try to add "rm" before the string but nothing happend.

Code:
find /var/www/folder -mtime +2 -iname "*jpg" -delete

---

