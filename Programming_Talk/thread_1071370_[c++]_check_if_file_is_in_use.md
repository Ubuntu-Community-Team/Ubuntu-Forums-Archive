---
title: "[c++] check if file is in use"
date: 2009-02-16
forum: Programming Talk
---

### Post by psysiu on 2009-02-16
hello,
I would like to check in C/C++ if any process is using (read/write) specified file, is it possible?
Thanks for any help

---

### Post by geirha on 2009-02-16
Don't know how, but the commands lsof and fuser can do that. You could look at their code and see how they do it.

```
$ dpkg -S `which lsof fuser`
lsof: /usr/bin/lsof
psmisc: /bin/fuser
$ apt-get source lsof psmisc

```

---

### Post by Rich78 on 2009-02-16
One way would be to try to open the file for write and catch / handle the error.

---

### Post by psysiu on 2009-02-23
I though about searching in lsof source but it looked a bit scary.
Catch error is not always possible because it is possible for a file to be in use by a few processes.
Because the main interest were threads which were part of the same project i decided to use file locks, it will be enough for now.

---

