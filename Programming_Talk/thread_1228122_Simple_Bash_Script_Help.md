---
title: "Simple Bash Script Help"
date: 2009-07-31
forum: Programming Talk
---

### Post by bfrosty on 2009-07-31
Hello,

I produced the following script to firstly check whether two drives are mounted and if so, synchronize them.

Today I got home and discovered that drive1 directory was empty and my drive2 (mirror) had synchronized with it, deleting all the content on the mirror drive. I remounted drive1 and the file contents were still there thankfully.

I'm hoping somebody can advise me on how I can improve my condition to ensure that this doesn't happen again... I thought my check was pretty consistent. How could I check whether the directories are non-empty also? I've tried a few methods from google, but I just can't get it to work.

```

#!/bin/bash

# If both external drives are mounted
if ((grep -q '/media/external' /etc/mtab) && (grep -q 'media/mirror' /etc/mtab)); then

    # List files to wake up drives
    cd /media/external
    ls
    cd /media/mirror
    ls

    # Syncronize external drive to mirror drive
    sudo rsync -av --progress --delete --exclude .Trash* /media/external/ /media/mirror/

else
    exit 1
fi

```

Thanks!!!

---

### Post by slakkie on 2009-07-31
```

function check_empty_dir() {
    local dir=shift
    local found=$(ls -1 $dir)
    if [ -n "$found" ] ; 
        return 1
    else
        return 0
    fi
}

check_empty_dir /path/to/dir
if [ $? -eq 0 ] ; then
    # rsync 
fi

```

---

