---
title: "bash script to check drive mounted"
date: 2009-05-26
forum: Programming Talk
---

### Post by bfrosty on 2009-05-26
Hi guys,

I have a basic bash script which I use to rsync one external drive to another external drive. I'm concerned that my script may delete everything from my destination drive if the source drive hasn't mounted properly.

How can I include a condition to check whether my external hard-drive is mounted? 

```

#!/bin/bash

# List files to wake up drives
cd /media/external
ls
cd /media/mirror
ls

# Synchronize external hard drive to mirror hard drive
sudo rsync -av --progress --delete --exclude .Trash* /media/external/ /media/mirror/

```

Both drives mounted (mount command):
```

/dev/sdc1 on /media/external type vfat (rw,uid=1000,gid=100,utf8,dmask=027,fmask=137)
/dev/sdd1 on /media/mirror type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

Could I use awk to grab the third column and compare that to a string or something? 

I'm running 9.04 x86 server edition.

Thanks!!

---

### Post by kaibob on 2009-05-27
> **bfrosty said:**
> ...How can I include a condition to check whether my external hard-drive is mounted?...


I don't know how to do what you want with the mount command, but I found this a while back, and it worked for me:

```
if grep '/media/disk' /etc/mtab > /dev/null 2>&1 ; then 
	echo mounted
else 
	echo "not mounted"
fi

```

You have to change '/media/disk' to whatever is appropriate.

---

### Post by rjack on 2009-05-27
I'd suggest ```
grep -q ...
``` instead of ```
grep ... > /dev/null 2>&1
```

---

### Post by bfrosty on 2009-05-27
Thanks a lot guys. Here's the current script, which works well:

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

---

### Post by tmow on 2012-09-27
I had the same issue, so I've solved it just creating a file in the external drive and checking that is there

[[ -f /media/external/mounted ]] && rsync -rtu --delete /media/external /media/mirror

---

### Post by sisco311 on 2012-09-27
Please don't bump old threads.

Thread closed.

[[img]http://ompldr.org/tYnpyNw[/img]](http://ompldr.org/vYnpyNw)

---

