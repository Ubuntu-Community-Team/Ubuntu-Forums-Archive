---
title: "Creative X-Fi Driver"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by bgast1 on 2008-05-04
I saw a tutorial on installing the Creative SoundBlaster X-Fi driver somewhere but I can't find it. I have downloaded the driver to my desktop and extracted to my desktop but I still don't get how to install it. 

I don't even know it it will work or if I have everything that I need installed to make it work. 

I have my on-board sound working, but I don't know if will sound that much better in Linux. In windows, there is a noticeable improvement over my on-board sound.

---

### Post by Sparkalo on 2008-05-05
Yeah, I use an X-Fi card too.  I haven't tried installing the drivers in 8.04, but when I did, I basically just downloaded the drivers, unpacked the archive, and then just ran the ./installer script.

Still, if something goes wrong, this thread has plenty of info:
[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

---

### Post by bgast1 on 2008-05-05
That was the thread that I was looking for. I think that I can follow those instructions down to the part where it says recommended and the OSS stuff. I don't know anything whatsoever about that. Also, if I do that first command that will install all of the dependencies necessary for that driver under ALSA?

If I do that and the driver still doesn't work (ALSA), then I am basically out of luck and must either buy a supported sound card or use my on-board sound, or God forbid, go back to windows?

How was the sound in the version you did install it on? I still really wonder if it will give me the superior sound that it did in windows over my on-board sound?

---

### Post by bgast1 on 2008-05-05
Don't exactly know what happened here other than I was unsucessful. The top of the thread that I took these instructions from said 'Doesn't work for 8.04 ATM'. I have kbuntu 8.04 KDE 4 installed but using a Gnome desktop at the moment. 

```
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
bob@bob-desktop:~/Desktop/XFiDrv_Linux_US-1.18$ 

```

---

### Post by st33med on 2008-05-05
These drivers do not work for Ubuntu Hardy Heron yet. You might want to try this:
[http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

---

### Post by bgast1 on 2008-05-05
Would I be best to install Gutsy Gibbon for a while until it gets sorted out for Hardy Heron. Or even God forbid that I ask on an Ubuntu forum Open Suse 10.3?

---

### Post by bgast1 on 2008-05-06
It's been over 20 hours since anyone has looked at this, figured it might have got lost in the shuffle, or no one knows whether my on-board sound is comparable to the X-Fi card with the beta driver, but wanted to bump this up one last time in case someone might know. 

I attempted to get it installed under Open Suse 10.3 but was not successful. I think because of dependencies. If it works under Ubuntu Gutsy Gibbon, I would be willing to install that tonight and give it a go until it works in Hardy Heron. I've just been doing a lot of installing over the last few days and would like to settle down on one distro for a while.

St33med-- I just wanted to you to know that I am not ignoring your suggestion. It's just that I am a little confused over the OSS thing and a bit uncertain on how to go about the link that you posted. Sometimes it takes a sledge hammer to knock some sense into this old brain.

---

