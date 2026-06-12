---
title: "[SOLVED] whata is a t permission?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-06-25
If I type ls -l / to see what is in my / directory, I get the following line in my output:

drwxrwxrwt  14 root root  4096 2008-06-25 20:23 tmp

I know what drwxrwx means.  But the last 3 letters of the first output on the line are "rwt".  What is the t for?

---

### Post by iaculallad on 2008-06-25
> **raymondvillain said:**
> If I type ls -l / to see what is in my / directory, I get the following line in my output:

drwxrwxrwt  14 root root  4096 2008-06-25 20:23 tmp

I know what drwxrwx means.  But the last 3 letters of the first output on the line are "rwt".  What is the t for?

The "t" character in your permission indicates that only the user (and the root) that has created the file inside of /tmp folder can delete/modify that specific file.

---

