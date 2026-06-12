---
title: "Installation of DWL-G122 wireless adapter"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by astr0bomber on 2008-05-05
Hey forum,

I am using the new Hardy Heron currently. I am a relative noob when it comes to Ubuntu. I have been looking around trying to find the best way to install the drivers and get my adapter working. I found the following post. As you can see, inside the post was a link to a tutorial. I have been following the tutorial. I have managed to complete up to Step 4. When I start Step 5 is when I run into problems. Here is the output.

```
astrobomber@astrobomber-desktop:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make clean
rm -rf *.o *~ .*.cmd *.ko *.mod.c .tmp_versions built-in.o
astrobomber@astrobomber-desktop:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/astrobomber/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/astrobomber/RT73_Linux_STA_Drv1.0.3.6/Module/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/astrobomber/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [all] Error 2
```

I don't know what Error 2 is.
Another thing I am curious about is when I downloaded the original tar.gz, where did it save it? Because it's unlikely I am going to get this done tonite, and if I continue this later and the file is in a temporary directory, it most likely won't be there when I come back. The following is the output from when I downloaded the tar.gz:

```
astrobomber@astrobomber-desktop:~$ wget http://www.ralink.com.tw/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz
--00:25:19--  http://www.ralink.com.tw/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz
           => `RT73_Linux_STA_Drv1.0.3.6.tar.gz'
Resolving www.ralink.com.tw... 192.72.83.242
Connecting to www.ralink.com.tw|192.72.83.242|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 338,250 (330K) [application/x-gzip]

100%[===========================================>] 338,250       94.43K/s    ETA 00:00

00:25:23 (94.31 KB/s) - `RT73_Linux_STA_Drv1.0.3.6.tar.gz' saved [338250/338250]
```

Any help with this problem would be much appreciated. This is becoming a problem because it's slowly being less likely that I will have access to a wired connection.

---

