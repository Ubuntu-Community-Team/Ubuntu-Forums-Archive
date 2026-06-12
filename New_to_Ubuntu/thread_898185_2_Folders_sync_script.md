---
title: "2 Folders sync script"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by shodan on 2008-08-23
Hi,
I want to have my home folder synced with folder on my other disk.
I want it to be exact image.
I installed rsync and put script into cron.daily
```

#!/bin/bash
rsync -aE --ignore-existing --delete /home/shodan/* /media/disk0/SYNC
```

I'm not sure about --delete option
Is above script ok?


From documentation:
> --delete
    This tells rsync to delete extraneous files from the receiving side (ones that aren't on the sending side), but only for the directories that are being synchronized. You must have asked rsync to send the whole directory (e.g. "dir" or "dir/") without using a wildcard for the directory's contents (e.g. "dir/*") since the wildcard is expanded by the shell and rsync thus gets a request to transfer individual files, not the files' parent directory. Files that are excluded from the transfer are also excluded from being deleted unless you use the --delete-excluded option or mark the rules as only matching on the sending side (see the include/exclude modifiers in the FILTER RULES section).

---

### Post by livestockPimp on 2008-08-23
all the delete option will do is remove the data from the destination folder if the source folder no longer has it.

ie; if you delete file.jpg from your home dir when it syncs it will remove it from the backup folder also.

---

### Post by shodan on 2008-08-23
Great, thats what i exactly wanted:)

---

### Post by dirtyhabanero on 2011-06-07
Holy crap...that's awesome! 

Anyone run into any problems using this script? Over samba/ftp connection?

---

