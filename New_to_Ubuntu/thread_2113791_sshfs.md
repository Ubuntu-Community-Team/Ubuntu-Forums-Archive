---
title: "sshfs"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by orangecsky on 2013-02-08
I am running a program through ssh, and trying to use sshfs to mount folders so that the program can open files from my local machine. I also would like the files to only be available to me, not other people who ssh to the remote machine.

I have tried

```
sshfs -o idmap=user $USER@far:/local_folder ~/remote_folder
```but it does the opposite from what I would like it to.

Please advise.

Thank you.

---

