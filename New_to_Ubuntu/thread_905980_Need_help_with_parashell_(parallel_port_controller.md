---
title: "Need help with parashell (parallel port controller)"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by chriscross93 on 2008-08-30
I have a program (parashell) which allows me to directly control my parallel port.  My problem is that it seems ubuntu wont allow it access to may parallel port.  This is what happens.....

```
zach@ZACHSROOM:~$ parashell
USAGE: parashell [PORT] [DATA]
 ie., parashell 0x378 128
zach@ZACHSROOM:~$ parashell 0x378 1
ERROR: Can't gain access to port 378
zach@ZACHSROOM:~$ sudo parashell 0x378
[sudo] password for zach: 
USAGE: parashell [PORT] [DATA]
 ie., parashell 0x378 128
zach@ZACHSROOM:~$ sudo parashell 0x378 1
ERROR: Can't gain access to port 378
zach@ZACHSROOM:~$ 
```

As you can see, even running it as root doesn't seem to help.

-Zach

---

### Post by gmxgeek on 2008-08-30
did you write this yourself, or is it available online. If online, can you provide a link to the main website?

Also, check that port number, as i don't know if that is accurate. (Not much experience with parallel ports)


also, this might help you out
[http://ubuntuforums.org/showthread.php?t=905637](http://ubuntuforums.org/showthread.php?t=905637)

---

### Post by kalross on 2012-02-02
Just add user to the group that owns the port.

Check group ownership:

sudo ls -l /dev/parport0

Mine is root:lp

Say your username is user:

sudo usermod -a -G lp user

---

### Post by overdrank on 2012-02-02
Thanks for you input. Back to sleep thread. Thread closed.

---

