---
title: "Problem cleaning up /boot and installing new kernels"
date: 2017-11-25
forum: New to Ubuntu
---

### Post by ddeoli on 2017-11-25
Hello,

I'm new to Ubuntu and Linux.

I'm having problems cleaning up /boot and installing new kernel versions.

First, I tried using Synaptic to remove the old versions. This is what it returns:

```
(Reading database... 714253 files and directories currently installed.)
Removinglinux-image-extra-4.4.0-77-generic (4.4.0-77.98) ...
run-parts: executing/etc/kernel/postinst.d/apt-auto-removal 4.4.0-77-generic/boot/vmlinuz-4.4.0-77-generic
run-parts: executing/etc/kernel/postinst.d/initramfs-tools 4.4.0-77-generic/boot/vmlinuz-4.4.0-77-generic
update-initramfs:Generating /boot/initrd.img-4.4.0-77-generic


gzip: stdout: Nospace left on device
E: mkinitramfsfailure cpio 141 gzip 1
update-initramfs:failed for /boot/initrd.img-4.4.0-77-generic with 1.
run-parts:/etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: errorprocessing package linux-image-extra-4.4.0-77-generic (--remove):
 subprocessinstalled post-removal script returned error exit status 1
Removinglinux-image-extra-4.4.0-83-generic (4.4.0-83.106) ...
run-parts: executing/etc/kernel/postinst.d/apt-auto-removal 4.4.0-83-generic/boot/vmlinuz-4.4.0-83-generic
run-parts: executing/etc/kernel/postinst.d/initramfs-tools 4.4.0-83-generic/boot/vmlinuz-4.4.0-83-generic
update-initramfs:Generating /boot/initrd.img-4.4.0-83-generic


gzip: stdout: Nospace left on device
E: mkinitramfsfailure cpio 141 gzip 1
update-initramfs:failed for /boot/initrd.img-4.4.0-83-generic with 1.
run-parts:/etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: errorprocessing package linux-image-extra-4.4.0-83-generic (--remove):
 subprocessinstalled post-removal script returned error exit status 1
Errors wereencountered while processing:
linux-image-extra-4.4.0-77-generic
linux-image-extra-4.4.0-83-generic
E: Sub-process/usr/bin/dpkg returned an error code (1)
A package failed toinstall.  Trying to recover:
Setting uplinux-image-extra-4.4.0-98-generic (4.4.0-98.121) ...
run-parts: executing/etc/kernel/postinst.d/apt-auto-removal 4.4.0-98-generic/boot/vmlinuz-4.4.0-98-generic
run-parts: executing/etc/kernel/postinst.d/initramfs-tools 4.4.0-98-generic/boot/vmlinuz-4.4.0-98-generic
update-initramfs:Generating /boot/initrd.img-4.4.0-98-generic


gzip: stdout: Nospace left on device
cpio: write error:Broken pipe
E: mkinitramfsfailure cpio 1 gzip 1
update-initramfs:failed for /boot/initrd.img-4.4.0-98-generic with 1.
run-parts:/etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: errorprocessing package linux-image-extra-4.4.0-98-generic (--configure):
 subprocessinstalled post-installation script returned error exit status 1
dpkg: dependencyproblems prevent configuration of linux-image-generic:
 linux-image-genericdepends on linux-image-extra-4.4.0-98-generic; however:
  Packagelinux-image-extra-4.4.0-98-generic is not configured yet.


dpkg: errorprocessing package linux-image-generic (--configure):
 dependency problems- leaving unconfigured
dpkg: dependencyproblems prevent configuration of linux-signed-image-generic:
linux-signed-image-generic depends onlinux-image-extra-4.4.0-98-generic; however:
  Packagelinux-image-extra-4.4.0-98-generic is not configured yet.


dpkg: errorprocessing package linux-signed-image-generic (--configure):
 dependency problems- leaving unconfigured
dpkg: dependencyproblems prevent configuration of linux-generic:
 linux-genericdepends on linux-image-generic (= 4.4.0.98.103); however:
  Packagelinux-image-generic is not configured yet.


dpkg: errorprocessing package linux-generic (--configure):
 dependency problems- leaving unconfigured
dpkg: dependencyproblems prevent configuration of linux-generic-lts-utopic:
linux-generic-lts-utopic depends on linux-generic; however:
  Packagelinux-generic is not configured yet.


dpkg: errorprocessing package linux-generic-lts-utopic (--configure):
 dependency problems- leaving unconfigured
dpkg: dependencyproblems prevent configuration of linux-signed-generic:
linux-signed-generic depends on linux-signed-image-generic (=4.4.0.98.103); however:
  Packagelinux-signed-image-generic is not configured yet.


dpkg: errorprocessing package linux-signed-generic (--configure):
 dependency problems- leaving unconfigured
dpkg: dependencyproblems prevent configuration of linux-signed-generic-lts-utopic:
linux-signed-generic-lts-utopic depends on linux-signed-generic;however:
  Packagelinux-signed-generic is not configured yet.


dpkg: errorprocessing package linux-signed-generic-lts-utopic (--configure):
 dependency problems- leaving unconfigured

```

