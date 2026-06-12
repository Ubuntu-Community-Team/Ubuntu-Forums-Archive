---
title: "[SOLVED] How do i check if a package manager is running with BASH"
date: 2008-01-18
forum: Programming Talk
---

### Post by oodlesOfmoodles on 2008-01-18
Hey!

I'm writing a script that will automatically do some things for the user. I want, at one point, for the script to install VLC for DVD playback. How do I check to see if a package manger is running so I can create a prompt that tells the user to close out of synaptic or wait until the update-manager is done working.

How would I go about doing this?


Thanks!

---

### Post by SOULRiDER on 2008-01-18
You could check if theres a lock.

---

### Post by oodlesOfmoodles on 2008-01-18
Yea that's what I was thinking, but how do I do that?

---

### Post by kevykev on 2008-01-18
Well the lock file is /var/lib/dpkg/lock. In c you could try to open the file with:

```

fd = open ("/var/lib/dpkg/lock", O_RDWR | O_CREAT | O_TRUNC, 0640);
if (fd == -1) {
  // cant get lock
}
// lock the file .. do work

// unlock and close the file

```

in bash you might be able to use lsof to see if the file is open

```

if lsof /var/lib/dpkg/lock >> /dev/null; then
  # file is locked
  exit 1
fi

```

Not sure about this tho

---

### Post by Keith Hedger on 2008-01-18
how about ```
top -bn1| grep apt
``` any output will show that apt or synaptic is runing.

---

### Post by stroyan on 2008-01-18
Strace of synaptic shows that /var/lib/dpkg/lock is used with a lockf (or fcntl F_SETLK) type of lock.
Bash doesn't have any direct way to test a lockf lock.  You could use a bit of python to test for the lock.  Here is a quick first try-```
#!/bin/bash
python << END
import struct, fcntl, os, sys
f = open("/var/lib/dpkg/lock", 'w')
try:
    fcntl.lockf(f, fcntl.LOCK_EX|fcntl.LOCK_NB)
except IOError:
    sys.exit(1)
sys.exit(0)
END
echo $?
``` You might want  to first test for uid equal to root.  Otherwise the open will fail.  That should have a different user message.

---

### Post by oodlesOfmoodles on 2008-01-18
I just tested kevykev's suggestion and it works perfectly (though i had to add 'sudo' before the 'lsof').

Thanks for all your help! I love this forum.

---

### Post by Thund3rstruck on 2008-01-19
If the following returns an integer greater than 1 then synaptic is running

```

ps aux | grep -c synaptic

```

---

### Post by oodlesOfmoodles on 2008-01-19
can you explain what that command does? that would be awesome!


thanks for your help

---

### Post by stroyan on 2008-01-19
```
ps aux | grep -c synaptic
``` is running ps to print all user commands and their arguments.  The a option lists all users.
The u option adds more (unnecessary) fields of information.
The x option includes processes that don't have a controlling terminal.

The output of ps is piped to grep -c which counts the number of lines that contain the string 'synaptic'.
That number is almost always at least one because the grep process itself contains the string in its arguments as printed by ps.  
But sometimes grep is not started by the time that ps is done running.
That makes the results inconsistent.

If you really want to use searching for a synaptic process then you would be better served  by```
pgrep -c synaptic
```The pgrep command looks at only the process name and not the arguments passed to a process.
That avoid the inconsistent results that grep of full ps output produces.
And it uses less resources that piping ps output through grep.

But checking for just synaptic is not really reliable since the dpkg lock can be held by other programs such as dpkg, apt-get, or aptitude.

---

### Post by oodlesOfmoodles on 2008-01-23
Thanks for your help and time.
The explanations of the commands really help.

Thanks again!

---

