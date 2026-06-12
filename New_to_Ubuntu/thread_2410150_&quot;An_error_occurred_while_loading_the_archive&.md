---
title: "&quot;An error occurred while loading the archive&quot;"
date: 2019-01-11
forum: New to Ubuntu
---

### Post by redus on 2019-01-11
Hey all when I try to open a file that I have downloaded the Archive Manager window pops up and an error message states, "An error occurred while loading the archive." Any ideas on how to fix this? Thank you very much!!

---

### Post by Impavidus on 2019-01-11
Is the file indeed supposed to be an archive?

Do you mind if we use the terminal? The text interface is easier if we communicate in forum posts. Try```
file [path/to/file]
```substituting the path to the file, like```
file Download/archive.tar.gz
```You can even type file<space> in your terminal and drag the file into it. That should tell us what kind of file Ubuntu thinks it is.

The next step will be trying the terminal to unpack the file, but we have to know first what kind of file it is.

---

### Post by redus on 2019-01-14
I'm not sure how to write like I'm typing in the terminal, but I believe I've figured it out. I was trying to open a .exe file when I guess, for whatever reason, Linux uses those tar.gz files. Thank you!!

---

### Post by Impavidus on 2019-01-15
.exe files are Windows executables that are useless on Linux – with a few exceptions. Sometimes you may have success running .exe files using wine, some .exe files are .NET stuff you can run using mono and some .exe files are auto-extracting zip archives and the archive manager can handle those. That's why the archive manager popped up.

.tar.gz is probably the most common archive format on Linux, but there are several others.

---