For your information, here are some of the results I got by running the following commands:

```
uname -r 

4.4.0-98-generic
```

```
df -h

Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.9G     0  3.9G   0% /dev
tmpfs                        789M  9.6M  779M   2% /run
/dev/mapper/ubuntu--vg-root  450G   64G  364G  15% /
tmpfs                        3.9G   96M  3.8G   3% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda2                    237M  222M  2.2M 100% /boot
/dev/sda1                    511M  3.4M  508M   1% /boot/efi
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        789M   60K  789M   1% /run/user/1000

```


```

dpkg -l | grep linux

ii  console-setup-linux                        1.108ubuntu15.3                                all          Linux specific part of console-setup
ii  libselinux1:amd64                          2.4-3build2                                    amd64        SELinux runtime shared libraries
ii  libselinux1:i386                           2.4-3build2                                    i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                             1.10.0-1                                       amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                       1.10.0-1                                       amd64        Video4linux frame format conversion library
ii  linux-base                                 4.0ubuntu1                                     all          Linux image base package
ii  linux-firmware                             1.157.13                                       all          Firmware for Linux kernel drivers
iU  linux-generic                              4.4.0.98.103                                   amd64        Complete Generic Linux kernel and headers
iU  linux-generic-lts-utopic                   4.4.0.98.103                                   amd64        Complete Generic Linux kernel and headers (dummy transitional package)
ii  linux-headers-4.4.0-77                     4.4.0-77.98                                    all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-77-generic             4.4.0-77.98                                    amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-83                     4.4.0-83.106                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-83-generic             4.4.0-83.106                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-97                     4.4.0-97.120                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-97-generic             4.4.0-97.120                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-98                     4.4.0-98.121                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-98-generic             4.4.0-98.121                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                      4.4.0.98.103                                   amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-utopic           4.4.0.98.103                                   amd64        Generic Linux kernel headers (dummy transitional package)
rc  linux-image-3.16.0-41-generic              3.16.0-41.57~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-62-generic              3.16.0-62.83~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-67-generic              3.16.0-67.87~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-73-generic              3.16.0-73.95~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-76-generic              3.16.0-76.98~14.04.1                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-77-generic               4.4.0-77.98                                    amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-83-generic               4.4.0-83.106                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-97-generic               4.4.0-97.120                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-98-generic               4.4.0-98.121                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-30-generic        3.16.0-30.40~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-41-generic        3.16.0-41.57~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-43-generic        3.16.0-43.58~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-44-generic        3.16.0-44.59~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-45-generic        3.16.0-45.60~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-46-generic        3.16.0-46.62~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-48-generic        3.16.0-48.64~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-49-generic        3.16.0-49.65~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-50-generic        3.16.0-50.67~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-51-generic        3.16.0-51.69~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-52-generic        3.16.0-52.71~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-53-generic        3.16.0-53.72~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-55-generic        3.16.0-55.74~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-59-generic        3.16.0-59.79~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-60-generic        3.16.0-60.80~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-62-generic        3.16.0-62.83~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-67-generic        3.16.0-67.87~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-70-generic        3.16.0-70.90~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-71-generic        3.16.0-71.92~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-73-generic        3.16.0-73.95~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-76-generic        3.16.0-76.98~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-77-generic        3.16.0-77.99~14.04.1                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic         4.4.0-34.53                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-36-generic         4.4.0-36.55                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic         4.4.0-38.57                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-generic         4.4.0-45.66                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-generic         4.4.0-47.68                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-51-generic         4.4.0-51.72                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-53-generic         4.4.0-53.74                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-59-generic         4.4.0-59.80                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic         4.4.0-62.83                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-generic         4.4.0-66.87                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-75-generic         4.4.0-75.96                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-77-generic         4.4.0-77.98                                    amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-83-generic         4.4.0-83.106                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-97-generic         4.4.0-97.120                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-98-generic         4.4.0-98.121                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                        4.4.0.98.103                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                       4.4.0-98.121                                   amd64        Linux Kernel Headers for development
iU  linux-signed-generic                       4.4.0.98.103                                   amd64        Complete Signed Generic Linux kernel and headers
iU  linux-signed-generic-lts-utopic            4.4.0.98.103                                   amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
rc  linux-signed-image-3.16.0-41-generic       3.16.0-41.57~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-43-generic       3.16.0-43.58~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-44-generic       3.16.0-44.59~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-45-generic       3.16.0-45.60~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-46-generic       3.16.0-46.62~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-48-generic       3.16.0-48.64~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-49-generic       3.16.0-49.65~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-50-generic       3.16.0-50.67~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-51-generic       3.16.0-51.69~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-52-generic       3.16.0-52.71~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-53-generic       3.16.0-53.72~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-55-generic       3.16.0-55.74~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-59-generic       3.16.0-59.79~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-60-generic       3.16.0-60.80~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-62-generic       3.16.0-62.83~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-67-generic       3.16.0-67.87~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-70-generic       3.16.0-70.90~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-71-generic       3.16.0-71.92~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-73-generic       3.16.0-73.95~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-76-generic       3.16.0-76.98~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-77-generic       3.16.0-77.99~14.04.1                           amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-34-generic        4.4.0-34.53                                    amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-36-generic        4.4.0-36.55                                    amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-38-generic        4.4.0-38.57                                    amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-51-generic        4.4.0-51.72                                    amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-59-generic        4.4.0-59.80                                    amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-62-generic        4.4.0-62.83                                    amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-66-generic        4.4.0-66.87                                    amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-83-generic        4.4.0-83.106                                   amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-97-generic        4.4.0-97.120                                   amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-98-generic        4.4.0-98.121                                   amd64        Signed kernel image generic
iU  linux-signed-image-generic                 4.4.0.98.103                                   amd64        Signed Generic Linux kernel image
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu5                           all          base package for ALSA and OSS sound systems
ii  pptp-linux                                 1.8.0-1                                        amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                   3:6.03+dfsg-11ubuntu1                          amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                            3:6.03+dfsg-11ubuntu1                          all          collection of bootloaders (common)
ii  syslinux-legacy                            2:3.63+dfsg-2ubuntu8                           amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                 2.27.1-6ubuntu3.3                              amd64        miscellaneous system utilities

```
I also tried:

