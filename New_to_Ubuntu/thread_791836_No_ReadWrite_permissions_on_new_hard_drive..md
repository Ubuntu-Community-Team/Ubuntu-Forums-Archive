---
title: "No Read/Write permissions on new hard drive."
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Alex Carroll on 2008-05-12
I got a new SATA hard drive today - a Samsung Spinpoint 500GB - and when I fitted it, I used Gparted to add two partitions. These were both fat32 or vfat to make it compatible with the Windows dual boot I am going to try.

After following the guide posted [[COLOR="Red"]here[/COLOR]](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/), the drive showed up, but I had no permissions. A reboot made the drive name a bit tidier, but still no permissions. I have tried the "sudo chmod 777 /home/alex/Storage" command, as well as "sudo chmod 777 /dev/sda1" and "sudo chmod -R 2777 /home/alex/Storage"

The first two commands show no errors and appear to work, but when I check the drive, I still cannot write to it. The third command tells me "chmod: changing permissions of `/home/alex/Storage': Operation not permitted"

I was thinking of logging on as root and changing the permissions using the menu, but I'm sure there's a command that can do it for me.

Thanks in advance.

---

### Post by TeoBigusGeekus on 2008-05-12
Try
```
sudo chown -R yourusername dev/sda1
```

---

### Post by Inxsible on 2008-05-12
It is strange that your drive is mounted under /home/alex/Storage, unless you specifically mounted it there. Normally USB drives get mounted under /media.

Could you post the output of the following command```
sudo fdisk -l
``` -l is a lowercase L

---

### Post by Alex Carroll on 2008-05-12
I did specifically mount it there.

```
Disk /dev/hdc: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a7bc248

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3890    31246393+  83  Linux
/dev/hdc2            3891        4866     7839720    5  Extended
/dev/hdc5            3891        4866     7839688+  82  Linux swap / Solaris

Disk /dev/hdd: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12a87c45

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        4866    39086113+  83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 byt
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00051d9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38245   307202931    b  W95 FAT32
/dev/sda2           38246       60801   181181070    b  W95 FAT32

```

TeoBigusGeekus, that command also had no effect.

I just tried running Nautilus as root and using the properties menu, but each time I change a setting it resets itself. I can create files and folders as root, though.

---

### Post by Inxsible on 2008-05-12
Ok if you are sure you mounted it at /home/alex/Storage then you need to use the following command to get ownership
```
sudo chown -R *<your-username>:<your group>* /home/alex/Storage
```

---

### Post by Alex Carroll on 2008-05-12
```
alex@alex-desktop:~$ sudo chown -R alex:alex /home/alex/Storage
chown: changing ownership of `/home/alex/Storage/Test write/list-test.txt': Operation not permitted
chown: changing ownership of `/home/alex/Storage/Test write/list-test.txt~': Operation not permitted
chown: changing ownership of `/home/alex/Storage/Test write': Operation not permitted
chown: changing ownership of `/home/alex/Storage': Operation not permitted

```

---

### Post by TeoBigusGeekus on 2008-05-12
2 questions:

1) Have you installed window$ on that drive? If yes, it might be a problem of not having shut it down properly, in which case you should boot into window$, let it load completely and then restart and boot into Ubuntu.

2) What's this file list-test.txt?

---

### Post by Alex Carroll on 2008-05-12
Windows hasn't been installed yet, and the "list-test.txt" was a file I created as root to ensure the drive wasn't read-only.

E: I just remembered I used the command "sudo mkdir /home/alex/Storage" to create that directory. Would that mean the directory belonged to root when it was created?

---

### Post by Inxsible on 2008-05-12
Wait a minute. I just realized that it was a FAT drive. FAT drives will not hold ownership info. FAT drives should have read write capabilities by default in Ubuntu.

---

### Post by TeoBigusGeekus on 2008-05-12
Log in as root, delete the folder Test Write and retype Inxsible's command.

---

### Post by Alex Carroll on 2008-05-12
```
alex@alex-desktop:~$ sudo chown -R alex:alex /home/alex/Storage
chown: changing ownership of `/home/alex/Storage': Operation not permitted

```

---

### Post by Inxsible on 2008-05-12
Can you post the output of ```
df -h
```

---

### Post by TeoBigusGeekus on 2008-05-12
I give up - sorry, I've used all my Ubuntu knowledge...

A suggestion: why don't you reformat the drive as ntfs? It will be able to handle files larger than 4gbs and you might have better luck with ntfs-config.

---

### Post by hyper_ch on 2008-05-12
it's fat32 so permissions should not have an effect...

If you're going to keep that partition do:

(1) create mount point
```

sudo mkdir /media/XXX
sudo chown USER.USER media/XXX

```
Replace XXX with a name (use no spaces or special chars)
and USER is your username

(2) add it to your fstab
```

gksu gedit /etc/fstab

```
and add:
```

/dev/sda1 /media/XXX vfat rw,defaults,uid=1000,gid=1000,umask=0000 0 0 

```

(3) now reload fstab
```

sudo mount -a

```

---

### Post by Alex Carroll on 2008-05-12
```
alex@alex-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1              30G   24G  4.0G  86% /
varrun                503M   92K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M  100K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   36M  467M   8% /lib/modules/2.6.22-14-generic/volatile
/dev/hdd1              37G   24G   12G  68% /alex
/dev/sda1             293G   16K  293G   1% /home/alex/Storage

```

Thanks for the help anyway, TeoBigusGeekus.

---

