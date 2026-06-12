---
title: "my home drive is showing up twice"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-07-06
i really want to fix this i have one drive showing up twice but dont want to mess anything up.
i have it listed under /dev/sda3 and it show up again under gvfs-fuse-daemon

why is it doing this and how can i fix this?

---

### Post by llama320 on 2008-07-06
i'm not sure why it's doing this but it might help if you post the output of this command

```
cat /etc/fstab
```

Your fstab may have been edited to automount your /home drive at startup (I don't know why)

You might also try unmounting the drive from /dev with

```
sudo umount /dev/sda3
```

^^This shouldn't mess anything up because you can always remount it later

Good Luck

---

### Post by PatrickMoore on 2008-07-06
> **llama320 said:**
> i'm not sure why it's doing this but it might help if you post the output of this command

```
cat /etc/fstab
```

Your fstab may have been edited to automount your /home drive at startup (I don't know why)

You might also try unmounting the drive from /dev with

```
sudo umount /dev/sda3
```

^^This shouldn't mess anything up because you can always remount it later

Good Luck


fstab is
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0073e8ca-e864-4c8b-bc81-3a701ebc97d7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=ddbc44b8-a749-419c-9b6a-60501e1488a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

``` i cannot unmount until i find my live disk.

---

### Post by mc4man on 2008-07-06
> i have it listed under /dev/sda3 and it show up again under gvfs-fuse-daemon
I think that's normal,- where are you seeing it twice?
For instance while I have a separate / and /home you'll see / shown twice. (really only exists once)

---

### Post by PatrickMoore on 2008-07-06
> **mc4man said:**
> I think that's normal,- where are you seeing it twice?
For instance while I have a separate / and /home you'll see / shown twice. (really only exists once)
there  and in my conky posting it comes up under home and external h.d.

---

### Post by mc4man on 2008-07-06
I wouldn't worry about it, if you don't want it affecting disk usage analyzer just uncheck it in preferences. ( the numbers will change but everything stays the same relatively speaking - capacity, used, available more accurately reflected with it unchecked)
don't know about conky

---

