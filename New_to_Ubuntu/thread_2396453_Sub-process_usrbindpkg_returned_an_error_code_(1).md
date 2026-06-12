---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2018-07-16
forum: New to Ubuntu
---

### Post by hp1999 on 2018-07-16
I am running Ubuntu 16.04. Whenever I run sudo apt-get upgrade command it gives me following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
22 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up procps (2:3.3.10-4ubuntu2.4) ...
/var/lib/dpkg/info/procps.postinst: 102: /var/lib/dpkg/info/procps.postinst: update-rc.d: not found
dpkg: error processing package procps (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of cups-daemon:
 cups-daemon depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing package cups-daemon (--configure):
 dependency problems - leaving unconfigured
Setting up grub-common (2.02~beta2-36ubuntu3.18) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          /var/lib/dpkg/info/grub-common.postinst: 6: /var/lib/dpkg/info/grub-common.postinst: update-rc.d: not found
dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.02~beta2-36ubuntu3.18); however:
  Package grub-common is not configured yet.


dpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on grub-common (= 2.02~beta2-36ubuntu3.18); however:
  Package grub-common is not configured yet.


dpkg: error processing package grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 2.02~beta2-36ubuntu3.18); however:
  Package grub-common is not configured yet.
 grub-pc depends on grub2-common (= 2.02~beta2-36ubuntu3.18); however:
  Package grub2-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 2.02~beta2-36ubuntu3.18); however:
  Package grub-pc-bin is not configured yet.


dpkg: error processinNo apport report written because MaxReports is reached already
                                                                                   No apport report written because MaxReports is reached already
                                                                                                                                                 No apport report written because MaxReports is reached already
                               g package grub-pc (--configure):
 dependency problems - leaving unconfigured
