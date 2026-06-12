---
title: "need to mount my partition"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by vivek shekar on 2008-08-20
hi,

I have installed Ubunthu 8.04 to my system,
earlier i have the some data in /var and in /home so while installing i did not format those partitions.
And now how i get that back?

---

### Post by prshah on 2008-08-20
> **vivek shekar said:**
> 
I have installed Ubunthu 8.04 to my system,
earlier i have the some data in /var and in /home so while installing i did not format those partitions.

During the installation, at the partitioning phase, you have the option to specify mount points for various partitions; did you specify those partitions to have mount points of "/var" and "/home", or did you just specify a "/" mount point?

---

### Post by vivek shekar on 2008-08-20
s i have gave those this is how my patitions look now...Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              14G  4.8G  8.5G  37% /
varrun                442M  108K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   60K  442M   1% /dev
devshm                442M   12K  442M   1% /dev/shm
lrm                   442M   39M  404M   9% /lib/modules/2.6.24-19-generic/volatile
/dev/sda7             1.9G   72M  1.7G   4% /boot


if i want the access i need to mount for those files.
but there was one potion to load automaically during new sessions?
It is not giving uid when i dispay /etc/fstab.

---

### Post by prshah on 2008-08-20
> **vivek shekar said:**
> [code[Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              14G  4.8G  8.5G  37% /
varrun                442M  108K  442M   1% /var/run
varlock               442M     0  442M   0% /var/lock
udev                  442M   60K  442M   1% /dev
devshm                442M   12K  442M   1% /dev/shm
lrm                   442M   39M  404M   9% /lib/modules/2.6.24-19-generic/volatile
/dev/sda7             1.9G   72M  1.7G   4% /boot
[/code]
It is not giving uid when i dispay /etc/fstab.

I'm sorry but I can't understand what you are trying to say. In any case...

1) the command "vol_id" and "blkid" will give you the UUID```

sudo blkid /dev/sda1
sudo vol_id /dev/sda1
```

Note that both require the use of "sudo"

2) From what you've posted above, it doesn't seem as though your old partitions for "/home" and "/var" are on this disk. Can you post the output of ```
sudo fdisk -l
```

Giving 1.9Gb for "/boot" is overkill; you should reduce this. Note also that placing your "/boot" on an extended partition is a bad idea; not that you can do anything about this now; this information is for the future.

---

### Post by vivek shekar on 2008-08-21
see ill tel u in detail about my problem.

Earlier i was having Zenwalk in my system.File system was XFS there..,

That time i had some partitions including home and var.

And now i have installed Ubuntu while installing i did not formet home and var.

Now i can access the data through mount /dev/sda....

Now i am asking is there any way to mount /var /home automaticall during login?

---

### Post by Too Late on 2008-08-21
I think all you have to do is to edit your /etc/fstab file. Post its contents here if you are unsure what to do.

---

### Post by vivek shekar on 2008-08-21
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=556279f2-d60f-4f82-a99d-fd2f4a0cbf65 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda7
UUID=97188347-22c9-4464-a6ee-be55d614491a /boot           ext3    relatime        0       2
# /dev/hda8
UUID=36711427-e99d-44d1-b139-6029b2b365fe none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by prshah on 2008-08-21
> **vivek shekar said:**
> ```
# /etc/fstab: static file system information.
UUID=556279f2-d60f-4f82-a99d-fd2f4a0cbf65 /               ext3    relatime,errors=remount-ro 0       1
UUID=97188347-22c9-4464-a6ee-be55d614491a /boot           ext3    relatime        0       2
UUID=36711427-e99d-44d1-b139-6029b2b365fe none            swap    sw              0       0
0
```

I cannot see any linux ext3/XFS partitions for "/var" and "/home" from what you are posting here. Unless you post the result of the fdisk command (from post #4), the information you have given here indicates to me that you've overwritten the "/home" and "/var" partitions of your Zenwalk distro, since there are no XFS partitions listed here.

---

### Post by Kyle1981 on 2008-08-21
in fact, you should mount them when you install your system, you don't need format them. 

but you have installed, so you can edit /etc/fstab file to mount.

---

### Post by vivek shekar on 2008-08-22
Here i am posting fdisk details......


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            4375       19457   121154197+   5  Extended
/dev/sda3            2551        4374    14651280   83  Linux
/dev/sda5            4375       17390   104550988+  83  Linux
/dev/sda6           17391       18971    12699351   83  Linux
/dev/sda7           18972       19214     1951866   83  Linux
/dev/sda8           19215       19457     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by vivek shekar on 2008-08-22
my /etc/fstab lokks like this...

How i should mount them?


# /etc/fstab: static file system information.
UUID=556279f2-d60f-4f82-a99d-fd2f4a0cbf65 /               ext3    relatime,errors=remount-ro 0       1
UUID=97188347-22c9-4464-a6ee-be55d614491a /boot           ext3    relatime        0       2
UUID=36711427-e99d-44d1-b139-6029b2b365fe none            swap    sw              0       0
0

---

### Post by vivek shekar on 2008-08-28
HI,

I have ubuntu8.04 LTS in my machine.
I have installed apache2 successfully.
Now i am trying to install PHP after restarting apache2 its giving following error mess....  

root@vivek-desktop:~# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                             apache2: apr_sockaddr_info_get() failed for vivek-desktop
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (no pid file) not running
apache2: apr_sockaddr_info_get() failed for vivek-desktop
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs






please help to me solve this...

---

