---
title: "Getting sound working?!"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by KazPed on 2008-09-15
Hey guys, i am a complete beginner at Ubuntu so please bare with me :) I donwloaded and installed the most recent Ubuntu yesterday, and its all working fine apart from getting my sound working. I have found the correct drivers for my sound card (Creative X-Fi Platinum Fatal1ty Champion Series) and downloaded the tar.gz folder on my desktop. could anyone give me a step by step guide on how to install it? ive read the read me for it and it says something about ALSA? I have no idea what to do?! thanks guys.

---

### Post by KazPed on 2008-09-15
anyone? :confused:

---

### Post by acidsolution on 2008-09-15
first try installing alsa 

```
 sudo apt-get install alsa
```

and than install alsa mixer gui to set your settings 

```
 sudo apt-get install alsamixergui
```

---

### Post by KazPed on 2008-09-15
ive done that, still no joy, what next anyone? when i click on the sound icon in the top right. it says "No volume control GStreamer plugins and/or devices found."
once again i am a beginner so i apologize if i am troubling you!

---

### Post by northern lights on 2008-09-15
Can you please post the output of ```
sudo lshw -C multimedia
```and```
cat /proc/asound/cards
```Thank you.

---

### Post by KazPed on 2008-09-15
output of "sudo lshw -C multimedia":

 *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 6
       bus info: pci@0000:03:06.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=32 maxlatency=5 mingnt=4

And output of "cat /proc/asound/cards":

--- no soundcards ---


I guess thats not a good thing?:confused:

---

### Post by northern lights on 2008-09-15
At first I thought it wouldn't look as dim as you feared, since the device not being listen in /proc/ just means the module isn't loaded and lshw showed that there's no driver assigned.

However it seems that there's no Linux driver yet at all. Compare with [http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs").

For the OP's sake, someone correct me...

---

### Post by bobnutfield on 2008-09-15
> (Creative X-Fi Platinum Fatal1ty Champion Series) and downloaded the tar.gz folder on my desktop. 

What driver have you downloaded and where did you get it?  If it is in fact the correct driver, we can help you installit.

---

### Post by KazPed on 2008-09-15
i have found the driver for my sound card and worked out what to do. I run the installer in Root, cause thats what it tells me to do, but it says installing then a lot of text comes up quickly then it closes before i can read it :S

---

### Post by northern lights on 2008-09-15
> **bobnutfield said:**
> What driver have you downloaded and where did you get it?
Good question.

@the OP: Please give the source of the driver and the file type. Did you compile from source or download a binary?

---

### Post by bobnutfield on 2008-09-15
I have found conflicting information about that card and Linux.  Apparently there is a beta driver here:

