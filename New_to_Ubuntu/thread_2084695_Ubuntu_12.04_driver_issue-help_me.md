---
title: "Ubuntu 12.04 driver issue-help me"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by justine007 on 2012-11-16
Hi,
I am newbe to linux and ubuntu. I have a confusion, How to find out graphic card vendor of my mother board. I did following,
In terminal I issued ```
sudo lshw -c video
``` and got following:
```
*-display               
       description: VGA compatible controller
       product: C61 [GeForce 7025 / nForce 630a]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
        resources: irq:22 memory:de000000-deffffff memory:c0000000-cfffffff  memory:dd000000-ddffffff memory:dffc0000-dffdffff
```

Then I issued ```
sudo modinfo nouveau
``` and got following:
```
filename:       /lib/modules/3.2.0-29-generic-pae/kernel/drivers/gpu/drm/nouveau/nouveau.ko
license:        GPL and additional rights
description:    nVidia Riva/TNT/GeForce
author:         Stephane Marchesin
srcversion:     5399A281CEF0E1FB0CEDBDB
alias:          pci:v000012D2d*sv*sd*bc03sc*i*
alias:          pci:v000010DEd*sv*sd*bc03sc*i*
depends:        drm,drm_kms_helper,ttm,mxm-wmi,video,i2c-algo-bit
intree:         Y
vermagic:       3.2.0-29-generic-pae SMP mod_unload modversions 686 
parm:           agpmode:AGP mode (0 to disable AGP) (int)
parm:           modeset:Enable kernel modesetting (int)
parm:           vbios:Override default VBIOS location (charp)
parm:           vram_pushbuf:Force DMA push buffers to be in VRAM (int)
parm:           vram_notify:Force DMA notifiers to be in VRAM (int)
parm:           duallink:Allow dual-link TMDS (>=GeForce 8) (int)
parm:           uscript_lvds:LVDS output script table ID (>=GeForce 8) (int)
parm:           uscript_tmds:TMDS output script table ID (>=GeForce 8) (int)
parm:           ignorelid:Ignore ACPI lid status (int)
parm:           noaccel:Disable all acceleration (int)
parm:           nofbaccel:Disable fbcon acceleration (int)
parm:           force_post:Force POST (int)
parm:           override_conntype:Ignore DCB connector type (int)
parm:           tv_disable:Disable TV-out detection
 (int)
parm:           tv_norm:Default TV norm.
        Supported: PAL, PAL-M, PAL-N, PAL-Nc, NTSC-M, NTSC-J,
            hd480i, hd480p, hd576i, hd576p, hd720p, hd1080i.
        Default: PAL
        *NOTE* Ignored for cards with external TV encoders. (charp)
parm:           reg_debug:Register access debug bitmask:
        0x1 mc, 0x2 video, 0x4 fb, 0x8 extdev,
        0x10 crtc, 0x20 ramdac, 0x40 vgacrtc, 0x80 rmvio,
        0x100 vgaattr, 0x200 EVO (G80+).  (int)
parm:           perflvl:Performance level (default: boot)
 (charp)
parm:           perflvl_wr:Allow perflvl changes (warning: dangerous!)
 (int)
parm:           msi:Enable MSI (default: off)
 (int)
parm:           ctxfw:Use external HUB/GPC ucode (fermi)
 (int)
```

I think vendor is nvidia, right? If yes what drivers should I install for ubuntu 12.04 ?

After  installing ubuntu, sound and graphics working without installing any  additional drivers. But will performance increase if I install  proprietary drivers ?

In software center I found the following:

NVidia binary X.Org driver ('version 173' driver)  - not installed,
NVidia binary X.Org driver ('current' driver) - not installed,
NVidia binary X.Org driver ('version 96' driver) - not installed,
Additional Drivers (jockey-kde) - not installed,
Additional Drivers (jockey-gtk) - Installed. 
Which of these drivers should I install ? Please help.

Many thanks.

---

### Post by coffeecat on 2012-11-16
You are using the default open source nouveau driver.

Questions: are you getting satisfactory performance? Is the Unity desktop working OK for you? Are you a gamer?

The nouveau driver has much improved in recent releases and for your video chipset should give adequate performance. If your answers to the first two questions above are yes, then I suggest you don't bother installing the proprietary nvidia driver. If you are a gamer then you might get better performance with the nvidia driver, in which case I *think* you would need the 173 driver for that video chipset, but others might be able to confirm.

But if the system is working OK, my advice would be to not fix what isn't broken.

---

### Post by mlentink on 2012-11-16
Go to the Ubuntu Software Center. In the menubar click 'Edit' and then 'Software Sources'. A window will open on which you can click the additional drivers tab.

Have fun

P.S.: I totally agree with Coffeecat

---

### Post by justine007 on 2012-11-16
> **coffeecat said:**
> 

Questions: are you getting satisfactory performance? Is the Unity desktop working OK for you? Are you a gamer?



The performance is satisfactory indeed, and I am not a gamer,  but I have one more problem,  when booting monitor shows an "input not supported" message. I am using acer monitor. I changed /etc/default/grub :
```
#GRUB_GFXMODE=640x480
``` to
```
GRUB_GFXMODE=640x480
```But that not fixed the problem.
Thanks for your supper fast support.

PS: @[[COLOR=#97310e]**coffeecat**[/COLOR]]("http://ubuntuforums.org/member.php?u=129087") Are you from kerala, India. Because mansooned malabar has some relation with that.

---

