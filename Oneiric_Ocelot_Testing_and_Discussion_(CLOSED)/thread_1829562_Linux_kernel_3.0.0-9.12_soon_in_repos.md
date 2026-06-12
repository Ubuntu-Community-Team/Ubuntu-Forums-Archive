---
title: "Linux kernel 3.0.0-9.12 soon in repos"
date: 2011-08-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-20
The new linux kernel version 3.0.0-9.12 (= 3.0.3) is building in Launchpad and will soon be in Oneiric repos.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-9.12](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-9.12)

> **Changelog**
linux (3.0.0-9.12) oneiric; urgency=low

  [ Andy Whitcroft ]

  * [Config] standardise CONFIG_NETFILTER_XT_TARGET_TCPOPTSTRIP=m
  * [Config] move ECRYPT_FS back to =y for all architectures
    - LP: #827197
  * record the compiler in the ABI and check for inconsistant builds

  [ Leann Ogasawara ]

  * Revert "SAUCE: OMAP: DSS2: enable hsclk in dsi_pll_init for OMAP36XX"
  * Revert "SAUCE: OMAP: DSS2: check for both cpu type and revision, rather
    than just revision"
  * Revert "SAUCE: ARM: OMAP: Add macros for comparing silicon revision"
  * rebase to v3.0.2
  * rebase to v3.0.3
  * Temporarily ignore module check
  * [Config] Set CONFIG_DM_MIRROR=m on amd64, i386, and arm
  * [Config] Set CONFIG_DM_MULTIPATH=m on amd64, i386, and arm
  * [Config] Set CONFIG_DM_SNAPSHOT=m on amd64, i386, and arm
  * [Config] Enable CONFIG_EDAC_AMD8111=m on powerpc
  * [Config] Enable CONFIG_EDAC_AMD8131=m on powerpc
  * [Config] Enable CONFIG_EDAC_CPC925=m on powerpc
  * [Config] Enable CONFIG_EDAC_PASEMI=m on powerpc
  * [Config] Set CONFIG_EFI_VARS=m on amd64 and i386

  [ Stefan Bader ]

  * [Upstream] xen-blkfront: Drop name and minor adjustments for emulated
    scsi devices
    - LP: #784937
  * [Config] Force perf to use libiberty for demangling
    - LP: #783660

  [ Stefano Stabellini ]

  * [Upstream] xen: Do not enable PV IPIs when vector callback not present
    - LP: #791850

  [ Tim Gardner ]

  * [Config] updateconfigs after rebase to 3.0.2

  [ Upstream Kernel Changes ]

  * Not all systems expose a firmware or platform mechanism for changing
    the backlight intensity on i915, so add native driver support.
    - LP: #568611
  * rebase to v3.0.2
  * rebase to v3.0.3
 -- Leann Ogasawara <email address hidden>   Mon, 15 Aug 2011 13:35:57 -0700

---

### Post by dino99 on 2011-08-21
installed but get:

Error! Module version 4.1.0_Ubuntu for vboxdrv.ko
is not newer than what is already found in kernel 3.0.0-9-generic-pae (4.1.2).
You may override by specifying --force.

and some others related too.

---

### Post by xebian on 2011-08-21
The versioning is a little confusing.
If it's 3.0.3 shouldn't it be 3.0.3-n-generic?  The 3.0.0-n-generic looks like it's a 3.0.0 iteration.

---

### Post by tekstr1der on 2011-08-21
Agreed. If they stick with this new convention going forward, the 3.1.x series kernels will be 3.1.0-n. This means the 3rd digit will always be zero on Ubuntu kernel spins. Makes no sense to me!

---

### Post by cecilpierce on 2011-08-21
And still all those errors on boot.

---

### Post by Gunss on 2011-08-22
I'm using lowlatency tree kernel and the performance improved a lot! It should be somehow the default kernel.

I've a slow machine with dual core 2.53Ghz + 1GB ddr2 of memory and everything are better.

---

