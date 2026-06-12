---
title: "gaprted number absurd"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-03-19
Hi,

Just did a clean insatll of Ubuntu 13.10 on someone's netbook. There are almost no user data in the /home partition yet gparted reports that 11G is used (/dev/sda5, see screenshot) The outputs of df -h on the other hand indicate that there is almost nothing in /home, which is what one would expect

```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        20G  4.0G   15G  22% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           356M  1.1M  355M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.8G  152K  1.8G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda5       664G  402M  630G   1% /home

```

What is going on?

---

### Post by monkeybrain20122 on 2014-03-19
Just checked with gparted using a Fedora live usb, same result: 11G is used in sdb5, where does that come from?

---

### Post by ajgreeny on 2014-03-19
That will be the reserved blocks set aside from the available space to allow for journalling etc etc in an ext# filesystem to make sure it does not run out of space.

It is possible to reduce that if you need to with **tune2fs**,  but is it really worth it? I suspect not on that machine.

See **man tune2fs** for details.

---

### Post by sudodus on 2014-03-19
A newly created Ext filesystems sets a certain percentage of space as available for root user only.

I think your output from df is not counting that space.

---

### Post by monkeybrain20122 on 2014-03-19
11G for administration? Doesn't sound right.

---

### Post by Impavidus on 2014-03-19
675GiB is the size of the partition on the disk. 11GiB is used for file system overhead, leaving 664GiB for storage. This is the number reported by df. Of these 664GiB 5% is reserved for root (which is a bit much nowadays) and 402MiB is used, leaving 630GiB available.

---

### Post by mcduck on 2014-03-19
Actually the reserved space on Ext filesystems is completely different thing from file system overhead (and journalling).

By default, any newly created Ext filesystems sets a certain percentage of space as available for root user only. The reason for this is that Linux systems need to create certain files and folders when the machine is booted, and therefore if any regular user would be able to fill the disk to 100% the system would end being unable to work or even start any more. (Another reason is that while Ext doesn't usually suffer from slow down due to file system fragmentation, it will start to cause issues if the drive gets too full so you'd want to avoid filling it to 100% anyway.)

However, the default reserved percentage has become way too large with the huge hard drives we have these days, and of course if the drive in question is just a storage drive and not a system one, you don't need to worry about the reserved space anyway apart from the fragmentation slowness on too full drive). In these cases you can safely use the "tune2fs" command to reduce or disable the reserved space.

From *tune2fs* man page:
[I]-m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated by privileged  processes.    Reserving
              some number of filesystem blocks for use by privileged processes is done to avoid filesystem fragmenta&#8208;
              tion, and to allow system daemons, such as syslogd(8), to continue to  function  correctly  after  non-
              privileged processes are prevented from writing to the filesystem.  Normally, the default percentage of
              reserved blocks is 5%.
[/I]

---

