---
title: "how to fix this error message"
date: 2011-08-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-08-13
The following partially installed packages will be configured:
  nvidia-current 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up nvidia-current (280.13-0ubuntu1) ...
update-alternatives: error: alternative link /usr/lib/xorg/extra-modules is already managed by gl_conf.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nvidia-current (280.13-0ubuntu1) ...
update-alternatives: error: alternative link /usr/lib/xorg/extra-modules is already managed by gl_conf.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 nvidia-current
                                         
ray@ray-GC660AA-ABA-SR5123WM:~$ 

tks

---

### Post by paul_in_london on 2011-08-13
Haven't seen that error before, but there could be something on this page which helps:

[https://github.com/MrMEEE/bumblebee/issues/493](https://github.com/MrMEEE/bumblebee/issues/493)

---

### Post by rburkartjo on 2011-08-13
solved just removed with ubuntu software center

---

### Post by rburkartjo on 2011-08-13
removed binary xorg driver, kernel module and udpau library-nvidia current

---

### Post by paul_in_london on 2011-08-13
> **rburkartjo said:**
> removed binary xorg driver, kernel module and udpau library-nvidia current

Ok, it just looked when I skimmed through that page as if you might be able to fix it without removing any packages.

---

### Post by apos on 2011-10-03
Same error here:
```
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Module is not there:
```
root@panama:/home/apos# ls **/lib/modules/3.0.0-12-generic/updates/dkms/**
hdaps.ko  thinkpad_ec.ko  tp_smapi.ko  vboxdrv.ko  vboxnetadp.ko  vboxnetflt.ko  vboxpci.ko

```

Doing manuall installation via dkms works. Probably you have to do an uninstall first:
```

root@panama:/home/apos# **dkms install -m nvidia-current/280.13 -k $(uname -r)**

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.0.0-12-generic module KERNDIR=/lib/modules/3.0.0-12-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/3.0.0-12-generic/build.........
cleaning build area....

DKMS: build Completed.

nvidia_current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod....

DKMS: install Completed.
```

There we go ;)
```
root@panama:/home/apos# ls /lib/modules/3.0.0-12-generic/updates/dkms/
hdaps.ko  **nvidia_current.ko**  thinkpad_ec.ko  tp_smapi.ko  vboxdrv.ko  vboxnetadp.ko  vboxnetflt.ko  vboxpci.ko
```

Hope this helps somebody until fixed.

---

### Post by apos on 2011-10-03
The above method is only getting things done ...

I fixed the problem doing the following:

```
apt-get remove --purge nvidia-settings nvidia-current
```

For some reason the following directory was not removed and that caused the error, so just delete it:
```
rm -rf /var/lib/dkms/nvidia-current/
```

Then reininstalled nvidia:
```
apt-get install nvidia-settings nvidia-current
```

Voilá :guitar:

---

