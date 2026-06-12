---
title: "Mount Folder to notime and Change Scheduler to deadline"
date: 2017-06-15
forum: New to Ubuntu
---

### Post by amolzambare on 2017-06-15
Hello All,

I have Ubuntu 14.04 VM instance, I am using for riak database as per riak performance tuning data folder must be 'notime' and scheduler set to deadline

1. How to mount notime on folder?
mount -o remount,noatime /var/lib/riak
This not working for me

2. Change scheduler to deadline
cat /sys/block/xvda/queue/scheduler
none


echo deadline /sys/block/xvda/queue/scheduler
deadline

This command dont change scheduler same result none.

Thanks

---

### Post by oldfred on 2017-06-15
I think you left out the redirect > in your command. But that is temporary, see this:
[https://wiki.archlinux.org/index.php/Improving_performance#Tuning_IO_schedulers](https://wiki.archlinux.org/index.php/Improving_performance#Tuning_IO_schedulers)

You should see available schedulers, (the active scheduler is denoted by brackets)But does a VM treat things differently?
cat /sys/block/sd**X**/queue/schedulerold precise used cfq
 fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 
newer trusty uses deadline
fred@trusy-ar:~$ cat /sys/block/sda/queue/scheduler
noop [deadline] cfq  

I permanent mount partitions in fstab with this:
```
# / was on /dev/sda6 during installation
UUID=255a2800-b871-4fdf-a809-16987e64b8b3  /    ext4    noatime,errors=remount-ro 0     1

```

---

