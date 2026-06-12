---
title: "How to find entries present in one file but not in another?"
date: 2014-02-15
forum: Programming Talk
---

### Post by vasa1 on 2014-02-15
I have two files: **A** and **B** which are lists with one string per line and both have been sorted in the same way and do not contain duplicates. 

Is there a command line way to make a third file, **C**, containing entries present *only* in **A**.

---

### Post by mikewhatever on 2014-02-15
That would be diff. See man diff for more info.

---

### Post by steeldriver on 2014-02-15
How about grep -f?

```
fgrep -vf B A > C
```

---

### Post by vasa1 on 2014-02-15
"comm" looks like what I want: [http://stackoverflow.com/questions/8533851/way-to-output-differences-between-two-files-preferably-using-command-line](http://stackoverflow.com/questions/8533851/way-to-output-differences-between-two-files-preferably-using-command-line)

---

### Post by vasa1 on 2014-02-15
> **steeldriver said:**
> How about grep -f?

```
fgrep -vf B A > C
```
Actually, this ^^^ works. Thanks!

---

### Post by steeldriver on 2014-02-15
I didn't know about comm, but it looks like that would be more efficient for files that are already sorted

```
comm -23 A B > C
```

---

