---
title: "Get error message installing wine"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by poetellington305 on 2012-08-28
GET ERROR MESSAGE ON INSTALLING WINE:

1. Did: sudo  add-apt-repository ppa:ubuntu-wine/ppa
 ...that went fine.
2.Did: sudo apt-get update
 ...get error message: "E: unable to lock adminsistration directory(/var/lib/dpkg),is another process using it."

3. I don't know if this helps: but I downloaded "valgrind-3.7.0", 2 days ago.

Hoping you can help me, thanks in advance...
bye...

---

### Post by PhantomTurtle on 2012-08-28
Were you installing anything while trying to do sudo apt-get update? Only one thing can be done at a time with apt. If that is not the case then try this,
```
ps -e | grep apt
```
in terminal.
That will show you what processes are using apt. Next you want to kill those processes using the command,

```
sudo kill 1245
```

The number I put in, 1245 will be replaced with the number that the previous command outputted. Hope that helps.

EDIT: Also make sure you don't have synaptic or the Ubuntu Software Center open because those are the programs that use apt.

---

