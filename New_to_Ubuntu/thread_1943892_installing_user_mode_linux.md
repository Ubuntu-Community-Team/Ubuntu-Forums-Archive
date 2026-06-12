---
title: "installing user mode linux"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by kaazzz on 2012-03-20
i tried to install user mode linux but failed to compalil the kernal 
the error log is:
gcc -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -O2 -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -D__arch_um__ -DSUBARCH=\"x86_64\" -Dvmap=kernel_vmap -Din6addr_loopback=kernel_in6addr_loopback -Iarch/um/include  -I/home/gman/linux-2.6.15.1/arch/um/kernel/tt/include  -I/home/gman/linux-2.6.15.1/arch/um/kernel/skas/include -D_FILE_OFFSET_BITS=64 -fno-builtin -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -S -o arch/um/user-offsets.s arch/um/sys-x86_64/user-offsets.c
arch/um/sys-x86_64/user-offsets.c:14:22: fatal error: asm/user.h: No such file or directory
compilation terminated.
 
how can i fix this help me:popcorn::confused:

---

### Post by Jest3r on 2012-03-24
Hello,

 I think you are running in to problems because the asm/user.h has been moved into sys/user.h, with some updates as well.

 
Perhaps updating the kernel that you are trying to compile or upgrading the version of user mode linux will get around the issues.

2.6.15.1 was release in 2006

---

