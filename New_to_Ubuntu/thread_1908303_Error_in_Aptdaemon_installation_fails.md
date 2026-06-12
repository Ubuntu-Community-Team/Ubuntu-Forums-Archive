---
title: "Error in Aptdaemon: installation fails"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by verizion on 2012-01-13
I am unable to install any new software either through software center or the terminal.
The terminal gives an error:
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

The software center gives an error:
An unhandlable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.
This error first occurred when I was trying to install java applet.

---

### Post by sanderd17 on 2012-01-13
> **verizion said:**
> I am unable to install any new software either through software center or the terminal.
The terminal gives an error:
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

First: try a reboot. If that doesn't work, can I see what permissions your lock file has?

```

ls -l /var/lib/dpkg/lock

```

---

### Post by verizion on 2012-01-16
rebooting doesn't work.
The command: ls -l /var/lib/dpkg/lock
gives the following output:-
-rw-r----- 1 root root 0 2012-01-13 14:52 /var/lib/dpkg/lock

---

### Post by sanderd17 on 2012-01-16
> **verizion said:**
> rebooting doesn't work.
The command: ls -l /var/lib/dpkg/lock
gives the following output:-
-rw-r----- 1 root root 0 2012-01-13 14:52 /var/lib/dpkg/lock

Ok, since you rebooted, there is no process still using the lock, so you can safely remove it:

```

sudo rm -f /var/lib/dpkg/lock

```

After this, you should be able to install packages again.

---

### Post by lawrencrj on 2012-02-07
I have the same problem and neither rebooting or 
using term to enter sudo rm -f etc. help.  I still get the same 
message "an unhandlable error has occurred" whenever I try to install anything.  I have been over two hours trying different solutions (some of which have worked for other people but not for me.

---

### Post by sanderd17 on 2012-02-08
> **lawrencrj said:**
> I have the same problem and neither rebooting or 
using term to enter sudo rm -f etc. help.  I still get the same 
message "an unhandlable error has occurred" whenever I try to install anything.  I have been over two hours trying different solutions (some of which have worked for other people but not for me.

do you get exactly the same error? and what does the "ls" command from my second post say?

---

