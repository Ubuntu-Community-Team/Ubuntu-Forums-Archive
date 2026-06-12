---
title: "Sub-process /usr/bin/dpkg returned an error code (1) package for older version 18.04"
date: 2019-11-29
forum: New to Ubuntu
---

### Post by six62 on 2019-11-29
six@6:~$ ```
sudo apt-get remove amdgpu
[sudo] password for six: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'amdgpu' is not installed, so not removed
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 amdgpu-dkms : Depends: amdgpu-core but it is not going to be installed
 amdgpu-lib : Depends: amdgpu-core (= 19.20-812932) but it is not going to be installed
 glamor-amdgpu : Depends: amdgpu-core but it is not going to be installed
 gst-omx-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libdrm-amdgpu-common : Depends: amdgpu-core but it is not going to be installed
 libdrm2-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libdrm2-amdgpu:i386 : Depends: amdgpu-core:i386
 libegl1-amdgpu-mesa : Depends: amdgpu-core but it is not going to be installed
 libegl1-amdgpu-mesa:i386 : Depends: amdgpu-core:i386
 libgbm1-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libgbm1-amdgpu:i386 : Depends: amdgpu-core:i386
 libgl1-amdgpu-mesa-dri : Depends: amdgpu-core but it is not going to be installed
                          Recommends: libtxc-dxtn-s2tc0 but it is not installable or
                                      libtxc-dxtn0 but it is not installable
 libgl1-amdgpu-mesa-dri:i386 : Depends: amdgpu-core:i386
                               Recommends: libtxc-dxtn-s2tc0:i386 but it is not installable or
                                           libtxc-dxtn0:i386 but it is not installable
 libglapi-amdgpu-mesa : Depends: amdgpu-core but it is not going to be installed
 libglapi-amdgpu-mesa:i386 : Depends: amdgpu-core:i386
 libllvm7.1-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libllvm7.1-amdgpu:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-client0 : Depends: amdgpu-core but it is not going to be installed
 libwayland-amdgpu-client0:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-egl1 : Depends: amdgpu-core but it is not going to be installed
 libwayland-amdgpu-egl1:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-server0 : Depends: amdgpu-core but it is not going to be installed
 libwayland-amdgpu-server0:i386 : Depends: amdgpu-core:i386
 mesa-amdgpu-va-drivers : Depends: amdgpu-core but it is not going to be installed
 mesa-amdgpu-va-drivers:i386 : Depends: amdgpu-core:i386
 mesa-amdgpu-vdpau-drivers : Depends: amdgpu-core but it is not going to be installed
 mesa-amdgpu-vdpau-drivers:i386 : Depends: amdgpu-core:i386
 xserver-xorg-amdgpu-video-amdgpu : Depends: amdgpu-core but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
six@6:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  amdgpu-core
The following NEW packages will be installed:
  amdgpu-core
0 upgraded, 1 newly installed, 0 to remove and 22 not upgraded.
44 not fully installed or removed.
Need to get 0 B/2.420 B of archives.
After this operation, 12,3 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 file:/var/opt/amdgpu-pro-local ./ amdgpu-core 19.20-812932 [2.420 B]
(Reading database ... 265816 files and directories currently installed.)
Preparing to unpack .../amdgpu-core_19.20-812932_all.deb ...
ERROR: This package can only be installed on Ubuntu 18.04.
dpkg: error processing archive /var/opt/amdgpu-pro-local/./amdgpu-core_19.20-812
932_all.deb (--unpack):
 new amdgpu-core package pre-installation script subprocess returned error exit 
status 1
Errors were encountered while processing:
 /var/opt/amdgpu-pro-local/./amdgpu-core_19.20-812932_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by six62 on 2019-11-29
I have tryed everything in all the forums please help

---

### Post by wildmanne39 on 2019-11-29
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

### Post by Impavidus on 2019-11-29
Which version of Ubuntu? And 32 bit or 64 bit? Can you tell what might have caused this problem?

---

### Post by six62 on 2019-12-01
64 bit ubuntubudgie 19.10 I have tryed to install amdgpu drivers but it says that it can only be installed for older versions like 18.04 so it got stuck and no command seems to get me out of this situation

---

### Post by Impavidus on 2019-12-01
I haven't got much experience with graphics drivers, but if I'm not mistaken, all amd gpu stuff is now open source and built in, so no need to install amdgpu drivers. I think you should remove all those packages it complains about. But then, I don't use 19.10 or amd graphics. If necessary, you can use```
sudo dpkg --remove package-name
```to remove packages when apt refuses to work because of dependency issues, provided that the missing dependency is only required to make a package work, not to install it.

---

### Post by mörgæs on 2019-12-01
> **six62 said:**
> I have tryed everything in all the forums please help

Whoa, that sounds like several years of work. 

Please begin with a hardware description for example by running ```
sudo lshw -C video
``` and posting the output in CODE tags.

---

### Post by six62 on 2019-12-01
```
six@6:~$ sudo dpkg --remove amdgpu
[sudo] password for six: 
Sorry, try again.
[sudo] password for six: 
dpkg: warning: ignoring request to remove amdgpu which isn't installed
six@6:~$ ^C
six@6:~$ sudo apt-get install spyder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 amdgpu-dkms : Depends: amdgpu-core but it is not going to be installed
 amdgpu-lib : Depends: amdgpu-core (= 19.20-812932) but it is not going to be installed
 glamor-amdgpu : Depends: amdgpu-core but it is not going to be installed
 gst-omx-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libdrm-amdgpu-common : Depends: amdgpu-core but it is not going to be installed
 libdrm2-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libdrm2-amdgpu:i386 : Depends: amdgpu-core:i386
 libegl1-amdgpu-mesa : Depends: amdgpu-core but it is not going to be installed
 libegl1-amdgpu-mesa:i386 : Depends: amdgpu-core:i386
 libgbm1-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libgbm1-amdgpu:i386 : Depends: amdgpu-core:i386
 libgl1-amdgpu-mesa-dri : Depends: amdgpu-core but it is not going to be installed
                          Recommends: libtxc-dxtn-s2tc0 but it is not installable or
                                      libtxc-dxtn0 but it is not installable
 libgl1-amdgpu-mesa-dri:i386 : Depends: amdgpu-core:i386
                               Recommends: libtxc-dxtn-s2tc0:i386 but it is not installable or
                                           libtxc-dxtn0:i386 but it is not installable
 libglapi-amdgpu-mesa : Depends: amdgpu-core but it is not going to be installed
 libglapi-amdgpu-mesa:i386 : Depends: amdgpu-core:i386
 libllvm7.1-amdgpu : Depends: amdgpu-core but it is not going to be installed
 libllvm7.1-amdgpu:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-client0 : Depends: amdgpu-core but it is not going to be installed
 libwayland-amdgpu-client0:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-egl1 : Depends: amdgpu-core but it is not going to be installed
 libwayland-amdgpu-egl1:i386 : Depends: amdgpu-core:i386
 libwayland-amdgpu-server0 : Depends: amdgpu-core but it is not going to be installed
 libwayland-amdgpu-server0:i386 : Depends: amdgpu-core:i386
 mesa-amdgpu-va-drivers : Depends: amdgpu-core but it is not going to be installed
 mesa-amdgpu-va-drivers:i386 : Depends: amdgpu-core:i386
 mesa-amdgpu-vdpau-drivers : Depends: amdgpu-core but it is not going to be installed
 mesa-amdgpu-vdpau-drivers:i386 : Depends: amdgpu-core:i386
 spyder : Depends: python-spyder (= 3.3.6+dfsg1-2) but it is not going to be installed
          Depends: python2.7:any
 xserver-xorg-amdgpu-video-amdgpu : Depends: amdgpu-core but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
