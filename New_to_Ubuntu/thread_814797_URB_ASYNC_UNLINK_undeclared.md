---
title: "URB_ASYNC_UNLINK undeclared"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Hirashgeff on 2008-06-01
when I try to install h9601 driver

i did following

in src path of modem Driver    i ran make
but after some time URB_ASYNC_UNLINK undeclared message comes 
and stop processing 
why is this
help

---

### Post by quelx on 2008-06-01
I'm no kernel hacker, but judging from the output from the beginning of **make** I'd say their source doesn't match what the 2.6.24 kernel expects to see.  Given the date of the latest driver *2005-11-18* I think the kernel has changed enough that their driver won't compile against it.

```
gcc -c  -Wall -Wstrict-prototypes -fomit-frame-pointer -fno-strict-aliasing -pipe -fno-strength-reduce -mcpu=i486 -falign-loops=2 -falign-jumps=2 -falign-functions=2  -I/usr/src/linux-source-2.6.24/include -I./inc -I../Gti -D__KERNEL__ -DMODULE  -DGSI_LAN -DGSI_WAN -DNMPX -DQUASAR -DANNEXA -DGTI_USE_INTERNAL_TARGET -DGTI_LITTLE_ENDIAN -DINTERR_OD_LOW_ACT -DGSI_USB -DGTI_USB -DGTI_USE_CUSTOMER_DEFINED_IO -DFAST_SNR_STATUS -DATM_LOOPBACK -DEEPROM -DEEPROMv2 -DCRYSTAL -DGTI_MONACO_USB -DGTI_DSPMONACO -DMONACO -DDBG=0 -DATMSTATISTICS -DGTI_DMT -DDMT -DSOFTSAR -DGSI_USB -O2  -o src/usbbulk.o src/usbbulk.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
In file included from /usr/src/linux-source-2.6.24/include/linux/string.h:11,
                 from ./inc/common.h:62,
                 from ./inc/GpSnull.h:8,
                 from ./inc/Gp.h:16,
                 from src/usbbulk.c:22:
/usr/src/linux-source-2.6.24/include/linux/types.h:197: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘resource_size_t’
In file included from ./inc/common.h:62,
                 from ./inc/GpSnull.h:8,
                 from ./inc/Gp.h:16,
                 from src/usbbulk.c:22:
/usr/src/linux-source-2.6.24/include/linux/string.h:19:24: error: asm/string.h: No such file or directory
In file included from ./inc/common.h:62,
                 from ./inc/GpSnull.h:8,
                 from ./inc/Gp.h:16,
                 from src/usbbulk.c:22:

```

---

