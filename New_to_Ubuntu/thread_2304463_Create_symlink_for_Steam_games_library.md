---
title: "Create symlink for Steam games library"
date: 2015-11-26
forum: New to Ubuntu
---

### Post by shannon5 on 2015-11-26
So I have a 1.5 terabyte secondary drive that I use for storing large amounts of date and games. My Ubuntu runs on its own SSD. The 1.5 terabyte drive is formatted in NTFS because my Windows installation also needs to access it.

I have steam on Linux and I want to install some games.  Steam allows me to set a Steam Library Folder. I would like this on my other, large drive.  When I go to set the folder I can only see my SSD's folder structure. I'm assuming I need to mount my other drive or create a symlink, but I'm too much of a newb to really understand it. The link should persist through reboots.

Please, I need an adult to help me. ;)

---

### Post by Bucky Ball on 2015-11-26
With the external drive plugged in, open a terminal and:

```
sudo blkid
```

Post the output here between code tags, please (see last link in my signature).

Then, 

```
nano /etc/fstab
```

Post that file here. By the sounds of it, you want the drive to mount at boot. You don't need a symlink for that. Not related. :)

PS: The HDD should show up in your file manager and mount when you click it. You're saying it doesn't?

---

### Post by shannon5 on 2015-11-27
The drive does show up in the Unity file manager.

Output of blkid:
```

/dev/sda1: LABEL="System Reserved" UUID="267430D27430A689" TYPE="ntfs" 
/dev/sda2: UUID="16303BF3303BD887" TYPE="ntfs" 
/dev/sda3: UUID="141214D91214C1A2" TYPE="ntfs" 
/dev/sdb1: UUID="16b66b22-781b-4b77-9c30-27e3ee426c37" TYPE="ext4" 
/dev/sdb5: UUID="c05031d2-f139-4f0c-9d62-8ed7457fb820" TYPE="swap" 
/dev/sdc1: LABEL="Data" UUID="369CB1D19CB18C3D" TYPE="ntfs" 

```


/etc/fstab
  GNU nano 2.2.6                                                        File: /etc/fstab                                                                                                                       

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=16b66b22-781b-4b77-9c30-27e3ee426c37 /               ext4    noatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=c05031d2-f139-4f0c-9d62-8ed7457fb820 none            swap    sw              0       0

```



EDIT: I believe this is the drive I want to mount as I did label it 'data'
/dev/sdc1: LABEL="Data" UUID="369CB1D19CB18C3D" TYPE="ntfs"

---

### Post by Bucky Ball on 2015-11-27
> **shannon5 said:**
> The drive does show up in the Unity file manager.

... and I presume it doesn't mount when you click on it??? You didn't say. And please use code tags as I asked. See the last link in my signature. Best if you can follow advice and answer questions to help us help you. :)

Ok. If it doesn't mount when you click on it, create a mount point in /mnt. Call it what you want, but here, we'll use 'Data'.

```
sudo mkdir /mnt/Data
```

Open the fstab file:

```
sudo nano /etc/fstab
```

... and make it look like this (copy/paste the bold section):

```
GNU nano 2.2.6 File: /etc/fstab


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sdb1 during installation
UUID=16b66b22-781b-4b77-9c30-27e3ee426c37 / ext4 noatime,errors=remount-ro 0 1
[B]# Entry for /dev/sdc1
UUID=369CB1D19CB18C3D   /mnt/Data   ntfs-3g defaults,locale=en_AU.UTF-8     0       0[/B]
# swap was on /dev/sdb5 during installation
UUID=c05031d2-f139-4f0c-9d62-8ed7457fb820 none swap sw 0 0
```

In the fstab line, see this: locale=en_AU.UTF-8. You need to change 'locale=**en_AU**.UTF-8' to your language/location. 

Reboot and report back. You may need to install ntfs-3g to get it working, but check it out before we go there. Again, please click the partition in the file manager and see if it mounts prior to spending time on all this.

---

### Post by shannon5 on 2015-11-27
Thanks for the help so far. A quick note, it DOES show up in the Unity file manager and I can even right click and 'unmount' it if I want.

What I'm looking for is how to address the drive by it's path.  Assuming I was in my home folder in a terminal, how would I get to the drive?  I need the path to put in the steam library option.

Doing the rest of what you said now.

---

### Post by Bucky Ball on 2015-11-27
What is the path in the address bar of your file manager??? It is probably /media/username/Data, where 'username' is your user name and 'Data' is the name you've called the partition.

The address in the file manager is exactly the same as you would use from a terminal, regardless of what folder you're in.

```
cd /media/username/Data
```

... and changed directory (cd) to your Data partition. That simple. The file manager uses exactly the same address path as a terminal would. Forget changing fstab. You don't need to.

---

### Post by shannon5 on 2015-11-27
Welp, saw your reply too late.  I changed fstab. The drive is now no longer visible in the launcher, but I located it under /mnt/Data/ and the path works fine now. Steam is using it.   I'd really love to understand what just happened and what other options I had here, but that'll have to wait till I get back from work.

Thank you so much for your patience and fast replies. I really appreciate it.

---

