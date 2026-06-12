---
title: "Mounting an external hard disk and fstab settings"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2013-05-24
Hello

Yesterday, I reformatted my external hard drive ext4, from the ntfs that was on there before.
But when I go to mount the drive, it says that only root can do that.

I added the drive to /etc/fstab:

```

/dev/sdh1    /media/Seagate   ext4    defaults     0        2

```

Are there any other parameters I need to enter in fstab to get the drive to mount automatically when it is plugged in? Or should I pursue a different solution?

Thanks.

---

### Post by dargaud on 2013-05-24
You should use a UUID instead of /dev/sdh1 which can change from one reboot to the next. Here's a simple example:

UUID=c4772215-281a-4372-8818-1be03b790637 /Big ext4 noatime,relatime 0 0

Then do sudo mount -a

---

### Post by Senior_Buckethead on 2013-05-24
Here is the entry in fstab:
```

# Seagate External HDD
UUID=d4964716-bc5b-43b2-bfa3-379daf0a068d /Big ext4 noatime,relatime 0 0

```

I was looking at the fstab..DUH Glenn.. WHERES THE MOUNT POINT..!!

so now, fstab entry is:
```

# Seagate External HDD
UUID=d4964716-bc5b-43b2-bfa3-379daf0a068d /media/Seagate ext4 noatime,relatime 0 0

```

And it mounts on start and is tickedy boo.

#SOLVED.

---

