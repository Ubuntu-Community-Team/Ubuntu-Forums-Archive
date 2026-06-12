---
title: "Error with ssh/rsync"
date: 2016-04-22
forum: New to Ubuntu
---

### Post by paulo-castillo on 2016-04-22
Hi, i´m new with ubuntu, and i'm trying to make backups with rsync and windows with cygwin and i've the following errors:

```
user@equip:~$ rsync -rv "/cygdrive/c/test2" \ 'user@equip:/home/user/test/'                   user@equip´s password:
Permission denied, please try again.
  user@equip´s password:
Permission denied, please try again.
  user@equip´s password:
Permission denied (publickey,password).
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(605) [sender=3.0.9]
user@equip´s:~$

```

In the part of password, i put the correct password and i can´t access with that backup test.

i´m doing with the followed link:

[http://sleepyhead.de/howto/?href=rsync](http://sleepyhead.de/howto/?href=rsync)

and the part of test i´ve the error 

Thanks a lot!

---

### Post by Habitual on 2016-04-22
It appears to me you are rsync'ing from user@equip to user@equip

Try
```
rsync -rv /cygdrive/c/test2 user@equip:/home/user/test/
```

Have a look at [http://rsync.net/resources/howto/rsync.html](http://rsync.net/resources/howto/rsync.html)

---

