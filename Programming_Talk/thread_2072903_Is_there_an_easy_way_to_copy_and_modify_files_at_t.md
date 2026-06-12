---
title: "Is there an easy way to copy and modify files at the same time?"
date: 2012-10-18
forum: Programming Talk
---

### Post by Shaftway on 2012-10-18
I'm trying to keep two java source trees in sync, but they've got different package names, so I'm building a script to copy from one tree to the other.  So I want to do a recursive copy, but as I copy the files I want to run them through something like sed to replace package and import names.  Is there a clever command line way to do this?

---

### Post by Vaphell on 2012-10-18
recursive copy as in cp -r? if so, you can't inject sed in the middle.
Can't you run loop over files of destination dir and sed them?

```
while read -r f; do sed -i 's///' "$f"; done < <( find $dest_dir -type f )
```
or ```
find $dest_dir -type f -exec sed -i ... "{}" \;
```

---

