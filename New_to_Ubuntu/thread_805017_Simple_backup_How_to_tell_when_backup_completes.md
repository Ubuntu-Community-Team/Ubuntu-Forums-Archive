---
title: "Simple backup: How to tell when backup completes?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Chimmer on 2008-05-23
I'm using [Simple Backup Suite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") to backup my Ubuntu data. Is there any way to tell when the backup completes?

For example, I do manual backups only to an external hard drive. Plug it in, do the backup, unplug it until next time.

The backups run fine but it never tells me when the operation is finished. I'll get a message saying it's running in the background but that's it. The only way I know it's done is when I see the hard drive activity light stop blinking.

I'm use to windows telling me something is finished. Is there an easier way in ubuntu?

Thanks!

---

### Post by quelx on 2008-05-23
I don't know of a completely elegant method, but if you open a terminal **ALT-F2** > **gnome-terminal**

then type ```
top
``` you can see the process (gzip and/or sbackupd) at the... top while the backup is running.  When it's finished they will go away.

---

### Post by Chimmer on 2008-05-23
That'll work...thanks!

---

### Post by sdennie on 2008-05-24
You could also type the following:

```

while ps ax | grep THE_PID_OF_THE_BACKUP | grep -v grep > /dev/null ; do sleep 1; done ; echo "It's finished"

```

If you take the process ID that sbackup gives you when you hit "Backup Now!", changing THE_PID_OF_THE_BACKUP to the the number it tells you, it will print "It's finished" when the backup is done.

---

### Post by Chimmer on 2008-05-24
> **vor said:**
> You could also type the following:

```

while ps ax | grep THE_PID_OF_THE_BACKUP | grep -v grep > /dev/null ; do sleep 1; done ; echo "It's finished"

```

If you take the process ID that sbackup gives you when you hit "Backup Now!", changing THE_PID_OF_THE_BACKUP to the the number it tells you, it will print "It's finished" when the backup is done.

Thanks...I'll try that one also!

---

