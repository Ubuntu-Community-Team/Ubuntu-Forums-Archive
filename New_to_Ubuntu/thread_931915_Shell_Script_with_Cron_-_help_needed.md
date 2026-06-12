---
title: "Shell Script with Cron - help needed"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Mindzai on 2008-09-27
Hi

I'm trying to write my first shell script. The purpose is to check a folder for new files, determine if they are RAR archives, if they are, check if they have already been extracted by the script, extract them if not, and finally move them to a new location.

The script I have written is as follows:

```
#!/bin/sh

for file in $(find /media/disk/incoming/finished/ -iregex '.*\.\(rar\|001\)')
do
    echo -n "checking file ${file##*/}..."
    onblacklist=`grep -c $file /media/disk/incoming/unpacking/blacklist`
    if [ $onblacklist -ne 0 ]; then
        echo "already unpacked"
    else
        echo "not unpacked yet"
        echo -n "unpacking..."
        unrar e -inul -o- $file
        echo "done!"
        echo -n "adding to blacklist..."
        echo $file >> /media/disk/incoming/unpacking/blacklist
        echo "done!"
    fi
done
ls -rt /media/disk/incoming/unpacking | grep -v '\(^unpack_torrents.sh$\|^blacklist$\|^cron.log$\)' | xargs -I{} mv {} /media/disk/incoming/unpacked

```

I have 2 questions relating to this.

1. When I run this script manually, it works as I expect, ie files are unpacked into the same directory as the script (/media/disk/incoming/unpacking/) and then moved to the specified location (/media/disk/incoming/unpacked/). However, when I run this script using cron, all files get placed into my home directory, and do not get moved (or rather, i expect they do get moved but again into the home directory in which they already reside). Is there any reason why cron is causing the script to ignore my file paths? In case it matters, here is my crontab entry:

```
0 * * * * /media/disk/incoming/unpacking/unpack_torrents.sh >> /media/disk/incoming/unpacking/cron.log
```

2. I'm sure this script probably looks pretty horrible to more advanced shell coders than myself. Can anyone suggest improvements or a better way of achieving my goal than the one I'm using here?

Any help appreciated. :)

---

### Post by Mindzai on 2008-09-28
bump - anyone able to help me out?

---

### Post by jordilin on 2008-09-29
In the cron job redirect standard error to standard output, otherwise you will not be able to see if something wrong happened, i.e.:

```
0 * * * * /media/disk/incoming/unpacking/unpack_torrents.sh >> /media/disk/incoming/unpacking/cron.log  2>&1
```

Run a couple of tests and see what happens

---

