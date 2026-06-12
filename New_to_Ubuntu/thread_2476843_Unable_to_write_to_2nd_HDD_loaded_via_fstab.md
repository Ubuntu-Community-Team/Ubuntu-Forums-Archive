---
title: "Unable to write to 2nd HDD loaded via /fstab"
date: 2022-07-09
forum: New to Ubuntu
---

### Post by r2020r on 2022-07-09
Hi,

I added 2nd HDD to Ubuntu 22.04. Mount point is /media/july/hdd2. Unable to copy from /home/Documents to /media/july/hdd2

**/ect/fstab content**
      UUID=974c54f9-aec4-47a3-baf6-9ff1d8fbc8d3 /media/july/hdd2  ext4  defaults 0 0




**Permissions for mount point (after a reboot)**
      july@july-HP-ZBook-15:/media/july$ ls -ltr
      total 4
      drwxr-xr-x 3 root root 4096 Jul  9 23:00 hdd2

I made following changes to permissions. **Changes made to permission get overwritten once machine reboots**. Is there a way to persists the permission changes?
     july@july-HP-ZBook-15:/media/july$ chmod -R 777 /media/july/hdd2
     july@july-HP-ZBook-15:/media/july$ sudo chown -R july /media/july/hdd2


     july@july-HP-ZBook-15:/media/july$ ls -ltr
     drwxrwxrwx 2 july root 4096 Jul  9 16:01 hdd2

[B]Questions
[/B]a) The change in permission that I am making are they sufficient? Note: In spite of this copy fails **from File Manager UI**
b) How can I make sure the permission changes are permanent?

Seems I am missing something. 
Please help resolve this.

Thanks

---

### Post by #&amp;thj^% on 2022-07-09
Be carefull using  "chown -R" It's not needed or wise.
mine looks like:
```
/dev/disk/by-uuid/be93f3dc-cd54-4321-9a9f-558c1317fc44 /mnt/be93f3dc-cd54-4321-9a9f-558c1317fc44 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```
With mine it will automount on bootup just letting you know. Some don't want it to automount, I did..
EDIT: With mine it opens with /home so all permissions and ownership are handled correctly.

---

### Post by oldfred on 2022-07-10
I am not seeing a partition, like sdb1?
If no partition(s), then you have a very large floppy drive. While that may be able to be done, most Linux tools expect to see partitions.

If large drive better to use gpt partitioning rather than the old MBR(msdos) partitioning from the 1980's.

You can also use gparted but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.
thne add the partition(s) you want.

I put my data partitions normally in /home into my data partition and link all the folders back.

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &


My data partition:
sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown -R $USER:$USER /mnt/data
# The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data

And yes the -R is recursive. Only use an a data partition, never on any system partition or you may totally break system.

---

### Post by r2020r on 2022-07-10
Thanks everyone.  It got resolved :-)

I had to use > sudo chown $USER:$USER /media/july/hdd2
I read when we use $USER, OS replaces with actual username.

I was using (where july is the username) > sudo chown july /media/july/hdd2

---

