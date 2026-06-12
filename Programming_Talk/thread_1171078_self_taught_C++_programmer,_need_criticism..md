---
title: "self taught C++ programmer, need criticism."
date: 2009-05-27
forum: Programming Talk
---

### Post by sp0tz on 2009-05-27
Wanted to upload a ~30MB file, the limit is 1MB. Not gonna happen. Mods, please delete this.

---

### Post by majamba on 2009-05-27
your reflection depends on the code
and how do structure your program

if it is well organized it might be easy to follow what are you doing
the most important part
lining braces
using indentation

don't repeat stuff, usually bad habit write a once use it many times
don't be afraid to use contants-great help when having to type a number 20 times
reuse your code
watch out those pointers

---

### Post by jon zendatta on 2009-05-27
Why not create a new file

[PHP]touch newfile[/PHP]

Then split your file into 30-31 files less than 1Mb, download individually then join together.
[PHP]
cat file1 file2 file3 etc > newfile[/PHP]

although i'm sure someone will have a more automated solution:KS

---

### Post by dwhitney67 on 2009-05-27
30 MB is 30*1024*1024, or 31457280 Bytes.  If say, for instance, a typical file has 4096 bytes in it, that 30MB would equate to about 7680 files.  Now it is possible that this project contains graphics files, and not just source code.  But I don't think we need to see every morsel of the project; I would think that the source files are all that are needed for any review to take place.

In any case, IMO, I would say to anyone who is capable of writing 30MB of code, that it is kind of late to be seeking constructive criticism.  But I guess that re-writing the code (should it be necessary) is what is done all of the time in the s/w industry, but for one individual to do it seems incredulous.

Anyhow, in the future, the OP should consider looking into the 'tar' and/or 'gzip' commands when the desire strikes to post a large project.

---

### Post by lensman3 on 2009-05-28
Use the "split" command to break the tar ball into pieces and then upload the pieces.  "split" does a nice job naming each of the pieces.  The "split" program was written in the '70's.    Do a man on split.  There are lots of command line options. 

Then use "cat" to join everything back up.

---

