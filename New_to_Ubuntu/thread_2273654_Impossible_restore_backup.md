---
title: "Impossible restore backup"
date: 2015-04-14
forum: New to Ubuntu
---

### Post by isthevene on 2015-04-14
Hello everybody ):Pfirst of all sorry for my bad english!

Unfortunately today, due to a blackout, the touchpad and the wifi of my pc stopped working (it couldn't find the hardware).
So I decided to format the pc and reinstall ubuntu 14.04 after a backup made with the application system.
After the installation of ubuntu I start to restore the backup, and here's the surprise: restore failed with unknown error


```
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1494, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1488, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1337, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1426, in do_backup
    list_current(col_stats)
  File "/usr/bin/duplicity", line 675, in list_current
    user_info = u"%s %s" % (dup_time.timetopretty(path.getmtime()),
  File "/usr/lib/python2.7/dist-packages/duplicity/dup_time.py", line 148, in timetopretty
    return time.asctime(time.localtime(timeinseconds))
ValueError: timestamp out of range for platform time_t
```

help me please :(

thank you all

---

### Post by cariboo on 2015-04-14
You may have gone a bit to far, as you probably repaired the problem by starting in recovery mode, then running:

```
fsck  /dev/sdX
```

where /dev/sdX = the partition you have Ubuntu installed on.

As far as restoring from backup, the log output does tell you what the problem is:

```
File "/usr/lib/python2.7/dist-packages/duplicity/dup_time.py", line 148, in timetopretty
    return time.asctime(time.localtime(timeinseconds))
ValueError: timestamp out of range for platform time_t
```

There seems to be a problem with the date of the duplicity package, in other words the problem is with the program you used to create the backup, and there may be no way to recover from the error.

---

### Post by isthevene on 2015-04-15
> **cariboo907 said:**
> 
There seems to be a problem with the date of the duplicity package, in other words the problem is with the program you used to create the backup, and there may be no way to recover from the error.

Is there any other program which could restore backup files? I hope there's one way to solve my problem :(

---

### Post by cariboo on 2015-04-15
What format does duplicity use when creating the backup files, eg: tar.gz, or some other compression format.

---

### Post by isthevene on 2015-04-16
The format is .gpg

---

