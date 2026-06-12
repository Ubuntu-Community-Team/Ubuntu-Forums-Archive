---
title: "wubi?"
date: 2014-03-17
forum: New to Ubuntu
---

### Post by newbietwo on 2014-03-17
I know WUBI is frowned upon.  I have heard that in 13.04 and 13.10 it is unreliable.

Is the WUBI in 12.04 reliable and the recommended one if you choose to use it?

I do not want to partition a relatively new Windows 8.1 hard drive even though I have done it many times before with Gparted.  Thanks.

---

### Post by Impavidus on 2014-03-17
The biggest problem of wubi is that it doesn't work with Windows 8. Or more specifically, systems with UEFI and GPT partitioning, which is typically used by Win 8, always on preinstalled systems.

---

### Post by mastablasta on 2014-03-17
furthermore it is not maintained anymore.

---

### Post by oldfred on 2014-03-17
If you have gpt partitioning there is no more 4 primary partition limit, so adding partitions is easy. It just is the entire Windows & secure boot and fast boot issues have made any install a bit more difficult.
Just use Windows to shrink Windows and reboot a couple of times to let Windows update to new size and run chkdsk. Then you can install to unallocated space.
You do need to have fastboot off and secure boot off if 8.1. Grub currently will not boot 8.1 with secure boot on from grub menu. You should be able to boot both from UEFI menu.

---

### Post by Frogs Hair on 2014-03-17
12.10 was  the last Ubuntu  ISO to include Wubi and as written.[SIZE=2][/SIZE]

> [h=4][SIZE=2]Windows installer is not compatible with Windows 8 or UEFI firmware, and is not available for Ubuntu 13.10.[/SIZE][/h]

---

