---
title: "Manually turn off secondary HDD in optical bay?"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by Zenrunner92 on 2012-01-22
I recently installed a dual boot (Ubuntu 10.04 and Win 7) SSD on my laptop, then moved my old HDD to the optical bay for media/doc storage only.  

Anyway, I hear/feel it spinning and humming constantly even when not in use.  Is there a command or a setting I can use to have it spin down (if that's the correct verb) unless I am actually using it to read or write data?

Would like to conserve power, reduce heat (though it doesn't feel hot) in a bay that wasn't expressedly designed for it) and possibly prolong HDD's lifespan.

---

### Post by Frogs Hair on 2012-01-22
I think there is a spin-down disks when ever possible option in power management om 10.04 .

---

### Post by Zenrunner92 on 2012-01-23
How would that "spin down" command affect my onboard OS drive which is an SSD?  I wish there was a way to specify which drive does what.

---

### Post by Grenage on 2012-01-23
I have soon only one case where power-saving functions caused problems with an SSD - and that was a long time ago.  I'd enable it and see how it fares.

---

### Post by matt_symes on 2012-01-23
Hi

Take a look at 

```
man hdparm
```or search for it on the Internet.

You can set the power management features for the rotatory hard drive using that command.

I have never used it wit an SSD but i would be very surprised it if did not work.

Kind regards

---

### Post by dargaud on 2012-01-23
In Ubuntu I've never been able to get a secondary non-system disk to spin down for more than a few seconds. I issue the hdparm command, I hear it spin down, and it starts spinning right back up, all the while lsof shows no activity on the disk.

---

### Post by matt_symes on 2012-01-23
Hi

> **dargaud said:**
> In Ubuntu I've never been able to get a secondary non-system disk to spin down for more than a few seconds. I issue the hdparm command, I hear it spin down, and it starts spinning right back up, all the while lsof shows no activity on the disk.

Are you really in Antarctica ? :p

To see what is trying to access the drive you can run this command from a terminal

 ```
echo 1 | sudo tee /proc/sys/vm/block_dump
```and then see what is accessing the drive using

```
tail -f /var/log/syslog
```or by reading the kernel ring buffer using dmesg.

That may point to why the drive is not staying spinned down.

Kind regards

---

### Post by dargaud on 2012-01-23
> **matt_symes said:**
> Are you really in Antarctica ? :p
Not at the moment, but [I used to]("http://www.gdargaud.net/Antarctica/").

```
echo 1 | sudo tee /proc/sys/vm/block_dump
tail -f /var/log/syslog
```

Thanks, I didn't know this trick. Well, I just tried it, and  it seems to be nfs:
```
Jan 23 19:27:52 penguin kernel: [69735.971773] nfsd(3150): dirtied inode 59375645 (1998 - Cassandra) on dm-0
Jan 23 19:27:53 penguin kernel: [69735.996276] nfsd(3150): dirtied inode 59375646 (2000 - Image) on dm-0
Jan 23 19:27:58 penguin kernel: [69741.824128] jbd2/dm-0-8(3009): WRITE block 2927888576 on dm-0 (8 sectors)
Jan 23 19:27:58 penguin kernel: [69741.824154] jbd2/dm-0-8(3009): WRITE block 2927888584 on dm-0 (8 sectors)

```

---

