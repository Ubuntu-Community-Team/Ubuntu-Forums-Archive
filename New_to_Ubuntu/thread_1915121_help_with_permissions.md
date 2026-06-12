---
title: "help with permissions"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by Submicro on 2012-01-25
Hello

Can someone tell me how to change permissions on folders and files recursively using a terminal??

SubMicro

---

### Post by lisati on 2012-01-25
*Thread moved to **Absolute Beginner Talk**.*

---

### Post by mwd5650 on 2012-01-25
chmod -R will change permissions
chown -R will change ownership
chgrp -R will change group
 
 
For more info you can: 
 
man chmod
man chown
man chgrp 
 
 
Matt

---

### Post by CharlesA on 2012-01-25
> **Submicro said:**
> Hello

Can someone tell me how to change permissions on folders and files recursively using a terminal??

SubMicro
Which folder are you trying to change permissions on? Normally you would use commands that do things recursively with care.

---

### Post by Submicro on 2012-01-25
Thanks guys

I'm changing permissions to An eagle folder.

---

### Post by CharlesA on 2012-01-25
As long as you aren't changing the permissions on any of the system folders, you should be fine. :)

---

### Post by Morbius1 on 2012-01-25
Just be careful how you use "chmod -R"

If you use the octal mode, for example:
```
chmod -R 0777 /home/morbius/folder
```All folders will be executable ( which you must have or else you won't be able to open them ) but also all your files will be marked as executable which you do not want to do.

If you use this method however:
```
chmod -R a+rwX /home/morbius/folder
```All folders will be executable but all files will not unless they were marked as executable to begin with. That's what the big "X" does.

---

### Post by CharlesA on 2012-01-25
> **Morbius1 said:**
> 
If you use this method however:
```
chmod -R a+rwX /home/morbius/folder
```All folders will be executable but all files will not unless they were marked as executable to begin with. That's what the big "X" does.

I didn't know that. Thanks! :)

---

