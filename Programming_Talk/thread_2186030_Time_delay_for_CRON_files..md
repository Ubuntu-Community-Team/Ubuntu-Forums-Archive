---
title: "Time delay for CRON files."
date: 2013-11-05
forum: Programming Talk
---

### Post by graphicsmanx1 on 2013-11-05
Im trying to create a bash script that will execute on some folders and files that are dropped into a shared network folder.  I thought about writing some script that will run on X files after X time but I was curious to know if the folders/files dropped to the shared folder change the created date?  How can I time the bash script to move the files after an interval of X time to allow full folder transfer across the network?

---

### Post by TheFu on 2013-11-05
Excellent.

Look into stat() and mtime.

I would run the script hourly (use @hourly inside the crontab [**man -s 5 crontab** for more]), and if the file modification time is less than 2 minutes ago, I would skip that file until the next hour ... assuming it is unmodified at least 2 min when the script runs the following hour.

The amount of time the script takes to run might be important to know too.  If this is batch processing long running tasks, then you may want to queue those batch tasks using **TaskSpooler**.

The ABSG [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) might be helpful too.

I hope these leads help someone.

---

### Post by ian-weisser on 2013-11-05
Perhaps the *inoticoming* package:

```
Description-en: trigger actions when files hit an incoming directory
 inoticoming is a daemon to watch a directory with Linux's inotify
 framework and trigger actions once files with specific names are placed
 in there.
 .
 For example it can be used to wait for .changes files uploaded
 into a directory and call reprepro to put them into your repository.
```

Or the *gamin* package:

```
Description-en: trigger actions when files hit an incoming directory
 inoticoming is a daemon to watch a directory with Linux's inotify
 framework and trigger actions once files with specific names are placed
 in there.
 .
 For example it can be used to wait for .changes files uploaded
 into a directory and call reprepro to put them into your repository.
```

The kernel's inotify function tracks changes to the filesystem. You can use it to monitor a folder and watch for changes.
You can find a lot more with the command **apt-cache search inotify**, including python bindings, command-line bindings, cron-like tools, etc.

---

### Post by graphicsmanx1 on 2013-11-05
can you still distinguish between a created time and modified time if you are moving files/folders across a network?

---

### Post by ofnuts on 2013-11-05
There is no "creation time" in unix file systems (some file systems support a "birth time"). The "c" time is a "change" time (any change to the inode (mv/chmod/chown...)), while the "m" time that deals with change to the contents. But oif course if you transfer a file to a new file system, its change time will always be at least as recent as when it appeared on that file system, while the modification time can still be years in the past.

---

