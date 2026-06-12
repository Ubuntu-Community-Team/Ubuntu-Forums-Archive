---
title: "Shell scripting question"
date: 2009-08-18
forum: Programming Talk
---

### Post by gt2nv on 2009-08-18
**FIXED**

So right now i am trying to write a script for my work, and i am kind of a beginner at it.  I am writing this shell script to compare some things in /dev/.  What i am wanting the script to do is cd /dev/; do a ls -al and then grep for the cdrom.  After this i want it to compare the link that is set to cdrom to let me know if it is for example the hda, hdb, sda, sdb or etc.  Here is what i have so far.  

#!/bin/sh

cd /dev
ls -al /dev/ | grep -F "cdrom "
if [ "cdrom " = "/dev/hda" ];
        then echo "true"
        else echo "false"
fi

I was just going to write a bunch of arguments like this to figure out what they are on.  After i get so far with this i am going to have it write a string in the fstab, but i am not that far yet.

Can you guys help me out?

---

### Post by cdenley on 2009-08-18
How about this?
```

#!/bin/sh
DRIVE="/dev/hda"
ls -l /dev|grep -qs "cdrom -> $DRIVE\$"
if [ $? -eq 0 ]
then
        echo true
else
        echo false
fi

```

---

