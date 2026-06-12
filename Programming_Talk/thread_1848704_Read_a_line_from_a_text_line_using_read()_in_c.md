---
title: "Read a line from a text line using read() in c"
date: 2011-09-23
forum: Programming Talk
---

### Post by mecrazycoder on 2011-09-23
Hi,
  Can anyone here tell me how to read a line from a text file using read() in c. Actually I dont want to use fgets to read. For eg, Test.txt contains something like

i 1000 10000
d 1000 1239000  and I want to read each line using read().

---

### Post by PaulM1985 on 2011-09-23
Reading from this thread might help you get started:

[http://ubuntuforums.org/showthread.php?t=1103327](http://ubuntuforums.org/showthread.php?t=1103327)

Paul

---

### Post by Bachstelze on 2011-09-23
Part of being a good programmer is knowing the right tool for the job. Here the right tool is fgets, not read.

*EDIT:* Unless this is homework, in which case we don't do that here.

---

### Post by nvteighen on 2011-09-23
> **Bachstelze said:**
> Part of being a good programmer is knowing the right tool for the job. Here the right tool is fgets, not read.

*EDIT:* Unless this is homework, in which case we don't do that here.

Yeah, the unusually restrictive setup that has been mentioned makes this very likely to be homework... read() should be used just for very low-level file access in UNIX/Unix-like OSs (it's not part of the C Standard!). In fact, I don't know any practical use of the open/read/write trio outside very low-level OS stuff (ASM or stuff that needs to interface the kernel system calls for some good reason...).

If you want to read binary, use fread, which is from the C Standard.

---

