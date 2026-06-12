---
title: "Visual Diff viewer which can create report / patch"
date: 2009-08-05
forum: Programming Talk
---

### Post by jackel7007 on 2009-08-05
I would like to compare 2 versions of a program, And i would like to have the differences exported to a document so I can print it.

So far meld didn't do the trick, it works great, but (i believe) it misses the output to some sort of file.

anyone has an Idea?

---

### Post by dbd on 2009-08-06
The command line command "diff" should do the trick. By default it will just print to the screen the difference between the two versions of your program, but you can just use ">" to redirect the output to a file of your choice. For example:
```
diff version1 version2 > differences
```
Will take the differences between the files "version1" and "version2" and save them in the file "differences".
Then you can just open up "differences" with your favourite text-editor / word-processor and print it.

---

### Post by geirha on 2009-08-06
I find unified context diffs easier to read, and you probably want to compare directories? So maybe you want
```
diff -ru src1/ src2/ >changes.patch
```

The resulting file is a patch file, so you can pass it to patch's stdin.

```
patch -p0 <changes.patch  # Should make src2/ equal to src1/
```

---

### Post by jackel7007 on 2009-09-21
Is there anyway to export only the differences?
I don't want any rule numbers in the exported diff file..

---

### Post by unutbu on 2009-09-21
jackel7007, maybe this?
```
diff --suppress-common-lines -y file1 file2 | sed -e 's/^[[:space:]]*//g'
```

---

### Post by jackel7007 on 2009-09-22
I think we found the same, as i already had that.
For the thing I want it works... SO thanks anyway!

But i would like to have a visual (some frontend for diff?) which can do the trick.

I have 2 sql files.
One is an old backup, the other one is newer backup.

What i would like to do is create a third file, which contains the sql statements which were added between the backups.

So in this way I can revert to my old backup, and then add (manual or just a selection) the new data to it.

---

### Post by unutbu on 2009-09-22
jackel7007, I'm not sure if I understand your situation fully, but perhaps what you are looking for is version control software. It will allow you to save as many "versions" of a file as you want, and allow you to compare any two versions with diff. You can revert to any version that you save (commit).

For example, let's say you save sql files in /backup. Then you could install bzr with
```

sudo apt-get install bzr
cd /backup
bzr init
```

This will setup a bzr branch in /backup. All it does really is add a directory /backup/.bzr. Let's say your old sql backup is called /backup/backup.sql.
You can save it by running
```

bzr add backup.sql
bzr commit -m "old backup as of xxxx-xx-xx"
```

Then you can save your new backup on top of your old on to the same location: /backup/backup.sql
```

bzr commit -m "new backup as of xxxx-xx-xx" 
```

You can compare the two versions by running
```

bzr diff
```

and you can revert to either version by running
```

bzr revert -r 1  # /backup/backup.sql will be reverted to the old sql file
```

or
```

bzr revert -r 2  # revert to the second revision.


```

---

### Post by myle on 2009-09-22
Kompare (for KDE)

---

### Post by jackel7007 on 2009-09-23
Unutbu, thanks for your great explanation...
It's a bit overkill for what i want know, but i'm sure that your info will come in handy on a day! thanks!

Myle,

i know about kompare, which is a great app... but i'm on ubuntu now, so kompare is not an option unfortunately..

So anyone knows another application for ubuntu?

---

