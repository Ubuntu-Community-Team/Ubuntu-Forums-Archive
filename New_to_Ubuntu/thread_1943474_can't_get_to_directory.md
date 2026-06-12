---
title: "can't get to directory?"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by mashavecher on 2012-03-19
Hi.
To install software I need to run script in terminal. Manual says Go to the directory where files are. I've downloaded all the files and placed them to folder (/home/user/documents/ARB) When I type cd ARB, no such file or directory comes out. What am I doing wrong? And how do I get there?
Thank's

---

### Post by TeoBigusGeekus on 2012-03-19
Type the whole path, ie:
```
cd /home/user/Documents/ARB
```

---

### Post by cortman on 2012-03-19
> **mashavecher said:**
> Hi.
To install software I need to run script in terminal. Manual says Go to the directory where files are. I've downloaded all the files and placed them to folder (/home/user/documents/ARB) When I type cd ARB, no such file or directory comes out. What am I doing wrong? And how do I get there?
Thank's

The problem is your default shell directory is /home/user, and you have them one layer deeper. The correct command would be

```
cd Documents/ARB
```

---

### Post by mashavecher on 2012-03-19
Thank's

---

