---
title: "How to add patch in Ubuntu/Linux?"
date: 2009-11-09
forum: Programming Talk
---

### Post by K-Z on 2009-11-09
hey....this is Kshitiz. I am new to linux. I have designed a scheduling algorithm which I want to in Linux. Can you please guide me how to proceed for that or what material I should refer??

---

### Post by StunnerAlpha on 2009-11-09
You want to implement your scheduling algorithm within the Linux kernel itself? Or you need to make an application?

---

### Post by K-Z on 2009-11-13
> **StunnerAlpha said:**
> You want to implement your scheduling algorithm within the Linux kernel itself? Or you need to make an application?

I want to implement scheduling algorithm.....

---

### Post by Zugzwang on 2009-11-13
> **K-Z said:**
> I want to implement scheduling algorithm.....

I'm afraid that this does not answer the question.

---

### Post by K-Z on 2009-11-14
I want to implement scheduling algorithm in linux kernel.....can you please help me how to proceed for that. I have downloaded source code "sched.c" but I am not able to understand that code. can I get complete documentation for the code????? Please give me the link....

---

### Post by dwhitney67 on 2009-11-14
> **K-Z said:**
> I want to implement scheduling algorithm in linux kernel.....can you please help me how to proceed for that. I have downloaded source code "sched.c" but I am not able to understand that code. can I get complete documentation for the code????? Please give me the link....

I hate to be the one to 'rain on your parade', but if you cannot understand the basics of the kernel code, how to rebuild it, etc., I don't think you are ready to deploy your new scheduling algorithm.

Building the kernel is fairly trivial (with the appropriate instructions), so if you want to give it a go, here's some help:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
[http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

However, patching individual kernel module(s) may require deeper knowledge of C and the kernel library.

P.S.  If you have a patch file, you can use the 'patch' utility to merge your changes with the original file(s).  The command usages looks something like:
```

patch -p1 MyFile.patch

```
A patch file, which is generated using the utility 'diff', looks something like:
```

Submitted By: Jim Gifford (patches at jg555 dot com)
Date: 2005-10-29
Initial Package Version: 2.6.14
Origin: Grant Gundler (parisc linux)
Upstream Status: in -mm
Description: Make the tulip drivers follow the chipset specs

diff -Naur linux-2.6.14.orig/drivers/net/tulip/21142.c linux-2.6.14/drivers/net/tulip/21142.c
--- linux-2.6.14.orig/drivers/net/tulip/21142.c 2005-10-28 00:02:08.000000000 +0000
+++ linux-2.6.14/drivers/net/tulip/21142.c      2005-10-30 03:54:09.000000000 +0000
@@ -172,7 +172,7 @@
                        int i;
                        for (i = 0; i < tp->mtable->leafcount; i++)
                                if (tp->mtable->mleaf[i].media == dev->if_port) {
-                                       int startup = ! ((tp->chip_id == DC21143 && (tp->revision == 48 || tp->revision == 65)));
+                                       int startup = ! ((tp->chip_id == DC21143 && tp->revision == 65));
                                        tp->cur_index = i;
                                        tulip_select_media(dev, startup);
                                        setup_done = 1;
diff -Naur linux-2.6.14.orig/drivers/net/tulip/media.c linux-2.6.14/drivers/net/tulip/media.c
--- linux-2.6.14.orig/drivers/net/tulip/media.c 2005-10-28 00:02:08.000000000 +0000
+++ linux-2.6.14/drivers/net/tulip/media.c      2005-10-30 03:54:09.000000000 +0000
@@ -44,8 +44,10 @@

 /* MII transceiver control section.
    Read and write the MII registers using software-generated serial
-   MDIO protocol.  See the MII specifications or DP83840A data sheet
-   for details. */
+   MDIO protocol.
+   See IEEE 802.3-2002.pdf (Section 2, Chapter "22.2.4 Management functions")
+   or DP83840A data sheet for more details.
+   */

 int tulip_mdio_read(struct net_device *dev, int phy_id, int location)
 {
@@ -261,24 +263,56 @@
                                u16 *reset_sequence = &((u16*)(p+3))[init_length];
                                int reset_length = p[2 + init_length*2];
                                misc_info = reset_sequence + reset_length;
-                               if (startup)
+                               if (startup) {
+                                       int timeout = 10;       /* max 1 ms */
                                        for (i = 0; i < reset_length; i++)
                                                iowrite32(get_u16(&reset_sequence[i]) << 16, ioaddr + CSR15);
+                               
+                                       /* flush posted writes */
+                                       ioread32(ioaddr + CSR15);
+
+                                       /* Sect 3.10.3 in DP83840A.pdf (p39) */
+                                       udelay(500);
+
+                                       /* Section 4.2 in DP83840A.pdf (p43) */
+                                       /* and IEEE 802.3 "22.2.4.1.1 Reset" */
+                                       while (timeout-- &&
+                                               (tulip_mdio_read (dev, phy_num, MII_BMCR) & BMCR_RESET))
...

```

---

