---
title: "access other hard drives in ubuntu server 14.04.1"
date: 2015-01-30
forum: New to Ubuntu
---

### Post by evan20 on 2015-01-30
Hello, I'm very new to linux,  I've just built a pc to use as a media server.  I have 3 HDD's, 1 will be used for just the OS and primary files, the other 2 will be used for media storage.  
How can I access the other HDD's to create folders and add files etc.  

Thanks.

---

### Post by nilla78ro on 2015-01-30
Hello, 
you can find everything here :
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by evan20 on 2015-01-30
already read through them, no help.  All I need is a command to get from the main HDD that root is on, to the other HDD that will store the media.

---

### Post by Bashing-om on 2015-01-30
evan20; Hi !

To access files on the other hard drives one must first attach the file system to "root". This is done by making up a mount point; for instance:
```

sudo mkdir /mnt/test

```
now through that 'mount point' we mount a file system .. say there is a partition number 1 on the 2nd hard drive, and the file system on this sdb1 is ubuntu's ext4; then one does a number like so:
```

sudo mount /dev/sdb1 /mnt/test

```
OK ! now you have the file system attached and are able to manipulate the files on sdb1. To look:
```

ls -al /mnt/test
ls -al /mnt/test/<some_directory>

```
one mount point to a destination at a time .. make as many mount points as one needs if opening other file systems.

When done, MUST UN-mount what you manually mounted - failure to do so will result in file system corruption at some level:
```

sudo umount /mnt/test

```

[INDENT][INDENT][INDENT]hope that helps
[/INDENT][/INDENT][/INDENT]

---

### Post by evan20 on 2015-01-30
Brilliant, thanks so much.

---

### Post by sandyd on 2015-01-30
Hi, if you have found a solution, please mark your thread as solved by going to Thread Tools -> Mark thread as solved.


Thanks!

---

