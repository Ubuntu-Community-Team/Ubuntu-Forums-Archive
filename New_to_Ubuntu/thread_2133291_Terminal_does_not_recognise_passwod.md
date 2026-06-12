---
title: "Terminal does not recognise passwod"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by spoonsey on 2013-04-07
When I try to enter my passord on the terminal (ubuntu 12.10) at third attempt each time I get te following error. I wish to run a command to update drivers for a dell inspiron 1501 for wifi, but when I try to run the command the terminal will not accept my password. It returns the following error

[sudo] password for joe:
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
joe@joe-Inspiron-1501:~$ 

As far as I am aware there is no other process running.

Any help would be greatly appreciated.

---

### Post by wildmanne39 on 2013-04-07
The password is being accepted it is the install command that is failing

Do you have more then one install program running like software center and the terminal? that usually means to close one, if that does not work reboot and then try again,
Thanks

---

### Post by Impavidus on 2013-04-07
1: When people complain the terminal doesn't accept their password it usually means they get confused because the terminal doesn't show any visual conformation that a password is being entered. There are no letters, not even ***. Still, input of the password works. Just type it and hit enter.
2: When you don't give the correct password sudo will give you an error message after the third try:```
sudo: 3 incorrect password attempts
```I don't know of any other error that occurs after every three atempts.
3: The error you show indicates sudo accepted your password but the package manager you launched with sudo (you tried a package manager, didn't you?) couldn't get a lock, as Wild Man indicated. The error you get when you try to run that command without root privileges is different.

---

### Post by agent-squirrel on 2013-04-08
The easiest way around a package manager lock is just to reboot and rerun your command.

---

### Post by siddharth007 on 2013-04-08
I second that.However another workaround would be forcing off the lock by manually removing the "lock" files.Use this command
```
*sudo rm /var/lib/apt/lists/lock*
```

You may also need to delete the lock file in the cache directory.For this,use this command
```
*sudo rm /var/cache/apt/archives/lock*
```

Then force package re-configuration
```
dpkg --configure -a
```

Note there are two dashes(--) before configure.

---

### Post by newb85 on 2013-04-08
> **siddharth007 said:**
> I second that.However another workaround would be forcing off the lock by manually removing the "lock" files.

Yes, but remember, that lock was built into the system for a reason.  If some other package management operation is running, it's probably not a good idea to override the lock and run the one you want simultaneously.  The first thing I would do is check for other instances (Software Center, Update Manager, Synaptic, other terminal apt-gets, etc.), and then I would try rebooting.

---

