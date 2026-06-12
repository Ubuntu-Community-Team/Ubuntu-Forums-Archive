---
title: "What is this?"
date: 2017-08-04
forum: New to Ubuntu
---

### Post by iblueflash on 2017-08-04
```
iblueflash@iblueflash-X556UQK:~$ sudo apt update && sudo apt upgrade
[sudo] password for iblueflash: 
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty InRelease
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates InRelease [89,2 kB]
Hit:3 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security InRelease [89,2 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 DEP-11 Metadata [51,9 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main DEP-11 64x64 Icons [23,9 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/universe amd64 DEP-11 Metadata [78,0 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/universe DEP-11 64x64 Icons [86,7 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 DEP-11 Metadata [5.840 B]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/main amd64 DEP-11 Metadata [11,7 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/universe amd64 DEP-11 Metadata [14,4 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security/universe DEP-11 64x64 Icons [31,0 kB]
Ign:13 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease         
Hit:14 [http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu](http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu) xenial InRelease
Hit:15 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Fetched 482 kB in 5s (81,1 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gamin guile-2.0-libs i965-va-driver liba52-0.7.4 libaacs0 libass5
  libavcodec57 libavutil55 libbasicusageenvironment1 libbdplus0 libbluray2
  libcddb2 libchromaprint1 libcrystalhd3 libdc1394-22 libdca0
  libdirectfb-1.2-9 libdvbpsi10 libdvdnav4 libdvdread4 libebml4v5
  libedataserverui-1.2-1 libfaad2 libgamin0 libgc1c2 libgme0
  libgnome-games-support-1-2 libgnome-games-support-common libgroupsock8
  libgsm1 libiso9660-8 libkate1 liblivemedia57 liblua5.2-0 libmad0
  libmatroska6v5 libmp3lame0 libmpcdec6 libmpeg2-4 libmpg123-0 libopenjp2-7
  libopenmpt-modplug1 libopenmpt0 libproxy-tools libqqwing2v5
  libresid-builder0c2a libsdl-image1.2 libshine3 libsidplay2v5 libsndio6.1
  libsoxr0 libssh-gcrypt-4 libssh2-1 libswresample2 libtwolame0 libupnp6
  libusageenvironment3 libva-drm1 libva-x11-1 libva1 libvcdinfo0 libvlc-bin
  libvlc5 libvlccore8 libwxsmithlib0 libx264-148 libx265-110 libxcb-xv0
  libxvidcore4 libzvbi-common libzvbi0 linux-headers-4.10.0-19
  linux-headers-4.10.0-19-generic linux-image-4.10.0-19-generic
  linux-image-extra-4.10.0-19-generic mesa-va-drivers va-driver-all valgrind
  vlc-bin vlc-data vlc-l10n vlc-plugin-base vlc-plugin-notify vlc-plugin-qt
  vlc-plugin-samba vlc-plugin-skins2 vlc-plugin-video-output
  vlc-plugin-video-splitter vlc-plugin-visualization
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-4.10.0-30 linux-headers-4.10.0-30-generic
  linux-image-4.10.0-30-generic linux-image-extra-4.10.0-30-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic linux-libc-dev
4 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 62,4 MB of archives.
After this operation, 308 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-image-4.10.0-30-generic amd64 4.10.0-30.34 [20,2 MB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-image-extra-4.10.0-30-generic amd64 4.10.0-30.34 [30,0 MB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-generic amd64 4.10.0.30.31 [1.784 B]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-image-generic amd64 4.10.0.30.31 [2.312 B]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-headers-4.10.0-30 all 4.10.0-30.34 [10,6 MB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-headers-4.10.0-30-generic amd64 4.10.0-30.34 [688 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-headers-generic amd64 4.10.0.30.31 [2.282 B]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main amd64 linux-libc-dev amd64 4.10.0-30.34 [914 kB]
Fetched 62,4 MB in 1min 13s (853 kB/s)                                         
Selecting previously unselected package linux-image-4.10.0-30-generic.
(Reading database ... 245778 files and directories currently installed.)
Preparing to unpack .../0-linux-image-4.10.0-30-generic_4.10.0-30.34_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
Done.
Unpacking linux-image-4.10.0-30-generic (4.10.0-30.34) ...
Selecting previously unselected package linux-image-extra-4.10.0-30-generic.
Preparing to unpack .../1-linux-image-extra-4.10.0-30-generic_4.10.0-30.34_amd64.deb ...
Unpacking linux-image-extra-4.10.0-30-generic (4.10.0-30.34) ...
Preparing to unpack .../2-linux-generic_4.10.0.30.31_amd64.deb ...
Unpacking linux-generic (4.10.0.30.31) over (4.10.0.29.30) ...
Preparing to unpack .../3-linux-image-generic_4.10.0.30.31_amd64.deb ...
Unpacking linux-image-generic (4.10.0.30.31) over (4.10.0.29.30) ...
Selecting previously unselected package linux-headers-4.10.0-30.
Preparing to unpack .../4-linux-headers-4.10.0-30_4.10.0-30.34_all.deb ...
Unpacking linux-headers-4.10.0-30 (4.10.0-30.34) ...
Selecting previously unselected package linux-headers-4.10.0-30-generic.
Preparing to unpack .../5-linux-headers-4.10.0-30-generic_4.10.0-30.34_amd64.deb ...
Unpacking linux-headers-4.10.0-30-generic (4.10.0-30.34) ...
Preparing to unpack .../6-linux-headers-generic_4.10.0.30.31_amd64.deb ...
Unpacking linux-headers-generic (4.10.0.30.31) over (4.10.0.29.30) ...
Preparing to unpack .../7-linux-libc-dev_4.10.0-30.34_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.10.0-30.34) over (4.10.0-29.33) ...
Setting up linux-image-4.10.0-30-generic (4.10.0-30.34) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.10.0-30-generic
Found initrd image: /boot/initrd.img-4.10.0-30-generic
Found linux image: /boot/vmlinuz-4.10.0-29-generic
Found initrd image: /boot/initrd.img-4.10.0-29-generic
Found linux image: /boot/vmlinuz-4.10.0-28-generic
Found initrd image: /boot/initrd.img-4.10.0-28-generic
Found linux image: /boot/vmlinuz-4.10.0-19-generic
Found initrd image: /boot/initrd.img-4.10.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-libc-dev:amd64 (4.10.0-30.34) ...
Setting up linux-headers-4.10.0-30 (4.10.0-30.34) ...
Setting up linux-image-extra-4.10.0-30-generic (4.10.0-30.34) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.10.0-30-generic
Found initrd image: /boot/initrd.img-4.10.0-30-generic
Found linux image: /boot/vmlinuz-4.10.0-29-generic
Found initrd image: /boot/initrd.img-4.10.0-29-generic
Found linux image: /boot/vmlinuz-4.10.0-28-generic
Found initrd image: /boot/initrd.img-4.10.0-28-generic
Found linux image: /boot/vmlinuz-4.10.0-19-generic
Found initrd image: /boot/initrd.img-4.10.0-19-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-headers-4.10.0-30-generic (4.10.0-30.34) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
Setting up linux-image-generic (4.10.0.30.31) ...
Setting up linux-headers-generic (4.10.0.30.31) ...
Setting up linux-generic (4.10.0.30.31) ...
```

---

### Post by vasa1 on 2017-08-04
Terminal output generated by the commands you ran.

---

### Post by Autodave on 2017-08-04
Looks like a normal update to me. Is there something in particular you are referring to?

Please, from now on, put a long post like that inside of quote tags so that people with slower internet connections don't have to wait so long.

---

### Post by deadflowr on 2017-08-04
Please use code tags when posting the output from a terminal.
(In the Reply to Thread press the # to use code tags)
or for manual use do [noparse]```
 terminal-output-goes-here
```[/noparse]
as in write [noparse]```
 
```[/noparse]
placing the terminal output in between the two code brackets.

---

### Post by iblueflash on 2017-08-04
ok

---

### Post by deadflowr on 2017-08-04
So, my only question is, does the output just end/hang at the last line
> Setting up linux-generic (4.10.0.30.31) ...
 or does the output eventually bring you back to your prompt:
> iblueflash@iblueflash-X556UQK:~$

---

### Post by Impavidus on 2017-08-04
The only thing that strikes me as a little odd is the large number of packages that can be autoremoved. Most of them are libraries, not applications, so it doesn't seem likely you'll suddenly miss anything if you uninstall them.

---

