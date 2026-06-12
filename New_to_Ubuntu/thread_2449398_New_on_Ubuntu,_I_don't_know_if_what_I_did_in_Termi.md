---
title: "New on Ubuntu, I don't know if what I did in Terminal is good and properly"
date: 2020-08-26
forum: New to Ubuntu
---

### Post by denisdell on 2020-08-26
Hi,

I'm new on Ubuntu (my version is 18.04 LTS) and I have tried to accommodate myself with the Terminal but I don't if what I did there is good and properly.

Can you check it for me ?

```

**denis@dell:~$ sudo apt purge neofetch**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'neofetch' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb btrfs-tools cryptsetup-bin dmraid giblib1 gir1.2-geocodeglib-1.0 gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 kpartx kpartx-boot libdebian-installer4 libdmraid1.0.0.rc16 libfwup1
  libid3tag0 libido3-0.1-0 libimlib2 libllvm8 libnvidia-cfg1-418 libnvidia-cfg1-430 libnvidia-common-418 libnvidia-common-430 libnvidia-compute-418 libnvidia-compute-430 libnvidia-decode-418
  libnvidia-decode-430 libnvidia-encode-418 libnvidia-encode-430 libnvidia-fbc1-418 libnvidia-fbc1-430 libnvidia-gl-418 libnvidia-gl-430 libnvidia-ifr1-418 libnvidia-ifr1-430 libtimezonemap-data
  libtimezonemap1 linux-headers-5.0.0-1063-oem-osp1 linux-image-5.0.0-1063-oem-osp1 linux-modules-5.0.0-1063-oem-osp1 linux-oem-osp1-headers-5.0.0-1016 linux-oem-osp1-headers-5.0.0-1063
  nvidia-compute-utils-418 nvidia-compute-utils-430 nvidia-dkms-418 nvidia-dkms-430 nvidia-utils-418 nvidia-utils-430 python3-icu python3-pam rdate scrot ubuntu-web-launchers
  xserver-xorg-video-nvidia-418 xserver-xorg-video-nvidia-430
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
**denis@dell:~$ sudo apt --purge remove neofetch**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'neofetch' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb btrfs-tools cryptsetup-bin dmraid giblib1
  gir1.2-geocodeglib-1.0 gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 kpartx
  kpartx-boot libdebian-installer4 libdmraid1.0.0.rc16 libfwup1 libid3tag0
  libido3-0.1-0 libimlib2 libllvm8 libnvidia-cfg1-418 libnvidia-cfg1-430
  libnvidia-common-418 libnvidia-common-430 libnvidia-compute-418
  libnvidia-compute-430 libnvidia-decode-418 libnvidia-decode-430
  libnvidia-encode-418 libnvidia-encode-430 libnvidia-fbc1-418
  libnvidia-fbc1-430 libnvidia-gl-418 libnvidia-gl-430 libnvidia-ifr1-418
  libnvidia-ifr1-430 libtimezonemap-data libtimezonemap1
  linux-headers-5.0.0-1063-oem-osp1 linux-image-5.0.0-1063-oem-osp1
  linux-modules-5.0.0-1063-oem-osp1 linux-oem-osp1-headers-5.0.0-1016
  linux-oem-osp1-headers-5.0.0-1063 nvidia-compute-utils-418
  nvidia-compute-utils-430 nvidia-dkms-418 nvidia-dkms-430 nvidia-utils-418
  nvidia-utils-430 python3-icu python3-pam rdate scrot ubuntu-web-launchers
  xserver-xorg-video-nvidia-418 xserver-xorg-video-nvidia-430
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
**denis@dell:~$ sudo apt-get purge --auto-remove neofetch**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'neofetch' is not installed, so not removed
The following packages will be REMOVED:
  apt-clone* archdetect-deb* btrfs-tools* cryptsetup-bin* dmraid* giblib1*
  gir1.2-geocodeglib-1.0* gir1.2-timezonemap-1.0* gir1.2-xkl-1.0* kpartx*
  kpartx-boot* libdebian-installer4* libdmraid1.0.0.rc16* libfwup1*
  libid3tag0* libido3-0.1-0* libimlib2* libllvm8* libnvidia-cfg1-418*
  libnvidia-cfg1-430* libnvidia-common-418* libnvidia-common-430*
  libnvidia-compute-418* libnvidia-compute-430* libnvidia-decode-418*
  libnvidia-decode-430* libnvidia-encode-418* libnvidia-encode-430*
  libnvidia-fbc1-418* libnvidia-fbc1-430* libnvidia-gl-418* libnvidia-gl-430*
  libnvidia-ifr1-418* libnvidia-ifr1-430* libtimezonemap-data*
  libtimezonemap1* linux-headers-5.0.0-1063-oem-osp1*
  linux-image-5.0.0-1063-oem-osp1* linux-modules-5.0.0-1063-oem-osp1*
  linux-oem-osp1-headers-5.0.0-1016* linux-oem-osp1-headers-5.0.0-1063*
  nvidia-compute-utils-418* nvidia-compute-utils-430* nvidia-dkms-418*
  nvidia-dkms-430* nvidia-utils-418* nvidia-utils-430* python3-icu*
  python3-pam* rdate* scrot* ubuntu-web-launchers*
  xserver-xorg-video-nvidia-418* xserver-xorg-video-nvidia-430*
0 upgraded, 0 newly installed, 54 to remove and 20 not upgraded.
After this operation, 476 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 227301 files and directories currently installed.)
Removing apt-clone (0.4.1ubuntu2) ...
Removing archdetect-deb (1.117ubuntu6.18.04.1) ...
Removing btrfs-tools (4.15.1-1build1) ...
Removing cryptsetup-bin (2:2.0.2-1ubuntu1.1) ...
Removing dmraid (1.0.0.rc16-8ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Removing scrot (0.8-18) ...
Removing giblib1:amd64 (1.2.4-11) ...
Removing ubuntu-web-launchers (18.04.7) ...
Removing gir1.2-geocodeglib-1.0:amd64 (3.25.4.1-4ubuntu0.18.04.1) ...
Removing gir1.2-timezonemap-1.0 (0.4.5) ...
Removing gir1.2-xkl-1.0:amd64 (5.4-3) ...
Removing kpartx-boot (0.7.4-2ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Removing kpartx (0.7.4-2ubuntu3) ...
Removing libdebian-installer4:amd64 (0.110ubuntu2) ...
Removing libdmraid1.0.0.rc16 (1.0.0.rc16-8ubuntu1) ...
Removing libfwup1:amd64 (12-3bionic2) ...
Removing libimlib2:amd64 (1.4.10-1) ...
Removing libid3tag0:amd64 (0.15.1b-13) ...
Removing libido3-0.1-0:amd64 (13.10.0+17.04.20161028-0ubuntu1) ...
Removing libllvm8:amd64 (1:8-3~ubuntu18.04.2) ...
Removing xserver-xorg-video-nvidia-418:amd64 (430.50-0ubuntu0.18.04.2) ...
Removing libnvidia-cfg1-418:amd64 (430.50-0ubuntu0.18.04.2) ...
Removing libnvidia-cfg1-430:amd64 (440.100-0ubuntu0.18.04.1) ...
Removing libnvidia-ifr1-418:amd64 (430.50-0ubuntu0.18.04.2) ...
Removing libnvidia-gl-418:amd64 (430.50-0ubuntu0.18.04.2) ...
Removing libnvidia-common-418 (430.50-0ubuntu0.18.04.2) ...
Removing libnvidia-common-430 (440.100-0ubuntu0.18.04.1) ...
Removing libnvidia-encode-418:amd64 (430.50-0ubuntu0.18.04.2) ...
Removing libnvidia-decode-418:amd64 (430.50-0ubuntu0.18.04.2) ...
Removing nvidia-utils-418:amd64 (430.50-0ubuntu0.18.04.2) ...
Removing libnvidia-compute-418:amd64 (430.50-0ubuntu0.18.04.2) ...
Removing libnvidia-compute-430:amd64 (440.100-0ubuntu0.18.04.1) ...
Removing libnvidia-decode-430:amd64 (440.100-0ubuntu0.18.04.1) ...
Removing libnvidia-encode-430:amd64 (440.100-0ubuntu0.18.04.1) ...
Removing libnvidia-fbc1-418:amd64 (430.50-0ubuntu0.18.04.2) ...
Removing libnvidia-fbc1-430:amd64 (440.100-0ubuntu0.18.04.1) ...
Removing libnvidia-gl-430:amd64 (440.100-0ubuntu0.18.04.1) ...
Removing libnvidia-ifr1-430:amd64 (440.100-0ubuntu0.18.04.1) ...
Removing libtimezonemap1:amd64 (0.4.5) ...
Removing libtimezonemap-data (0.4.5) ...
Removing linux-headers-5.0.0-1063-oem-osp1 (5.0.0-1063.68) ...
Removing linux-image-5.0.0-1063-oem-osp1 (5.0.0-1063.68) ...
/etc/kernel/prerm.d/dkms:
dkms: removing: nvidia 440.100 (5.0.0-1063-oem-osp1) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia
Version: 440.100
Kernel:  5.0.0-1063-oem-osp1 (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.0.0-1063-oem-osp1/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia-modeset.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.0.0-1063-oem-osp1/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia-drm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.0.0-1063-oem-osp1/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia-uvm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.0.0-1063-oem-osp1/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...

DKMS: uninstall completed.
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.0.0-1063-oem-osp1
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/42_oem-kernel-parameter-suspend-to-ram.cfg'
Sourcing file `/etc/default/grub.d/42_oem-kernel-parameter-tsc-reliable.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.0.0-1067-oem-osp1
Found initrd image: /boot/initrd.img-5.0.0-1067-oem-osp1
Found linux image: /boot/vmlinuz-5.0.0-1065-oem-osp1
Found initrd image: /boot/initrd.img-5.0.0-1065-oem-osp1
Adding boot menu entry for EFI firmware configuration
done
Removing linux-modules-5.0.0-1063-oem-osp1 (5.0.0-1063.68) ...
Removing linux-oem-osp1-headers-5.0.0-1016 (5.0.0-1016.18) ...
Removing linux-oem-osp1-headers-5.0.0-1063 (5.0.0-1063.68) ...
Removing nvidia-compute-utils-418:amd64 (430.50-0ubuntu0.18.04.2) ...
Removing nvidia-compute-utils-430:amd64 (440.100-0ubuntu0.18.04.1) ...
Removing nvidia-dkms-418 (430.50-0ubuntu0.18.04.2) ...
Removing nvidia-dkms-430 (440.100-0ubuntu0.18.04.1) ...
Removing nvidia-utils-430:amd64 (440.100-0ubuntu0.18.04.1) ...
Removing python3-icu (1.9.8-0ubuntu1) ...
Removing python3-pam (0.4.2-13.2ubuntu4) ...
Removing rdate (1:1.2-6) ...
Removing xserver-xorg-video-nvidia-430:amd64 (440.100-0ubuntu0.18.04.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1.2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-1067-oem-osp1
(Reading database ... 173832 files and directories currently installed.)
Purging configuration files for kpartx-boot (0.7.4-2ubuntu3) ...
Purging configuration files for dmraid (1.0.0.rc16-8ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Purging configuration files for libnvidia-compute-418:amd64 (430.50-0ubuntu0.18.04.2) ...
Purging configuration files for linux-modules-5.0.0-1063-oem-osp1 (5.0.0-1063.68) ...
dpkg: warning: while removing linux-modules-5.0.0-1063-oem-osp1, directory '/lib/modules/5.0.0-1063-oem-osp1' not empty so not removed
Purging configuration files for linux-image-5.0.0-1063-oem-osp1 (5.0.0-1063.68) ...
Processing triggers for initramfs-tools (0.130ubuntu3.9) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-1067-oem-osp1

```

If any knows ?

---

### Post by deadflowr on 2020-08-26
It looks fine.
As far as the output you never had neoftech installed and the listing of packages it wanted to remove were those packages marked
as either no longer needed (those are packages that were originally installed to satisfy the dependency needs of another package which has since been removed)
or the package has a new version installed and the one marked for removal has been deemed obsolete.

---

### Post by denisdell on 2020-08-26
I tried only to remove completely the screenfetch and neofetch packages. 

I thought I removed some necessary drivers or important things. So, I should do not worry about that.

Thanks for the answer.

---