```
sudo apt-get remove --purge linux-image-4.4.0-77-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-77 linux-headers-4.4.0-77-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-4.4.0-77-generic* linux-image-extra-4.4.0-77-generic
  linux-image-extra-4.4.0-83-generic
0 upgraded, 0 newly installed, 3 to remove and 72 not upgraded.
9 not fully installed or removed.
After this operation, 371 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 425804 files and directories currently installed.)
Removing linux-image-extra-4.4.0-77-generic (4.4.0-77.98) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-77-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-77-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-77-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-83-generic (4.4.0-83.106) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-83-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-83-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.4.0-77-generic
 linux-image-extra-4.4.0-83-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```



Could someone help me figure out how to solve these problems?

---

### Post by oldos2er on 2017-11-25
Can you run ```
sudo apt autoremove
``` ?

---

### Post by ddeoli on 2017-11-25
Hi oldos2er:

Thanks for the help!

This is what I get:
```

sudo apt autoremove

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-4.4.0-77-generic linux-image-extra-4.4.0-83-generic
0 upgraded, 0 newly installed, 2 to remove and 72 not upgraded.
9 not fully installed or removed.
After this operation, 304 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 425804 files and directories currently installed.)
Removing linux-image-extra-4.4.0-77-generic (4.4.0-77.98) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-77-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-77-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-77-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-83-generic (4.4.0-83.106) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-83-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-83-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.4.0-77-generic
 linux-image-extra-4.4.0-83-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by ddeoli on 2017-11-30
Hi,

I'm still struggling with this. 
Could someone help me please?

Thanks in advance!

---

### Post by mörgæs on 2017-12-02
It seems like your install is at least dating back from the 14.10 days, maybe older.
Have you considered a fresh install of a later release?

---

### Post by photonxp on 2017-12-02
From the output of the "df -h" command

> 
/dev/sda2                    237M  222M  2.2M **100% /boot**

This showed the **/boot** partition is full, so it's impossible to install new kernel packages.

---

### Post by Impavidus on 2017-12-02
Try```
sudo dpkg --purge linux-image-4.4.0-77-generic linux-image-extra-4.4.0-77-generic
sudo dpkg --purge linux-image-4.4.0-83-generic linux-image-extra-4.4.0-83-generic
```It may give some warnings, but with a bit of luck it will remove two old kernels.

---

### Post by ddeoli on 2017-12-02
Thanks everyone!


[COLOR=#000000]**Mörgæs:**  I have 16.04.3 LTS running on my machine. I'm new to this, so I'm curious about what made you think it was something like 14.10.

[/COLOR]
[COLOR=#000000]**Photonxp:** Yes, it was full. The problem was that I couldn't remove old kernels using Synaptic, for example.


[/COLOR]**Impavidus:** It worked! It gave me a warning related to grub configuration file: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
                  Is that something to be concerned about?

                  Also, I think there is a minor correction to be made. Instead of linux-extra-4.4.0-77-generic, it should have been linux-image-extra-4.4.0-77-generic

```

