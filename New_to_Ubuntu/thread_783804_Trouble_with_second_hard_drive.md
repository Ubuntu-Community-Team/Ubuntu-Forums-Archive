---
title: "Trouble with second hard drive"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Silvanesti on 2008-05-06
Hi,

I just installed ubuntu last saturday. i decided i really wasn't using anything unique to windows and wanted to try something new.

I have two internal hard drives on my computer. When i was installing i put the ubuntu stuff on the smaller one (20gigs), and i figured i could use the larger 80gig one to store all my media on.

i formated the second hard drive as ext2, created a mount point, and thought i mounted it, and added an entry in the boot txt thing. but in all the walkthroughs it says that it should now display the drive for use. 

If i go directly to where the mount point is, the folder says it has 70gigs of free space, but it seems incredibly weird to go to /mnt/storage every time i want to access something. 

Did i accually mount the drive correctly, should it display an icon of a hard drive like it does when i plug in my external? 

thanks

---

### Post by forestpixie on 2008-05-06
Can you post these 2 please

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Silvanesti on 2008-05-06
Ok, here it is.

```

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97de97de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76029452

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux


```


```

mike@mike-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda1
UUID=d18b4f38-237d-46cd-8706-c6c4bc06519d  /               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=3e060697-4753-4328-9c67-dcc096821543  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdb1                                  /mnt/storage     ext2         defaults
```

---

### Post by Xiong Chiamiov on 2008-05-06
If you want to have your 2nd hard drive mounted at, say, /files, then first create a folder for it:
```

sudo mkdir /files

```
and then open your fstab for writing
```

gksudo gedit /etc/fstab

```
and change the last line to be
```

/dev/sdb1                                  /files     ext2         defaults   0  0

```

Note: gksudo is just a special version of sudo that is designed for graphical applications.  You can use sudo instead if you want, but it's a good idea to get in the habit of using gksudo (or kdesudo for Kubuntu users) so that you don't mess up your permissions.

---

### Post by hyper_ch on 2008-05-06
And why do you use Ext2 on the drive?

you could also make a symlink on your desktop to go to /mnt/storage

```

cd ~/Desktop
sudo ln -s /mnt/storage Storage

```

---

### Post by vanadium on 2008-05-06
> you could also make a symlink on your desktop to go to /mnt/storage

This is the only way you should do it (if you want a tidy system, that is)! You do not even need to be root to perform the command hyper_ch suggested. This means that you can leave out the "sudo" ("do as root user (administrator)".

There is also a graphical way to make these symbolic links using Nautilus. Navigate to /mnt. Open another nautilus window containing your home directory. Middle-mouse-click "storage" and drag it to your home folder. Release mouse button and choose "Make link". (if you do not have tree buttons or a scroll wheel, you 'emulate' the third button pressing left+right simultaneously).

A more "visible" way to do this is right-click, then "make link", but unfortunately, you need to be root for this because the link is written in the current directory at first.

---

### Post by hyper_ch on 2008-05-06
you can do symlinks as normal user?

---

### Post by didac on 2008-05-06
Instead of the following line in /etc/fstab

```
/dev/sdb1  /files     ext2         defaults   0  0
```

try this:

```
/dev/sdb1  /media/sdb1    ext2         defaults   0  1
```

Then create the directory:

```
sudo mkdir /media/sdb1
```

After rebooting, you should see icons in the desktop. If not, launch gconf-editor from the terminal. Navigate to /apps/nautilus/desktop and in the right panel check volumes_visible

---

### Post by vanadium on 2008-05-06
Good suggestion. In unix/linux you can mount a disk anywhere. However, to keep things conventional and tidy, it is preferred that you mount either under /mnt or under /media. Drives mounted under /media will show up as an icon on the desktop. When mounted under /mnt, they won't.

The mount point should only be of relevance/known to the system administrator. For the users, create symbolic links to these mount points so that they never need to navigate outside their home directory.

> you can do symlinks as normal user?

You can create symlinks and hardlinks whereever you have user rights to write.

---

### Post by Silvanesti on 2008-05-06
thanks a ton guys! that helps a lot!

> **hyper_ch said:**
> And why do you use Ext2 on the drive?




I had heard that ext2 was the perfered format for ubuntu insted of what it was formatted as (fat32) is there a downside to ext2, or a better one to use?

I was told that the only (or at least the best place) to mount is in the /mnt folder. but is that the reason that its not showing up as an icon?

thanks again!

---

### Post by vanadium on 2008-05-07
ext2 is the same as ext3, except that there is no journaling. This means it is faster and you have more available space :)

Obviously, there is a flip side as well. :( ext2 is more prone to be damaged in case of a power outage or another writing error. With journaling, a drive can easily be "rolled back" to the state before the error. For ext2, the only option is to go through a long file system check to repair the damage.

For a file system primarily meant for storage, e.g. a drive with music, pictures, you are quite fine with ext2. For an intensively used drive (reading, writing, deleting all the time) ext3 is the safer bet.

---

