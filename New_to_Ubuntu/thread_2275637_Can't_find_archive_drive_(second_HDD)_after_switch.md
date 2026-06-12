---
title: "Can't find archive drive (second HDD) after switching to Ubuntu server 14.04"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by mreilander81 on 2015-04-27
Hi all,
I am a complete linux command line noob. I had ubuntu desktop running on an older computer specifically for running plex server. The main drive that had the operating system had failed, so I replaced the drive and installed Ubuntu server, as I would also like to use it as a file server and run it headless. My question is, how do I access the content and/or make directories on the archive drive? I'm not sure how to do this without a GUI.

---

### Post by Bashing-om on 2015-04-27
mreilander81; Hi !

On a hard drive that is partitioned and file systems in-place from terminal one can access the file system(s)
a) Make up a mount point from which to attach the external file system(s)
```

sudo mkdir /mnt/backup

```
'backup' can be any reference you prefer

b) have a look and see what the partitions are on the storage drive:
```

sudo fdisk -lu

```

c) let's say the storage drive is 'sdb' and you want to access the file system on the 1st partition :
```

sudo mount /dev/sdb1 /mnt/backup

```
to see the files on that mounted file system:
```

ls -al /mnt/backup

```
bear in mind we do not know at this time who has ownership of the file system .. possible that you might have to change them to "you" (chown command) .

All there is to it ..
ReMemBer -> any file system you mount manually MUST be manually UNmounted; else file system corruption at some level will result:
d) 
```

sudo umount /mnt/backup

```

I do expect there to be some minor adjustments to be made. Once you are this far along, and have additional questions/concerns we will address them at that time.

[INDENT][INDENT]simple as falling out of bed
[INDENT][INDENT][INDENT][INDENT]wide awake
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

