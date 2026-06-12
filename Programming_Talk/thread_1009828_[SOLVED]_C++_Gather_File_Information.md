---
title: "[SOLVED] C++ Gather File Information"
date: 2008-12-13
forum: Programming Talk
---

### Post by pcman312 on 2008-12-13
I am looking for a way to gather information about a given file/directory using C++ in linux. Essentially, I want to emulate at least some of the functionality of the File object in Java. I'd like to limit the amount of system() calls to a minimum (0 preferred).

Little background: I'm making a file browser and I'd like to be able to get information about a file other than its name.

---

### Post by dwhitney67 on 2008-12-13
Read the man-pages on these C library functions:
[LIST]
[*]opendir()
[*]readdir()
[*]closedir()
[*]stat()
[/LIST]

---

### Post by geirha on 2008-12-13
To determine the file type you can use libmagic, which is the library the file command uses. Install [libmagic-dev](apt:libmagic-dev) and read the manpage libmagic(3).

---

### Post by pcman312 on 2008-12-15
Ok, thanks for the help.

---

