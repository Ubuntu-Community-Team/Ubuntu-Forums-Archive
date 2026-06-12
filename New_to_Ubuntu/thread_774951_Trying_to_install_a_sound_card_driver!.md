---
title: "Trying to install a sound card driver!"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by msp.ohara on 2008-04-29
Sorry guys but I have no idea what I'm doing!  Any help would be great!  This is the message I'm getting?!

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful

Any ideas where I went wrong?

---

### Post by martrn on 2008-04-29
Have you tried :
```
sudo apt-get install build-essential
```
Then retry-ed what you were doing before ???

---

### Post by shad0w_walker on 2008-04-29
You need to install the various tools needed for compiling software. The easiest way of doing this is just installing build-essential by using:

```

sudo apt-get install build-essential

```

I have to ask though, why are you compiling the drivers yourself? I haven't encountered any normal soundcards that don't have atleast average support myself. Details of the card make/model could probably help if its working but has some strange issue (Low volume even at max, buzzing or some other issue)

---

### Post by msp.ohara on 2008-04-29
No sound at all!  The sound icon has a red cross through it.  Here is what it said after most recent install try,

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

Any ideas?

---

### Post by spiderbatdad on 2008-04-29
it looks like installer needs to be run with the path to alsa as outlined in the readme file.

```
 ./installer --with-alsainc=<ALSA_include_directory>


```

>   On 2.6 kernels, the location of the ALSA source include directory


      is parsed automatically from the running kernel.


      If it is not in the standard place, specify the path via

   
   --with-alsainc=<ALSA_include_directory>. 

Dont know where that is off the top of my head.

---

### Post by msp.ohara on 2008-04-29
If only I new what that meant?  Sorry, i've never used this before and all of this help you are giving me in invaluable!  Thanks:)

---

### Post by spiderbatdad on 2008-04-29
don't really know but it seems like something like this:```
sudo ./installer --with-alsainc=/usr/src/`uname -r`
```backticks '`' located on the ~ key usually.

---

### Post by msp.ohara on 2008-04-29
Well for the first time it's said installation complete but there is still a red cross next to the volume controller, No volume controller GStreamer plugins and or devices found??

Do I need to do a reboot?

---

### Post by spiderbatdad on 2008-04-29
reboot! reboot!

---

### Post by msp.ohara on 2008-04-29
Nope!  Still no luck sadly?! 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Just some of the messages that I am getting?!

---

### Post by spiderbatdad on 2008-04-29
lol. can't figure out which thread to post in...you have two going.
You never said whether you were running Hardy. And I suspected it would be a problem due to pulse audio. I don't know if you'll have any luck with the preferences>>sound settings by setting everything to alsa...

---

### Post by spiderbatdad on 2008-04-29
You may have to remove pulseaudio in synaptic package manager...caution this will also remove ubuntu-desktop...which isn't as bad as it sounds, but you may lose functionality of some apps and need to reinstall it. That not the same as removing gdm...just want you to be aware. You probably would have had better luck with the previous kernel (2.6.22-14-generic) I believe you can get that from synaptic and updateinitramfs -u (thingy) and get the kernel in /boot/grub/menu.lst as an option...this is a bit of work...you're going to need patience and more help than i can give probably.

---

### Post by msp.ohara on 2008-04-29
To be honest I think that I might just as well give up already!  I do not have a bloody clue what's going on with this Hardy Heron thing! :(

---

### Post by spiderbatdad on 2008-04-29
I have the same problem with the latest kernel 2.6.24-16-generic. Fortunately I installed Hardy during the alpha 1 release. It still used the 2.6.22-14 kernel. Check synaptic package manger. Everything you need is there. You need the 2.6.22-14-generic kernel and the linux headers. You will need to udate grub. then you should have a bootable kernel with sound. check your messages.

---

### Post by spiderbatdad on 2008-04-29
see this link: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Upgrade)

---

