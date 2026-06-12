---
title: "Dkms fails to build nvidia module for kernel 3.0-01"
date: 2011-06-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-06-10
New 3 series kernel (3.0-01) rc2 will be soon in Oneiric repos.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0-0.1](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0-0.1)

State in Launchpad is still new, so to test this, it must be downloaded manually.

I did try to install this kernel.
I am using nvidia-current (propietary dirvers) version 275.09.
However, nvidia module installation failed, dkms could not build it.

Could it be that nvidia drivers do not yet support this kernel.

---

### Post by dino99 on 2011-06-10
have you tried with the 260.xx version ?

---

### Post by Harry33 on 2011-06-10
> **dino99 said:**
> have you tried with the 260.xx version ?

No I haven't.
I thought this newer beta version has the latest support for newer software.
Also, the latest stable is 270.41.19.
The latest in Oneiric repos is 270.41.06.

---

### Post by portis on 2011-06-10
I managed to workaround this compile error.
If you are interested, you can do:

1. patch /usr/src/linux-3.0-0-generic/include/linux/rcupdate.h
  according to [http://choon.net/forum/read.php?21,82725](http://choon.net/forum/read.php?21,82725)

2. this file /usr/src/nvidia-current-275.09.04/dkms.conf prevents build with kernels newer than 2.6, so you have to modify the line:
          OBSOLETE_BY=3.0.0

3. in the file /usr/src/nvidia-current-275.09.04/nv-linux.h, there's a section:
#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 4, 7)
#  error This driver does not support 2.4 kernels older than 2.4.7!
#elif LINUX_VERSION_CODE < KERNEL_VERSION(2, 5, 0)
#  define KERNEL_2_4
#elif LINUX_VERSION_CODE < KERNEL_VERSION(2, 6, 0)
#  error This driver does not support 2.5 kernels!
#elif LINUX_VERSION_CODE < KERNEL_VERSION(2, 7, 0)
#  define KERNEL_2_6
#else
#  error BLAHBLAH
#endif

so you have to replace error BLAHBLAH with something like   define KERNEL_2_6
so that we pretend it's a 2.6 kernel.


You should then run

sudo dkms build -m nvidia-current -v 275.09.04 -k 3.0-0-generic
sudo dkms install -m nvidia-current -v 275.09.04 -k 3.0-0-generic



I installed 275.09.04 version of nvidia driver, so far so good.

---

### Post by dino99 on 2011-06-10
seems that nobody have reported that issue yet. As Portis have found a work around, it should be usefull to open a bug report to let the nvidia users running the new kernel.

Will wait a few hours then report it if not done.

Edit: filled as  Bug #795562

---

### Post by Harry33 on 2011-06-11
OK now this is fixed.
Xorg-edgers great PPA does have the newest beta nvidia-current 275.09.04 with hte kernel 3.0 patch.

Now the installation of the Oneiric kernel 3.0-01 rc2 works well.

---

### Post by IntuitiveNipple on 2011-06-15
I thought I'd record here a fix for a related build issue for nvidia-current (270.29) with Lucid using kernel 3.0.0.

Since the Linux kernel has finally removed the Big Kernel Lock (BKL) the file **include/linux/smp_lock.h** has been deleted. However, the nvdia source still includes it (although the nvdia module doesn't call the declared functions).

The solution is to remove the include directive from **/usr/src/nvidia-current-270.29/nv-linux.h**. Here I've enclosed it in an #if 0 preprocessor expression, which means the code will not be used:

```
#if !defined(KERNEL_2_4)
#include <linux/sched.h>            /* suser(), capable() replacement   */
#include <linux/moduleparam.h>      /* module_param()                   */
#if 0
#include <linux/smp_lock.h>         /* kernel_locked                    */
#endif
#include <asm/tlbflush.h>           /* flush_tlb(), flush_tlb_all()     */
#include <asm/kmap_types.h>         /* page table entry lookup          */
#endif
```

---

### Post by Harry33 on 2011-06-15
> **IntuitiveNipple said:**
> I thought I'd record here a fix for a related build issue for nvidia-current (270.29) with Lucid using kernel 3.0.0.

Since the Linux kernel has finally removed the Big Kernel Lock (BKL) the file **include/linux/smp_lock.h** has been deleted. However, the nvdia source still includes it (although the nvdia module doesn't call the declared functions).

The solution is to remove the include directive from **/usr/src/nvidia-current-270.29/nv-linux.h**. Here I've enclosed it in an #if 0 preprocessor expression, which means the code will not be used:

```
#if !defined(KERNEL_2_4)
#include <linux/sched.h>            /* suser(), capable() replacement   */
#include <linux/moduleparam.h>      /* module_param()                   */
#if 0
#include <linux/smp_lock.h>         /* kernel_locked                    */
#endif
#include <asm/tlbflush.h>           /* flush_tlb(), flush_tlb_all()     */
#include <asm/kmap_types.h>         /* page table entry lookup          */
#endif
```

This is the Oneiric Development Forum, not for Lucid.
This issue in Oneiric has been completely fixed, both in Oneiric official repos (270.41.19) and in xorg-edgers (nvidia-current 275.09.07).

---