[http://www.linuxscrew.com/2007/09/27/creative-sound-blaster-x-fi-linux-driver/]("http://www.linuxscrew.com/2007/09/27/creative-sound-blaster-x-fi-linux-driver/")

But, I also found this little blurb, indicating there isn't a driver:

[http://digg.com/linux_unix/XFI_linux_drivers_cancelled_DRM_says_no_to_Linux]("http://digg.com/linux_unix/XFI_linux_drivers_cancelled_DRM_says_no_to_Linux")

Please post the full name of the driver you have downloaded, and if it is possible, we can help you install it.

---

### Post by KazPed on 2008-09-15
i downloaded it from the creative labs site. went into support section, found my sound card, then found a Linux beta driver. [http://support.creative.com/downloads/welcome.aspx?nDriverType=11#type_11](http://support.creative.com/downloads/welcome.aspx?nDriverType=11#type_11)

thats the link where i found it. I downloaded it onto desktop as a tar.gz file then unpacked it to desktop aswell.

---

### Post by bobnutfield on 2008-09-15
I see.  I check it out for you and apparently this is the file:

>  XFiDrv_Linux_US-1.18.tar.gz.

If it is extracted to your desktop, do you know how to install a source file?  If not, what files are currently shown on the desktop?

---

### Post by KazPed on 2008-09-15
i unpacked it to my desktop. There is a folder of the same name and in the folder is Disclaim.txt, installer, License.txt, Readme.txt and XFiDrv_Linux_US-1.18.tar.bz2. I dont know how to install a source file. I tried running the installer by using sudo and dragging it after it, but after agreeing to various license and terms stuff, i get this message:

Installation is in progress. Please wait...
tar: /home/kasper/XFiDrv_Linux_US-1.18.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful

---

### Post by bobnutfield on 2008-09-15
OK, you may not have the compiler installed.  I am not on Ubuntu right now, so I cannot check the name, but I believe what you need is to do this first:

> sudo apt-get install build-essentials

This should install the gcc compiler for you.  Hopefully, if I have gotten the name of the app you need wrong, someone will correct me.  If they do not, try it as I have shown.

After the compiler is installed, open a terminal and type:

> cd /Desktop

This where your files are.  There is a README file and that usually has the installation instructions.  There is obviously an install script included, so try to do it again in the /Desktop directory. There may also be some special parameters to be added in the README file, though there may not be.  There is probably an instruction in the README file on how to start the installer from the command line, just make sure you are in the /Desktop directory.

---

### Post by northern lights on 2008-09-15
The package name is singular - it's```
sudo apt-get install build-essential
```
Otherwise, I concur.

---

### Post by KazPed on 2008-09-15
did the build essentials, it was sudo apt-get build-essential. no S. However when i use the cd /Desktop says "No such file directory" also i got abit lost on the bit about the desktop. could you explain any more? sorry!

---

### Post by bobnutfield on 2008-09-15
Open a terminal.  You will be in your /home directory.  Type:

> ls

This will list everything in your home directory.  One of the listings should be "Desktop" (without the quotes).  From there, you should be able to simply type

> cd /Desktop

to put you in the /Desktop directory.  If you have a color output in your terminal,the directories will be colored blue.  Try the command again to get into your /Desktop directory.  But read the README file for instructions.  I do not have that file,  but if you run into difficulty I will download the file and see if there are any special instructions.  But, since all the files are on your Desktop, you will have to be in that directory to install the app.

---

### Post by KazPed on 2008-09-15
the README.txt for the driver says this:

====================================================================

  Sound Blaster X-Fi Linux 32/64-bit Beta Driver Readme File

  April 2008

====================================================================

The purpose of this document is to describe how the X-Fi Linux device 
driver is built, packaged, and released.





Quick install

=============


1) You must have the fully configured source for the Linux kernel and 
   ALSA which you
 want to use for this device driver. Partial installed 
   kernels (e.g. From distribution makers) may be unusable for this 
   action.




2) Run one of the following commands as root in the terminal:



   ./installer
   


   OR


   ./installer --with-alsainc=<ALSA_include_directory>



  * ALSA Source Tree


   
   On 2.6 kernels, the location of the ALSA source include directory

      is parsed automatically from the running kernel.

      If it is not in the standard place, specify the path via
   
   --with-alsainc=<ALSA_include_directory>.

 
   
  On 2.4 kernels, the location of the ALSA source include directory

      must be specified via --with-alsainc=<ALSA_include_directory>.



  * Note
      If integrated ALSA is to be used to build, --with-alsainc option

      must not be specified.







Uninstall

=========


In the terminal,


1) Change directory to /opt/Creative/XFiDrv_Linux_US-1.18



2) Run the following command as root


   ./configure

   make uninstall



 * Note

      For GNOME users, You may need to close the Volume Control
      applet before uninstalling. Right-click the Volume icon on the
      GNOME panel and select "Remove From Panel"



3) Manually delete all files in /opt/Creative/XFiDrv_Linux_US-1.18









Copyright (c) 2008 Creative Technology Ltd. All rights reserved.

====================================================================

  End of Readme File

====================================================================

---

### Post by KazPed on 2008-09-15
Sorry for another long post, but i tried installing it through terminal and it looked like it was going well. but it mentioned something about kernel compilers. here is what it said:

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
Installation Unsuccesful


Any ideas?

---

### Post by KazPed on 2008-09-15
hope i havent scared you off! im just desperate! :(

---

### Post by bobnutfield on 2008-09-15
> 
1) You must have the fully configured source for the Linux kernel and
ALSA which you
want to use for this device driver. Partial installed
kernels (e.g. From distribution makers) may be unusable for this
action.

I think you will need the kernel source files as well.  I will soon be on my Ubuntu computer, so I will post back in about 20 minutes to tell you which file to install.  In the meantime, you might try yourself.  Open a terminal and type:

> uname -r

This will tell you the exact kernel you have.  The in Synaptic Package Manager, look for the kernel source file for that kernel. The file will probably end in .src or something similar.

---

### Post by KazPed on 2008-09-15
my kernel is "2.6.24-19-generic"
having a look for stuff to do with it in Synaptic package manager now.

---

### Post by KazPed on 2008-09-15
i dont really know wat im looking for! so i'll wait for you to get onto Ubuntu :)

---

### Post by bobnutfield on 2008-09-15
Ok, you can either install from the package manage or from the command line.  The file you are looking for is:

> linux-headers-generic

You should also install:

> sudo apt-get install alsa-source

based on the information in the README file.

Once you have those installed, try your installer again.

---

### Post by KazPed on 2008-09-15
hmm, still nothing. The linux-headers-generic were already installed, and i installed the other the alsa source thing. but got this message:

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

### Post by bobnutfield on 2008-09-15
> checking for built-in ALSA... no
checking for existing ALSA module... no
checking to modify of kernel linux/kmod.h... no

I am not familiar with this driver, but I am wondering from the above why ALSA is not being detected by the installer.

ALSA is included in the installation of Ubuntu, so I do not understand the above.  Try:

> sudo apt-get install alsa-base && sudo apt-get install alsa-utils

If it is already installed, it will tell you so.

---

### Post by KazPed on 2008-09-15
yea already installed :confused: hmmmm

---

### Post by KazPed on 2008-09-15
there is a part in the README which says

2) Run one of the following commands as root in the terminal:



   ./installer
   


   OR


   ./installer --with-alsainc=<ALSA_include_directory>



  * ALSA Source Tree


   
   On 2.6 kernels, the location of the ALSA source include directory

      is parsed automatically from the running kernel.

      If it is not in the standard place, specify the path via
   
   --with-alsainc=<ALSA_include_directory>.


Could it be anything to do with the directory of where the ALSA stuff is?

---

### Post by bobnutfield on 2008-09-15
Possibly, but I have to admit I am stumped.  But, I will do a little research and see if I can come up with an answer for you.  In the meantime, hopefully someone with more knowledge of source installations will chime in.  You could try the suggest parameter with the installer.  But, you'll need to locate the directory for the ALSA source files.  You might try:


> whereis alsa-source

That may give you details of where it is located.  I believe the directory is /sbin/alsa.  Try that parameter.

Edit:  The location is probably going to be standard.  So this parameter is not going to help.

---

### Post by KazPed on 2008-09-15
hmmm i dont know. yea lets hope we get an expert on installing drivers for X Fi linux drivers!

---

### Post by bobnutfield on 2008-09-15
I am investigating now to see what I can find.

---

### Post by bobnutfield on 2008-09-15
I have a post in another forum for software.  I have not found anything except for the suggestion that may ALSA needed to be installed from source, but I do not agree with that.  Your driver should install with the existing ALSA module in Ubuntu.  When I find another suggestion I will post back.  In the meantime, you might consider starting another post in the Software forum to see if someone else can help.

Sorry I have not been able to get you through this yet.

---

### Post by KazPed on 2008-09-15
no worries, i appreciate all the help :)

---

