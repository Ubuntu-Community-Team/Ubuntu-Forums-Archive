---
title: "VM or Laptop"
date: 2020-08-04
forum: New to Ubuntu
---

### Post by comolaflor1234 on 2020-08-04
I'm very new to Linux, so I wanted to get some recommendations. Should I continue using a VM or purchase a laptop? I understand the laptop will give me more storage space, since I won't be sharing with my host machine, but what are some other benefits? Thanks in advance!

---

### Post by crip720 on 2020-08-04
Should gain speed and power running directly on hardware.  Usually not required to buy another laptop, unless using someones elses computer.  If you have quite a bit of free space on your drive can dual boot, or just buy an external drive and install Linux on that.  Would continue with using the VM and learning more.  Can google installing as dual boot.  Not all computers/laptops are the same so would be good to test Linux if get another laptop.

---

### Post by TheFu on 2020-08-04
Portability.  If you don't need that, don't bother with laptops. They are more expensive, slower, less expandable than a desktop or even a boot-bot sized desktop using an itx motherboard.

VMs are great, especially when setup correctly.  I love VMs since they remove the HW ties for the OS.  Upgrading the underlying hardware immediately upgrades the performance.

---

### Post by pbear42 on 2020-08-05
A few thoughts.  Best reason to get a second computer, IMHO, is to have a backup if your primary has to go to the shop.  TheFu makes a fair point about the advantages of a desktop, but laptops have the obvious advantage of taking less space.  Either way, a used Win7 machine will run Ubuntu fine and those a super cheap these days.

If you don't care about having a backup computer, installing to USB drive may make more sense.  Be sure to use a hard drive (HDD or SSD), not a regular flash drive.  The latter aren't engineered for the rigors of running an OS.  Also, if your main computer runs UEFI, be aware there's a bug in the installer to work around.  Not difficult, but not something want to be surprised by.  Bonus advantage of the USB hard drive solution, you can use the same drive for backup of your main system.

As for staying with a VM, depends on how good your hardware.  If you're getting by with two cores and 4 GB RAM, that's not giving Linux a fair chance.  If you have eight cores and 16 GB RAM, well, that more than plenty.  In between, say four cores and 8 GB RAM is enough, but running on bare metal will be more fun.

No right or wrong answer for something like this.  Just my $0.02's worth.

---

