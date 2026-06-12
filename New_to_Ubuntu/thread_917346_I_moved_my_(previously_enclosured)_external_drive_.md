---
title: "I moved my (previously enclosured) external drive internally...how do I mount?"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-09-11
I had a 750gb internal drive that I used with an external enclosure that contained all of my music and other personal files.  I just bought a new server to I decided to take off the enclosure and use it internally.  I have everything hooked up...but how do I get Ubuntu Server to read the drive?  I obviously don't want to format everything...I just want it to show up like it used to when it was external with all of my files in-tact.  Any help would be appreciated.

---

### Post by knattlhuber on 2008-09-11
You just need to change the location of the drive (the part that says /dev/sdxx) in /etc/fstab. The mount point will remain the same. Upon restart, it should mount automatically.

---

### Post by TMcKSmith on 2008-09-12
> **knattlhuber said:**
> You just need to change the location of the drive (the part that says /dev/sdxx) in /etc/fstab. The mount point will remain the same. Upon restart, it should mount automatically.

I never actually "mounted" the external drive though in the fstab before - I just would plug it in while my Xubuntu was loaded and it would mount automatically...so I don't know what location to put.

---

### Post by WRDN on 2008-09-12
> **TMcKSmith said:**
> I never actually "mounted" the external drive though in the fstab before - I just would plug it in while my Xubuntu was loaded and it would mount automatically...so I don't know what location to put.

If Xubuntu has the equivalent of "Computer" in Ubuntu, look there for the drive. Otherwise, you can mount it manually.

First type:

```
sudo fdisk -l
```

This will allow you to find the device ID for the drive. It will have the format /dev/sdaN or /dev/hdaN (where N represents the number). The "a" in /dev/sda can also be different and refers to the physical drive ID. For example, if the first drive was /dev/sda then the second would be /dev/sdb and the third would be /dev/sdc etc.

Once you've found this, make a mount point for the partition:

```
sudo mkdir /media/files
```

You can replace "files" with something else if you wish.

Now, mount the drive:

```
sudo mount /dev/[device] /media/files
```


To automatically mount the drive:

```
sudo gedit /etc/fstab
```

Now, add the line:

> /dev/[device] /media/files ext3 defaults 0 0

You will have to replace the device ID, the mount point (if you change the name) and you may have to change the filesystem from "ext3" to whatever filesystem is in use.

---

