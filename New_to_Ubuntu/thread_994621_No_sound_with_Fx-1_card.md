---
title: "No sound with Fx-1 card"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by johntuck on 2008-11-26
Can someone help me in how to install the driver for the FX-1 sound card. When I install Ubuntu I have no sound. I can't find any decent guide to help a newbie

---

### Post by handydan918 on 2008-11-26
> **johntuck said:**
> Can someone help me in how to install the driver for the FX-1 sound card. When I install Ubuntu I have no sound. I can't find any decent guide to help a newbie

Well, before you can install the driver, you have to find the driver.


Did you find the driver?

---

### Post by johntuck on 2008-11-26
I did find the driver just not sure what to do with it
[http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx](http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx)

---

### Post by handydan918 on 2008-11-27
Do you mean you don't know what to do with an archive file?

---

### Post by johntuck on 2008-11-27
Well I know that it has to be extracted but what I really need is a step by step guide on how to install it.

---

### Post by handydan918 on 2008-11-27
> **johntuck said:**
> Well I know that it has to be extracted but what I really need is a step by step guide on how to install it.

There is no one protocol for handling a tar.gz file. It could contain source code that needs to be compiled, ot it could be an installer script that needs to be made executable run. 
The tar.gz file should have a readme file. 

To uncompress your file, try ```
tar -zxvf XFiDrv_Linux_US-1.18.tar.gz
```

Good luck with that card. I haven't heard anything great about that beta driver yet. Hope it works for you.

---

### Post by handydan918 on 2008-11-27
Here's the readme. It doesn't look too promising.

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

### Post by johntuck on 2008-11-27
Any chance that I can get it a little easier explained - you are talking to a newbie here. I managed to untar it into my Home folder. The readme gives me the following info:
====================================================================


  Sound Blaster X-Fi Linux 32/64-bit Driver Source Release Readme File

  September 2008


====================================================================


The purpose of this document is to describe how to build and install the 
X-Fi Linux device driver.






Quick install


=============

In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install



Uninstall

=========

In terminal,

1) Goto source directory

2) Execute make command as root

   make uninstall





Copyright (c) 2008 Creative Technology Ltd. All rights reserved.

====================================================================

  End of Readme File

====================================================================

I did the following with the following results:


john@john-desktop:~$ tar -zxvf '/home/john/Desktop/XFiDrv_Linux_Public_US_1.00.tar.gz' 
XFiDrv_Linux_Public_US_1.00/
XFiDrv_Linux_Public_US_1.00/ctmixer.c
XFiDrv_Linux_Public_US_1.00/cthw20k1.c
XFiDrv_Linux_Public_US_1.00/ct20k1reg.h
XFiDrv_Linux_Public_US_1.00/ctsrc.h
XFiDrv_Linux_Public_US_1.00/ctimap.h
XFiDrv_Linux_Public_US_1.00/ctamixer.c
XFiDrv_Linux_Public_US_1.00/ctamixer.h
XFiDrv_Linux_Public_US_1.00/ctdaio.c
XFiDrv_Linux_Public_US_1.00/ctatc.c
XFiDrv_Linux_Public_US_1.00/ctsrc.c
XFiDrv_Linux_Public_US_1.00/xfi.c
XFiDrv_Linux_Public_US_1.00/ctutils.h
XFiDrv_Linux_Public_US_1.00/cthw20k2.c
XFiDrv_Linux_Public_US_1.00/ctresource.c
XFiDrv_Linux_Public_US_1.00/ctresource.h
XFiDrv_Linux_Public_US_1.00/ctatc.h
XFiDrv_Linux_Public_US_1.00/README
XFiDrv_Linux_Public_US_1.00/ct20k2reg.h
XFiDrv_Linux_Public_US_1.00/ctvmem.c
XFiDrv_Linux_Public_US_1.00/cthardware.h
XFiDrv_Linux_Public_US_1.00/cthardware.c
XFiDrv_Linux_Public_US_1.00/ctdrv.h
XFiDrv_Linux_Public_US_1.00/ctpcm.h
XFiDrv_Linux_Public_US_1.00/COPYING
XFiDrv_Linux_Public_US_1.00/ctvmem.h
XFiDrv_Linux_Public_US_1.00/ctpcm.c
XFiDrv_Linux_Public_US_1.00/Disk.id
XFiDrv_Linux_Public_US_1.00/Makefile
XFiDrv_Linux_Public_US_1.00/ctmixer.h
XFiDrv_Linux_Public_US_1.00/ctdaio.h
XFiDrv_Linux_Public_US_1.00/ctimap.c
john@john-desktop:~$ ./installer
bash: ./installer: No such file or directory
john@john-desktop:~$ '/home/john/XFiDrv_Linux_Public_US_1.00/Makefile' 
bash: /home/john/XFiDrv_Linux_Public_US_1.00/Makefile: Permission denied
john@john-desktop:~$  '/home/john/XFiDrv_Linux_Public_US_1.00' 
bash: /home/john/XFiDrv_Linux_Public_US_1.00: is a directory
john@john-desktop:~$ '/home/john/XFiDrv_Linux_Public_US_1.00' 
bash: /home/john/XFiDrv_Linux_Public_US_1.00: is a directory
john@john-desktop:~$ cd '/home/john/XFiDrv_Linux_Public_US_1.00' 
john@john-desktop:~/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for john: 
make -C /lib/modules/2.6.24-21-generic/build M=/home/john/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  LD      /home/john/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/xfi.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/ctatc.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/ctpcm.o
/home/john/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function ‘ct_alsa_pcm_create’:
/home/john/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of ‘snd_pcm_new’ discards qualifiers from pointer target type
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/ctmixer.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/ctsrc.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/ctamixer.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/ctdaio.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/john/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "snd_pcm_period_elapsed" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_integer" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_device_new" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_set_ops" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_notify" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_free_pages" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_ioctl" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_malloc_pages" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_new" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_new1" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_minmax" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_preallocate_pages_for_all" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_free" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_register" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_new" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_add" [/home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
  CC      /home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/john/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
