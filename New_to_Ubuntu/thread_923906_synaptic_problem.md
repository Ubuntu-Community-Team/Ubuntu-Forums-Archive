---
title: "synaptic problem"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by nynoah on 2008-09-18
Ok I have a snynaptic problem.  Its the usual, can not get a lock.  So I typed in the Sudo dpkg --configure -a and this is what I got back.  Never seen this........huh.

[I]noah@noah-desktop:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
noah@noah-desktop:~$ [/I]

Any Ideas?

---

### Post by mc4100 on 2008-09-18
> **nynoah said:**
> Ok I have a snynaptic problem.  Its the usual, can not get a lock.  So I typed in the Sudo dpkg --configure -a and this is what I got back.  Never seen this........huh.

[I]noah@noah-desktop:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
noah@noah-desktop:~$ [/I]

Any Ideas?

It means there is another application (probably synaptic) that is running, you need to close that program, run the command, and then you can return to using it.
Edit: Oops, are you saying there is a stale lock (ie., no other programs running)?

---

### Post by oldsoundguy on 2008-09-18
you can't re-configure from the terminal if the updater or synaptic is open.  Sometimes, re-booting it the choice before you run the configure command as synaptic may be locked open and be attempting to update on it's own.

---

### Post by iaculallad on 2008-09-18
On your terminal, find the process ID:

```
ps ax | grep dpkg
ps ax | grep synaptic
```

and kill it:

```
sudo kill -9 PID
```

You could also try:

```
sudo killall synaptic
```

---

### Post by nynoah on 2008-09-18
OK I rebooted and it solved itself.........well so far as I can see.

---

