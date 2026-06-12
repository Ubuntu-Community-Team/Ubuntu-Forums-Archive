---
title: "getting partitions in python"
date: 2007-06-17
forum: Programming Talk
---

### Post by Borzo on 2007-06-17
Hi All,

Is it possible to get the patition list from Python?, something like fdisk -l output?

thanks

---

### Post by meatpan on 2007-06-17
I'm not sure about python packages for this task, but there should be a /proc/partitions file on your machine.  The /proc filesytems has a ton of useful data structures that are used by the kernel, and many of them are open for inspection by users.

That said, consider opening and parsing the /proc/partitions file.  Perhaps you can make a little class that will wrap this.

Here is what the file looks like on my machine:
```

major minor  #blocks  name

   8     0   17783239 sda
   8     1     104391 sda1
   8     2   17671500 sda2
   8    16   71687325 sdb
   8    17   71681998 sdb1
 253     0   15597568 dm-0
 253     1    2031616 dm-1

```

You could make a 'partition' class, which is a single entry from this list (4 files/members), and then a method to create a list of these classes.

This actually sounds like a pretty useful extension.  Let me know what you come up with!

---

### Post by pmasiar on 2007-06-17
you can execute any shell command frpm Python, save results to a file and then parse them.

---

### Post by Smygis on 2007-06-17
```

>>> import commands
>>> mnt = commands.getoutput("mount")
>>> print mnt
/dev/hdb6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hdb7 on /boot type ext3 (rw)
/dev/hdb8 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type ext3 (rw)
/dev/hda2 on /media/hda2 type ext3 (rw)
/dev/hdg1 on /media/hdg1 type vfat (rw,utf8,umask=007,gid=46)
>>> 

```

Something like that?

And you can do;

```

>>> mnt = commands.getoutput("cat /proc/partitions")
>>> print mnt
major minor  #blocks  name

   3     0   19551168 hda
   3     1    6345675 hda1
   3     2   13205398 hda2
   3    64   19551168 hdb
   3    66          1 hdb2
   3    69     835348 hdb5
   3    70    9767425 hdb6
   3    71     192748 hdb7
   3    72    8755393 hdb8
  34     0   19551168 hdg
  34     1   19542568 hdg1
   8     0     992000 sda
   8     1     991747 sda1
>>> 

```

aswell

---

### Post by WW on 2007-06-17
Since /proc/partitions is a file, there is no need to use 'cat' with commands.getoutput().  Just read the file:
```

>>> procfile = open("/proc/partitions")
>>> parts = [p.split() for p in procfile.readlines()[2:]]
>>> procfile.close()
>>> parts[0]
['3', '0', '117220824', 'hda']
>>> parts[1]
['3', '1', '14651248', 'hda1']
>>>

```

---

### Post by Borzo on 2007-06-17
I think i will go for either running a shell command and parsing it or reading /proc/partitions, but does /proc/partitions list the partition type aswell? ( blocks and name are obvious but i don't know what minor/major are )

thanks

---

