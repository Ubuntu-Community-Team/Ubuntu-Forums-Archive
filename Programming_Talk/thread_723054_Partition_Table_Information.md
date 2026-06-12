---
title: "Partition Table Information"
date: 2008-03-13
forum: Programming Talk
---

### Post by neerajnama on 2008-03-13
hi

I am working with linux kernel 2.6.12, i want to read partition table information for 250 G.B.
harddisk.

I am using 48-bit LBA addressing and i am able to read primary partition information but not able to read extended(information for logical partition) partition information, i found starting sector no of extended partition, when i read from that starting sector i found all zeros 16 bytes information,please tell me how do i read,thanks.

with regards
neeraj

---

### Post by Martin Witte on 2008-03-13
I'm not too sure about your question, do you want to read the output of linux command 'df'?

---

### Post by ebichete on 2008-03-14
There is a library you can use for this kind of information. It is called libparted.

Install libparted and libparted-dev (development files). It should give you all the information you want and more.

---

### Post by tipul07 on 2009-08-26
I tried to read extended partition table too, but got into bogus info when I read first sector of extended partition.
I tried to dump partition table with dd and it worked. So I got dd.c source code and compiled, but when I run it I get same bogus info.
Could it be bcuz of the toolchain used?

When I ldd compiled dd.c code I get:
```

ldd ./dd2
linux-gate.so.1 =>  (0xb7f07000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d89000)
/lib/ld-linux.so.2 (0xb7f08000)

```

But when I ldd distribution dd binary file I get:
```

ldd /bin/dd
linux-gate.so.1 =>  (0xb8027000)
librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb8003000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ea0000)
libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7e86000)
/lib/ld-linux.so.2 (0xb8028000)

```

I know that I can use libparted, but only thing I need to do is present user what partitions he has on a specific hard drive.

So basic ideea is to get MBR and then get starting sector/block of extended partition and then read that sector and extract partion info from that partition table and so on till I finish extended partition chain rite? There is no offset or whatever between starting sector/block and actual location of partition table of that extended table...

Any1 got any ideeas about this?

Regards,
Andy

---

