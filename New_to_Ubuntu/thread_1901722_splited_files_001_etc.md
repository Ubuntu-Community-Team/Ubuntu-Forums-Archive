---
title: "splited files 001 etc"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by vagelism on 2011-12-29
Hello to all. Happy new year.


How can I join splited flies in file format...001 001 etc?
Thank you

---

### Post by The Cog on 2011-12-29
I would use cat (short for concatenate) to rejoin them.
First, make sure that you have the right selection. If the parts are all called "myfile.001" etc, then 
> echo myfile*
should list them in the right order. Assuming it does, then 
> cat myfile* > outfile
should copy them all in the right order to myfile.

---

### Post by vagelism on 2011-12-29
Thank you very much!

---

### Post by Mark Phelps on 2011-12-29
If that doesn't work, then Google for a program named HJsplit.  You can download a java version for free that will run in Linux.

---

