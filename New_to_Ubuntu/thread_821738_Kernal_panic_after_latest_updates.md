---
title: "Kernal panic after latest updates"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by saratchandra on 2008-06-07
I'm unable to boot to the latest kernel sometimes. I get the error message
> Kernel panic: VFS: unable to mount root fs on unknown-block(0,0) 

I can login to the old kernel version and run everything properly. It is fixing itself after a few boots to the old kernel. I updated to Linux 2.6.24-18-generic (x86_64). Please help:(:(

P.S I'm dual booting with windows

---

### Post by Chelives1928 on 2008-09-21
Have you found a fix to this yet?  I have the same problem.  I have a Hard drive with windows and Hardy dual booting.  I went to upgrade to Intrepid and then upon reboot I had that same error message.  I can't access anything unless i'm on an old Hardy live cd.  I've searched the forums and no luck yet.  here is what comes up when i hit fdisk

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
48 heads, 46 sectors/track, 442379 cylinders
Units = cylinders of 2208 * 512 = 1130496 bytes
Disk identifier: 0xba07c583

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *       23190      442379   462784512    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e952e94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       22585   181413981    7  HPFS/NTFS
/dev/sdb2           22586       22950     2931862+  82  Linux swap / Solaris
/dev/sdb3           22951       30401    59850157+  83  Linux

Disk /dev/sdd: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   
```

---

### Post by Chelives1928 on 2008-09-21
Bump

---

### Post by saratchandra on 2008-09-23
I booted to the old kernel and reinstalled the new kernel using synaptic. Never had the problem again.

---