john@john-desktop:~/XFiDrv_Linux_Public_US_1.00$ make install
Copy module files...
mkdir: cannot create directory `/lib/modules/2.6.24-21-generic/kernel/drivers/ssound': Permission denied
make: *** [install] Error 1
john@john-desktop:~/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.24-21-generic/build M=/home/john/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
rm: cannot remove `/home/john/XFiDrv_Linux_Public_US_1.00/.tmp_versions/ctxfi.mod': Permission denied
make[1]: *** [crmodverdir] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [all] Error 2
john@john-desktop:~/XFiDrv_Linux_Public_US_1.00$ make install
Copy module files...
mkdir: cannot create directory `/lib/modules/2.6.24-21-generic/kernel/drivers/ssound': Permission denied
make: *** [install] Error 1
john@john-desktop:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
make: *** [install] Segmentation fault
john@john-desktop:~/XFiDrv_Linux_Public_US_1.00$ 


Hope this helps - it is sure new land to me

---

### Post by handydan918 on 2008-12-02
What I was trying to tell you is that this driver is new to EVERYONE, including creative! It is alpha stuff at it's worst! If it works, great! If not, buy a card that does!

---

### Post by zarcom on 2008-12-13
here is what I did:

1) Extract the file that you have downloaded by double-clicking on it (I assume you have some sort of .tar compression program installed).  Then extract it to your desktop.

2) Open up a terminal window and type this in (or you can click & drag between the ";s, but just follow along):

"sudo -rm" (this will remove all the permissions I believe, I could be wrong on this)

3) Once thats settled, re-open your terminal and navigate your way to your sound driver, then type this in:

"make install", you SHOULD see a bunch of files installing (by displaying a list).

4) Go to your Main Menu (I assume you have your red-icon on top of your upper_taskbar that looks like a "nutt" of some sort lol), then go to:

System>Control Centre>Hardware, click on the icon Sounda.

5) Look through your list that says CA106, this obviously stands for Creative Audio version 1.6 (*shrugs*).  There should be about 3-4 versionf on there, test out each of them (by hitting the test icon on the right), and you should hear that annoying BEEEEEEP.

6) Keep doing this until you have your sound fully set up for all the catagories that are listed in the Sound window :).

Enjoy :) and I hope this has helped.

Note: I am too new to this, so if anyone can add (or find another solution), on how to set up permissions, please speak now :).

Good luck and Take care.

---

### Post by kreppnar on 2010-03-28
My sound is working with the latest version of Alsa, without having to install the creative driver. But does anyone know of or heared if they have been able to get the I/O Module for the Sound Blaster Xfi Platinum to work? I really want to use it to record some guitar, but i cant seem to figure out how to get an input from the jacks. If anyone knows anything about it!, please help!

 Thanks

-Kreppnar-

---

