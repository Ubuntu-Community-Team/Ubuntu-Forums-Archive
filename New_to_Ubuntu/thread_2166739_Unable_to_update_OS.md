---
title: "Unable to update OS"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by steve10 on 2013-08-10
I try to update using

```
sudo apt-get update && sudo apt-get upgrade
```

I get this 

```
The following packages have unmet dependencies: linux-image-generic-pae : Depends: linux-image-3.2.0-44-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

```

I run

```
sudo apt-get upgrade -f
```

and i get this 

```
Extracting templates from packages: 100%Preconfiguring packages ...
(Reading database ... 310176 files and directories currently installed.)
Unpacking linux-image-3.2.0-51-generic-pae (from .../linux-image-3.2.0-51-generic-pae_3.2.0-51.77_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-51-generic-pae_3.2.0-51.77_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-51-generic-pae': No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-51-generic-pae /boot/vmlinuz-3.2.0-51-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-51-generic-pae /boot/vmlinuz-3.2.0-51-generic-pae
Preparing to replace linux-firmware 1.79.4 (using .../linux-firmware_1.79.6_all.deb) ...
Unpacking replacement linux-firmware ...
Preparing to replace libc-bin 2.15-0ubuntu10.3 (using .../libc-bin_2.15-0ubuntu10.4_i386.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-51-generic-pae_3.2.0-51.77_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried to delete the old kernels and I have tried to install gparted so I can increase the size of /boot put it always errors and comes comes down to the unmet dependencies

---

### Post by ibjsb4 on 2013-08-11
```
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-51-generic-pae_3.2.0-51.77_i386.deb (--unpack):  failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-51-generic-pae': [COLOR=#ff0000]No space left on device[/COLOR]
```

Thats saying you have not removed the old kernels.  Have a look here:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9)

---

