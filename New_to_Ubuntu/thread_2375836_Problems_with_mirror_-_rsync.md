---
title: "Problems with mirror - rsync"
date: 2017-10-27
forum: New to Ubuntu
---

### Post by sed_faster on 2017-10-27
I have this script:
```

#!/bin/bash


today=backup_$(date +%d-%m-%y_%H-%M-%S)
# create a folder inside server git
ssh user@142.191.51.41 mkdir /media/drive/$today/
# create a var with path folder inside server
destiny=user@142.191.51.41:/media/drive/$today


# mirror Documents
rsync -av /home/user/Documents/ $destiny/Documents/
# mirror VirtualBox\ VMs
rsync -av /home/user/VirtualBox\ VMs/ $destiny/VirtualBox\ VMs/
# mirror Downloads
rsync -av /home/user/Downloads/ $destiny/Downloads/

```


Happen two things weirds:
1-Don't created right  the folder "VirtualBox VMs". Maybe this happen because the name of the folder has spaces. How can I fix this, to get handle folder names with spaces.
2-On directory copy (mirror), which is was created on server, missing files. When I did right button on this three folders the result of report it was, for example, 1000 files. If I did the same task on backup folders on my server the counting is was 340 files. It is missing 660 files. The least but not the last, the space which all 3 folders occupy it is the same, both on the server and on the client.


How can I handle this?
Thanks

---

### Post by TheFu on 2017-10-28
IME, rsync gets confused by huge files - anything over 2G was my experience.  I tried to backup VMs doing something similar myself, but found rsync too WAY-TO-LONG compared to treating each VM like a physical server for backups.  

In the end, I switched to rdiff-backup and reduced system backups from 45-90 minutes for each system down to 2-7 minutes for each.  rdiff-backup has a command that is very, very, similar to rsync.  It uses ssh, just like rsync.  Plus, versioning is built-into rdiff-backup, so you don't need to use date-stamps in your backups. That happens automatically.

As for handling spaces in paths - use quoting.  In the future, it is just easier to always use - or _ characters instead of spacing to make your scripts easier. Quoting is basic scripting technique. Search "ABSG linux" to learn more.
```
rsync -av "/home/user/VirtualBox VMs/" "$destiny/VirtualBox VMs/"

```

```
$ rdiff-backup --exclude-special-files  {source} {target}

``` is the normal way to backup a system.  Either the source or the target can be remote - specified just like the rsync.  Try it with /etc/ - that's a tiny directory. You'll see how awesome rdiff-backup is.  There's nothing proprietary about the backup files.  The most recent backup is just like an rsync (a mirror) and older backups are diffs.gz.  It is highly efficient both for network transfers and disk storage, so the backups are much quicker.  Plus, they are versioned, automatically.  Nice!

Is your "media drive" using a Linux file system?  If not, then half of the most important backup information would be lost - permissions and ownership.  Grabbing a VDI file, this isn't too bad, but if you switch to performing backups from "inside" the VM, it will be very, very, bad and effectively make the backups next to useless, except as reference for later.

---

