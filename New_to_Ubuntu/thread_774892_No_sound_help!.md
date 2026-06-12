---
title: "No sound help!"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by msp.ohara on 2008-04-29
Hi guys! I am totally, 100% new to this Linux OS and am liking what i've seen so far! However, I have no clue whatsoever about how to install a program. For example, I have downloaded the driver for my sound card and cannot get my head around installing it.  Here is the link for the sound card driver  

[http://uk.europe.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=3&Product_Name=X-Fi+Xtreme+Gamer&Product_ID=15853&modelnumber=&driverlang=1033&OS=12&select=0&x=37&y=9](http://uk.europe.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=3&Product_Name=X-Fi+Xtreme+Gamer&Product_ID=15853&modelnumber=&driverlang=1033&OS=12&select=0&x=37&y=9)

Any help would be fantastic!

---

### Post by aheckler on 2008-04-29
Download the file to your desktop, right-click it, and choose "Extract here".

Then do these in terminal:

```
cd ~/Desktop/XFiDrv_Linux_US-1.18
sudo chmod +x ./installer
sudo ./installer
```

---

### Post by spiderbatdad on 2008-04-29
Hi. What release of Ubuntu are you running? It may not work with pulseaudio in Hardy...says alsa is required in the readme file.

Let's say the package is on your desktop. Right click it and select extract here. A folder will be created. You can then throw the package away if you like. Click on the folder to open it, and read the readme file...it says to run ./installer as root. You will need to be in the same directory as the file to run it, so...open terminal and run```
cd Desktop/XfiDrv_Linux.blah blah
```You can use the tab key to auto complete the path name and avoid typos...remember everything is case sensitive. Once you are in the right directory, run ```
sudo ./installer
``` If there is a problem you may need to specify the path to alsa as suggested in the readme for the 2.6 kernel.

---

### Post by msp.ohara on 2008-04-29
Thank you so much for that!  A really fast response too!  So how would I install my Printer driver?

---

### Post by msp.ohara on 2008-04-29
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful

Any ideas where I went wrong?

---

### Post by spiderbatdad on 2008-04-29
visit [http://localhost:631](http://localhost:631)

---

### Post by spiderbatdad on 2008-04-29
> **msp.ohara said:**
> checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful

Any ideas where I went wrong?

```
sudo apt-get install build-essential
```try again.

---

### Post by msp.ohara on 2008-04-29
Yeah, someone else has given me that advice too and this was the message I had,

Installation is in progress. Please wait...
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
checking for GCC version... Kernel compiler: Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

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
checking for ISA support in kernel... yes
checking for processor type... i586
checking for ISA DMA API... yes
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

### Post by Denvercobra on 2008-04-29
Just a thought, 
open terminal and type Alsamixer
then make sure all values are at 100

---

### Post by spiderbatdad on 2008-04-29
```
sudo ./installer --with-alsainc=/usr/src/`uname -r`
```

---

### Post by msp.ohara on 2008-04-29
mike@mike-desktop:~$ Alsamixer
bash: Alsamixer: command not found
mike@mike-desktop:~$ 

That's what happened when I typed that!?

:)

---