Setting up keyboard-configuration (1.108ubuntu15.4) ...
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
/var/lib/dpkg/info/keyboard-configuration.postinst: 162: /var/lib/dpkg/info/keyboard-configuration.postinst: update-rc.d: not found
dpkg: error processing package keyboard-configuration (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of console-setup-linux:
 console-setup-linux depends on keyboard-configuration (= 1.108ubuntu15.4); however:
  Package keyboard-configuration is not configured yet.


dpkg: error processing package console-setup-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on console-setup-linux; however:
  Package console-setup-linux is not configured yet.
 console-setup depends on keyboard-configuration (= 1.108ubuntu15.4); however:
  Package keyboard-configuration is not configured yet.


dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Setting up ifupdown (0.8.10ubuntu1.4) ...
/var/lib/dpkg/info/ifupdown.postinst: 56: /var/lib/dpkg/info/ifupdown.postinst: update-rc.d: not found
dpkg: error processing package ifupdown (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Setting up plymouth (0.9.2-3ubuntu13.5) ...
update-initramfs: deferring update (trigger activated)
/var/lib/dpkg/info/plymouth.postinst: 35: /var/lib/dpkg/info/plymouth.postinst: update-rc.d: not found
dpkg: error processing package plymouth (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
 plymouth-theme-ubuntu-text depends on plymouth (= 0.9.2-3ubuntu13.5); however:
  Package plymouth is not configured yet.


dpkg: error processing package plymouth-theme-ubuntu-text (--configure):
 dependency problems - leaving unconfigured
Setting up apport (2.20.1-0ubuntu2.18) ...
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/apport.postinst: 35: /var/lib/dpkg/info/apport.postinst: update-rc.d: not found
dpkg: error processing package apport (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
 apport-gtk depends on procps; however:
  Package procps is not configured yet.


dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cups-core-drivers:
 cups-core-drivers depends on cups-daemon (>= 2.1.3-4ubuntu0.5); however:
  Package cups-daemon is not configured yet.


dpkg: error processing package cups-core-drivers (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-label:
 plymouth-label depends on plymouth (= 0.9.2-3ubuntu13.5); however:
  Package plymouth is not configured yet.


dpkg: error processing package plymouth-label (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-logo:
 plymouth-theme-ubuntu-logo depends on plymouth (= 0.9.2-3ubuntu13.5); however:
  Package plymouth is not configured yet.
 plymouth-theme-ubuntu-logo depends on plymouth-label (= 0.9.2-3ubuntu13.5); however:
  Package plymouth-label is not configured yet.


dpkg: error processing package plymouth-theme-ubuntu-logo (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-core-hwe-16.04:
 xserver-xorg-core-hwe-16.04 depends on keyboard-configuration; however:
  Package keyboard-configuration is not configured yet.


dpkg: error processing package xserver-xorg-core-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-amdgpu-hwe-16.04:
 xserver-xorg-video-amdgpu-hwe-16.04 depends on xorg-video-abi-23; however:
  Package xorg-video-abi-23 is not installed.
  Package xserver-xorg-core-hwe-16.04 which provides xorg-video-abi-23 is not configured yet.
 xserver-xorg-video-amdgpu-hwe-16.04 depends on xserver-xorg-core-hwe-16.04 (>= 2:1.18.99.901); however:
  Package xserver-xorg-core-hwe-16.04 is not configured yet.


dpkg: error processing package xserver-xorg-video-amdgpu-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-radeon-hwe-16.04:
 xserver-xorg-video-radeon-hwe-16.04 depends on xorg-video-abi-23; however:
  Package xorg-video-abi-23 is not installed.
  Package xserver-xorg-core-hwe-16.04 which provides xorg-video-abi-23 is not configured yet.
 xserver-xorg-video-radeon-hwe-16.04 depends on xserver-xorg-core-hwe-16.04 (>= 2:1.18.99.901); however:
  Package xserver-xorg-core-hwe-16.04 is not configured yet.


dpkg: error processing package xserver-xorg-video-radeon-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-ati-hwe-16.04:
 xserver-xorg-video-ati-hwe-16.04 depends on xorg-video-abi-23; however:
  Package xorg-video-abi-23 is not installed.
  Package xserver-xorg-core-hwe-16.04 which provides xorg-video-abi-23 is not configured yet.
 xserver-xorg-video-ati-hwe-16.04 depends on xserver-xorg-core-hwe-16.04 (>= 2:1.18.99.901); however:
  Package xserver-xorg-core-hwe-16.04 is not configured yet.
 xserver-xorg-video-ati-hwe-16.04 depends on xserver-xorg-video-radeon-hwe-16.04; however:
  Package xserver-xorg-video-radeon-hwe-16.04 is not configured yet.


dpkg: error processing package xserver-xorg-video-ati-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-intel-hwe-16.04:
 xserver-xorg-video-intel-hwe-16.04 depends on xorg-video-abi-23; however:
  Package xorg-video-abi-23 is not installed.
  Package xserver-xorg-core-hwe-16.04 which provides xorg-video-abi-23 is not configured yet.
 xserver-xorg-video-intel-hwe-16.04 depends on xserver-xorg-core-hwe-16.04 (>= 2:1.18.99.901); however:
  Package xserver-xorg-core-hwe-16.04 is not configured yet.


dpkg: error processing package xserver-xorg-video-intel-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for initramfs-tools (0.122ubuntu8.11) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-45-generic
cp: cannot stat '/usr/lib/initramfs-tools/etc/dhcp/': No such file or directory
Errors were encountered while processing:
 procps
 cups-daemon
 grub-common
 grub2-common
 grub-pc-bin
 grub-pc
 keyboard-configuration
 console-setup-linux
 console-setup
 ifupdown
 plymouth
 plymouth-theme-ubuntu-text
 apport
 apport-gtk
 cups-core-drivers
 plymouth-label
 plymouth-theme-ubuntu-logo
 xserver-xorg-core-hwe-16.04
 xserver-xorg-video-amdgpu-hwe-16.04
 xserver-xorg-video-radeon-hwe-16.04
 xserver-xorg-video-ati-hwe-16.04
 xserver-xorg-video-intel-hwe-16.04
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


     I am a noob in Ubuntu. How can I solve this problem?

---

### Post by Impavidus on 2018-07-16
That's a weird problem.

Some packages can't be configured because your system can't find **update-rc.d**, which should be present in /usr/sbin/ and is considered essential on Ubuntu systems. Some other packages can't be configured because their dependencies can't. Try this to see if it's really missing:```
ls -l /usr/sbin/update-rc.d
```It's supposed to be there and to be executable.

If the file is not there, try reinstalling **init-system-helpers**:```
sudo apt-get install --reinstall init-system-helpers
```

Have you at some point manually deleted system files or messed up permissions? Or maybe file system damage by hard reboot while installing updates?

---

### Post by hp1999 on 2018-07-21
Yes, I had repaired my file system in 'initramfs' shell while booting up by running fsck command. Reinstalling init-system-helpers worked. Thanks so much

---

### Post by Impavidus on 2018-07-21
Great. Could you mark this thread as solved?

---

