---
title: "Bash System BackUpScript [opinions please, not a question]"
date: 2010-05-20
forum: Programming Talk
---

### Post by CSInDevelopment on 2010-05-20
I just wondered what everyone thought of my backup script ?
(its my second version of it and I am interested if there are any ways you think I could improve it)
keep in mind I dont need my config files in home backed up and the data I work on is on 2 other partitions leaving home as a mere scratch-pad.
```

#!/usr/bin/bash
# Script for backing up the system to a specified position
directory_list=`ls -1 /`
# loop all directories in /
for directory in $directory_list
do
    case $directory in
    
    "cdrom")
        ;;

    "home")
        ;;

    "dev")
        ;;
    
    "media")
        ;;

    "mnt")
        ;;

    "tmp")
        ;;

    *)
        echo "starting directory" $directory
        sudo tar -cvf $1$directory.tar /$directory
        sudo gzip $1$directory.tar
        echo $directory " complete"
        ;;
    esac
done
echo "Back up complete, remember to perform this after every update or software installation"

```

---

### Post by yaaarrrgg on 2010-05-20
Looks nice!  You could also drop the files into a folder:

    /backups/

and hash by

    hash=$(date '+%Y-%m-%d')
    mkdir /backups/$hash

That would give you multiple snapshots.  Then you could set a cron to run this.

---

