---
title: "What is the ubuntu command for singe file information?"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by lendon210 on 2012-05-03
I need to find a command to enter  into the terminal that will allow me to see a detailed list of  information about a file. Such information should be the file's create  date, date last saved, number of revisions the file had, time spent on the file and so forth.

I have tried to use the ls command but it doesn't give all of the information I am looking for. I believe there is a command out there that will do this.

---

### Post by Cheesemill on 2012-05-03
'ls -l' will give you the mtime (time the file was last modified).
'ls -lu' will give you the atime (time the file was last accessed).
'ls -lc' will give you the ctime (time the inode was last changed).

Bear in mind that the atime is only changed if the filesystem isn't mounted without the noatime flag.

I don't think that the rest of the information that you are after is stored anywhere.

---

### Post by JRV on 2012-05-03
And "file" will give you more information about a file, Example:```
jack@manx:~$ file /bin/bash
/bin/bash: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x6dafe33f9353cbb054b1b1f7b079545992575757, stripped

```

---

