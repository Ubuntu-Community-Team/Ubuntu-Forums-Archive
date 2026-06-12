---
title: "Creative X-FI Extreme Gamer Driver Install"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by Killaspike on 2008-07-21
I download the beta drivers from creative for linux and start installing them, I then run into an error and I cannot figure out why it is stopping.
Here is the terminal readout:

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
checking for directory with kernel source... /lib/modules/2.6.24-19-generic/build
checking for directory with kernel build... 
checking for directory with ALSA include files... /lib/modules/2.6.24-19-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-19-generic
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
checking for directory to store kernel modules... /lib/modules/2.6.24-19-generic/kernel/sound
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

### Post by Killaspike on 2008-07-21
bump

---

### Post by LightRaven on 2008-07-26
I would like to know the anwser to this question as well. Same sound card.

---

### Post by shellback84 on 2008-07-26
First of all I am no Ubuntu expert. However, I feel very secure in my computer hardware knowledge and because I own an X-FI sound card myself and my own problems with it, I have done extensive research on this sound card. The plan and simple truth is, the card has some fatal flaws. One of those flaws is good drivers and truth be told after all my research I think the card has a hardware bug that makes writing good drivers almost impossible for many motherboards. This is for Windows Vista and XP not Linux. If there is problems with those two OS's then you can see why there will be problems with Ubuntu. I tried everything to get my X-FI sound card to work in Ubuntu and other Linux OS's with no joy. 

My best advice, use an older sound card (if you have one) or the built into your motherboard sound and Ubuntu will see those sound devices and work.

---

### Post by Nepherte on 2008-07-26
My only success to make the card work is to use OSSv4: [http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961) I hope it works for you.

---

### Post by shellback84 on 2008-07-26
I failed to mention that going to Creatives own web site and see for yourselves the problems the X-FI is having. The newest drivers for XP (my personal opinion) degrade the sound quality so the card will work in more (I did not use the word most) motherboards and work better with Vista than it did. Last, what ever you do, do not engage the 24 bit crystalizer while playing a game.

---

### Post by LightRaven on 2008-07-27
> **Nepherte said:**
> My only success to make the card work is to use OSSv4: [http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961) I hope it works for you.

Edit: The guide worked for me with my Extreme Gamer. But don't rush through the guide then you will fail hard as I did :). Thanks!

---

### Post by Lovok on 2008-07-31
I also followed the guide for the OSSv4, and everything works fine, except my mic. I am wondering if I should install this beta drive as well, or should I just not risk it?

---

### Post by LightRaven on 2008-07-31
Did you get the sound in flash to work?

---

### Post by Nepherte on 2008-07-31
> **LightRaven said:**
> Did you get the sound in flash to work?
Worked like a charm for me. I just followed the **ADDENDUM2: Sound in Flash** from the tutorial.

---

### Post by LightRaven on 2008-08-01
> **Nepherte said:**
> Worked like a charm for me. I just followed the **ADDENDUM2: Sound in Flash** from the tutorial.

Sadly it didn't work for me. Using Extreme + FireFox.

---

### Post by bettertennis on 2008-08-06
I have the X-fi Elite Pro, and UBUNTU is the first system that I have not had it work perfectly on.  I had 0 problems with various versions of XP Pro for 5 years, this thread is the first I've seen with legit problems.  Will try the OSSv4 thread and see how it goes...

---

### Post by Nepherte on 2008-08-06
If you look on the internet, you'll find loads of driver issues related to Creative. Not only for linux, but for vista as well.

---

### Post by Stenrad on 2008-10-13
Hi all!

I just used the following guide for my XiFi Gamer Extreme:-

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675]("http://ubuntuforums.org/showpost.php?p=4823915&postcount=675")

Hope that helps!

All the best,

Stenrad.

---

### Post by LightRaven on 2008-12-28
To all the ppl with same problem:

Ubuntu 8.10 and the new drivers (8 nov) on the creative web site, solved this problem. Enjoy!

---

### Post by the_dark_light on 2009-08-19
According to the readme on the current version of the driver it's as simple as:

tar -xvzf Driver.tar.gz
cd Driver
sudo make
sudo make install

I've managed to get that far with no errors but no sound.  I expect I'm probably being dense and forgot to load the module or something like that.  (My brain has turned to tofu, I managed to do something similar a few weeks ago with a wireless driver from VIA arena but it's fallen out of my head)

---

