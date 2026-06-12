---
title: "Backup Script"
date: 2006-06-21
forum: Programming Talk
---

### Post by Permafrost91 on 2006-06-21
I'm a mere beginner at scripts but basically I would like to run a simple script every week via a crontab that
(1) mounts a local partition
(2) rsyncs one directory with the newly mounted partition to make a backup
(3) unmounts the local partition

First off, I'm also backing up to a remote disk but this is a low traffic webserver and I've found it to be helpful to just keep a copy on the machine locally for quick backups or recoveries in case I reinstall the machine. At any rate ...

The script currently looks like this basically:
```
#!/bin/bash
sudo mount /dev/hda6 /backup
sudo rsync -az --delete /server/ /backup
sudo umount /backup

```

The script does what I want it to do as it stands but none of these commands work without sudo ... so how can I run this script as a crontab without using sudo because I won't be able to supply the sudo password?

Thanks!

---

### Post by IYY on 2006-06-21
Add it to /etc/crontab and set the user field to 'root'.

---

### Post by Permafrost91 on 2006-06-21
sweet thanks! that does it

---

