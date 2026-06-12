---
title: "[c] Directory traversal"
date: 2011-08-20
forum: Programming Talk
---

### Post by dawwin on 2011-08-20
I'm writing simple FTP server and I've got a question about directory traversal. 
When user sends a directory or file path I check if this contains string "..". An error is returned when it's found. If not then I create full path like
```
[shared directory] + "/" + [directory from user]
```where [shared directory] is for example "/home/user/ftp". After that I use stat() to determine, if path exists and check if this is file or directory.
Is there anything else what I need to do to make this secure?

---

### Post by Bachstelze on 2011-08-20
If what you want is prevent the user from going out of /home/user/ftp, why not use chroot()?

---

### Post by dawwin on 2011-08-20
I need to have access to some configuration files which are not placed in /home/user/ftp

---

### Post by ofnuts on 2011-08-20
> **dawwin said:**
> I need to have access to some configuration files which are not placed in /home/user/ftpNormally, on connection, you spawn another process running with th userid of the connected user and possibly chrooted. The listener parent has access to the config file anyway. The child can be passed the relevant config parameters as command arguments.

---

