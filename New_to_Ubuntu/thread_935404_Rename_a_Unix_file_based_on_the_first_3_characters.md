---
title: "Rename a Unix file based on the first 3 characters of data in file"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by jchappel on 2008-10-01
--------------------------------------------------------------------------------

I'm looking to determine if I can use a grep command to read file and rename the file based on the first 3 characters of the data in the file.

An example is:

Read FileA
If the first 3 positions of the data in the file are "ITP", then rename the file as FileA_ABC, else if the first 3 positions are "UNB" then rename the file FileA_DEF.

I believe I might be able to use the GREP command to identify the data but not sure how to rename the file being processed.

Appreciate any feedback.

---

### Post by handydan918 on 2008-10-01
> not sure how to rename the file being processed.
renaming is done via the mv command.
```
mv test_old test_new
```

---

### Post by porchrat on 2008-10-01
are those 3 characters a separate word in the file or are they part of a larger word?

---

