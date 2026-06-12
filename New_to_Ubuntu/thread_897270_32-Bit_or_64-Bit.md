---
title: "32-Bit or 64-Bit"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Generic Bond on 2008-08-22
I know this is probably stupid, but how do you know whether you are a 32-Bit or a 64-Bit user?

---

### Post by Lvcoyote on 2008-08-22
By the version you installed, it was either a 64 bit or 32 bit version.  If you downloaded it then post a link to what you downloaded, if it's a Ubuntu CD that you have, just look at the CD.

---

### Post by k8bopibu on 2008-08-22
Run ```
uname -a
``` in a terminal. You should see x86_64 if you are a 64-bit user. if not then you will see something such as i386, i686 or such. Refer to this thread for more: [894044](http://ubuntuforums.org/showthread.php?t=894044)

~k8

---

### Post by ilrudie on 2008-08-22
The specific command is ```
uname -m
```uname -a also works its just got a lot more info in it.

---

