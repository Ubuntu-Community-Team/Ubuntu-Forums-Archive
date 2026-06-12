---
title: "Python/Paramiko Problem"
date: 2011-02-28
forum: Programming Talk
---

### Post by 102jon on 2011-02-28
Hi, I'm trying to use the paramiko module to download files from an sftp server using the sftp.get function. I am clearly specifying the full remote and local paths, however I get either one of two error (depending on which directories I am downloading from/to). The first one is IOError Errno 2: No such file or directory, even though i have checked and the full file paths exist. The second error simply says IOError: Failure. On this second error, it takes a really long time to get there, so it seems as if stuff has been downloading, and yet the directories are still empty. Any insight?

---

### Post by juancarlospaco on 2011-02-28
... fabric ?

---

### Post by cgroza on 2011-02-28
Code.. Give us the CODE!

---

### Post by 102jon on 2011-02-28
Nevermind, I figured out the problem. Thanks anyways.

---

### Post by cgroza on 2011-03-03
> **102jon said:**
> Nevermind, I figured out the problem. Thanks anyways.
Your solution may be helpful for others that find themselves in the same situation.

---

