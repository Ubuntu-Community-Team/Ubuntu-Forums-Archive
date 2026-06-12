---
title: "Accessing files problem"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by Stanich on 2012-09-12
So I've been messing with ubuntu, don't really know how, but I managed to f**k it up, so I had only seen desktop background. As I had no idea what to do, I decided to install Ubuntu once more, on different partition.

I did so, and now I don't know how to access files I had there. 

When I post ```
sudo fdisk -l
``` in terminal, I get following result:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000c3d9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   459720350   229859151+  83  Linux
/dev/sda2       459720702   976771071   258525185    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       968843264   976771071     3963904   82  Linux swap / Solaris
/dev/sda6       459720704   968843263   254561280   83  Linux

Partition table entries are not in disk order

```Any ideas?

---

### Post by SlugSlug on 2012-09-12
```
sudo mkdir /mnt/sda5; sudo mkdir /mnt/sda6; sudo mount /dev/sda5 /mnt/sda5; sudo mount /dev/sda6 /mnt/sda6; ls /mnt/sda* -R
```

---

### Post by Bucky Ball on 2012-09-12
SlugSlug, as this is the second install my guess is it's on sda6 and that's already mounted along with sda5 which is the swap.

Second guess is that the files required are in the /home directory in sda1, the original install, and that partition may already be listed in the side pane of the file manager, as easy as clicking and it should mount then going to /home and moving the files over. If it won't mount, then:

```
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
```

---

### Post by Stanich on 2012-09-12
Managed to mount it guys, thx. Went with ```
sudo mkdir /storage
```
And than mounting it.

---

### Post by newb85 on 2012-09-12
> **Stanich said:**
> So I've been messing with ubuntu, don't really know how, but I managed to f**k it up, so I had only seen desktop background. As I had no idea what to do, I decided to install Ubuntu once more, on different partition.

F.Y.I., you probably only did something to bork your shell--probably would have been fixable using the CLI in Recovery Mode.

At any rate, glad you're back up and running.

---

