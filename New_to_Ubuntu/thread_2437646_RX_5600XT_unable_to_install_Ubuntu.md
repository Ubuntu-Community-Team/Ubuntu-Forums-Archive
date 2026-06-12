---
title: "RX 5600XT unable to install Ubuntu"
date: 2020-02-27
forum: New to Ubuntu
---

### Post by ulanddanne2 on 2020-02-27
Hi, 

Can't install Ubuntu or POP!_OS with my new build. The installation halts shortly after it begins (long before any GUI or live environment). The USB-sticks (both Ubuntu and POP) works flawlessly on my MacBook Pro. 

Ubuntu safe mode (graphics) let me boot in to the live environment and install Ubuntu, won't boot from internal HDD afterwards. 

My specs: 
Ryzen 3600 
Gigabyte B450i Aorus pro wifi (latest bios)
Sapphire RX 5600 XT (New bios)
16 GB Corsair Vengeance RGB black 3466mhz
Samsung 960 250GB (NVME)

---

### Post by mastablasta on 2020-02-27
Ubuntu 19.10?

[https://www.phoronix.com/scan.php?page=article&item=rx5600xt-linux-vbios&num=1](https://www.phoronix.com/scan.php?page=article&item=rx5600xt-linux-vbios&num=1)

> [COLOR=#121212][FONT=sans-serif]As outlined in the launch-day review, when moving to the new vBIOS release on the Radeon RX 5600 XT it actually led to much worse performance than the original vBIOS release. It turns out that an updated SMC firmware is needed for compatibility with the changed clocks, which is found in the latest Windows driver but hasn't yet propagated out for Linux users. Without the updated SMC firmware, the higher clocks could be rejected and basically sticking the graphics card in a low-power state. Fortunately, no AMDGPU DRM kernel driver patches are needed or other changes... Just an updated Navi 10 SMC binary to be dropped in /lib/firmware/amdgpu/ and updating initramfs and a reboot to then enjoy the RX 5600 XT with updated vBIOS behaving on Linux.[/FONT][/COLOR]

also note the kernel used in the test.

---

### Post by ulanddanne2 on 2020-02-27
Yes, 19.10

Don't believe the second bios (low power state) has any changes in clock speed etc. Could always try the non oc-bios switch...

---

### Post by mastablasta on 2020-02-28
my point is it's relatively new hardware. so you need newest possible driver and all that.

looks like ti works well for the phoronix guy and on par with nvidia rivals. 

perhaps using the kernel in 20.04 (still in beta) might be an option ?! it could be that card is not the issue and the motherboard is. hard to say without more information. 

boot in "safe mode" (that's nomodeset parameter that was used, right?), then check the logs and also check what car dis recognised by the OS.

EDIT: see this: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1863759](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1863759)
this means you should also try a newer or older kernel. Manjaro has very new kernel and can boot into live session.

sometime si wonder what they are doing with kernels and how come no one notices this on testing (since many people use AMD)

---

### Post by CatKiller on 2020-02-28
You may find it helpful to add [this PPA](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa) for a new version of Mesa.

---

