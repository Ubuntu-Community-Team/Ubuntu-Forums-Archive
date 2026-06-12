---
title: "Ubuntu freezes boot with &quot;Loading Initial Ramdisk&quot;"
date: 2022-12-04
forum: New to Ubuntu
---

### Post by vairamvlinux on 2022-12-04
Hi,

I'm working in Ubuntu 22.04LTS OS, where it was booting with kernel 5.15.0-53 & 5.15.0-56. But when I want to boot the kernel 5.15.0-54 with:
```
CONFIG_PCIEAER_INJECT
``` …enable, booting freezes with message "Loading Initial Ramdisk". I tried the below suggestion


[LIST=1]
[*]adding name generic
[*]dist-upgrade & upgrade
[*]nomodeset in grub menu
[*]dis_ucode_ldr in grub menu
[*]removing the "quiet splash"
[/LIST]

But no luck,

By adding the:```
initcall_debug ignore_loglevel=1 earlycon=efifb
```…i got to know that boot hangs at:
```
printk: console [tty0] enable
printk: bootconsole [efifb0] disabled
```

I guess we don't need to downgrade/upgrade the microcode, because other kernel(5.15.0-53 & 5.15.0-56) are works with MicrocodeUpdate Driver:v2.2.

Below are the steps, i use to build the kernel

```
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.0.4.tar.xz
tar xvf linux-5.0.15.tar.xz
make x86_64_defconfig
make menuconfig
make
sudo make modules_install
sudo make install
sudo upgrade-grub
```

Motherboard detail: AMD EPYC 7702P

Let me know if anybody have a suggestion.

Thanks in advance

---

