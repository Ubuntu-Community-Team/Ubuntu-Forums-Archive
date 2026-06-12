---
title: "I screwed up my permissions...."
date: 2008-04-29
forum: New to Ubuntu
---

### Post by mashamoo on 2008-04-29
Hi,

I was mucking about with some include files and i have somehow managed to muck up all my permissions! when I do an ls -la on /usr/include I get:
.
.
.
.

?--------- ? ? ? ?                ? /usr/include/wait.h
?--------- ? ? ? ?                ? /usr/include/wand
?--------- ? ? ? ?                ? /usr/include/wchar.h
?--------- ? ? ? ?                ? /usr/include/wctype.h
?--------- ? ? ? ?                ? /usr/include/wordexp.h
?--------- ? ? ? ?                ? /usr/include/X11
?--------- ? ? ? ?                ? /usr/include/xlocale.h
?--------- ? ? ? ?                ? /usr/include/zconf.h
?--------- ? ? ? ?                ? /usr/include/zlibdefs.h
?--------- ? ? ? ?                ? /usr/include/zlib.h
(not all shown)

Each file is highlightered red as well, probably indicating an unknown permission or something.
I tried chmod 777 /usr/include just to try and set the permissions on one of these h-files and it doesn't do jack.

Could someone please tell me either how to restore my permissions or another fix?

---

### Post by Joeb454 on 2008-04-29
try doing sudo chmod instead.

It might work :)

---

### Post by Sjovan on 2008-04-29
sudo chmod -R a=rwx /usr/include <--- gives every one read, wright and execute.

---

### Post by hyper_ch on 2008-04-29
> **Sjovan said:**
> sudo chmod -R a=rwx /usr/include <--- gives every one read, wright and execute.

Not a good thing in the /usr folder

---

### Post by scorp123 on 2008-04-29
> **Sjovan said:**
> sudo chmod -R a=rwx /usr/include <--- gives every one read, wright and execute. That was bad advice! Now everything and everyone can screw up his system!

---

### Post by mashamoo on 2008-04-29
Nah I was doing sudo chmod 777 but didn't work. Although if i manually set the permission for the directory ( /usr/include/. ) that seemed to fix it... kind of.

Ive fixed most of it now. I am trying to recursively set all permissions within a directory to rw r r.

The command I am trying to execute is this:

sudo chmod -R 644 /usr/include/TK

But this keeps setting all the permissions to ??? within the TK directory. 

Any solution? Its not a big deal cos there aren't that many files, i can do it manually. But still... I thought this would work?

---

### Post by scorp123 on 2008-04-29
> **mashamoo said:**
>  I was mucking about with some include files and i have somehow managed to muck up all my permissions!  You just learned an important lesson ;) ... Don't mess with file permissions unless you perfectly know what you're doing!

> **mashamoo said:**
>  when I do an ls -la on /usr/include I get:
?--------- ? ? ? ?                ? /usr/include/wait.h
?--------- ? ? ? ?                ? /usr/include/wand
?--------- ? ? ? ?                ? /usr/include/wchar.h
?--------- ? ? ? ?                ? /usr/include/wctype.h
?--------- ? ? ? ?                ? /usr/include/wordexp.h
?--------- ? ? ? ?                ? /usr/include/X11
?--------- ? ? ? ?                ? /usr/include/xlocale.h
?--------- ? ? ? ?                ? /usr/include/zconf.h
?--------- ? ? ? ?                ? /usr/include/zlibdefs.h
?--------- ? ? ? ?                ? /usr/include/zlib.h
(not all shown)  OK, let's try and fix this mess. Please follow these shell commands -- you will have to execute those commands as "root" so please make sure you don't mistype anything, OK?
```
sudo su -
cd /usr/include
find . -type d -exec chmod 755 {} \;
find . -type f -exec chmod 644 {} \;
chown -R root:root /usr/include/*
exit 
``` That should restore the permissions as they should be.

---

