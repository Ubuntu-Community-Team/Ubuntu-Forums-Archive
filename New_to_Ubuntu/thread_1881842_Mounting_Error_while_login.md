---
title: "Mounting Error while login"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by greendragons on 2011-11-16
I have a partition ext4
```

UUID=b2690794-b60a-4603-821b-802a985888ef /media/XMachines ext4 defaults,umask=133,dmask=022,uid=1000,gid=1000

```

While booting up it shows cannot mount this partition...and after i login, when i try to mount it from nautilus it shows only root can do it.... on other hand i can mount other partitions without problem.

Thnx!!

---

### Post by Morbius1 on 2011-11-16
> umask=133,dmask=022,uid=1000,gid=1000All of those options in your fstab line can only be used for Windows filesystems not Linux filesystems.

Change the fstab line to this:
```
 UUID=b2690794-b60a-4603-821b-802a985888ef /media/XMachines ext4 defaults,noatime 0 2
```If you currently have mounted that partition manually unmount it then run the following command to mount the partition with the new fstab line - saves you a reboot:
```
sudo mount -a
```Once it's mounted to achieve your desired ownership:
```
sudo chown morbius:morbius /media/XMachines
```*[COLOR=Blue]Change morbius to your own user name[/COLOR]*

---

### Post by greendragons on 2011-11-16
Thnx!!!! 
Well tht solves my problem and also it's really good that without reboot i can mount thorugh fstabs :D

---

