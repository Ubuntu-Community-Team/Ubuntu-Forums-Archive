---
title: "Program to join multiple .m4b files?"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by rom3lol on 2011-12-27
I have multiple .m4b files which I would like to join into a single one; ffmpeg doesn't support m4b output. 
Is there a program/ command that would do what i'm searching for?

---

### Post by ron999 on 2011-12-27
> **rom3lol said:**
> 
Is there a program/ command that would do what i'm searching for?

Hi
I think this is how to do the job with **MP4Box** (part of gpac).
Write the first file to "output.m4b", then use MP4Box to cat the others.

```
cp file1.m4b output.m4b ; \
MP4Box \
-cat file2.m4b \
-cat file3.m4b \
-cat file4.m4b \
-cat file5.m4b \
output.m4b
```

EDIT
Probably be OK to have the output file with _m4a_ extension instead of m4b, "output.m4a"

---

### Post by rom3lol on 2012-01-04
> **ron999 said:**
> Hi
I think this is how to do the job with **MP4Box** (part of gpac).
Write the first file to "output.m4b", then use MP4Box to cat the others.

```
cp file1.m4b output.m4b ; \
MP4Box \
-cat file2.m4b \
-cat file3.m4b \
-cat file4.m4b \
-cat file5.m4b \
output.m4b
```EDIT
Probably be OK to have the output file with _m4a_ extension instead of m4b, "output.m4a"

Thank you, that's simple enough!:D

---

