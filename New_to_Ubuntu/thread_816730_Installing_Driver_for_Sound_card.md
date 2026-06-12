---
title: "Installing Driver for Sound card"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by mjrwingnut on 2008-06-03
I'm running Kubuntu 8.04 64 bit on a AMD Quad Core Asus Motherboard with a Sound Blaster® X-Fi™ XtremeGamer sound card.

I download the driver file to my home directory. I next then unzipped the file.

I typed "sudo ./installer" and this is the result:

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... no
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.24-17-generic/kernel/sound
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for ISA DMA API... yes
checking for 32bit compat support... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for Procfs support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new unlocked/compat_ioctl... no
configure: creating ./config.status
config.status: creating Makefile.conf
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful

was I suppose to do this instead? ./installer --with-alsainc=<ALSA_include_directory>

if so where would I find alsa on my system.

Any help is greatly appreciated

---

### Post by Xiong Chiamiov on 2008-06-03
You might have to add "sudo" to the front of it.  There is [a very comprehensive guide]("http://ubuntuforums.org/showthread.php?t=205449") to sound problems.

---

