---
title: "Find single, not duplicate, files."
date: 2012-06-19
forum: New to Ubuntu
---

### Post by ofb on 2012-06-19
I want to find what files are not backed up. So far, the apps I've checked only show the duplicates. I need an output that shows what files are the sole copies.

Context: The backup destination does not have quite enough space to simply back-up everything. Previous partial backups have been made. There was a list of what was not backed up, but the list has been lost. 

Time has moved on, so the sole-copy files could be anywhere, not just down one branch. Also they may have new names, so the comparison must be checksum.

Anyone happens to know what comparison app does this?

---

### Post by MG&amp;TL on 2012-06-21
Assuming two top-level directories, *diff* should do the trick.

```
diff -r /path/to/backup /path/to/data
```Should give you lots of "only in:" messages to help you work out what needs to be done.

So if you had a tree like this:

/path/to/backup:
-folder1: file1, file 2
-folder2: file1

/path/to/data:
-folder1: file1, file2
-folder2: file1, file2

...diff should tell you that only /path/to/data has folder2/file2.

Hope that helps.

---

### Post by ofb on 2012-06-25
Fabulous. Thank you so much. A quick test shows this catches both filename changes and edits that kept the original filename.

I'm not sure if it detects file changes by checksum or size, but then again I can't imagine any edit I would do that wouldn't alter byte size.

---

### Post by sudodus on 2012-06-25
***diff*** detects differences between two files. If they are text files, lines with differences (if any) will be printed to the standard output (screen). Test it with two small slightly different text files! 'Binary' files will be reported to be different if a single byte is different.

Alternatives: If you keep the names and locations of your files, you can use ***rsync*** or ***unison*** to synchronize two directory trees.

---

