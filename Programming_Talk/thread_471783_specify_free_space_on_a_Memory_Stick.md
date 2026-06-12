---
title: "specify free space on a Memory Stick?"
date: 2007-06-12
forum: Programming Talk
---

### Post by kcy29581 on 2007-06-12
Hi all,

I need to specify the exact amount of free space on a Memory Stick, for work.

For example I have a 64 Mb Memory Stick, and I need it to have exactly 2272 kb of free space.

I know how to create a dummy file using dd and /dev/zero, in case this helps:
```
dd bs=1024k count=1 if=/dev/zero of=dummy
```

Anyone able to help?

---

### Post by Ramses de Norre on 2007-06-12
Use the df (disk free) command and give it the appropriate block size:
```
df --block-size=1kB /media/your_device
```

---

