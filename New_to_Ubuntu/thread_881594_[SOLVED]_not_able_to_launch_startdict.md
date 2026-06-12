---
title: "[SOLVED] not able to launch startdict"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by imgkg on 2008-08-06
hi guys , i have installed startdict  but i am not able to launch it i tried by terminal method it gives a error
 ```
~$ stardict

** ERROR **: Can not open config file: /home/user/.stardict/stardict.cfg, reason: File is empty

aborting...
Aborted
 

```

any ideas what could be problem

---

### Post by nick_h on 2008-08-06
Delete the file.  It will create a new one for you.

From your home directory type:
```
rm .stardict/stardict.cfg
```

---

### Post by krebscycle on 2010-01-05
It worked. I had the same problem, and nick_h's solution has solved the issue.

---

### Post by Sovello on 2010-01-13
Waw... what a simple and appropriate soln. it worked for my karmic distro too.
thanks a lot...
karibu:eek:

---

