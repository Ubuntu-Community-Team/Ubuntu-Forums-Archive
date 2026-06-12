---
title: "Using root"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Benbow on 2008-07-13
I have installed Cinelerra and when I ran it for the first time it told me that one of my processes was "low". It told me to run this -
echo"0x7fffffff">/proc/sys/kernel/shmmax -
as root. I have tried sudo without success. How do I carry out this operation?

---

### Post by Master Chief on 2008-07-13
Try:

```
su
```

Enter password and type

```
exit
```

when you're done.

---

### Post by spiderbatdad on 2008-07-13
su requires disabling the lock on the root account...a bad idea. Also su by itself does nothing. It simply says switch user with no user specified. su sudo would do what the previous post suggests, but you don't want to do that.

To create a root session for your current login:
```
sudo -i
```then enter your password. When you close the terminal, the session is over.

---

### Post by Benbow on 2008-07-13
su + password when requested fails with su: Authentication failure

Any other ideas?

---

### Post by The Cog on 2008-07-13
Try this:
> sudo -i
echo"0x7fffffff">/proc/sys/kernel/shmmax -

---

### Post by jakwriter on 2009-05-14
I'm having the same problem.  I found install directions here

[]("//http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5377288")

sudo -i gets me root, but then

```
jack@GeneralHQ:~$ sudo -i
root@GeneralHQ:~# echo"0x7fffffff">/proc/sys/kernel/shmmax - 
-bash: echo0x7fffffff: command not found

```

The overall problem is that Cinelerra needs more memory correct?  I've followed the directions from the above website, but something isn't working.  I'm running Hardy and those directions are for Gutsy.  Any tips on adjustments that need to be made?

Thanks

---

### Post by NightwishFan on 2009-05-14
I think you need to add a space after 'echo'.

---

### Post by jakwriter on 2009-05-14
It's always something, eh?  The space did it, Cinelerra up and running.  Thank you very much.

---

### Post by wizard10000 on 2009-05-14
> **spiderbatdad said:**
> su requires disabling the lock on the root account...a bad idea. Also su by itself does nothing. It simply says switch user with no user specified.

su defaults to root.

---

### Post by spiderbatdad on 2009-05-14
Only if you have unlocked the root account. This is not supported. Also this thread is quite old to  be ressurected.

---

