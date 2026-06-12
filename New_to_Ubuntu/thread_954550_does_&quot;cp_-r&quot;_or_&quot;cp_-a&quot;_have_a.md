---
title: "does &quot;cp -r&quot; or &quot;cp -a&quot; have a bug?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by garyed on 2008-10-21
This is in response to the thread yesterday about copying files & subdirectories. I asked it at the end of the thread after it had been marked solved so I thought it might be better to start a new thread, apologies if I'm out of line.
Anyways here goes,

Isn't this a bug in the cp command because if you use:
```
 cp -a ./music/* ./any_diredctory 
```
it copies all files recursively & preserves the directory structure but if you use:
```
 cp -a ./music/*.mid ./any_diredctory 
```
it doesn't copy the files recursively but only the parent directory files.
The same thing happens if you use the "cp -r" command.
Am I missing something?

---

### Post by cek on 2008-10-21
I don't think this is a bug, just a slight misunderstanding of how the command works.

The filter expression (*.mid) is done prior to the copy operation.  Therefore, only items that match the *.mid filter are actually copied.  This means that recursively there will be no subdiretories* that match the filter and therefore none are copied.

* NOTE:  If you had a directory named directory.mid that contained files with a .mid extension, I believe that directory and its contained files would be copied preserving the structure.

---

### Post by garyed on 2008-10-21
I understand your logic so on that premise it wouldn't be considered a bug as much as a limitation of the cp command. It seems to me to be an oversight in the actual design of the command though not being a programmer its probably a lot more complicated than that. I'm just a little disappointed that DOS xcopy has that useful feature & Linux cp doesn't. It's one of the rare times that I would favor a DOS command over a Linux one. So now my scorecard reads:

Microsoft - 1       Linux -  1,357  <g>

---

### Post by hyper_ch on 2008-10-21
use "find" instead

---

### Post by vanadium on 2008-10-21
How could you do so preserving the directory structure?

---

### Post by Idefix82 on 2008-10-21
To preserve the directory structure I find tar the most handy command.

---

