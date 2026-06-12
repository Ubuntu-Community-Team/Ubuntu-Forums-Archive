---
title: "Howto install Ubuntu 8.04 and ZenWalk side-by-side?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Jeo_fin on 2008-11-07
Hello!
I have installed Ubuntu 8.04 with this partitions
sda2 /home (33GiB)
sda3 extended (21GiB)
  sda5 / (ubuntu) (11.6GiB)
  sda6 / (zenwalk) (9.4 GiB)
sda1 linux-swap (boot) (2.33Gib)

I know this swap+boot isn't good but everything runs ok.

First I installed Hardy, then I installed ZenWalk 5.2 (standard edition) from cd. I did not run LILO. I added /boot/grub/menu.lst these lines ```

# Zenwalk Linux
title Zenwalk Linux
root (hd0,5)
kernel (hd0,5)/boot/vmlinuz root=/dev/hda3 vga=0x31A video=vesafb:mtrr,ywrap splash=silent
initrd (hd0,5)/boot/initrd.splash

```

when I run ZenWalk from grub it says "kernel panic" something.. I think problems lies there that I havent compiled kernel.
Any good ideas or walk-thru's how to install ubuntu and zenwalk dualboot?

Best Regards
Jeo
Finland

---

