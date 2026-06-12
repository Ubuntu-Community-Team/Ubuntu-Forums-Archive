---
title: "Linux Kernel module build “make modules” get error"
date: 2013-05-02
forum: Packaging and Compiling Programs
---

### Post by ThangLe on 2013-05-02
I am using Eclipse Juno, Ubuntu OS 64bit 13.04. I try to build Linux modules  in Eclipse for ARM platform. Compiler: Sourcery CodeBench for ARM.  Eclipse for ARM plug-in installed.

When I run make commands in terminal with root permission, then  everything goes on OK. But when I try build in Eclipse, the make target: "make uImage" is  successful but "make modules" and "make modules_install" failed. Below  is error i got when I run "make modules". I tried to run Eclipse in root  permission (in terminal run: **sudo ./eclipse**) but error still happens. What went wrong here ?. Thanks


[I]make -j2 modules 
  CHK     include/generated/uapi/linux/version.h
  CHK     include/generated/utsrelease.h
make[1]: `include/generated/mach-types.h' is up to date.
  CC      scripts/mod/devicetable-offsets.s
  CALL    scripts/checksyscalls.sh
  GEN     scripts/mod/devicetable-offsets.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTLD  scripts/mod/modpost
  Building modules, stage 2.
  MODPOST 11 modules
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/acenic/tg1.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/acenic/tg2.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/adaptec/starfire_rx.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/adaptec/starfire_tx.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/dsp56k/bootstrap.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/atmsar11.fw' doesn't match  the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/bnx2x/bnx2x-e1-6.2.9.0.fw'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/bnx2x/bnx2x-e1h-6.2.9.0.fw'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/bnx2x/bnx2x-e2-6.2.9.0.fw'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/bnx2/bnx2-mips-09-6.2.1a.fw'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/bnx2/bnx2-rv2p-09-6.0.17.fw'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/bnx2/bnx2-rv2p-09ax-6.0.17.fw'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/bnx2/bnx2-mips-06-6.2.1.fw'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/bnx2/bnx2-rv2p-06-6.0.15.fw'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/sun/cassini.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/cxgb3/t3b_psram-1.1.0.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/cxgb3/t3c_psram-1.1.0.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/cxgb3/ael2005_opt_edc.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/cxgb3/ael2005_twx_edc.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/cxgb3/ael2020_twx_edc.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/matrox/g200_warp.fw' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/matrox/g400_warp.fw' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/r128/r128_cce.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/R100_cp.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/R200_cp.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/R300_cp.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/R420_cp.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RS690_cp.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RS600_cp.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/R520_cp.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/R600_pfp.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/R600_me.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV610_pfp.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV610_me.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV630_pfp.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV630_me.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV620_pfp.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV620_me.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV635_pfp.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV635_me.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV670_pfp.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV670_me.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RS780_pfp.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RS780_me.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV770_pfp.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV770_me.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV730_pfp.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV730_me.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV710_pfp.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/radeon/RV710_me.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/av7110/bootcode.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/ttusb-budget/dspbootcode.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/e100/d101m_ucode.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/e100/d101s_ucode.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/e100/d102e_ucode.bin'  doesn't match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/myricom/lanai.bin' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/cis/LA-PCM.cis' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/cis/PCMLM28.cis' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/cis/DP83903.cis' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/cis/NE2K.cis' doesn't match  the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/cis/tamarack.cis' doesn't  match the target pattern
/home/thangle/git/linux-stable/scripts/Makefile.fwinst:45: target  `/home/thangle/modules_install/lib/firmware/cis/PE-200.cis' doesn't  match the target pattern[/I]


However, if I build in terminal with command: **make ARCH=arm CROSS_COMPILE=arm-none-linux-gnueabi- modules**
  It's OK. 


[I]CHK     include/generated/uapi/linux/version.h
  CHK     include/generated/utsrelease.h
make[1]: `include/generated/mach-types.h' is up to date.
  CC      kernel/bounds.s
  GEN     include/generated/bounds.h
  CC      arch/arm/kernel/asm-offsets.s
  GEN     include/generated/asm-offsets.h
  CALL    scripts/checksyscalls.sh
  CC      scripts/mod/empty.o
  MKELF   scripts/mod/elfconfig.h
  CC      scripts/mod/devicetable-offsets.s
  GEN     scripts/mod/devicetable-offsets.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  CC [M]  crypto/rng.o
  CC [M]  crypto/krng.o
  CC [M]  crypto/ansi_cprng.o
  CC [M]  drivers/usb/gadget/f_loopback.o
  CC [M]  drivers/usb/gadget/f_sourcesink.o
  CC [M]  drivers/usb/gadget/mass_storage.o
  CC [M]  drivers/usb/gadget/serial.o
  CC [M]  drivers/usb/gadget/zero.o
  CC [M]  drivers/usb/gadget/inode.o
  CC [M]  drivers/usb/gadget/usbstring.o
  CC [M]  drivers/usb/gadget/config.o
  CC [M]  drivers/usb/gadget/epautoconf.o
  CC [M]  drivers/usb/gadget/composite.o
  CC [M]  drivers/usb/gadget/functions.o
  LD [M]  drivers/usb/gadget/libcomposite.o
  CC [M]  drivers/usb/gadget/f_acm.o
  LD [M]  drivers/usb/gadget/f_ss_lb.o
  CC [M]  drivers/usb/gadget/u_serial.o
  LD [M]  drivers/usb/gadget/g_zero.o
  LD [M]  drivers/usb/gadget/gadgetfs.o
  LD [M]  drivers/usb/gadget/g_mass_storage.o
  LD [M]  drivers/usb/gadget/g_serial.o
  Building modules, stage 2.
  MODPOST 11 modules
  CC      crypto/ansi_cprng.mod.o
  LD [M]  crypto/ansi_cprng.ko
  CC      crypto/krng.mod.o
  LD [M]  crypto/krng.ko
  CC      crypto/rng.mod.o
  LD [M]  crypto/rng.ko
  CC      drivers/usb/gadget/f_acm.mod.o
  LD [M]  drivers/usb/gadget/f_acm.ko
  CC      drivers/usb/gadget/f_ss_lb.mod.o
  LD [M]  drivers/usb/gadget/f_ss_lb.ko
  CC      drivers/usb/gadget/g_mass_storage.mod.o
  LD [M]  drivers/usb/gadget/g_mass_storage.ko
  CC      drivers/usb/gadget/g_serial.mod.o
  LD [M]  drivers/usb/gadget/g_serial.ko
  CC      drivers/usb/gadget/g_zero.mod.o
  LD [M]  drivers/usb/gadget/g_zero.ko
  CC      drivers/usb/gadget/gadgetfs.mod.o
  LD [M]  drivers/usb/gadget/gadgetfs.ko
  CC      drivers/usb/gadget/libcomposite.mod.o
  LD [M]  drivers/usb/gadget/libcomposite.ko
  CC      drivers/usb/gadget/u_serial.mod.o
  LD [M]  drivers/usb/gadget/u_serial.ko[/I]

Regards,
Thang Le

---

