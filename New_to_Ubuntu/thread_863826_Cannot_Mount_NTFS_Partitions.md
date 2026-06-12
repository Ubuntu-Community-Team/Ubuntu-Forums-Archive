---
title: "Cannot Mount NTFS Partitions"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by techmunkey on 2008-07-18
Had everything working fine and now I cannot mount my two NTFS partitions.I got some updates a few days ago and that was when they stopped responding.

I am running 8.04.1 
[http://picasaweb.google.com/techmunkey/LINUXERRORS](http://picasaweb.google.com/techmunkey/LINUXERRORS)

Linux pecuter 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
System info
Dell Inspiron 1520
Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
Memory 2025 MiB
GeForce 8400M GS
NVIDIA UNIX x86 Kernel Module  173.14.09  Wed Jun  4 23:43:17 PDT 2008

---

### Post by HDave on 2008-07-18
I get this all the time.  Apparently if windows doesn't shut down correct and properly unmount the NTFS partitions, then they have some NTFS flag set that says it is in a questionable state.  However, 99.9% of the time, there is nothing really wrong.

You have two choices:

a) go back into windows and propertly unmount/shutdown the system.
b) use the command line to mount the drives and apply the "force" option yourself

I always go with option b as it is WAY simpler.  Depending on your setup, your mount command will be different, but mine looks like this:

```
sudo mount -f /dev/sdb3 /mnt/winxp
```

Once you do this once, you can re-mount again normally without seeing the error.

---

