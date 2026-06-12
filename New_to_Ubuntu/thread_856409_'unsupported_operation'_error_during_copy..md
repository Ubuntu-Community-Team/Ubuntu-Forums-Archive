---
title: "'unsupported operation' error during copy."
date: 2008-07-11
forum: New to Ubuntu
---

### Post by esbo on 2008-07-11
I was trying to copy the data on my XP drive onto my second drive using Ubuntu (Wubi) about halfway through it came up with 'unsupported operation
while copying'. skip/retry/cancel
Retry didn't work and skip gave the same error on all then ext files so I
canceled.I can't copy anything across now it seem, not without a reboot I
guess.

This is version 7.0.4 (approx).

I has a few other errors earlier but I think these had odd characters,
(chinese) in the file names, possibly.

---

### Post by dracayr on 2008-07-11
try doing it with cp from the command line:

```
cp -v /Path/to/file /path/to/destination/
```

do you get an error? what does it say?

dracayr

---

### Post by esbo on 2008-07-11
> **dracayr said:**
> try doing it with cp from the command line:

```
cp -v /Path/to/file /path/to/destination/
```

do you get an error? what does it say?

dracayr

I am not too sure how to specify the drives, it says /media in the properties
of the path but it is on c:/ so I am not sure how I do it.
I am copying a file on C: to f: so do I put c: etc? or do I use the /host thing?

---

