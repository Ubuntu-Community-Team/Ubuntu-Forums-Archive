---
title: "can't use ext3"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-11-09
i freshly installed ubuntu 8.04.i have got five partitions,one ntfs,second fat32,third ext3(root partition),fourth swap and fifth another ext3 partition(where i want to store my music,videos and other data).now,i tried copying my music files from the ntfs partition to the fifth (ext3) partition,but i could not.but after i ran the command "sudo nautilus" and navigated to that ext3 partition,i could easily get the job done.so the problem i suppose is with permissions,anyways this is not the case with the ntfs and fat partitions.it is cumbersome going to the terminal and running the command and keying in the password before i can do any such operation with that ext3 partition.i want it to be accessible just as any other ntfs or fat partition.its mount point is /media/sda7 which i purposely chose while installing hardy.how do i fix this?thanks in advance.

if i fail to get this fixed,i shall have to convert that partition to ntfs,which i do not want.
i also wanted to know if ext3 partitions are faster than the ntfs counterparts?

---

### Post by drs305 on 2008-11-09
If I read the post correctly, you don't have user permissions on the ext3 partition /media/sda7. You can run the following to correct that:
Add this to fstab or edit the /dev/sda7 setting:
```

/dev/sda7 /media/sda7 ext3 defaults,user 0 2

```

Run this to set the ownership of /media/sda7 to yourself. I've got the recursive switch (-R) on - don't use the switch if you don't want it to affect all subfolders/files:
```

sudo chown -R your.user.name /media/sda7
chmod 750 -R /media/sda7

```

Unmount and mount for the fstab settings to take effect:
```

sudo umount /dev/sda7
sudo mount /dev/sda7

```

---

### Post by sisco311 on 2008-11-09
never mind.
i'm slow.

---

