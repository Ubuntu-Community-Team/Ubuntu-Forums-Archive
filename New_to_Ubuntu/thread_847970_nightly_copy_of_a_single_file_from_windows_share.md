---
title: "nightly copy of a single file from windows share?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by nhasian on 2008-07-03
Hello,

I need to do a nightly copy of a single file from a windows xp workstation on my local network to my pc running Ubuntu Hardy 8.04  I'm thinking this can be accomplished with rsync and cron?  Not sure how to do that or even if those are the correct tools for the job?  I'm open to suggestions.

a few quick notes about my setup: both pcs have static IPs if that makes any difference.  Also I've shared the folder containing the file on the windows xp workstation and can successfully access it in nautilus with smb://computername/sharename/
although i'm prompted for a username and password, there is none and i just hit connect.

I hope i have provided enough information and thanks in advance!

---

### Post by hyper_ch on 2008-07-03
(1) figure out how to copy the file in the command line from the xp workstation to your ubuntu

(2) next put that in a shell script (that's very simple, basically it's the command from [1] plus a header... something like
```

#!/bin/bash
cp ................

```

(3) read about cron and how scheduling is done there

(3.1.) I prefer to write the cronjobs to a cron.txt file which I then add to cron by issuing
```

crontab cron.txt

```

You cannot use the "sudo" command in a cronjob. If you do require to make steps as root, then the cronjob must be added as root cron, use this for that:
```

sudo crontab cron.txt

```

---

### Post by nhasian on 2008-07-03
okay i'm learning as I go here.  can i just copy the file over or do i always have to mount the windows share first, copy the file, then un mount the windows share?

I created a mountpoint in /media/dazzle then I tried to do:

```
sudo mount -t cifs //computername/sharename /media/dazzle -o guest
```

but i received this error:

>  wrong fs type, bad option, bad superblock on //computername/sharename,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

