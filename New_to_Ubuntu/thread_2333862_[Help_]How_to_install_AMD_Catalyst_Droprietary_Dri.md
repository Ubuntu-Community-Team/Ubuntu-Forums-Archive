---
title: "[Help ]How to install AMD Catalyst Droprietary Driver on Ubuntu 15.1"
date: 2016-08-13
forum: New to Ubuntu
---

### Post by mrminhlong on 2016-08-13
Hello, I'm trying to install AMD Catalyst for my laptop but is not work.

My specs: 

           CPU: i5 4210U 1.7Ghz 
           RAM: 4Gb 
           Intel HD4400 intergrated 
           AMD r7 m265 discrete.

I follow the instruction in [Installer Notes ]("http://www2.ati.com/relnotes/amd-catalyst-graphics-driver-installer-notes-for-linux-operating-systems.pdf")from [AMD download page]("http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64")

Ubuntu 15.10 is supported but when I just run 
```
sudo sh ./amd-driver-installer-15.302-x86.x86_64.run
```
to install driver via GUI, all .deb files are extracted and install. In the end of progress, I got some warnings: 
```

          W: Possible missing firmware /lib/firmware/radeon/boniare_mc.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/mullins_sdma1.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kabini_sdma1.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kaveri_sdma1.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/hawaii_sdma1.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/bonaire_sdma1.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/mullins_uvd.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/hawaii_uvd.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kaveri_uvd.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kabini_uvd.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/bonaire_uvd.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/mullins_vce.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/hawaii_vce.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kaveri_vce.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kabini_vce.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/bonaire_vce.bin for module amdgpu
```

All progress details here:

           ```

Installing package for: Ubuntu/wily
           fglrx_15.302-0ubuntu_.deb
           fglrx-amdcccle_15.302-0ubuntu_.deb
           fglrx-dev_15.302-0ubuntu_.deb
           fglrx-core_15.302-0ubuntu_.deb
           Selecting previously unselected package fglrx-amdcccle.
           (Reading database ... 184617 files and directories currently installed.)
           Preparing to unpack fglrx-amdcccle_15.302-0ubuntu1_amd64.deb ...
           Unpacking fglrx-amdcccle (2:15.302-0ubuntu1) ...
           Selecting previously unselected package fglrx-core.
           Preparing to unpack fglrx-core_15.302-0ubuntu1_amd64.deb ...
           Unpacking fglrx-core (2:15.302-0ubuntu1) ...
           Selecting previously unselected package fglrx.
           Preparing to unpack fglrx_15.302-0ubuntu1_amd64.deb ...
           Unpacking fglrx (2:15.302-0ubuntu1) ...
           Setting up fglrx-core (2:15.302-0ubuntu1) ...
           update-alternatives: using /usr/lib/fglrx-core/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GFXCORE.conf (x86_64-linux-gnu_gfxcore_conf) in auto mode
           Loading new fglrx-core-15.302 DKMS files...
           First Installation: checking all kernels...
           Building only for 4.2.0-16-generic
           Building for architecture x86_64
           Building initial module for 4.2.0-16-generic
           Done.
           fglrx:
           Running module version sanity check.
            - Original module
            - No original module exists within this kernel
            - Installation
            - Installing to /lib/modules/4.2.0-16-generic/updates/dkms/
           depmod......

           DKMS: install completed.
           update-initramfs: deferring update (trigger activated)
           Setting up fglrx (2:15.302-0ubuntu1) ...
           update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
           Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
           Processing triggers for bamfdaemon (0.5.2~bzr0+15.10.20150627.1-0ubuntu1) ...
           Rebuilding /usr/share/applications/bamf-2.index...
           Setting up fglrx-amdcccle (2:15.302-0ubuntu1) ...
           Processing triggers for ureadahead (0.100.0-19) ...
           ureadahead will be reprofiled on next reboot
           Processing triggers for systemd (225-1ubuntu9) ...
           Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
           Processing triggers for mime-support (3.58ubuntu1) ...
           Processing triggers for initramfs-tools (0.120ubuntu6) ...
           update-initramfs: Generating /boot/initrd.img-4.2.0-16-generic
           W: Possible missing firmware /lib/firmware/radeon/boniare_mc.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/mullins_sdma1.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kabini_sdma1.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kaveri_sdma1.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/hawaii_sdma1.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/bonaire_sdma1.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/mullins_uvd.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/hawaii_uvd.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kaveri_uvd.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kabini_uvd.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/bonaire_uvd.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/mullins_vce.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/hawaii_vce.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kaveri_vce.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/kabini_vce.bin for module amdgpu
           W: Possible missing firmware /lib/firmware/radeon/bonaire_vce.bin for module amdgpu
           Processing triggers for libc-bin (2.21-0ubuntu4) ...
           fglrx-amdcccle_15.302-0ubuntu1_amd64.deb fglrx-core_15.302-0ubuntu1_amd64.deb fglrx_15.302-0ubuntu1_amd64.deb
           Removing the generated changes file
           Uninitialised file found, configuring.
           Using /etc/X11/xorg.conf
           Saving back-up to /etc/X11/xorg.conf.original-1
           fglrx-amdcccle_15.302-0ubuntu_.deb
           fglrx-dev_15.302-0ubuntu_.deb
           fglrx-core_15.302-0ubuntu_.deb
           Removing temporary directory: fglrx-install.opC2ej
```

After running "aticonfig --initial" and reboot. I got stuck at logo loading screen. 

Is there any one know how to install driver for Ubuntu 15.1? 

Thanks for advanced.

---

### Post by wildmanne39 on 2016-08-14
I just want to point out that 15.10 has reached EOL which means it is no longer supported and you will no longer receive updates not even security so you system will be as risk as of this moment though I do not think the driver is supported in 16.04 it is being worked on so you might want to install 14.04 for a little longer while they resolve the driver situation.

I believe the reason you can not install that driver is because the kernel you are using is to new an it is not supported in that kernel.

---

### Post by wildmanne39 on 2016-08-14
*Thread moved to **New to Ubuntu**.*

---

### Post by grahammechanical on 2016-08-14
> I  believe the reason you can not install that driver is because the  kernel you are using is to new an it is not supported in that kernel.

This is why it is best to use the Additional Drivers utility to install proprietary video drivers. Ubuntu developers cannot modify proprietary video drivers but they can patch the Linux kernel to get a driver module for a few proprietary video drivers.

Because Ubuntu 15.10 has reached End of Life the software repositories for 15.10 will soon be archived and moved to a new location. This will make it difficult, if not impossible, to update 15.10 or install proprietary video drivers. And doing an online upgrade to 16.04 may also be difficult.

Ubuntu 16.04 does not have any AMD proprietary video drivers because AMD have choosen not to upgrade their proprietary video drivers to work with the latest X Server display server. .All the AMD video driver effort is now being put into its open source video drivers. 

Regards.

---

### Post by kibohusky on 2016-08-14
Open software and sources and make any modification, the application will ask you if you want to reload and when you confirm it will update the cache. You can then go to Additional Drivers and select the flgrx you wish to use.

Note: 16.xx has dropped support for flgrx because the later xorg versions are incompatable.

---

