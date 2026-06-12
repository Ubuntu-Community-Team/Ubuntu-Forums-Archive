---
title: "problems with no space left on device"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by xap1234 on 2014-02-19
Okay so i tried to update my computer and got a message saying the pachage system is broken...i type in 'sudo apt-get install -f' and got this

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.2.0-59-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.2.0-59-generic but it is not going to be installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-59-generic-pae but it is not going to be installed
 yum : Depends: python-urlgrabber but it is not going to be installed
       Depends: rpm (>= 4.4.1) but it is not going to be installed
       Depends: python-rpm but it is not going to be installed
       Depends: python-sqlitecachec but it is not going to be installed
       Depends: python-sqlite but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
xap@xap-ubuntu-laptop:~$ yum clean packages
The program 'yum' is currently not installed.  You can install it by typing:
sudo apt-get install yum
xap@xap-ubuntu-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-59 linux-headers-3.2.0-59-generic linux-image-3.2.0-59-generic linux-image-3.2.0-59-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.2.0-59 linux-headers-3.2.0-59-generic linux-image-3.2.0-59-generic linux-image-3.2.0-59-generic-pae
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/89.4 MB of archives.
After this operation, 295 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 1195397 files and directories currently installed.)
Unpacking linux-image-3.2.0-59-generic (from .../linux-image-3.2.0-59-generic_3.2.0-59.90_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-59-generic_3.2.0-59.90_i386.deb (--unpack):
 unable to create `/lib/modules/3.2.0-59-generic/kernel/drivers/usb/c67x00/c67x00.ko.dpkg-new' (while processing `./lib/modules/3.2.0-59-generic/kernel/drivers/usb/c67x00/c67x00.ko'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-59-generic /boot/vmlinuz-3.2.0-59-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-59-generic /boot/vmlinuz-3.2.0-59-generic
Unpacking linux-headers-3.2.0-59 (from .../linux-headers-3.2.0-59_3.2.0-59.90_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-59_3.2.0-59.90_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-59/arch/um/include/asm/io.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-59/arch/um/include/asm/io.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-59-generic (from .../linux-headers-3.2.0-59-generic_3.2.0-59.90_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-59-generic_3.2.0-59.90_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-59-generic/include/config/scsi/dh/hp': No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-image-3.2.0-59-generic-pae (from .../linux-image-3.2.0-59-generic-pae_3.2.0-59.90_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-59-generic-pae_3.2.0-59.90_i386.deb (--unpack):
 unable to create `/lib/modules/3.2.0-59-generic-pae/kernel/drivers/mfd/pcf50633-adc.ko.dpkg-new' (while processing `./lib/modules/3.2.0-59-generic-pae/kernel/drivers/mfd/pcf50633-adc.ko'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-59-generic_3.2.0-59.90_i386.deb
 /var/cache/apt/archives/linux-headers-3.2.0-59_3.2.0-59.90_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-59-generic_3.2.0-59.90_i386.deb
 /var/cache/apt/archives/linux-image-3.2.0-59-generic-pae_3.2.0-59.90_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xap@xap-ubuntu-laptop:~$ sudo $ yum clean packages
sudo: $: command not found
xap@xap-ubuntu-laptop:~$ sudo yum clean pachages
sudo: yum: command not found
xap@xap-ubuntu-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-59 linux-headers-3.2.0-59-generic linux-image-3.2.0-59-generic linux-image-3.2.0-59-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.2.0-59 linux-headers-3.2.0-59-generic linux-image-3.2.0-59-generic linux-image-3.2.0-59-generic-pae
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/89.4 MB of archives.
After this operation, 295 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 1195397 files and directories currently installed.)
Unpacking linux-image-3.2.0-59-generic (from .../linux-image-3.2.0-59-generic_3.2.0-59.90_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-59-generic_3.2.0-59.90_i386.deb (--unpack):
 unable to create `/lib/modules/3.2.0-59-generic/kernel/drivers/mfd/pcf50633-adc.ko.dpkg-new' (while processing `./lib/modules/3.2.0-59-generic/kernel/drivers/mfd/pcf50633-adc.ko'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-59-generic /boot/vmlinuz-3.2.0-59-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-59-generic /boot/vmlinuz-3.2.0-59-generic
Unpacking linux-headers-3.2.0-59 (from .../linux-headers-3.2.0-59_3.2.0-59.90_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-59_3.2.0-59.90_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-59/arch/um/include/asm/irqflags.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-59/arch/um/include/asm/irqflags.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-59-generic (from .../linux-headers-3.2.0-59-generic_3.2.0-59.90_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-59-generic_3.2.0-59.90_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-59-generic/include/config/scsi/dh/rdac.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-59-generic/include/config/scsi/dh/rdac.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-image-3.2.0-59-generic-pae (from .../linux-image-3.2.0-59-generic-pae_3.2.0-59.90_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-59-generic-pae_3.2.0-59.90_i386.deb (--unpack):
 unable to create `/lib/modules/3.2.0-59-generic-pae/kernel/drivers/mfd/wm8400-core.ko.dpkg-new' (while processing `./lib/modules/3.2.0-59-generic-pae/kernel/drivers/mfd/wm8400-core.ko'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-59-generic_3.2.0-59.90_i386.deb
 /var/cache/apt/archives/linux-headers-3.2.0-59_3.2.0-59.90_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-59-generic_3.2.0-59.90_i386.deb
 /var/cache/apt/archives/linux-image-3.2.0-59-generic-pae_3.2.0-59.90_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

after reading a bit online i found that maybe my file systems were full, when i typed 'sudo ls -a' i get this

```
.               .goutputstream-6TDI1W  .goutputstream-EHU1WW  .goutputstream-M1CHXW  .goutputstream-TZHUYW
..               .goutputstream-6TR2GW  .goutputstream-EIUI1W  .goutputstream-M1X7NW  .goutputstream-U2KG5W
.adobe               .goutputstream-6VM2ZW  .goutputstream-EJC4JW  .goutputstream-M2B98W  .goutputstream-U6HNGW
.audacity-data           .goutputstream-6Y4SAX  .goutputstream-EJPO7W  .goutputstream-M3HALW  .goutputstream-U8R99W
Audiobooks           .goutputstream-6YL13W  .goutputstream-EK66PW  .goutputstream-M5J7GW  .goutputstream-UDQX4W
.avidemux           .goutputstream-71EH3W  .goutputstream-EK6YYW  .goutputstream-M77L2W  .goutputstream-UEJJTW
.bash_history           .goutputstream-768LSW  .goutputstream-EM7R9W  .goutputstream-M9HRPW  .goutputstream-UI114W
.bash_logout           .goutputstream-76NMXW  .goutputstream-ESI3ZW  .goutputstream-MAT5WW  .goutputstream-UK8DEW
.bashrc               .goutputstream-76OV2W  .goutputstream-EXYOJW  .goutputstream-MCQ8OW  .goutputstream-UL0FOW
BnetLog.txt           .goutputstream-779F7W  .goutputstream-F00D3W  .goutputstream-MDC8UW  .goutputstream-UL3Z6W
brasero.iso           .goutputstream-7961FW  .goutputstream-F09C6W  .goutputstream-MH47YW  .goutputstream-ULRM2W
.bzr.log           .goutputstream-7H19IW  .goutputstream-F25YOW  .goutputstream-MHF2PW  .goutputstream-UTD2JW
.cache               .goutputstream-7I3IPW  .goutputstream-F28UOW  .goutputstream-MI3XUW  .goutputstream-UX0GOW
.compiz-1           .goutputstream-7KT34W  .goutputstream-F33V2W  .goutputstream-MJPEOW  .goutputstream-UX3FXW
.config               .goutputstream-7MACYW  .goutputstream-F36W4W  .goutputstream-MK8ROW  .goutputstream-UZS0ZW
.dbus               .goutputstream-7MGQFW  .goutputstream-F5IIKW  .goutputstream-ML0UPW  .goutputstream-V0TILW
Desktop               .goutputstream-7N99VW  .goutputstream-F67LQW  .goutputstream-MS60JW  .goutputstream-V3PQSW
.dmrc               .goutputstream-7QFDPW  .goutputstream-F6TAHW  .goutputstream-MS7YPW  .goutputstream-V5DRQW
Documents           .goutputstream-7QIE0W  .goutputstream-F75BPW  .goutputstream-MTFB6W  .goutputstream-V5SCPW
Downloads           .goutputstream-7QYOIW  .goutputstream-F7BISW  .goutputstream-MXZPGW  .goutputstream-V6R1UW
.esd_auth           .goutputstream-7SKLMW  .goutputstream-F87Y8W  .goutputstream-MYE1XW  .goutputstream-V8QGOW
examples.desktop       .goutputstream-7XAE3W  .goutputstream-F8H4FW  .goutputstream-N39FUW  .goutputstream-VACP6W
Firefox_wallpaper.png  .goutputstream-83V1VW  .goutputstream-F9O48W  .goutputstream-N6FFAX  .goutputstream-VHDG0W
.fontconfig           .goutputstream-85DVZW  .goutputstream-F9OLTW  .goutputstream-N8MTNW  .goutputstream-VUE2GW
.gconf               .goutputstream-88SJVW  .goutputstream-FCC8IW  .goutputstream-N90D6W  .goutputstream-VVMDVW
.gconfd               .goutputstream-8CUTVW  .goutputstream-FDWUPW  .goutputstream-N9E86W  .goutputstream-VVUZ9W
.gegl-0.0           .goutputstream-8DZMZW  .goutputstream-FESSPW  .goutputstream-NE2NSW  .goutputstream-VYT3PW
.gimp-2.6           .goutputstream-8FQPRW  .goutputstream-FF1RFW  .goutputstream-NH7X2W  .goutputstream-VZBTIW
.gksu.lock           .goutputstream-8GFZNW  .goutputstream-FH3C6W  .goutputstream-NI3MZW  .goutputstream-W229UW
.gnome2               .goutputstream-8KHPKW  .goutputstream-FKO0KW  .goutputstream-NJUW1W  .goutputstream-W2SNUW
.gnome2_private        .goutputstream-8LJG9W  .goutputstream-FKSD6W  .goutputstream-NLZQZW  .goutputstream-W3588W
.gnupg               .goutputstream-8ML7WW  .goutputstream-FLPAWW  .goutputstream-NMC0GW  .goutputstream-W6NLEW
.goutputstream-00F09W  .goutputstream-8NBTQW  .goutputstream-FNCI8W  .goutputstream-NNH9GW  .goutputstream-W7BMTW
.goutputstream-02PT7W  .goutputstream-8OGWYW  .goutputstream-FPB09W  .goutputstream-NOK8TW  .goutputstream-WEHCPW
.goutputstream-05J9VW  .goutputstream-8QGKEW  .goutputstream-FU3J4W  .goutputstream-NRN4OW  .goutputstream-WF2IZW
.goutputstream-08D8NW  .goutputstream-8RBONW  .goutputstream-FVRTYW  .goutputstream-NTZ09W  .goutputstream-WGHIPW
.goutputstream-09DRKW  .goutputstream-8SWHYW  .goutputstream-G03V6W  .goutputstream-NV76FW  .goutputstream-WIA3TW
.goutputstream-09ES0W  .goutputstream-8WMQYW  .goutputstream-G2S2FW  .goutputstream-NYBLQW  .goutputstream-WIH9WW
.goutputstream-0E4OQW  .goutputstream-92UDGW  .goutputstream-G3DU1W  .goutputstream-O07MPW  .goutputstream-WINM9W
.goutputstream-0GSWHW  .goutputstream-93ZH8W  .goutputstream-G5LFAX  .goutputstream-O2AJ6W  .goutputstream-WOP6AX
.goutputstream-0I6QFW  .goutputstream-9573JW  .goutputstream-G61O7W  .goutputstream-O6UURW  .goutputstream-WQB4OW
.goutputstream-0K0XNW  .goutputstream-96FKWW  .goutputstream-G63OQW  .goutputstream-OAT4LW  .goutputstream-WTOV9W
.goutputstream-0O7E4W  .goutputstream-97VD7W  .goutputstream-GBE5XW  .goutputstream-OGMIXW  .goutputstream-WUNBWW
.goutputstream-0Q1FGW  .goutputstream-9813NW  .goutputstream-GRCX7W  .goutputstream-OIHHBX  .goutputstream-WWKH7W
.goutputstream-0QRDFW  .goutputstream-9ATONW  .goutputstream-GTELMW  .goutputstream-OMS3GW  .goutputstream-WXBA3W
.goutputstream-0QYCQW  .goutputstream-9B3YEW  .goutputstream-GTLOOW  .goutputstream-ON4TXW  .goutputstream-WZDXAX
.goutputstream-0RHU6W  .goutputstream-9CEGQW  .goutputstream-GX0PGW  .goutputstream-OPJUAX  .goutputstream-X14I3W
.goutputstream-0SQYHW  .goutputstream-9CF1PW  .goutputstream-GX3QYW  .goutputstream-OTIH0W  .goutputstream-X25KXW
.goutputstream-0X8N2W  .goutputstream-9CR6WW  .goutputstream-GXDY4W  .goutputstream-OYZJYW  .goutputstream-X2ZZGW
.goutputstream-0YJYNW  .goutputstream-9DOH4W  .goutputstream-GXJ97W  .goutputstream-OZ7XWW  .goutputstream-X32PLW
.goutputstream-0YXVXW  .goutputstream-9DWFOW  .goutputstream-GZNUOW  .goutputstream-P2N3IW  .goutputstream-X3LK7W
.goutputstream-131I1W  .goutputstream-9H2I3W  .goutputstream-H772NW  .goutputstream-P4Y7XW  .goutputstream-X4KFYW
.goutputstream-13XU7W  .goutputstream-9J9EAX  .goutputstream-H7X1UW  .goutputstream-P60X6W  .goutputstream-X5NJ7W
.goutputstream-1451NW  .goutputstream-9JQ8OW  .goutputstream-H8UQNW  .goutputstream-P6LM6W  .goutputstream-X77ULW
.goutputstream-14HQMW  .goutputstream-9KIM5U  .goutputstream-HCQT3W  .goutputstream-P8M7NW  .goutputstream-X7KN2W
.goutputstream-164QYW  .goutputstream-9KUBUW  .goutputstream-HCZVTW  .goutputstream-P8OB1W  .goutputstream-XDSBBX
.goutputstream-16808W  .goutputstream-9L3W1W  .goutputstream-HDEEUW  .goutputstream-PA2NHW  .goutputstream-XFHE8W
.goutputstream-1CEQ0W  .goutputstream-9Q3MQW  .goutputstream-HDVT1W  .goutputstream-PA9JFW  .goutputstream-XFP8PW
.goutputstream-1CGM0W  .goutputstream-9QGZZW  .goutputstream-HEAC9W  .goutputstream-PCWHXW  .goutputstream-XG03TW
.goutputstream-1EDJSW  .goutputstream-9SPCGW  .goutputstream-HH5SPW  .goutputstream-PEHNXW  .goutputstream-XIOPWW
.goutputstream-1FC9HW  .goutputstream-9TOPOW  .goutputstream-HHNHMW  .goutputstream-PG45PW  .goutputstream-XJNSOW
.goutputstream-1KSH3W  .goutputstream-9WPA7W  .goutputstream-HIRUAX  .goutputstream-PI2P3W  .goutputstream-XPYHFW
.goutputstream-1LYYNW  .goutputstream-9X2ZPW  .goutputstream-HSSGRW  .goutputstream-PJ3OPW  .goutputstream-XVLPQW
.goutputstream-1MOQAX  .goutputstream-9YOU0W  .goutputstream-HT8MWW  .goutputstream-PMH61W  .goutputstream-XXD32W
.goutputstream-1OVZUW  .goutputstream-A3RB0W  .goutputstream-HTYMAX  .goutputstream-PRZOTW  .goutputstream-XZD9PW
.goutputstream-1OWMOW  .goutputstream-A3UZ6W  .goutputstream-HWJIUW  .goutputstream-PTYF4W  .goutputstream-Y34VGW
.goutputstream-1T492W  .goutputstream-A4CNEW  .goutputstream-HYWSGW  .goutputstream-PVCE4W  .goutputstream-Y4LLKW
.goutputstream-1VUZYW  .goutputstream-A5UQEW  .goutputstream-HZ28PW  .goutputstream-PWB6OW  .goutputstream-Y87WNW
.goutputstream-1WH0NW  .goutputstream-A8MBVW  .goutputstream-I05L1W  .goutputstream-PWZCNW  .goutputstream-Y9OMQW
.goutputstream-1ZK8KW  .goutputstream-AB2TPW  .goutputstream-I3IF3W  .goutputstream-PYTFXW  .goutputstream-YBFVNW
.goutputstream-246X0W  .goutputstream-AJ0Q6W  .goutputstream-I4VZZW  .goutputstream-PZGL2W  .goutputstream-YC3W5W
.goutputstream-24OCPW  .goutputstream-AJT1EW  .goutputstream-I5351W  .goutputstream-Q2XMHW  .goutputstream-YE666W
.goutputstream-28778W  .goutputstream-ANCNOW  .goutputstream-I5NZ1W  .goutputstream-Q3BU8W  .goutputstream-YHDYFW
.goutputstream-2AJEVW  .goutputstream-AR2JBX  .goutputstream-I7GNPW  .goutputstream-Q5RZJW  .goutputstream-YHZP4W
.goutputstream-2C8FEW  .goutputstream-AS8QPW  .goutputstream-IAL4QW  .goutputstream-QED3SW  .goutputstream-YI14XW
.goutputstream-2HM19W  .goutputstream-AUV83W  .goutputstream-ICL8WW  .goutputstream-QHFKOW  .goutputstream-YKBMUW
.goutputstream-2JLA5W  .goutputstream-AV3N7W  .goutputstream-ICNZXW  .goutputstream-QHWNAX  .goutputstream-YKMNFW
.goutputstream-2JWCWW  .goutputstream-AWL8KW  .goutputstream-IGEQ8W  .goutputstream-QLUUUW  .goutputstream-YKQV9W
.goutputstream-2OF6RW  .goutputstream-AYLERW  .goutputstream-IH7EYW  .goutputstream-QOWVAX  .goutputstream-YL6D8W
.goutputstream-2VCG5W  .goutputstream-AYX0IW  .goutputstream-IIDT8W  .goutputstream-QPHI4W  .goutputstream-YMXGSW
.goutputstream-2YAM5W  .goutputstream-AZDU8W  .goutputstream-IJUF6W  .goutputstream-QPZEKW  .goutputstream-YOBI5W
.goutputstream-2YXF7W  .goutputstream-B4JJ0W  .goutputstream-IKUEJW  .goutputstream-QST7AX  .goutputstream-YQXV6W
.goutputstream-2Z9J6W  .goutputstream-B554NW  .goutputstream-IME2NW  .goutputstream-QTPH1W  .goutputstream-YRMRVW
.goutputstream-35AZ6W  .goutputstream-BBKLIW  .goutputstream-INP5GW  .goutputstream-QTSX5W  .goutputstream-Z1VCXW
.goutputstream-36UFPW  .goutputstream-BBUGNW  .goutputstream-INXFPW  .goutputstream-QWBTUW  .goutputstream-Z2WSHW
.goutputstream-36YN4W  .goutputstream-BDQCKW  .goutputstream-IT706W  .goutputstream-R0MD9W  .goutputstream-Z30HNW
.goutputstream-37606W  .goutputstream-BDZA0W  .goutputstream-ITPDYW  .goutputstream-R2EN8W  .goutputstream-Z4FQYW
.goutputstream-37CM2W  .goutputstream-BEVUKW  .goutputstream-IUO12W  .goutputstream-R36UAX  .goutputstream-Z7J6NW
.goutputstream-381SNW  .goutputstream-BFK28W  .goutputstream-IVUBAX  .goutputstream-R4DKXW  .goutputstream-ZC2V8W
.goutputstream-399UKW  .goutputstream-BGKBUW  .goutputstream-J8K75W  .goutputstream-R4OGXW  .goutputstream-ZCRE7W
.goutputstream-3C0F2W  .goutputstream-BGL96W  .goutputstream-JAG88W  .goutputstream-R752FW  .goutputstream-ZDXLQW
.goutputstream-3DYM6W  .goutputstream-BGSF7W  .goutputstream-JC864W  .goutputstream-R95S4W  .goutputstream-ZEBI7W
.goutputstream-3DZ17W  .goutputstream-BGW76W  .goutputstream-JFEGZW  .goutputstream-RAKD1W  .goutputstream-ZGQEYW
.goutputstream-3EUS8W  .goutputstream-BIJTNW  .goutputstream-JJ71JW  .goutputstream-RBKVLW  .goutputstream-ZKLIZW
.goutputstream-3IPL9W  .goutputstream-BKWCYW  .goutputstream-JJNLVW  .goutputstream-RBSBWW  .goutputstream-ZNP5JW
.goutputstream-3J3S6W  .goutputstream-BLSI4W  .goutputstream-JLDNZW  .goutputstream-RN8Z9W  .goutputstream-ZQH1OW
.goutputstream-3NH7YW  .goutputstream-BOSS7W  .goutputstream-JMSB7W  .goutputstream-ROHHQW  .goutputstream-ZSMM2W
.goutputstream-3NVNNW  .goutputstream-BV7EQW  .goutputstream-JMWNLW  .goutputstream-RSU5NW  .goutputstream-ZVZV6W
.goutputstream-3T9OPW  .goutputstream-BX9YJW  .goutputstream-JNI1PW  .goutputstream-RTMD4W  .goutputstream-ZX25VW
.goutputstream-3TWTEW  .goutputstream-BXDXPW  .goutputstream-JOW4KW  .goutputstream-RU8T8W  .goutputstream-ZZ7QYW
.goutputstream-3YT82W  .goutputstream-BXN37W  .goutputstream-JPWXQW  .goutputstream-RVK35W  .gphoto
.goutputstream-427WNW  .goutputstream-BY0TXW  .goutputstream-JTU5ZW  .goutputstream-RXNEZW  .gstreamer-0.10
.goutputstream-44PN7W  .goutputstream-BY72ZW  .goutputstream-JU4I7W  .goutputstream-RY170W  .gtk-bookmarks
.goutputstream-46G98W  .goutputstream-BZARAX  .goutputstream-JZ7TIW  .goutputstream-RYF37W  .gtkpod
.goutputstream-47EZTW  .goutputstream-C1AE0W  .goutputstream-K1YSYW  .goutputstream-S13NFW  .guvcviewrc
.goutputstream-48G62W  .goutputstream-C4ZB2W  .goutputstream-K2F20W  .goutputstream-S2P2XW  .guvcviewrc-videoX
.goutputstream-4INXXW  .goutputstream-C60U8W  .goutputstream-K3THPW  .goutputstream-S6EVAX  .gvfs
.goutputstream-4KIKQW  .goutputstream-C8JXMW  .goutputstream-K4DX8W  .goutputstream-S9C24W  .ICEauthority
.goutputstream-4LNEHW  .goutputstream-CDDVNW  .goutputstream-K4WPNW  .goutputstream-SANTPW  .icons
.goutputstream-4LNWQW  .goutputstream-CE0XNW  .goutputstream-K6WQ1W  .goutputstream-SB6NVW  .kde
.goutputstream-4THXTW  .goutputstream-CGTU8W  .goutputstream-K8CI4W  .goutputstream-SINWXW  .libreoffice
.goutputstream-4VJ59W  .goutputstream-CH8UAX  .goutputstream-K8UGQW  .goutputstream-SIVCMW  .local
.goutputstream-4ZPX9W  .goutputstream-CI4U6W  .goutputstream-KBQMEW  .goutputstream-SJF07W  .macromedia
.goutputstream-4ZT2NW  .goutputstream-CIO82W  .goutputstream-KGR9OW  .goutputstream-SJPNGW  .mission-control
.goutputstream-5005KW  .goutputstream-CJ8QFW  .goutputstream-KHLZVW  .goutputstream-SMP8AX  .mozilla
.goutputstream-500KQW  .goutputstream-CLEC2W  .goutputstream-KJKYYW  .goutputstream-SNNAFW  Music
.goutputstream-503AKW  .goutputstream-CMC6LW  .goutputstream-KK2KXW  .goutputstream-SNXGXW  ov51x-jpeg-0.5.4
.goutputstream-510F2W  .goutputstream-CT7SZW  .goutputstream-KLAQXW  .goutputstream-SNZC4W  ov51x-jpeg-0.5.4.tar.gz
.goutputstream-52DV7W  .goutputstream-CUN6NW  .goutputstream-KMN7MW  .goutputstream-SOA0IW  Pictures
.goutputstream-532GQW  .goutputstream-CXP5AX  .goutputstream-KRJWZW  .goutputstream-SQSKGW  .pki
.goutputstream-57A66W  .goutputstream-CZZ6EW  .goutputstream-KSRJQW  .goutputstream-SWUCYW  Podcasts
.goutputstream-59X0WW  .goutputstream-D27XOW  .goutputstream-KU8ZNW  .goutputstream-SYKXYW  .profile
.goutputstream-5CPVVW  .goutputstream-D60DGW  .goutputstream-KXI5VW  .goutputstream-SYO1PW  Public
.goutputstream-5I70TW  .goutputstream-D98ZJW  .goutputstream-KYJ06W  .goutputstream-T1NS8W  .pulse
.goutputstream-5IWRZW  .goutputstream-DDB8PW  .goutputstream-KZ2VMW  .goutputstream-T2V5ZW  .pulse-cookie
.goutputstream-5JZ3YW  .goutputstream-DDIZ6W  .goutputstream-L3U1MW  .goutputstream-T66OPW  .purple
.goutputstream-5OCG1W  .goutputstream-DEQCFW  .goutputstream-L4RSTW  .goutputstream-T6W39W  .shotwell
.goutputstream-5P5F8W  .goutputstream-DF9O7W  .goutputstream-L6CFZW  .goutputstream-T76D3W  .ssh
.goutputstream-5V5WNW  .goutputstream-DFMJOW  .goutputstream-LAUOQW  .goutputstream-T7L2WW  .sudo_as_admin_successful
.goutputstream-5W02YW  .goutputstream-DGAEWW  .goutputstream-LB6W5W  .goutputstream-T7OJYW  Templates
.goutputstream-5WF1SW  .goutputstream-DI135U  .goutputstream-LGM9EW  .goutputstream-T7SKRW  .themes
.goutputstream-5WMI0W  .goutputstream-DJRH4W  .goutputstream-LJE27W  .goutputstream-TASZ1W  .thumbnails
.goutputstream-5XF34W  .goutputstream-DJRTPW  .goutputstream-LK647W  .goutputstream-TB0BPW  .thunderbird
.goutputstream-5Y6P2W  .goutputstream-DK04NW  .goutputstream-LLUJ4W  .goutputstream-TC1ILW  tovid-0.34
.goutputstream-626T9W  .goutputstream-DKFY0W  .goutputstream-LN04EW  .goutputstream-TCHZ8W  Ubuntu One
.goutputstream-63EM0W  .goutputstream-DQ495U  .goutputstream-LNS77W  .goutputstream-TCKHVW  unity-launcher-editor
.goutputstream-64INRW  .goutputstream-DTLCWW  .goutputstream-LPHVZW  .goutputstream-TD5RPW  Videos
.goutputstream-66FJ7W  .goutputstream-DXL0SW  .goutputstream-LQ0V7W  .goutputstream-TG04PW  .VirtualBox
.goutputstream-66HH7W  .goutputstream-DYN43W  .goutputstream-LQ1YYW  .goutputstream-TGWR7W  VirtualBox VMs
.goutputstream-6AYOPW  .goutputstream-E1929W  .goutputstream-LS7UXW  .goutputstream-TPPZAX  .wine
.goutputstream-6EG2VW  .goutputstream-E310TW  .goutputstream-LSAJ3W  .goutputstream-TREO8W  .winff
.goutputstream-6EJ2GW  .goutputstream-E34MWW  .goutputstream-LVDU8W  .goutputstream-TRXF5W  .Xauthority
.goutputstream-6F511W  .goutputstream-E4FQ5W  .goutputstream-LVHHFW  .goutputstream-TUBXXW  .xsession-errors
.goutputstream-6FQW5W  .goutputstream-E70G9W  .goutputstream-LWZX3W  .goutputstream-TUT78W  .xsession-errors.old
.goutputstream-6G1E0W  .goutputstream-EGR7UW  .goutputstream-LXB7IW  .goutputstream-TUWWFW
.goutputstream-6NJ86W  .goutputstream-EGUC4W  .goutputstream-LYZZ7W  .goutputstream-TV88ZW
.goutputstream-6RDMVW  .goutputstream-EHELTW  .goutputstream-M0I5KW  .goutputstream-TY3OFW
```

when i typed 'df -i' i get 

```
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/sda6       1220608 1218221     2387  100% /
udev             206332     550   205782    1% /dev
tmpfs            209988     486   209502    1% /run
none             209988       3   209985    1% /run/lock
none             209988       7   209981    1% /run/shm
/dev/sda1        305216     508   304708    1% /boot
/dev/sda7      12214272   32307 12181965    1% /home
/dev/sda8       6111232    2007  6109225    1% /home/xap/Desktop/torrents
/dev/sda9       6111232     416  6110816    1% /home/xap/Desktop/100storage
/dev/sda10      4284416     440  4283976    1% /home/xap/Desktop/70storage
```

now i see a 100% used my question is how do i fix it, if this is even my problem, any help please?

---

### Post by TheFu on 2014-02-19
TL;DR - please post only important things.

Please use "code" tags - so things line up properly.
There is no easy fix for out-of-inodes.  A new file system needs to be created with either a higher density of inodes or much larger in size so the ratio of inodes-to-sectors is more favorable.  BTW, I get hit by this all-the-time, mostly on file systems where I'm trying to be stingy - like 4G server installations.

BTW - you probably want to cleamup old installed kernels too. [http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) explains.

---

### Post by xap1234 on 2014-02-19
Gee thanks...this is the ABSOLUTE BEGINNERS section right?  I am only asking cause I have no clue how what you posted could help me....

---

### Post by TheFu on 2014-02-19
Sorry - many experienced folks post here too. I didn't want to "talk down" to anyone.

Please post (using code tags) the output from:
```
sudo parted -l
```
and
```
sudo df -h
```
With the data from these, we can look for the easiest solution to the problem.

However .... it is likely that a complete backup and restore will be needed of the partition for a beginner. Other methods are likely too involved/complex to explain here. Sorry.  [http://blog.jdpfu.com/2013/02/01/out-of-disk-space-inodes](http://blog.jdpfu.com/2013/02/01/out-of-disk-space-inodes) is the same issue, but on a virtual machine.

For the other things, please use the "Adv Reply" to get more control with code-tags.

---

### Post by Impavidus on 2014-02-19
The .goutputstream-* files are the result of a known bug. They are in your home directory, which is on a separate partition, so they don't contribute to your problem. You can safely remove them with```
rm .goutputstream-*
```

You have 1.2 million inodes available on your root partition, which is few, and you use all of them, which is a lot. I have 8 million available and use less than 400,000. So I'm wondering, maybe you have a lot of old headers installed. They can consume loads of inodes. They are installed in /usr/src, so let's have a look there:```
ls /usr/src
``` With some luck you may be able to get your inode usage down to something reasonable without reformatting the partition.

---

### Post by TheFu on 2014-02-21
Thanks for the code-tags. Much easier to understand what is happening now.
2 issues, as Impavidus says.

Hopefully, you've removed all the .goutputstream files by now.

For help with the other, bigger, issue, we need the output from the other 2 commands requested previously.

Or ...let others know how you solved it AND please mark the thread as SOLVED.

---

### Post by xap1234 on 2014-02-22
okay with ls /usr/src i got 

```
linux-headers-3.2.0-25              linux-headers-3.2.0-43
linux-headers-3.2.0-25-generic      linux-headers-3.2.0-43-generic
linux-headers-3.2.0-25-generic-pae  linux-headers-3.2.0-43-generic-pae
linux-headers-3.2.0-26              linux-headers-3.2.0-44
linux-headers-3.2.0-26-generic      linux-headers-3.2.0-44-generic
linux-headers-3.2.0-26-generic-pae  linux-headers-3.2.0-44-generic-pae
linux-headers-3.2.0-27              linux-headers-3.2.0-45
linux-headers-3.2.0-27-generic      linux-headers-3.2.0-45-generic
linux-headers-3.2.0-27-generic-pae  linux-headers-3.2.0-45-generic-pae
linux-headers-3.2.0-29              linux-headers-3.2.0-48
linux-headers-3.2.0-29-generic      linux-headers-3.2.0-48-generic
linux-headers-3.2.0-29-generic-pae  linux-headers-3.2.0-48-generic-pae
linux-headers-3.2.0-30              linux-headers-3.2.0-49
linux-headers-3.2.0-30-generic      linux-headers-3.2.0-49-generic
linux-headers-3.2.0-30-generic-pae  linux-headers-3.2.0-49-generic-pae
linux-headers-3.2.0-31              linux-headers-3.2.0-51
linux-headers-3.2.0-31-generic      linux-headers-3.2.0-51-generic
linux-headers-3.2.0-31-generic-pae  linux-headers-3.2.0-51-generic-pae
linux-headers-3.2.0-32              linux-headers-3.2.0-52
linux-headers-3.2.0-32-generic      linux-headers-3.2.0-52-generic
linux-headers-3.2.0-32-generic-pae  linux-headers-3.2.0-52-generic-pae
linux-headers-3.2.0-33              linux-headers-3.2.0-53
linux-headers-3.2.0-33-generic      linux-headers-3.2.0-53-generic
linux-headers-3.2.0-33-generic-pae  linux-headers-3.2.0-53-generic-pae
linux-headers-3.2.0-34              linux-headers-3.2.0-54
linux-headers-3.2.0-34-generic      linux-headers-3.2.0-54-generic
linux-headers-3.2.0-34-generic-pae  linux-headers-3.2.0-54-generic-pae
linux-headers-3.2.0-35              linux-headers-3.2.0-55
linux-headers-3.2.0-35-generic      linux-headers-3.2.0-55-generic
linux-headers-3.2.0-35-generic-pae  linux-headers-3.2.0-55-generic-pae
linux-headers-3.2.0-38              linux-headers-3.2.0-56
linux-headers-3.2.0-38-generic      linux-headers-3.2.0-56-generic
linux-headers-3.2.0-38-generic-pae  linux-headers-3.2.0-56-generic-pae
linux-headers-3.2.0-39              linux-headers-3.2.0-57
linux-headers-3.2.0-39-generic      linux-headers-3.2.0-57-generic
linux-headers-3.2.0-39-generic-pae  linux-headers-3.2.0-58
linux-headers-3.2.0-41              linux-headers-3.2.0-58-generic
linux-headers-3.2.0-41-generic      virtualbox-4.1.12
linux-headers-3.2.0-41-generic-pae
```

---

### Post by xap1234 on 2014-02-22
Please feel free to talk down to me i really have no clue what i am doing most of the time! <G>
okay from 'sudo parted -l' i got

Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  5000MB  4999MB  primary   ext4            boot
 2      5001MB  500GB   495GB   extended
 5      5001MB  9999MB  4999MB  logical   linux-swap(v1)
 6      10.0GB  30.0GB  20.0GB  logical   ext4
 7      30.0GB  230GB   200GB   logical   ext4
 8      230GB   330GB   100GB   logical   ext4
 9      330GB   430GB   100GB   logical   ext4
10      430GB   500GB   70.1GB  logical   ext4

and from 'sudo df -h' i got 

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        19G   13G  4.5G  75% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           788M  912K  787M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  408K  2.0G   1% /run/shm
/dev/sda1       4.6G  1.4G  3.1G  30% /boot
/dev/sda7       184G   12G  163G   7% /home
/dev/sda8        92G   57G   31G  66% /home/xap/Desktop/torrents
/dev/sda9        92G   67G   21G  77% /home/xap/Desktop/100storage
/dev/sda10       65G   51G   11G  84% /home/xap/Desktop/70storage

---

### Post by xap1234 on 2014-02-22
i entered 'rm .goutputstream-*' and nothing seemed to happen how do i know if it worked?

---

### Post by TheFu on 2014-02-22
Please, please, please, please wrap all copy/paste commands and output in "code" tags **always**. It is just too hard to read otherwise.

How do you know if the **rm** command worked?  Are all those files gone?  **man rm** to learn more.

Having all those kernel source is a problem. Need to clean them up using **sudo aptitude autoremove**. This is needed as part of your weekly patching methods.  DO NOT just delete the files and directories. That will put the system into "APT HELL."  Minimal amounts of [system maintenance]("http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs") is needed for Ubuntu systems.

---

### Post by xap1234 on 2014-02-22
how do i wrap them in code tags?

---

### Post by Bashing-om on 2014-02-22
xap1234; Hi !

My little it to help and move things along;
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
The use of "code tags" really helps us to help you !

Linux assumes you know exactly what you are doing, a valid command is executed with no back talk or sass ! The system just does what it is told to do.

Prior to "properly" removing the old un-needed kernels, one must be sure NOT to remove the kernel that one is booting from; and to also keep one additional kernel as a backup in the event there is a problem.
To see what what the booting kernel is, run the terminal command:
```

uname -r

```

In the event you have difficulties removing those old kernels, by all means let us know so we can help. There are a number of means to remove them; my personal preference is from the terminal, using the package manager's tools.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by pqwoerituytrueiwoq on 2014-02-22
run this command to free up some space
sudo apt-get autoclean
that will get you enough to work with to get to the main cause of the problem
next remove your old kernels (google a guide) you only need the 2 with the highest version numbers
you can install bleachbit, it is a junk file cleaner

---

### Post by Impavidus on 2014-02-22
If rm did not complain that it couldn't remove the files, it removed them.

First use```
uname -r
```to confirm you are currently booting 3.2.0-57 or 3.2.0-58.

You have a lot of old header packages installed. These are consuming all your inodes, so you have to uninstall them. Ideally, you'd use the package manager to do so. Using autoremove doesn't work on 12.04 (it does on 13.10, I am told), so you have to do it the old-fashioned way:```
sudo dpkg --purge linux-headers-3.2.0-{25..56}{,-generic,-generic-pae}
```It may give you a few warnings about unknown packages or packages not installed, but this should uninstall your header packages, except the two most recent. However, with your package manager already in an inconsistent state, it may not work.

Before you can uninstall old packages you may have to fix the package manager, to fix the package manager you have to install the latest header package and to install the latest header package you have to uninstall some old ones first. The following solution seems to work.

First delete some files from the old header packages:```
sudo rm -r /usr/src/linux-headers-3.2.0-2*
```This will remove the bulk of the files belonging to header package version 3.2.0-25, 3.2.0-26, 3.2.0-27 and 3.2.0-29 and should free enough inodes to install version 3.2.0-59. Your system will be in an inconsistent state with some installed packages partially removed, which could brake your system if you actually try to use any of those packages. This can lead to the apt hell TheFu is refering too, so you have to be careful and only remove those files and directories, to keep the files properly registered in the package manager, and manually clean-up immediately afterwards.

Install headers version 3.2.0-59 and fix the package manager at the same time using```
sudo apt-get install -f
```Now properly uninstall the old header packages of which you already removed some files, along with the other old packages, using```
sudo apt-get purge linux-headers-3.2.0-{25..56}{,-generic,-generic-pae}
```This puts your package manager back into a clean state.

Given the number of inodes in your boot partition I think you also have a lot of old kernels installed. You can uninstall them with```
sudo apt-get purge linux-image-3.2.0-{25..56}-generic
```assuming those are the ones you have installed.

---

### Post by TheFu on 2014-02-22
```
sudo purge linux-headers-3.2.0-{25..56}{,-generic,-generic-pae}
```

This is missing **aptitude** or **apt-get**. "purge" is an option, not a program.  A few of the other example code snips above are missing them too. Simple mistake that I've made too, but confusing to someone not used to CLI.

I would NOT use **rm** to delete any package installed files. Always use the package manager.

---

### Post by Impavidus on 2014-02-23
Fixed that.

I agree it's a bad idea in general to rm files from installed packages, but I experienced that this is the typical case where the package manager can get into a deadlock: it refuses to uninstall anything until the dependencies have been fixed, which cannot be fixed until some disk space has been freed, for which old packaged have to be removed.

Now that I think again about it, pdkg --purge may be willing to remove the packages without insisting on fixing the dependencies first. Modifying my previous post again.

---

### Post by fdrake on 2014-02-23
after removing the old kernels run
```
sudo update-grub2
```
so that your grub won't have the old list

---

### Post by TheFu on 2014-02-23
The way that I've dealt with this was to MOVE the files temporarily to a different file system, clean up other packages, then move them back a little at a time and purge the files using the package manager.  Once that wasn't an option, so added a new /var/www partition and moved all the files down there (damn ruby-on-rails app with thousands and thousands of tiny files), freeing up / inodes.

Just took a power hit. Sunny and 72 deg outside today. Thanks to a few UPSes - nothing bad happened.  No power issues at all during recent ice/snow storms, but on a fantastic day like to day - BAM. Out for 10 seconds? Odd.

Here's that system today:
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1       7.1G  3.0G  3.7G  45% /
/dev/vda2       2.3G  801M  1.4G  38% /var/www

$ df -ih
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/vda1        454K  287K  167K   64% /
/dev/vda2        151K   56K   95K   38% /var/www
```

This is a virtual machine, so adding another virtual-HDD isn't THAT hard. I'd try using a USB-flash drive for the /usr/src stuff. Might be a little more advanced than an average Ubuntu user could handle? I don't know.

---

### Post by xap1234 on 2014-02-26
Thanks that fixed my problem! :)

---