sudo dpkg --purge linux-image-4.4.0-77-generic linux-extra-4.4.0-77-generic

(Reading database ... 425804 files and directories currently installed.)
Removing linux-image-4.4.0-77-generic (4.4.0-77.98) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-98-generic
Found initrd image: /boot/initrd.img-4.4.0-98-generic
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-4.4.0-77-generic (4.4.0-77.98) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
dpkg: warning: ignoring request to remove linux-extra-4.4.0-77-generic which isn't installed

```

---

### Post by Impavidus on 2017-12-03
> **ddeoli said:**
> [COLOR=#000000]
[/COLOR]**Impavidus:** It worked! It gave me a warning related to grub configuration file: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
                  Is that something to be concerned about?Not really. Having both a timeout and a hidden timeout doesn't make much sense, but update-grub will just ignore it (and give this warning). You can edit /etc/default/grub (with root permissions) to fix it, if you wish.

> Also, I think there is a minor correction to be made. Instead of linux-extra-4.4.0-77-generic, it should have been linux-image-extra-4.4.0-77-genericI thought that's what I wrote. I see no evidence that my post was altered...

After you uninstalled those old kernels (4.4.0-77 and 4.4.0-83), try to get the new one (4.4.0-98) properly installed.```
sudo apt install -f
```

---

### Post by mörgæs on 2017-12-03
> **ddeoli said:**
> 
[COLOR=#000000]**Mörgæs:**  I have 16.04.3 LTS running on my machine. I'm new to this, so I'm curious about what made you think it was something like 14.10.
[/COLOR]

Your output contains the words Utopic and kernel 3.16, both of which indicate that the system was installed as 14.10 (or earlier). I am aware that is has been upgraded after that. 

If you were experiencing other problems with the upgraded system then reinstalling was worth considering. As you have probably seen in the forum there are many posts here dealing with problems related to upgrading.

---

### Post by Tadaen_Sylvermane on 2017-12-03
Unfortunately there is no requirement that people remove outdated information from the internet. It's full of old garbage advice that is worthless and unnecessary these days.

There is simply zero reason for a separate /boot in a home environment, efi boot being the exception. With files getting bigger by the day, the old 256meg /boot idea is a joke. If you feel you really need a separate /boot then make it a couple gigs.
In business and enterprise, I can't speak to it as I don't have experience. But they also are more meticulous with managing their systems than any of us at home. They never have this issue because they keep a proper maintenance schedule on their systems. If you insist on having a ridiculously small /boot then keep up with maintenance and don't get upset when this type of thing happens. This is easily preventable by anyone with 5 minutes of free time or less.

My partitioning scheme is simple, 15g /, 80g /data, 2g swap, and 15g free all wrapped in lvm. I have never once had this issue and don't expect I ever will.

Ultimately you can only solve this by repartitioning. This will come back and bite you in the rear over and over until you do.

---

