---
title: "[SOLVED] How to find out hard disk and Add/Remove problem"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by JoHenning on 2008-10-18
Ok

i got a computer for free, i don't know exactly how many hard disks i have and how big they are, how can i find that out?

Then i tried to install a program using the Add/remove application but it always tells me:


An error occured
E: dpkg was interupted, you must manually run 'dpkg --configure-a' to correct the problem.
E:_cache->open()failed, please report.

what do i have to do?
thanks

---

### Post by jimmy the saint on 2008-10-18
sound to me like you need to run
```
dpkg --configure-a
```
to correct the problem.  As for the disk information you could run fdisk or go to system>administration>partition editor and look at what is there.

---

### Post by scragar on 2008-10-18
```
sudo fdisk -l
```will list HDs and partitions on them.
```
sudo dpkg --configure -a
```will sort out your install problems.

---

### Post by JoHenning on 2008-10-18
ok thanks the add/remove works again

however it told me i have a broken package and i shoudl locate it, but im not really sure how to do that?

---

### Post by drs305 on 2008-10-18
Another useful command for looking at your disks is:
```
df -Th | grep /dev/sd
```
(You can also run it simply as "df -Th" but you will get some generally extraneous information.)
It provides output similar to this: 
Partition, format, partition size, used, available, percentage used, mountpoint.
```

~: df -Th | grep /dev/sd
/dev/sda1     ext3     23G  9.4G   12G  45% /
/dev/sda2     ext3     34G  2.1G   30G   7% /home
/dev/sda3     ext3     31G  2.0G   27G   7% /media/data
/dev/sda5     ext3     50G   21G   27G  44% /media/data2
/dev/sda6     ext3    9.9G  461M  9.0G   5% /media/gparted
/dev/sdb1     ext3     68G   22G   43G  34% /media/VM
/dev/sdb2     ext3     29G   11G   18G  38% /media/backup
/dev/sdb3     ext3     88G   72G   14G  85% /media/backup.images

```

---

### Post by SunnyRabbiera on 2008-10-18
> **JoHenning said:**
> ok thanks the add/remove works again

however it told me i have a broken package and i shoudl locate it, but im not really sure how to do that?

Add/remove is a basic installer application.
For something more advanced try synaptic located under system> administration> synaptic package manager.
Synaptic can show you what packages are broken by going into "status" or "custom filters" and selecting "broken"
also you can go up to the menu and go to "edit" and select "find broken packages"

---

### Post by scragar on 2008-10-18
> **SunnyRabbiera said:**
> Add/remove is a basic installer application.
For something more advanced try synaptic located under system> administration> synaptic package manager.
Synaptic can show you what packages are broken by going into "status" or "custom filters" and selecting "broken"
also you can go up to the menu and go to "edit" and select "find broken packages"

or, you know, you could just run:
```
sudo apt-get install -f
```
to fix broken dependencies...

---

### Post by SunnyRabbiera on 2008-10-18
well just in case he doesnt want to do it the command line way.
Not everyones a command line guru you know.

---

### Post by scragar on 2008-10-18
Command line is easier to recive feedback from and it's faster, easier to explain, and harder to someone mess up, or miss something. I would much rather recive isntructions for a command to run, than, say a set of gui instructions.

---

### Post by JoHenning on 2008-10-18
well the add remove thing is fixed, thanks for that

it told me there was abroken package however i couldnt find it using synaptic so i guess its fixed too...

---

### Post by SunnyRabbiera on 2008-10-18
> **JoHenning said:**
> well the add remove thing is fixed, thanks for that

it told me there was abroken package however i couldnt find it using synaptic so i guess its fixed too...

it might have been a false positive or something, who knows.

---

