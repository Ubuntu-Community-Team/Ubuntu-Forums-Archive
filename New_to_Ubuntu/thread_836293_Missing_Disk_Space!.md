---
title: "Missing Disk Space!"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Mythrandil on 2008-06-21
I have /home on its own partition with a total size of 964.9 MiB, free space of 101.5 MiB Available of 52.8 MiB and 863.5 MiB used.

Now can someone tell me firstly why is available half of free space and secondly why when i go to properties of /home it says that total size used is only 298.8 MB?

I missing upto 600MiB, Really need this missing space!

---

### Post by drs305 on 2008-06-21
Please post the following so we can see what is going on:
```
df -Th
```

It is possible you have some large files in the trash. You can empty your user trash with:
```
rm -r ~/.local/share/Trash
```

---

### Post by Mythrandil on 2008-06-21
> **drs305 said:**
> Please post the following so we can see what is going on:
```
df -Th
```
```

Filesystem    Type     Size   Used  Avail Use% Mounted on
/dev/sda3     ext3      11G   3.4G   6.3G  35% /
varrun       tmpfs     1.1G    99k   1.1G   1% /var/run
varlock      tmpfs     1.1G      0   1.1G   0% /var/lock
udev         tmpfs     1.1G    62k   1.1G   1% /dev
devshm       tmpfs     1.1G    13k   1.1G   1% /dev/shm
lrm          tmpfs     1.1G    45M   1.1G   5% /lib/modules/2.6.24-18-generic/volatile
/dev/sda7     vfat      69G   9.1G    60G  14% /Share
/dev/sda6     ext3     1.1G   906M    56M  95% /home
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon      11G   3.4G   6.3G  35% /home/gary/.gvfs

```
> **drs305 said:**
> 
It is possible you have some large files in the trash. You can empty your user trash with:
```
rm -r ~/.local/share/Trash
```

Said directory doesn't exist.

---

### Post by chrisccoulson on 2008-06-21
Your output of df -h definately shows that 906MB of space is being used. As for the available space being approximately half of the remaining free space - this is because ext3 by default reserves 5% of the total disk space for the root user. This is to enable essential services on a machine to keep on running, even if you use up all available space. You can change the amount of space reserved to 0% by doing:
```
sudo tune2fs -m 0 /dev/sda6
```
Only change this on /home though. It is unlikely that the reserved space on /home would ever be utilised

---

### Post by drs305 on 2008-06-21
> **Mythrandil said:**
> Said directory doesn't exist.

That is the message generated if the user's Trash/files folder has been deleted (meaning you have no trash there). 

You can search for other Trash folders that might be taking up space although you shouldn't  have any other ones in your home directory unless there is another user on your machine:

```
sudo find /home -type d -iname Trash
```

---

### Post by nowshining on 2008-06-21
also notice that the linux system takes up X amount of space for safety purposes of which if needed up can disable. This allows u to login incase ur system space gets too tight.

---

