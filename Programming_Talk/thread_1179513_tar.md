---
title: "tar"
date: 2009-06-05
forum: Programming Talk
---

### Post by notsomeone on 2009-06-05
Is there a way to automatically check if a tar archive has one encapsulating directory, so that it won't spew loose files all over the current directory?
Ideally if there was no directory, one would be created before extracting.

If not, can anybody write a short bash script to check for that? Maybe something that checks if the last character of the first line of `tar tvf` is a "/".
I am fumbling with grep and sed but not getting it right.

---

### Post by stroyan on 2009-06-05
If the tar contains only one file or directory of files then this should output "1"-
```

tar tf somefile.tar | cut -d/ -f1 | sort | uniq | wc -l

```
It looks for how many unique directory or file names appear.
The parts after the first "/" character in each line are removed.

---

### Post by notsomeone on 2009-06-05
That works perfectly, thanks a lot.

---

### Post by MadCow108 on 2009-06-05
the same in messy ;)
tar -tvf test.tar| awk '{print $6}' | xargs -n 1 dirname | grep -x "." |wc -l

---

