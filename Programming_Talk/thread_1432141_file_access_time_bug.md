---
title: "file access time bug?"
date: 2010-03-17
forum: Programming Talk
---

### Post by xzero1 on 2010-03-17
Note: p80 is a bmp file and feh is a viewer program.

```
stat p80
  File: `p80'
  Size: 2764854   	Blocks: 5408       IO Block: 4096   regular file
Device: 80ah/2058d	Inode: 816402      Links: 1
Access: (0777/-rwxrwxrwx)  Uid: ( 1000/    kdog)   Gid: ( 1000/    kdog)
Access: 2010-03-17 11:37:50.197648560 -0500
Modify: 2009-02-21 14:11:39.000000000 -0600
Change: 2009-07-12 03:43:48.662389201 -0500
kdog@kdog-desktop:/media/400G/drv1_vol3/12G/ocp$ feh p80
kdog@kdog-desktop:/media/400G/drv1_vol3/12G/ocp$ stat p80
  File: `p80'
  Size: 2764854   	Blocks: 5408       IO Block: 4096   regular file
Device: 80ah/2058d	Inode: 816402      Links: 1
Access: (0777/-rwxrwxrwx)  Uid: ( 1000/    kdog)   Gid: ( 1000/    kdog)
Access: 2010-03-17 11:37:50.197648560 -0500
Modify: 2009-02-21 14:11:39.000000000 -0600
Change: 2009-07-12 03:43:48.662389201 -0500

```

Why is there *no* change in the access time stamp?

---

### Post by johnl on 2010-03-17
Type "mount" into the terminal.

Is the partition that contains "/media/400G/drv1_vol3/12G/" mounted with the "noatime" option?  This is a common option which can greatly improve disk performance by not updating file access times.  If you want access times to be updated, you need to remove "noatime" from your /etc/fstab for this partition.

---

### Post by geirha on 2010-03-17
It could also be due to relatime. From «man mount»:
```

       relatime
              Update inode access times relative to  modify  or  change  time.
              Access time is only updated if the previous access time was ear&#8208;
              lier than the current modify or change time. (Similar  to  noat&#8208;
              ime,  but  doesn't break mutt or other applications that need to
              know if a file has been read since the last time  it  was  modi&#8208;
              fied.)

```

---

### Post by xzero1 on 2010-03-17
The drive is not automounted, there is no entry in fstab.

I use the default options for mounting it (just click it in the gui). 

These results (including touch) might be more interesting...

```
stat p80
  File: `p80'
  Size: 2764854   	Blocks: 5408       IO Block: 4096   regular file
Device: 80ah/2058d	Inode: 816402      Links: 1
Access: (0777/-rwxrwxrwx)  Uid: ( 1000/    kdog)   Gid: ( 1000/    kdog)
Access: 2010-03-17 11:37:50.197648560 -0500
Modify: 2009-02-21 14:11:39.000000000 -0600
Change: 2009-07-12 03:43:48.662389201 -0500
kdog@kdog-desktop:/media/400G/drv1_vol3/12G/ocp$ feh p80
kdog@kdog-desktop:/media/400G/drv1_vol3/12G/ocp$ stat p80
  File: `p80'
  Size: 2764854   	Blocks: 5408       IO Block: 4096   regular file
Device: 80ah/2058d	Inode: 816402      Links: 1
Access: (0777/-rwxrwxrwx)  Uid: ( 1000/    kdog)   Gid: ( 1000/    kdog)
Access: 2010-03-17 11:37:50.197648560 -0500
Modify: 2009-02-21 14:11:39.000000000 -0600
Change: 2009-07-12 03:43:48.662389201 -0500
kdog@kdog-desktop:/media/400G/drv1_vol3/12G/ocp$ touch -a p80
kdog@kdog-desktop:/media/400G/drv1_vol3/12G/ocp$ stat p80
  File: `p80'
  Size: 2764854   	Blocks: 5408       IO Block: 4096   regular file
Device: 80ah/2058d	Inode: 816402      Links: 1
Access: (0777/-rwxrwxrwx)  Uid: ( 1000/    kdog)   Gid: ( 1000/    kdog)
Access: 2010-03-17 16:11:27.601118762 -0500
Modify: 2009-02-21 14:11:39.000000000 -0600
Change: 2010-03-17 16:11:27.595173898 -0500
kdog@kdog-desktop:/media/400G/drv1_vol3/12G/ocp$ 
```

Clearly, nothing is being changed by feh, yet the picture is displayed so the file has been accessed. I still don't understand this.

---

### Post by geirha on 2010-03-17
> **xzero1 said:**
> 
Clearly, nothing is being changed by feh, yet the picture is displayed so the file has been accessed. I still don't understand this.

That is not clear. What you've shown so far is consistent with relatime option set. What options is it mounted with?

```
grep /media/400G /proc/mounts
```

---

### Post by xzero1 on 2010-03-17
Thanks, remounting with strictatime option fixed it. I was a bit confused because the mount command did not show the relatime option, whereas cat /proc/mounts does.

---

