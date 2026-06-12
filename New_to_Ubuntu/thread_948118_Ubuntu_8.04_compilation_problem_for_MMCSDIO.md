---
title: "Ubuntu 8.04 compilation problem for MMC/SDIO"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by yamitmehta on 2008-10-14
Hello,

I downloaded the linux source for Ubuntu 8.04.
I tried to compile by 
fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers

given in the procuedure mentioned in
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
Alternate Build Method: The Old-Fashioned Debian Way

In compilation I am getting the following errors:-


 LD      drivers/mmc/host/built-in.o
  CC      drivers/mmc/mss/mss_core.o
drivers/mmc/mss/mss_core.c: In function ‘mss_eject_card’:
drivers/mmc/mss/mss_core.c:443: warning: format ‘%x’ expects type ‘unsigned int’, but argument 5 has type ‘struct mss_card *’
drivers/mmc/mss/mss_core.c: In function ‘mss_detect_change’:
drivers/mmc/mss/mss_core.c:592: warning: passing argument 1 of ‘schedule_work’ from incompatible pointer type
drivers/mmc/mss/mss_core.c: In function ‘mss_alloc_host’:
drivers/mmc/mss/mss_core.c:841: warning: assignment from incompatible pointer type
drivers/mmc/mss/mss_core.c: At top level:
drivers/mmc/mss/mss_core.c:249: warning: ‘mss_finish_request’ defined but not used
  CC      drivers/mmc/mss/mmc_protocol.o
drivers/mmc/mss/mmc_protocol.c: In function ‘mmc_card_init’:
drivers/mmc/mss/mmc_protocol.c:619: error: ‘struct scatterlist’ has no member named ‘page’
make[4]: *** [drivers/mmc/mss/mmc_protocol.o] Error 1
make[3]: *** [drivers/mmc/mss] Error 2
make[2]: *** [drivers/mmc] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.24'
make: *** [debian/stamp-build-kernel] Error 2


Please help me

[email]yamitmehta@rediffmail.com[/email]

---

