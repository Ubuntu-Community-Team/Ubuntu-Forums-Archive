---
title: "Error installing Soundblaster X-Fi Plat Driver 8.04"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by dtrot55 on 2008-04-25
Anyone have any success with the soundblaster drivers for x64? heres the code from my terminal


checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /opt/Creative/XFiDrv_Linux_US-1.18/drivers
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.24-16-generic/build
checking for directory with kernel build... 
checking for directory with ALSA include files... /lib/modules/2.6.24-16-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-16-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

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
checking for directory to store kernel modules... /lib/modules/2.6.24-16-generic/kernel/sound
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

---

### Post by Vich on 2008-04-25
I get those same uninformative error messages at the end. Am currently perusing [http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656) which I recommend you do also, and will post back here if I have any luck.

---

### Post by dtrot55 on 2008-04-25
that was the thread i followed.....:(

---

### Post by rcracer923 on 2008-04-27
i get the same error. we probably have to wait for creative to get around to updating the driver again to work with 8.04 unless someone finds some way to fix this sooner

---

### Post by djn48 on 2008-05-14
i have the exact same problem.
has anyone figured this one out yet?

thanks

---

### Post by dtrot55 on 2008-05-14
Use this link [http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656) and follow the OSS driver installation...thats the only way i have gotten the sound to work.

---

### Post by djn48 on 2008-05-14
thanks a lot! that guide did the job.
im only missing surround. i only get sound from the two front speakers.

any ideas?
thanks

---

### Post by djn48 on 2008-05-14
i just found out that i don't have sound on the headphones (plugged in the front bay of my x-fi platinum). this is much worse than not having surround.

any help is much appreciated.

thanks

---

### Post by dtrot55 on 2008-05-15
Yeah soundblasters driver is just a basic driver...only expect sound from 2 channels and nuthing else...its a beta driver and i dont think soundblaster cares much for the Linux users....unfortunately...but i think the 7.10 Gutsy it works because ALSA works...so you could try that.

---

