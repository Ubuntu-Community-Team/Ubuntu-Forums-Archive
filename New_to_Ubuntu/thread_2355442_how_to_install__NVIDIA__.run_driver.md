---
title: "how to install  NVIDIA  .run driver"
date: 2017-03-12
forum: New to Ubuntu
---

### Post by 243750496 on 2017-03-12
I know how to instsll open-source driver  in additional  driver in system  
I only want to try  .run driver 
But got a problem of
binary package for nvidia not found

---

### Post by T.J. on 2017-03-12
Could you post the associated build log please?

In the meantime, please make certain that you have the header and compiler installed.  These commands should make sure that they are installed for you.

sudo apt-get install module-assistant
sudo m-a prepare

You should be aware that installing drivers manually is no small feat, and you will have to perform maintenance from time to time as necessary.  I highly recommend using the packaged drivers, as they are tested and confirmed to work.

---

### Post by 243750496 on 2017-03-12
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Mar 13 10:23:31 2017
installer version: 378.13

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin

nvidia-installer command line:
    ./nvidia-installer

Unable to load: nvidia-installer ncurses v6 user interface

Using: nvidia-installer ncurses user interface
-> Detected 16 CPUs online; setting concurrency level to 16.
-> License accepted.
-> Installing NVIDIA driver version 378.13.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Are you sure you want to continue? (Answer: Continue installation)
-> Would you like to register the kernel module sources with DKMS? This will allow DKMS to automatically build a new module, if you install a different kernel later. (Answer: Yes)
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility libraries? (Answer: Yes)
-> Will install GLVND GLX client libraries.
-> Will install GLVND EGL client libraries.
-> Skipping GLX non-GLVND file: "libGL.so.378.13"
-> Skipping GLX non-GLVND file: "libGL.so.1"
-> Skipping GLX non-GLVND file: "libGL.so"
-> Skipping EGL non-GLVND file: "libEGL.so.378.13"
-> Skipping EGL non-GLVND file: "libEGL.so"
-> Skipping EGL non-GLVND file: "libEGL.so.1"
-> Skipping GLX non-GLVND file: "./32/libGL.so.378.13"
-> Skipping GLX non-GLVND file: "libGL.so.1"
-> Skipping GLX non-GLVND file: "libGL.so"
-> Skipping EGL non-GLVND file: "./32/libEGL.so.378.13"
-> Skipping EGL non-GLVND file: "libEGL.so"
-> Skipping EGL non-GLVND file: "libEGL.so.1"
Looking for install checker script at ./libglvnd_install_checker/check-libglvnd-install.sh
   executing: '/bin/sh ./libglvnd_install_checker/check-libglvnd-install.sh'...
   Checking for libglvnd installation.
   Checking libGLdispatch...
   Can't load library libGLdispatch.so.0: libGLdispatch.so.0: cannot open shared object file: No such file or directory
Will install libglvnd libraries.
Will install libEGL vendor library config file to /usr/share/glvnd/egl_vendor.d
-> Searching for conflicting files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64' (378.13):
   executing: '/sbin/ldconfig'...
-> done.
-> Driver file installation is complete.
-> Installing DKMS kernel module:
ERROR: Failed to run `/usr/sbin/dkms build -m nvidia -v 378.13 -k 4.10.0-11-generic`: 
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' -j16 NV_EXCLUDE_BUILD_MODULES='' KERNEL_UNAME=4.10.0-11-generic modules....(bad exit status: 2)
ERROR (dkms apport): binary package for nvidia: 378.13 not found
Error! Bad return status for module build on kernel: 4.10.0-11-generic (x86_64)
Consult /var/lib/dkms/nvidia/378.13/build/make.log for more information.
-> error.
ERROR: Failed to install the kernel module through DKMS. No kernel module was installed; please try installing again without DKMS, or check the DKMS logs for more information.
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.
```

---

### Post by Perfect Storm on 2017-03-13
You do know that you need to run the driver each time the kernel gets updated, just so you're prepared.
The best way is to use the nvidia drivers you can download through ubuntu.

---

