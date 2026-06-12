---
title: "Can not adjust resolution due to &quot;nomodeset&quot; with Intel Integrated Graphics"
date: 2021-03-23
forum: New to Ubuntu
---

### Post by fiftyfivenot on 2021-03-23
Hi everyone,


I have very little experience with Linux and therefore have been unable to resolve this issue with searching.


**My issue**: I would get a black screen when attempting to install Ubuntu 20.04 (likely due to UEFI). As a result, I ended up adding *nomodeset* setting to my grub ([following this guide]("https://www.stephenwagner.com/2019/05/05/ubuntu-linux-black-screen-frozen-system-after-upgrade-install/")). Unfortunately this resulted in my resolution being stuck at 1024x763. From my research, *nomodeset* is just a temporary solution that allows people to install proper drivers on their system. With that said, I keep reading that Intel Graphics Driver comes preinstalled in the kernel. Is this true? 

**Settings->About->Graphics** shows *llvmpipe (LLVM 11.0.0, 256 bit)* which I believe is incorrect and should say something along the lines of *Intel(R) UHD630*. At this point, I've attempted to update my grub with (according to [this post]("https://askubuntu.com/questions/1276966/ubuntu-20-04-lts-llvmpipe-llvm-10-0-0-256-bits-used-instead-of-nvidia-graph")): 

```

GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

```

Which resulted in inability to boot altogether. I had to reinstall Ubuntu since I could no longer figure out how to access grub during booting process.
[INDENT]My system:[/INDENT]

[LIST]
[*]Intel i7-10700 w/ Intel UHD Graphics 630
[*]ASRock B560M PRO4/AC LGA 1200
[*]No dedicated GPU
[*]Ubuntu is installed on a dedicated SSD
[/LIST]


Any helpful tips are appreciated,

Thank you in advance.

---

### Post by CatKiller on 2021-03-24
> **fiftyfivenot said:**
> As a result, I ended up adding *nomodeset* setting to my grub 

Don't do that. You're specifically disabling the Kernel Mode Setting driver, which is the only one you've got. 

It can be beneficial to disable *nouveau*'s KMS for the single boot before you install the proprietary *nvidia* driver, but not otherwise. 

> **Settings->About->Graphics** shows *llvmpipe (LLVM 11.0.0, 256 bit)* which I believe is incorrect and should say something along the lines of *Intel(R) UHD630*.

It would say something different if you hadn't deliberately disabled the driver. You're left with the software fallback since there's no other option.

---

### Post by fiftyfivenot on 2021-03-25
> Don't do that. You're specifically disabling the Kernel Mode Setting driver, which is the only one you've got.

This is the only way my system will boot. Also, I can not install NVIDIA drivers because I am using Intel UHD630 iGPU.

> It would say something different if you hadn't deliberately disabled the  driver. You're left with the software fallback since there's no other  option.

How can I enable Intel graphics driver while booted in *nomodeset* mode?

---

### Post by CatKiller on 2021-03-25
> **fiftyfivenot said:**
> How can I enable Intel graphics driver while booted in *nomodeset* mode?

You can't. That's what I just explained to you. nomodeset is you specifically disabling the driver.

I don't know what the actual problem is with your machine - bad cabling or bad EDID are possibilities - but "how can I disable a thing and have it still be enabled?" is nonsensical.

---

### Post by oldfred on 2021-03-27
Have you updated UEFI from Asrock?

Review settings in UEFI for video. It should be defaulting to Intel's video not an external (which does not exist).

---

### Post by fiftyfivenot on 2021-03-30
> **oldfred said:**
> Have you updated UEFI from Asrock?

Review settings in UEFI for video. It should be defaulting to Intel's video not an external (which does not exist).

Yup, I am running the latest version of UEFI and my GPU setting was set to Intel iGPU. No luck with running Ubuntu without *nomodeset*.


Thankfully I was able to get my hands on a dedicated GPU and Ubuntu works great with my "new" card. The problem is "solved". 

Thank you for your help [COLOR=#000000]oldfred and [/COLOR][COLOR=#000000]CatKiller.[/COLOR]

---

### Post by mastablasta on 2021-03-31
looks like the latest kernel (not ubuntu linux kernel but linux kernel) might be needed to get the chip running: [https://ubuntuforums.org/showthread.php?t=2459881](https://ubuntuforums.org/showthread.php?t=2459881)

i thought these chips were out for some time now, because for some reason their price is way lower than for old Ryzens.

---

### Post by oldfred on 2021-03-31
This user mentions 20.04 and 630:

> First things first, this issue does not exist on Ubuntu 20.04 with the beta 5.10 OEM kernel, although it does not work on the stock kernel or latest HWE
[https://unix.stackexchange.com/questions/642926/issues-with-igpu-uhd-630-from-i5-10400-and-no-monitor-signal-after-grub-screen](https://unix.stackexchange.com/questions/642926/issues-with-igpu-uhd-630-from-i5-10400-and-no-monitor-signal-after-grub-screen)

It looks like developers have codes to enable experimental graphic.
Saw this on the very new Xe graphics:
Gen12 Xe Graphics might not be working out-of-the-box depending upon your kernel. 
Re-booting the system while having "i915.force_probe=4c8a" Some distribution kernels including the likes of Ubuntu are already carrying the patch 
[https://www.phoronix.com/scan.php?page=article&item=intel-rkl-linux&num=1](https://www.phoronix.com/scan.php?page=article&item=intel-rkl-linux&num=1)

But this in searching on force_probe (bold mine)
**Please don't mention i915.force_probe** in end-user documentation #980 
[https://github.com/intel/media-driver/issues/980](https://github.com/intel/media-driver/issues/980)
[https://cateee.net/lkddb/web-lkddb/DRM_I915_FORCE_PROBE.html](https://cateee.net/lkddb/web-lkddb/DRM_I915_FORCE_PROBE.html)
[https://www.mail-archive.com/intel-gfx@lists.freedesktop.org/msg191190.html](https://www.mail-archive.com/intel-gfx@lists.freedesktop.org/msg191190.html)
 Also add new CONFIG_DRM_I915_FORCE_PROBE config option to replace the
> DRM_I915_ALPHA_SUPPORT option. This defaults to "*" if
> DRM_I915_ALPHA_SUPPORT=y.
> 
> Instead of replacing i915.alpha_support immediately, let the two coexist
> for a while, with a deprecation message, for a transition period.

And one user mentioned this:
> Sep 12, 2019 · cat /etc/modprobe. force_probe=%04x " "module parameter or ... I believe this is the intel HD 630. 


---

