---
title: "error when trying to install creative linux drivers"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by neokiva on 2012-11-24
gavin@gavin-System-Product-Name:~/Downloads/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/3.5.0-18-generic/build M=/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-18-generic'
  CC [M]  /home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-18-generic'
make: *** [all] Error 2
gavin@gavin-System-Product-Name:~/Downloads/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/3.5.0-18-generic/build M=/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-18-generic'
  CC [M]  /home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-18-generic'
make: *** [all] Error 2
this comes up when i try to use the make command and this when i try the make install 

gavin@gavin-System-Product-Name:~/Downloads/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/3.5.0-18-generic/build M=/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-18-generic'
  CC [M]  /home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-18-generic'
make: *** [all] Error 2
gavin@gavin-System-Product-Name:~/Downloads/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/3.5.0-18-generic/build M=/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-18-generic'
  CC [M]  /home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-18-generic'
make: *** [all] Error 2

can anyone help me please?

---

### Post by 2F4U on 2012-11-24
Do you have the kernel headers installed?

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by neokiva on 2012-11-24
> **2F4U said:**
> Do you have the kernel headers installed?

```
sudo apt-get install linux-headers-$(uname -r)
```

Yes, they are. it still doesn't work

---

### Post by squakie on 2012-11-24
I haven't seen the package you are trying to use - if you could point to a download for it perhaps I can try it here to see what happens.  In the mean time, I assume that if the README mentioned it that you already ran config before the make?

Also - please post back the output of:

ls -al /home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00

I also saw this link:  [http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)  which is VERY old.  Even the wiki I could find indicates nothing beyond Ubuntu 8.xx or 9.xx, says it is beta only, and shows nothing indicating it has been updated.    I would be surprised if it works in the newer releases of Ubuntu, as that is for very old kernel versions.  If you are following such a link, be sure the link is valid for the version of Ubuntu you are running - like 12.04 or 12.10.

You also might be better served to use edit your title to say you are looking for:

 <what ever soundblaster XF card/chipset you are using> drivers for Ubuntu <substitute your version of Ubuntu here>

---

### Post by neokiva on 2012-11-24
> **squakie said:**
> I haven't seen the package you are trying to use - if you could point to a download for it perhaps I can try it here to see what happens.  In the mean time, I assume that if the README mentioned it that you already ran config before the make?

Also - please post back the output of:

ls -al /home/gavin/Downloads/XFiDrv_Linux_Public_US_1.00

I also saw this link:  [http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)  which is VERY old.  Even the wiki I could find indicates nothing beyond Ubuntu 8.xx or 9.xx, says it is beta only, and shows nothing indicating it has been updated.    I would be surprised if it works in the newer releases of Ubuntu, as that is for very old kernel versions.  If you are following such a link, be sure the link is valid for the version of Ubuntu you are running - like 12.04 or 12.10.

You also might be better served to use edit your title to say you are looking for:

 <what ever soundblaster XF card/chipset you are using> drivers for Ubuntu <substitute your version of Ubuntu here> 
the read me didn't mention a configuration command before make and make install 

here's the output of ls :
drwxr-xr-x 4 gavin gavin  4096 Nov 24 21:47 .
drwxr-xr-x 7 gavin gavin  4096 Nov 24 19:57 ..
-rw-r--r-- 1 gavin gavin     8 Nov 24 13:52 built-in.o
-rw-r--r-- 1 gavin gavin   206 Nov 24 13:52 .built-in.o.cmd
-rw-r--r-- 1 gavin gavin 18395 Oct 30  2008 COPYING
-rw-r--r-- 1 gavin gavin 23121 Oct 30  2008 ct20k1reg.h
-rw-r--r-- 1 gavin gavin  3092 Oct 30  2008 ct20k2reg.h
-rw-r--r-- 1 gavin gavin 11946 Oct 30  2008 ctamixer.c
-rw-r--r-- 1 gavin gavin  2818 Oct 30  2008 ctamixer.h
-rw-r--r-- 1 gavin gavin 36032 Oct 30  2008 ctatc.c
-rw-r--r-- 1 gavin gavin  4497 Oct 30  2008 ctatc.h
-rw-r--r-- 1 gavin gavin 17111 Oct 30  2008 ctdaio.c
-rw-r--r-- 1 gavin gavin  2911 Oct 30  2008 ctdaio.h
-rw-r--r-- 1 gavin gavin   844 Oct 30  2008 ctdrv.h
-rw-r--r-- 1 gavin gavin  1610 Oct 30  2008 cthardware.c
-rw-r--r-- 1 gavin gavin  5532 Oct 30  2008 cthardware.h
-rw-r--r-- 1 gavin gavin 55739 Oct 30  2008 cthw20k1.c
-rw-r--r-- 1 gavin gavin 57323 Oct 30  2008 cthw20k2.c
-rw-r--r-- 1 gavin gavin  3690 Oct 30  2008 ctimap.c
-rw-r--r-- 1 gavin gavin  1184 Oct 30  2008 ctimap.h
-rw-r--r-- 1 gavin gavin 28177 Oct 30  2008 ctmixer.c
-rw-r--r-- 1 gavin gavin  1968 Oct 30  2008 ctmixer.h
-rw-r--r-- 1 gavin gavin 13377 Oct 30  2008 ctpcm.c
-rw-r--r-- 1 gavin gavin   620 Oct 30  2008 ctpcm.h
-rw-r--r-- 1 gavin gavin  6261 Oct 30  2008 ctresource.c
-rw-r--r-- 1 gavin gavin  2343 Oct 30  2008 ctresource.h
-rw-r--r-- 1 gavin gavin 23527 Oct 30  2008 ctsrc.c
-rw-r--r-- 1 gavin gavin  4420 Oct 30  2008 ctsrc.h
-rw-r--r-- 1 gavin gavin  1416 Oct 30  2008 ctutils.h
-rw-r--r-- 1 gavin gavin  6912 Oct 30  2008 ctvmem.c
-rw-r--r-- 1 gavin gavin  1462 Oct 30  2008 ctvmem.h
-rw-r--r-- 1 gavin gavin    50 Nov  4  2008 Disk.id
-rw-r--r-- 1 gavin sudo   1040 Oct 30  2008 Makefile
-rw-r--r-- 1 gavin gavin   816 Nov  4  2008 README
drwxrwxr-x 2 gavin gavin  4096 Nov 24 14:18 sound
drwxr-xr-x 2 gavin gavin  4096 Nov 24 13:52 .tmp_versions
-rw-r--r-- 1 gavin gavin  2788 Oct 30  2008 xfi.c


btw i did happen upon alsa but couldn't find a download of it

---

### Post by squakie on 2012-11-24
Now post an ls -al of the sound subfolder.

As I noted, I doubt any of this is going to work.  It appears to be WAY old and for extremely old kernels.  If you are running an ubuntu greater than version 8.04 or 8.10, I don't see this working.  I would strongly suggest changing the title as I mentioned, because what you need are the drivers for your sound card for the version of ubuntu you are running (like 12.04 or 12.10?).  If you need help changing the title to a more accurate title, please message an administrator for help.

---

### Post by 3rdalbum on 2012-11-24
I think a driver is already included in newer versions of Ubuntu. Do you have any sound at all? If you do, then the driver is already working.

---

