---
title: "Hard Disk Partition Ownership Change"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by clovisdecruz on 2013-06-15
Hello Everyone,

I have just created a logical partition in an extended partition using gparted partition extender. 

The name of my partition is New Data Logical. 
It's an ext2 filesystem
Path is /dev/sda5
Mount point is /media/clovis/New Data Logical
UUID is c3829704-d24f-4f50-86cf-c879b4658f3b

I'm not able to use this partition because it states that root is the owner. I'm not sure why it makes root the owner because I ran the GUI program using my administrator user account 'Clovis'.

How do i change the ownership to my 'Clovis' account? How do i ensure that a future partition created gives the logged on account access?

Thanks.
Clovis

---

### Post by prodigy_ on 2013-06-15
Any particular reason for using ext2? I guess not. It's still the default FS in gparted (d'oh!) but if the partition is still empty you should reformat with ext4 for journaling and better performance. Open Terminal and type: ```
sudo umount /dev/sda5
sudo mkfs.ext4 /dev/sda5
```

Re. your actual question - for extX file systems you can simply take ownership on everything recursively after mounting the partition:
```
sudo mount /dev/sda5 "/media/clovis/New Data Logical"
id=$(id -u) # no sudo here
sudo chown -R $id:$id "/media/clovis/New Data Logical"
```

Take note that root always owns a *partition* (as a block device, such as /dev/sda1). You can only take ownership on *file system* objects.

---

### Post by The Cog on 2013-06-15
An ext2/3/4 filesystem stores proper unix permissions, per directory and file. A newly formatted filesystem is owned by root. You can give ownership to whoever you like, and can give whatever permissions you like to the root of the filesystem. This makes the root of the filesystem owned by clovis, which group permissions for clovis:
```
sudo chown clovis:clovis /media/clovis/New Data Logical
```

When you ran the GUI to make the partition, you were doing so as root. No other user has the rights to make that kind of change. You gave your password to confirm your identity and be allowed to "borrow" root's id. In the avove command, "sudo" says you want to borrow root's identity - kind of like "run as administrator".

EDIT
As pointed out later on, you need quotes round names with spaces. Like this:
```
sudo chown clovis:clovis "/media/clovis/New Data Logical"
```
My bad.

---

### Post by clovisdecruz on 2013-06-15
Thanks Cog and Prodigy for your replies
After unmounting it and reformating it to ext4 I had to run the following command to make it work

sudo chown -R clovis:clovis /dev/sda5

For some reason its not accepting the volume name.

Thanks for your help.

---

### Post by prodigy_ on 2013-06-15
> **clovisdecruz said:**
> sudo chown -R clovis:clovis **/dev/sda5**
Reboot and you'll see that /dev/sda5 is still owned by root. Again, don't try to take ownership on block devices (or anything in /dev for that matter). 

There are ways to mount partitions as user without sudo:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by ajgreeny on 2013-06-15
> **clovisdecruz said:**
> Thanks Cog and Prodigy for your replies
After unmounting it and reformating it to ext4 I had to run the following command to make it work

sudo chown -R clovis:clovis /dev/sda5

For some reason its not accepting the volume name.

Thanks for your help.

Having re-formatted the partition/disk did you label it again as New Data Logical, or did you forget?  Also, when using the chown command, did you realise you need quotes in the command ```
sudo chown clovis:clovis. "/media/clovis/New Data Logical"
``` for the pathway, which unfortunately, The Cog omitted in his last post.

It is very easy to forget such quotes, which is precisely why I always use underscores in labels, folder or file names in linux in place of spaces; it makes life much simpler in the long run.

---

### Post by oldfred on 2013-06-15
I have always had trouble with spaces, so I stopped using them. You often need to escape them or add quotes to get them to work.

I now use CamelCase, under_score, or justonelongname to avoid spaces.

---

### Post by Rebelli0us on 2013-06-15
You can also use the Nautilus file manager (Permissions tab) to create directories and take ownership.

---

