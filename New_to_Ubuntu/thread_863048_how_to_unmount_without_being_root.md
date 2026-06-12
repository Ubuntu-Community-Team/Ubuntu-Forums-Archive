---
title: "how to unmount without being root"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by cjv8888 on 2008-07-18
I am dual booting with xp.
What happened was that I used Partition Magic at the xp to shrink the xp partition.  It went wrong and I got a BSOD.
I have Hardy on a separate HD and there is a storage partition on this HD which is shared with xp.
Since xp crashed , I have not been able to mount this storage partition. Then I read somewhere on the forum that this may be due to the volume being dirty and I downloaded a program to reset it.  After that I was able to mount it as root. Now how do I unmount it without being root?
I tried chown but am not sure if I got the syntax correct.  Anyway it did not work.
BTW, I was able to restore xp with Partimage and it is now booting normally but the storage partition is still locked as root.

---

### Post by meindian523 on 2008-07-18
What's the filesystem on the locked partition?Do you want that partition to be mountable and unmountable by the user?

---

### Post by iaculallad on 2008-07-18
> **cjv8888 said:**
> I am dual booting with xp.
What happened was that I used Partition Magic at the xp to shrink the xp partition.  It went wrong and I got a BSOD.
I have Hardy on a separate HD and there is a storage partition on this HD which is shared with xp.
Since xp crashed , I have not been able to mount this storage partition. Then I read somewhere on the forum that this may be due to the volume being dirty and I downloaded a program to reset it.  After that I was able to mount it as root. Now how do I unmount it without being root?
I tried chown but am not sure if I got the syntax correct.  Anyway it did not work.
BTW, I was able to restore xp with Partimage and it is now booting normally but the storage partition is still locked as root.

On your terminal:

```
sudo umount /dev/your_drive_to_unmount
```

---

### Post by cjv8888 on 2008-07-18
It is NTFS. I am trying to make it mount and unmount without being root, ie by user.

---

### Post by meindian523 on 2008-07-18
Follow iaculallad's advice.

---

### Post by cjv8888 on 2008-07-18
Thanks,I am able to mount and unmount it from the terminal, but is there some way of doing it without being the superuser.
Before XP crashed, I could mount and unmount it with 2 clicks.

---

### Post by iaculallad on 2008-07-18
> **cjv8888 said:**
> Thanks,I am unable to mount and unmount it from the terminal, but is there some way of doing it without being the superuser.
Before XP crashed, I could mount and unmount it with 2 clicks.

What error does it display when you issue the command below on your terminal?

```
sudo mount -a
```

Sure, there could be other way around this but you still need to issue your "privilege" user password. You could add it on your fstab file so that it will automatically mounted on startup.

---

### Post by cjv8888 on 2008-07-18
It was added to the fstab file already, so it mounts at boot.
But to unmount it, I have to do it at the terminal.
Sorry to seem to be fussing over nothing, but I am just wondering what changed the partition when WinXP crashed to suddenly require superuser to unmount it and if I can just undo the change to the way it was before.

---

### Post by hyper_ch on 2008-07-18
unmounting always requires superuser rights (except for removable media)

---

### Post by cjv8888 on 2008-07-18
> **hyper_ch said:**
> unmounting always requires superuser rights (except for removable media)
It didn't before. :confused:

---

### Post by Canis familiaris on 2008-07-18
> **hyper_ch said:**
> unmounting always requires superuser rights (except for removable media)

No I can mount and unmount the NTFS volumes without superuser priviledges

---

### Post by hyper_ch on 2008-07-18
I don't use ntfs drives anymore ;) so I might be mistaken ;)

---

### Post by sisco311 on 2008-07-18
Try to add this options to the fstab: *user,noauto*

---

### Post by sisco311 on 2008-07-18
> **hyper_ch said:**
> I don't use ntfs drives anymore ;) so I might be mistaken ;)
At boot time the partition is mounted by root, so only root can unmount it.
noauto = do not mount at boot time
user = allow a user to mount => the user can unmount it.

---

### Post by cjv8888 on 2008-07-18
> **sisco311 said:**
> Try to add this options to the fstab: *user,noauto*
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b334d7a0-58ce-4a3d-9d8c-5b57b1ad6270 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=9b44b01e-46ae-441a-a8b7-4ee686c33988 /home           ext3    relatime        0       2
# /dev/sda7
UUID=35ee917a-fe5e-47e5-8d4a-98f37a1d9de4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=BE74E659A274FB91 /media/Storage ntfs defaults,umask=007,gid=46 0 1
?add at the end of that

---

### Post by sisco311 on 2008-07-18
[COLOR=White]a[/COLOR]> UUID=BE74E659A274FB91 /media/Storage ntfs defaults,**noauto,user**,umask=007,gid=46 0 1                      

---

### Post by Canis familiaris on 2008-07-18
If you just want to access that Windows drive, you could force mount it:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt/windows -o force
```

Replace /dev/sda1 by your Windows partition
Replace /mnt/Windows by your mount point.

YOu could access the Windows partition then.

You could then unmount this Windows partition by:
```
sudo umount /dev/sda1
```

And Restart
Perhaps this will make your Windows partition behave in Ubuntu just like in did When you did not use Windows.

---

### Post by cjv8888 on 2008-07-18
Okay,
let me try that :)

---

### Post by cjv8888 on 2008-07-18
> UUID=BE74E659A274FB91 /media/Storage ntfs defaults,noauto,user,umask=007,gid=46 0 1 
When I did that, it would not even mount at boot.

---

### Post by cjv8888 on 2008-07-18
> **Anurag_panda said:**
> If you just want to access that Windows drive, you could force mount it:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt/windows -o force
```

Replace /dev/sda1 by your Windows partition
Replace /mnt/Windows by your mount point.

YOu could access the Windows partition then.

You could then unmount this Windows partition by:
```
sudo umount /dev/sda1
```

And Restart
Perhaps this will make your Windows partition behave in Ubuntu just like in did When you did not use Windows.

Thanks, but I had no trouble mounting the partition using the terminal, just trying to work out how to unmount without the terminal.

---

### Post by cjv8888 on 2008-07-18
> UUID=BE74E659A274FB91 /media/Storage ntfs defaults,user,umask=007,gid=46 0 1
I also tried the above but still cannot unmount directly.

---

### Post by Canis familiaris on 2008-07-18
I dont have the FSTAB entries for NTFS partitions in my PC but I can mount and unmount them without entering the root password.
Mounting is easy too. I just go to Places and select the partition. It works for me very well.
Perhaps you can try commenting out the fstab entriy for ntfs partition by #

---

### Post by cjv8888 on 2008-07-18
Could I try a change owner for the partition?

---

### Post by cjv8888 on 2008-07-18
> **Anurag_panda said:**
> I dont have the FSTAB entries for NTFS partitions in my PC but I can mount and unmount them without entering the root password.
Mounting is easy too. I just go to Places and select the partition. It works for me very well.
Perhaps you can try commenting out the fstab entriy for ntfs partition by #

I added the fstab entry myself and I used to be able to unmount it by right clicking on it, but since the Xp crashed the partition suddenly became root mountable only.

---

### Post by cjv8888 on 2008-07-31
ok

---

### Post by cjv8888 on 2008-07-31
sorry

---

