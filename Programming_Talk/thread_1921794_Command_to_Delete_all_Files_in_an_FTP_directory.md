---
title: "Command to Delete all Files in an FTP directory"
date: 2012-02-07
forum: Programming Talk
---

### Post by CrusaderAD on 2012-02-07
Is there an FTP command from the terminal line that can delete all files in a certain directory? I'm trying to purge a directory using a shell script.

---

### Post by Lars Noodén on 2012-02-07
I don't know about FTP, but in SFTP there is 'rm' and it works more or less like regular 'rm'

---

### Post by Rafterman414 on 2012-02-07
For removing FTP directories try rmdir

---

### Post by CrusaderAD on 2012-07-19
```
mdelete *
```

Will delete everything in the working directory.

---

