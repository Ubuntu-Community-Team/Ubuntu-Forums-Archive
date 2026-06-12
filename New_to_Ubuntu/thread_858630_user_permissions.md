---
title: "user permissions??"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Dissident85 on 2008-07-13
Hi all, I just wanted a little help with user permissions. I have a shared machine that I need to give other users permission to execute certain programs. It doesn’t have a desktop environment installed. How would I do this?

---

### Post by kk0sse54 on 2008-07-13
Use chmod to change permission or chown to change ownership. Type ```
man chmod
``` or ```
man chown
```to find out more

---

### Post by spydon on 2008-07-13
chown [-R] newowner filenames

**-R**	- Change the permission on files that are in the subdirectories of the directory that you are currently in.
**newowner**	- The alias/username of the new owner of the file.
**filenames**	- The file that you are changing the rights to.

You might need to use sudo sometimes.

---

