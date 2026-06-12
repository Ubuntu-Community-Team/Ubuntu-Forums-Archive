---
title: "[SOLVED] how to make storage partition on seperate HD"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-06
so i have ubuntu hardy and swap on my first HD (dev/sda1 and dev/sda2)

i just got another HD (dev/sdb1) 

how can i use it as storage?

i formated to ext3 with gparted 
then i made a mountpoint /media/Storage
then i mounted
```
sudo mount /dev/sdb1 media/Storage
```


but the problem is that now when i navigate to /media/Storage it says 40GB free (wich is right) but i see one folder named lost&found that i cant acess **and it wont let me make any new folders or anything**




EDIT: nevermind, all i had to do was change the ownership and permissions (duuuhhh)

---

### Post by Elfy on 2008-07-06
Just so you know, when you reboot you will have to mount it again. If you want it mount at boot add it to your fstab.

---

### Post by tjwoosta on 2008-07-06
> Just so you know, when you reboot you will have to mount it again. If you want it mount at boot add it to your fstab. 

i thought i would have to also, but actually i didnt
(i just rebooted and it was already mounted)

i think i might only be ntfs partitions that need to be added to fstab

---

### Post by gate on 2008-07-06
You most likely do not have permission to access the drive/folder. Try (in the command line or right clicking on the folder) changing the permissions to read/write/execute for everyone.

 command:
  ```
chmod 777 media/Storage/
```

  You should look in to having the computer automount the drive on startup. I am not very familiar with it, but you can set it so it grants you permission when it mounts.

---

### Post by tjwoosta on 2008-07-06
lol, way ahead of you

---

### Post by Elfy on 2008-07-06
> i think i might only be ntfs partitions that need to be added to fstabdon't think so - but if it's there then :)

---

### Post by tjwoosta on 2008-07-06
ok i see what happened


it actually made its own mountpoint (media/disk) and set itself all up automatically when i rebooted

so i never had to do anything except format to ext3 and restart

---