six@6:~$ 
```

As you can see too it says that it is not installed but it does not let me download anything either hence I can't download python for I thought that linux would be nice to improve myself as a computer engineer

---

### Post by six62 on 2019-12-01
I downloaded ubuntu budgie right next to windows ten and I thooght of leaving windows and right now I can't even login if I don't login from recovery mode I tryed to fix the issue from their dpkg fix broken packages but it does not work.To boot into linux I have to go to recovery each time or it will get stuck in
/dev/nvme0n1p5:clean,298489/6111232 files,3086100/244208664 blocks




```
six@6:~$ sudo lshw -C video
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: UHD Graphics 620 (Whiskey Lake)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:a1000000-a1ffffff memory:80000000-8fffffff ioport:4000(size=64) memory:c0000-dffff
  *-display UNCLAIMED
       description: Display controller
       product: Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:90000000-9fffffff memory:a0000000-a01fffff ioport:3000(size=256) memory:a2400000-a243ffff memory:a2440000-a245ffff
six@6:~$ 
```

Well,these are my specs I have the rx550x mobile and in windows you have to download it's drivers to go to radeon settings and I was actually going to do it for intel too but this seems really unlogical I mean why?
&#304;f any of you really trust their knowledge [Radeon™ Software for Linux® version 19.20 for Ubuntu 18.04.2]("https://drivers.amd.com/drivers/linux/amdgpu-pro-19.20-812932-ubuntu-18.04.tar.xz") download this and get stuck into the same mistake as me and if you can solve it:I don't know if you can actually back your stuff upp and if something goes wrong you can just start over from the beginning or not because if you can it could be nice to learn new stuff and it is my foolishness it says 18.04 but it was russian when i read it soo yeah I am thinking of trying alittle more it seems fun to enter every new thing that you learn but maybe I might need to delete ubuntu to solve this.I actually wanted to be really great at linux like to be awesome I will be the one not asking the questions but the one who actually answers them and everyone will be like asking me questions later on and I will be like ok do this and that and I will be like more than a cup of coffee seeds,my rank will be like "the seed" or something ahahaha.Soo let's set aside the pros and the cros:)

---

### Post by mörgæs on 2019-12-02
I suggest doing a clean install of 19.10 without adding graphics drivers. 

After that we can take a look at Spyder.

Please note that I don't know anything about dual boot.

---

