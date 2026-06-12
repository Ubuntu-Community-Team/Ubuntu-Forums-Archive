---
title: "can upgrade"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by se user on 2008-04-25
hello all i am havening a problem and i was wondering if you could help me i can't upgrade AT ALL i get a error and it gives me this log 

```
Installing busybox as dep of initramfs-tools
Installing sysvinit-utils as dep of initscripts
Starting
Starting 2
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5102 as a solution to upstart 30
  Removing upstart rather than change sysvinit
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 30 as a solution to upstart-compat-sysv 17
  Removing upstart-compat-sysv rather than change upstart
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 30 as a solution to startup-tasks 8
  Removing startup-tasks rather than change upstart
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 30 as a solution to system-services 8
  Removing system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 30 as a solution to upstart-logd 8
  Removing upstart-logd rather than change upstart
Investigating apparmor
Package apparmor has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 17 as a solution to apparmor 5
  Removing apparmor rather than change upstart-compat-sysv
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 4
  Removing ubuntu-minimal rather than change startup-tasks
Investigating apparmor-utils
Package apparmor-utils has broken dep on apparmor
  Considering apparmor 5 as a solution to apparmor-utils 2
  Removing apparmor-utils rather than change apparmor
Done
Starting
Starting 2
Investigating udev
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 10002 as a solution to udev 49
  Removing udev rather than change libdevmapper1.02
Investigating initramfs-tools
Package initramfs-tools has broken dep on udev
  Considering udev 49 as a solution to initramfs-tools 37
    Reinst Failed because of udev
  Removing initramfs-tools rather than change udev
Investigating volumeid
Package volumeid has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to volumeid 20
  Removing volumeid rather than change initramfs-tools
Investigating hal
Package hal has broken dep on udev
  Considering udev 49 as a solution to hal 19
  Removing hal rather than change udev
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 49 as a solution to libgphoto2-2 7
  Removing libgphoto2-2 rather than change udev
Investigating linux-image-2.6.22-14-generic
Package linux-image-2.6.22-14-generic has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to linux-image-2.6.22-14-generic 6
  Removing linux-image-2.6.22-14-generic rather than change initramfs-tools
Investigating gnome-power-manager
Package gnome-power-manager has broken dep on hal
  Considering hal 19 as a solution to gnome-power-manager 4
  Removing gnome-power-manager rather than change hal
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 7 as a solution to libsane 4
  Removing libsane rather than change libgphoto2-2
Investigating pcmciautils
Package pcmciautils has broken dep on udev
  Considering udev 49 as a solution to pcmciautils 4
  Removing pcmciautils rather than change udev
Investigating console-setup
Package console-setup has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to console-setup 4
  Removing console-setup rather than change initramfs-tools
Investigating gnome-session
Package gnome-session has broken dep on gnome-power-manager
  Considering gnome-power-manager 4 as a solution to gnome-session 4
  Removing gnome-session rather than change gnome-power-manager
Investigating hwdb-client-common
Package hwdb-client-common has broken dep on hal
  Considering hal 19 as a solution to hwdb-client-common 3
  Removing hwdb-client-common rather than change hal
Investigating usplash
Package usplash has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to usplash 3
  Removing usplash rather than change initramfs-tools
Investigating hpijs
Package hpijs has broken dep on libsane
  Considering libsane 4 as a solution to hpijs 2
  Removing hpijs rather than change libsane
Investigating linux-restricted-modules-2.6.22-14-generic
Package linux-restricted-modules-2.6.22-14-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-restricted-modules-2.6.22-14-generic 2
  Removing linux-restricted-modules-2.6.22-14-generic rather than change linux-image-2.6.22-14-generic
Investigating gnome-mount
Package gnome-mount has broken dep on hal
  Considering hal 19 as a solution to gnome-mount 2
  Removing gnome-mount rather than change hal
Investigating linux-ubuntu-modules-2.6.22-14-generic
Package linux-ubuntu-modules-2.6.22-14-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-ubuntu-modules-2.6.22-14-generic 2
  Removing linux-ubuntu-modules-2.6.22-14-generic rather than change linux-image-2.6.22-14-generic
Investigating libmtp6
Package libmtp6 has broken dep on udev
  Considering udev 49 as a solution to libmtp6 1
  Removing libmtp6 rather than change udev
Investigating gthumb
Package gthumb has broken dep on libgphoto2-2
  Considering libgphoto2-2 7 as a solution to gthumb 1
  Removing gthumb rather than change libgphoto2-2
Investigating network-manager
Package network-manager has broken dep on hal
  Considering hal 19 as a solution to network-manager 1
  Removing network-manager rather than change hal
Investigating linux-image-generic
Package linux-image-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-image-generic 1
  Removing linux-image-generic rather than change linux-image-2.6.22-14-generic
Investigating brltty
Package brltty has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to brltty 1
  Removing brltty rather than change initramfs-tools
Investigating update-notifier
Package update-notifier has broken dep on hal
  Considering hal 19 as a solution to update-notifier 1
  Removing update-notifier rather than change hal
Investigating usplash-theme-ubuntu
Package usplash-theme-ubuntu has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to usplash-theme-ubuntu 1
  Removing usplash-theme-ubuntu rather than change initramfs-tools
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 2 as a solution to foomatic-db-hpijs 1
  Removing foomatic-db-hpijs rather than change hpijs
Investigating gnome-volume-manager
Package gnome-volume-manager has broken dep on hal
  Considering hal 19 as a solution to gnome-volume-manager 1
  Removing gnome-volume-manager rather than change hal
Investigating hal-device-manager
Package hal-device-manager has broken dep on hal
  Considering hal 19 as a solution to hal-device-manager 1
  Removing hal-device-manager rather than change hal
Investigating linux-restricted-modules-generic
Package linux-restricted-modules-generic has broken dep on linux-restricted-modules-2.6.22-14-generic
  Considering linux-restricted-modules-2.6.22-14-generic 2 as a solution to linux-restricted-modules-generic 1
  Removing linux-restricted-modules-generic rather than change linux-restricted-modules-2.6.22-14-generic
Investigating sound-juicer
Package sound-juicer has broken dep on hal
  Considering hal 19 as a solution to sound-juicer 1
  Removing sound-juicer rather than change hal
Investigating f-spot
Package f-spot has broken dep on libgphoto2-2
  Considering libgphoto2-2 7 as a solution to f-spot 0
  Removing f-spot rather than change libgphoto2-2
Investigating hal-cups-utils
Package hal-cups-utils has broken dep on hal
  Considering hal 19 as a solution to hal-cups-utils 0
  Removing hal-cups-utils rather than change hal
Investigating xsane
Package xsane has broken dep on libsane
  Considering libsane 4 as a solution to xsane 0
  Removing xsane rather than change libsane
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 1 as a solution to rhythmbox 0
  Removing rhythmbox rather than change libmtp6
Investigating nvidia-glx-new
Package nvidia-glx-new has broken dep on nvidia-kernel-100.14.19
  Considering linux-restricted-modules-2.6.22-14-xen 0 as a solution to nvidia-glx-new 0
  Removing nvidia-glx-new rather than change nvidia-kernel-100.14.19
Investigating hplip
Package hplip has broken dep on libsane
  Considering libsane 4 as a solution to hplip 0
  Removing hplip rather than change libsane
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on foomatic-db-hpijs
  Considering foomatic-db-hpijs 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change foomatic-db-hpijs
Investigating network-manager-gnome
Package network-manager-gnome has broken dep on network-manager
  Considering network-manager 1 as a solution to network-manager-gnome 0
  Removing network-manager-gnome rather than change network-manager
Investigating grub
Package grub has broken dep on volumeid
  Considering volumeid 20 as a solution to grub 0
  Removing grub rather than change volumeid
Investigating linux-generic
Package linux-generic has broken dep on linux-image-generic
  Considering linux-image-generic 1 as a solution to linux-generic 0
  Removing linux-generic rather than change linux-image-generic
Investigating brltty-x11
Package brltty-x11 has broken dep on brltty
  Considering brltty 1 as a solution to brltty-x11 -1
  Removing brltty-x11 rather than change brltty
Investigating hwdb-client-gnome
Package hwdb-client-gnome has broken dep on hwdb-client-common
  Considering hwdb-client-common 3 as a solution to hwdb-client-gnome 3
  Removing hwdb-client-gnome rather than change hwdb-client-common
Done
Starting
Starting 2
Investigating hpijs
Package hpijs has broken dep on libsane
  Considering libsane 1 as a solution to hpijs 10000
  Added libsane to the remove list
  Fixing hpijs via keep of libsane
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 0
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 0
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 1
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 5 as a solution to libsane 1
  Removing libsane rather than change libgphoto2-2
Investigating hpijs
Package hpijs has broken dep on libsane
  Considering libsane 5 as a solution to hpijs 10000
  Added libsane to the remove list
  Fixing hpijs via keep of libsane
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 5 as a solution to libsane 10000
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 10000
  Added udev to the remove list
  Fixing libgphoto2-2 via keep of udev
Investigating udev
Package udev has broken dep on volumeid
  Considering volumeid 0 as a solution to udev 10000
  Added volumeid to the remove list
Package udev has broken dep on initramfs-tools
  Considering initramfs-tools 0 as a solution to udev 10000
  Added initramfs-tools to the remove list
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 2 as a solution to udev 10000
  Will not break libdevmapper1.02 as stated in Breaks field in udev
  Fixing udev via keep of volumeid
  Fixing udev via keep of initramfs-tools
Investigating udev
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 2 as a solution to udev 10000
  Will not break libdevmapper1.02 as stated in Breaks field in udev
Done
ERROR:root:Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
Installing busybox as dep of initramfs-tools
Installing sysvinit-utils as dep of initscripts
Starting
Starting 2
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5102 as a solution to upstart 30
  Removing upstart rather than change sysvinit
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 30 as a solution to upstart-compat-sysv 17
  Removing upstart-compat-sysv rather than change upstart
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 30 as a solution to startup-tasks 8
  Removing startup-tasks rather than change upstart
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 30 as a solution to system-services 8
  Removing system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 30 as a solution to upstart-logd 8
  Removing upstart-logd rather than change upstart
Investigating apparmor
Package apparmor has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 17 as a solution to apparmor 5
  Removing apparmor rather than change upstart-compat-sysv
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 4
  Removing ubuntu-minimal rather than change startup-tasks
Investigating apparmor-utils
Package apparmor-utils has broken dep on apparmor
  Considering apparmor 5 as a solution to apparmor-utils 2
  Removing apparmor-utils rather than change apparmor
Done
Starting
Starting 2
Investigating udev
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 10002 as a solution to udev 51
  Removing udev rather than change libdevmapper1.02
Investigating initramfs-tools
Package initramfs-tools has broken dep on udev
  Considering udev 51 as a solution to initramfs-tools 37
    Reinst Failed because of udev
  Removing initramfs-tools rather than change udev
Investigating volumeid
Package volumeid has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to volumeid 20
  Removing volumeid rather than change initramfs-tools
Investigating hal
Package hal has broken dep on udev
  Considering udev 51 as a solution to hal 19
  Removing hal rather than change udev
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 51 as a solution to libgphoto2-2 8
  Removing libgphoto2-2 rather than change udev
Investigating linux-image-2.6.22-14-generic
Package linux-image-2.6.22-14-generic has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to linux-image-2.6.22-14-generic 6
  Removing linux-image-2.6.22-14-generic rather than change initramfs-tools
Investigating gnome-power-manager
Package gnome-power-manager has broken dep on hal
  Considering hal 19 as a solution to gnome-power-manager 4
  Removing gnome-power-manager rather than change hal
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to libsane 4
  Removing libsane rather than change libgphoto2-2
Investigating pcmciautils
Package pcmciautils has broken dep on udev
  Considering udev 51 as a solution to pcmciautils 4
  Removing pcmciautils rather than change udev
Investigating console-setup
Package console-setup has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to console-setup 4
  Removing console-setup rather than change initramfs-tools
Investigating gnome-session
Package gnome-session has broken dep on gnome-power-manager
  Considering gnome-power-manager 4 as a solution to gnome-session 4
  Removing gnome-session rather than change gnome-power-manager
Investigating hwdb-client-common
Package hwdb-client-common has broken dep on hal
  Considering hal 19 as a solution to hwdb-client-common 3
  Removing hwdb-client-common rather than change hal
Investigating usplash
Package usplash has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to usplash 3
  Removing usplash rather than change initramfs-tools
Investigating hpijs
Package hpijs has broken dep on libsane
  Considering libsane 4 as a solution to hpijs 2
  Removing hpijs rather than change libsane
Investigating linux-restricted-modules-2.6.22-14-generic
Package linux-restricted-modules-2.6.22-14-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-restricted-modules-2.6.22-14-generic 2
  Removing linux-restricted-modules-2.6.22-14-generic rather than change linux-image-2.6.22-14-generic
Investigating gnome-mount
Package gnome-mount has broken dep on hal
  Considering hal 19 as a solution to gnome-mount 2
  Removing gnome-mount rather than change hal
Investigating linux-ubuntu-modules-2.6.22-14-generic
Package linux-ubuntu-modules-2.6.22-14-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-ubuntu-modules-2.6.22-14-generic 2
  Removing linux-ubuntu-modules-2.6.22-14-generic rather than change linux-image-2.6.22-14-generic
Investigating libmtp6
Package libmtp6 has broken dep on udev
  Considering udev 51 as a solution to libmtp6 1
  Removing libmtp6 rather than change udev
Investigating gthumb
Package gthumb has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to gthumb 1
  Removing gthumb rather than change libgphoto2-2
Investigating network-manager
Package network-manager has broken dep on hal
  Considering hal 19 as a solution to network-manager 1
  Removing network-manager rather than change hal
Investigating linux-image-generic
Package linux-image-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-image-generic 1
  Removing linux-image-generic rather than change linux-image-2.6.22-14-generic
Investigating brltty
Package brltty has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to brltty 1
  Removing brltty rather than change initramfs-tools
Investigating update-notifier
Package update-notifier has broken dep on hal
  Considering hal 19 as a solution to update-notifier 1
  Removing update-notifier rather than change hal
Investigating usplash-theme-ubuntu
Package usplash-theme-ubuntu has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to usplash-theme-ubuntu 1
  Removing usplash-theme-ubuntu rather than change initramfs-tools
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 2 as a solution to foomatic-db-hpijs 1
  Removing foomatic-db-hpijs rather than change hpijs
Investigating gnome-volume-manager
Package gnome-volume-manager has broken dep on hal
  Considering hal 19 as a solution to gnome-volume-manager 1
  Removing gnome-volume-manager rather than change hal
Investigating hal-device-manager
Package hal-device-manager has broken dep on hal
  Considering hal 19 as a solution to hal-device-manager 1
  Removing hal-device-manager rather than change hal
Investigating linux-restricted-modules-generic
Package linux-restricted-modules-generic has broken dep on linux-restricted-modules-2.6.22-14-generic
  Considering linux-restricted-modules-2.6.22-14-generic 2 as a solution to linux-restricted-modules-generic 1
  Removing linux-restricted-modules-generic rather than change linux-restricted-modules-2.6.22-14-generic
Investigating sound-juicer
Package sound-juicer has broken dep on hal
  Considering hal 19 as a solution to sound-juicer 1
  Removing sound-juicer rather than change hal
Investigating f-spot
Package f-spot has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to f-spot 0
  Removing f-spot rather than change libgphoto2-2
Investigating hal-cups-utils
Package hal-cups-utils has broken dep on hal
  Considering hal 19 as a solution to hal-cups-utils 0
  Removing hal-cups-utils rather than change hal
Investigating xsane
Package xsane has broken dep on libsane
  Considering libsane 4 as a solution to xsane 0
  Removing xsane rather than change libsane
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 1 as a solution to rhythmbox 0
  Removing rhythmbox rather than change libmtp6
Investigating nvidia-glx-new
Package nvidia-glx-new has broken dep on nvidia-kernel-100.14.19
  Considering linux-restricted-modules-2.6.22-14-xen 0 as a solution to nvidia-glx-new 0
  Removing nvidia-glx-new rather than change nvidia-kernel-100.14.19
Investigating hplip
Package hplip has broken dep on libsane
  Considering libsane 4 as a solution to hplip 0
  Removing hplip rather than change libsane
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on foomatic-db-hpijs
  Considering foomatic-db-hpijs 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change foomatic-db-hpijs
Investigating network-manager-gnome
Package network-manager-gnome has broken dep on network-manager
  Considering network-manager 1 as a solution to network-manager-gnome 0
  Removing network-manager-gnome rather than change network-manager
Investigating wine
Package wine has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to wine 0
  Removing wine rather than change libgphoto2-2
Investigating grub
Package grub has broken dep on volumeid
  Considering volumeid 20 as a solution to grub 0
  Removing grub rather than change volumeid
Investigating linux-generic
Package linux-generic has broken dep on linux-image-generic
  Considering linux-image-generic 1 as a solution to linux-generic 0
  Removing linux-generic rather than change linux-image-generic
Investigating brltty-x11
Package brltty-x11 has broken dep on brltty
  Considering brltty 1 as a solution to brltty-x11 -1
  Removing brltty-x11 rather than change brltty
Investigating hwdb-client-gnome
Package hwdb-client-gnome has broken dep on hwdb-client-common
  Considering hwdb-client-common 3 as a solution to hwdb-client-gnome 3
  Removing hwdb-client-gnome rather than change hwdb-client-common
Done
Starting
Starting 2
Investigating hpijs
Package hpijs has broken dep on libsane
  Considering libsane 1 as a solution to hpijs 10000
  Added libsane to the remove list
  Fixing hpijs via keep of libsane
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 0
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 0
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 1
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 5 as a solution to libsane 1
  Removing libsane rather than change libgphoto2-2
Investigating hpijs
Package hpijs has broken dep on libsane
  Considering libsane 5 as a solution to hpijs 10000
  Added libsane to the remove list
  Fixing hpijs via keep of libsane
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 5 as a solution to libsane 10000
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 10000
  Added udev to the remove list
  Fixing libgphoto2-2 via keep of udev
Investigating udev
Package udev has broken dep on volumeid
  Considering volumeid 0 as a solution to udev 10000
  Added volumeid to the remove list
Package udev has broken dep on initramfs-tools
  Considering initramfs-tools 0 as a solution to udev 10000
  Added initramfs-tools to the remove list
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 2 as a solution to udev 10000
  Will not break libdevmapper1.02 as stated in Breaks field in udev
  Fixing udev via keep of volumeid
  Fixing udev via keep of initramfs-tools
Investigating udev
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 2 as a solution to udev 10000
  Will not break libdevmapper1.02 as stated in Breaks field in udev
Done
ERROR:root:Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
Installing busybox as dep of initramfs-tools
Installing sysvinit-utils as dep of initscripts
Installing libntfs-3g16 as dep of ntfs-3g
Starting
Starting 2
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5102 as a solution to upstart 30
  Removing upstart rather than change sysvinit
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 30 as a solution to upstart-compat-sysv 17
  Removing upstart-compat-sysv rather than change upstart
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 30 as a solution to startup-tasks 8
  Removing startup-tasks rather than change upstart
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 30 as a solution to system-services 8
  Removing system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 30 as a solution to upstart-logd 8
  Removing upstart-logd rather than change upstart
Investigating apparmor
Package apparmor has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 17 as a solution to apparmor 5
  Removing apparmor rather than change upstart-compat-sysv
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 4
  Removing ubuntu-minimal rather than change startup-tasks
Investigating apparmor-utils
Package apparmor-utils has broken dep on apparmor
  Considering apparmor 5 as a solution to apparmor-utils 2
  Removing apparmor-utils rather than change apparmor
Done
Starting
Starting 2
Investigating udev
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 10002 as a solution to udev 51
  Removing udev rather than change libdevmapper1.02
Investigating initramfs-tools
Package initramfs-tools has broken dep on udev
  Considering udev 51 as a solution to initramfs-tools 37
    Reinst Failed because of udev
  Removing initramfs-tools rather than change udev
Investigating volumeid
Package volumeid has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to volumeid 20
  Removing volumeid rather than change initramfs-tools
Investigating hal
Package hal has broken dep on udev
  Considering udev 51 as a solution to hal 19
  Removing hal rather than change udev
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 51 as a solution to libgphoto2-2 8
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to libsane 6
  Removing libsane rather than change libgphoto2-2
Investigating linux-image-2.6.22-14-generic
Package linux-image-2.6.22-14-generic has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to linux-image-2.6.22-14-generic 6
  Removing linux-image-2.6.22-14-generic rather than change initramfs-tools
Investigating gnome-power-manager
Package gnome-power-manager has broken dep on hal
  Considering hal 19 as a solution to gnome-power-manager 4
  Removing gnome-power-manager rather than change hal
Investigating hplip
Package hplip has broken dep on libsane
  Considering libsane 6 as a solution to hplip 4
  Removing hplip rather than change libsane
Investigating pcmciautils
Package pcmciautils has broken dep on udev
  Considering udev 51 as a solution to pcmciautils 4
  Removing pcmciautils rather than change udev
Investigating console-setup
Package console-setup has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to console-setup 4
  Removing console-setup rather than change initramfs-tools
Investigating gnome-session
Package gnome-session has broken dep on gnome-power-manager
  Considering gnome-power-manager 4 as a solution to gnome-session 4
  Removing gnome-session rather than change gnome-power-manager
Investigating hwdb-client-common
Package hwdb-client-common has broken dep on hal
  Considering hal 19 as a solution to hwdb-client-common 3
  Removing hwdb-client-common rather than change hal
Investigating usplash
Package usplash has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to usplash 3
  Removing usplash rather than change initramfs-tools
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 4 as a solution to hpijs 2
  Removing hpijs rather than change hplip
Investigating linux-restricted-modules-2.6.22-14-generic
Package linux-restricted-modules-2.6.22-14-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-restricted-modules-2.6.22-14-generic 2
  Removing linux-restricted-modules-2.6.22-14-generic rather than change linux-image-2.6.22-14-generic
Investigating gnome-mount
Package gnome-mount has broken dep on hal
  Considering hal 19 as a solution to gnome-mount 2
  Removing gnome-mount rather than change hal
Investigating linux-ubuntu-modules-2.6.22-14-generic
Package linux-ubuntu-modules-2.6.22-14-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-ubuntu-modules-2.6.22-14-generic 2
  Removing linux-ubuntu-modules-2.6.22-14-generic rather than change linux-image-2.6.22-14-generic
Investigating libmtp6
Package libmtp6 has broken dep on udev
  Considering udev 51 as a solution to libmtp6 1
  Removing libmtp6 rather than change udev
Investigating gthumb
Package gthumb has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to gthumb 1
  Removing gthumb rather than change libgphoto2-2
Investigating network-manager
Package network-manager has broken dep on hal
  Considering hal 19 as a solution to network-manager 1
  Removing network-manager rather than change hal
Investigating linux-image-generic
Package linux-image-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-image-generic 1
  Removing linux-image-generic rather than change linux-image-2.6.22-14-generic
Investigating brltty
Package brltty has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to brltty 1
  Removing brltty rather than change initramfs-tools
Investigating update-notifier
Package update-notifier has broken dep on hal
  Considering hal 19 as a solution to update-notifier 1
  Removing update-notifier rather than change hal
Investigating usplash-theme-ubuntu
Package usplash-theme-ubuntu has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to usplash-theme-ubuntu 1
  Removing usplash-theme-ubuntu rather than change initramfs-tools
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 2 as a solution to foomatic-db-hpijs 1
  Removing foomatic-db-hpijs rather than change hpijs
Investigating gnome-volume-manager
Package gnome-volume-manager has broken dep on hal
  Considering hal 19 as a solution to gnome-volume-manager 1
  Removing gnome-volume-manager rather than change hal
Investigating hal-device-manager
Package hal-device-manager has broken dep on hal
  Considering hal 19 as a solution to hal-device-manager 1
  Removing hal-device-manager rather than change hal
Investigating linux-restricted-modules-generic
Package linux-restricted-modules-generic has broken dep on linux-restricted-modules-2.6.22-14-generic
  Considering linux-restricted-modules-2.6.22-14-generic 2 as a solution to linux-restricted-modules-generic 1
  Removing linux-restricted-modules-generic rather than change linux-restricted-modules-2.6.22-14-generic
Investigating sound-juicer
Package sound-juicer has broken dep on hal
  Considering hal 19 as a solution to sound-juicer 1
  Removing sound-juicer rather than change hal
Investigating f-spot
Package f-spot has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to f-spot 0
  Removing f-spot rather than change libgphoto2-2
Investigating hal-cups-utils
Package hal-cups-utils has broken dep on hal
  Considering hal 19 as a solution to hal-cups-utils 0
  Removing hal-cups-utils rather than change hal
Investigating xsane
Package xsane has broken dep on libsane
  Considering libsane 6 as a solution to xsane 0
  Removing xsane rather than change libsane
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 1 as a solution to rhythmbox 0
  Removing rhythmbox rather than change libmtp6
Investigating nvidia-glx-new
Package nvidia-glx-new has broken dep on nvidia-kernel-100.14.19
  Considering linux-restricted-modules-2.6.22-14-xen 0 as a solution to nvidia-glx-new 0
  Removing nvidia-glx-new rather than change nvidia-kernel-100.14.19
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on foomatic-db-hpijs
  Considering foomatic-db-hpijs 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change foomatic-db-hpijs
Investigating network-manager-gnome
Package network-manager-gnome has broken dep on network-manager
  Considering network-manager 1 as a solution to network-manager-gnome 0
  Removing network-manager-gnome rather than change network-manager
Investigating wine
Package wine has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to wine 0
  Removing wine rather than change libgphoto2-2
Investigating grub
Package grub has broken dep on volumeid
  Considering volumeid 20 as a solution to grub 0
  Removing grub rather than change volumeid
Investigating linux-generic
Package linux-generic has broken dep on linux-image-generic
  Considering linux-image-generic 1 as a solution to linux-generic 0
  Removing linux-generic rather than change linux-image-generic
Investigating brltty-x11
Package brltty-x11 has broken dep on brltty
  Considering brltty 1 as a solution to brltty-x11 -1
  Removing brltty-x11 rather than change brltty
Investigating hwdb-client-gnome
Package hwdb-client-gnome has broken dep on hwdb-client-common
  Considering hwdb-client-common 3 as a solution to hwdb-client-gnome 3
  Removing hwdb-client-gnome rather than change hwdb-client-common
Done
Starting
Starting 2
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 10000
  Added hplip to the remove list
Package hpijs has broken dep on libsane
  Considering libsane 1 as a solution to hpijs 10000
  Added libsane to the remove list
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 10000
  Added hplip to the remove list
  Fixing hpijs via keep of hplip
  Fixing hpijs via keep of libsane
  Fixing hpijs via keep of hplip
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 0
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 0
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 1
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 5 as a solution to libsane 1
  Removing libsane rather than change libgphoto2-2
Investigating hpijs
Package hpijs has broken dep on libsane
  Considering libsane 5 as a solution to hpijs 10000
  Added libsane to the remove list
  Fixing hpijs via keep of libsane
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 5 as a solution to libsane 10000
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 10000
  Added udev to the remove list
  Fixing libgphoto2-2 via keep of udev
Investigating udev
Package udev has broken dep on volumeid
  Considering volumeid 0 as a solution to udev 10000
  Added volumeid to the remove list
Package udev has broken dep on initramfs-tools
  Considering initramfs-tools 0 as a solution to udev 10000
  Added initramfs-tools to the remove list
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 2 as a solution to udev 10000
  Will not break libdevmapper1.02 as stated in Breaks field in udev
  Fixing udev via keep of volumeid
  Fixing udev via keep of initramfs-tools
Investigating udev
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 2 as a solution to udev 10000
  Will not break libdevmapper1.02 as stated in Breaks field in udev
Done
ERROR:root:Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
ERROR:root:Cache can not be locked (E:Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable), E:Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?)
ERROR:root:Cache can not be locked (E:Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable), E:Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?)
Installing busybox as dep of initramfs-tools
Installing sysvinit-utils as dep of initscripts
Installing libntfs-3g16 as dep of ntfs-3g
Starting
Starting 2
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5102 as a solution to upstart 30
  Removing upstart rather than change sysvinit
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 30 as a solution to upstart-compat-sysv 17
  Removing upstart-compat-sysv rather than change upstart
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 30 as a solution to startup-tasks 8
  Removing startup-tasks rather than change upstart
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 30 as a solution to system-services 8
  Removing system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 30 as a solution to upstart-logd 8
  Removing upstart-logd rather than change upstart
Investigating apparmor
Package apparmor has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 17 as a solution to apparmor 5
  Removing apparmor rather than change upstart-compat-sysv
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 4
  Removing ubuntu-minimal rather than change startup-tasks
Investigating apparmor-utils
Package apparmor-utils has broken dep on apparmor
  Considering apparmor 5 as a solution to apparmor-utils 2
  Removing apparmor-utils rather than change apparmor
Done
Starting
Starting 2
Investigating udev
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 10002 as a solution to udev 51
  Removing udev rather than change libdevmapper1.02
Investigating initramfs-tools
Package initramfs-tools has broken dep on udev
  Considering udev 51 as a solution to initramfs-tools 37
    Reinst Failed because of udev
  Removing initramfs-tools rather than change udev
Investigating volumeid
Package volumeid has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to volumeid 20
  Removing volumeid rather than change initramfs-tools
Investigating hal
Package hal has broken dep on udev
  Considering udev 51 as a solution to hal 19
  Removing hal rather than change udev
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 51 as a solution to libgphoto2-2 8
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to libsane 6
  Removing libsane rather than change libgphoto2-2
Investigating linux-image-2.6.22-14-generic
Package linux-image-2.6.22-14-generic has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to linux-image-2.6.22-14-generic 6
  Removing linux-image-2.6.22-14-generic rather than change initramfs-tools
Investigating gnome-power-manager
Package gnome-power-manager has broken dep on hal
  Considering hal 19 as a solution to gnome-power-manager 4
  Removing gnome-power-manager rather than change hal
Investigating hplip
Package hplip has broken dep on libsane
  Considering libsane 6 as a solution to hplip 4
  Removing hplip rather than change libsane
Investigating pcmciautils
Package pcmciautils has broken dep on udev
  Considering udev 51 as a solution to pcmciautils 4
  Removing pcmciautils rather than change udev
Investigating console-setup
Package console-setup has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to console-setup 4
  Removing console-setup rather than change initramfs-tools
Investigating gnome-session
Package gnome-session has broken dep on gnome-power-manager
  Considering gnome-power-manager 4 as a solution to gnome-session 4
  Removing gnome-session rather than change gnome-power-manager
Investigating hwdb-client-common
Package hwdb-client-common has broken dep on hal
  Considering hal 19 as a solution to hwdb-client-common 3
  Removing hwdb-client-common rather than change hal
Investigating usplash
Package usplash has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to usplash 3
  Removing usplash rather than change initramfs-tools
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 4 as a solution to hpijs 2
  Removing hpijs rather than change hplip
Investigating linux-restricted-modules-2.6.22-14-generic
Package linux-restricted-modules-2.6.22-14-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-restricted-modules-2.6.22-14-generic 2
  Removing linux-restricted-modules-2.6.22-14-generic rather than change linux-image-2.6.22-14-generic
Investigating gnome-mount
Package gnome-mount has broken dep on hal
  Considering hal 19 as a solution to gnome-mount 2
  Removing gnome-mount rather than change hal
Investigating linux-ubuntu-modules-2.6.22-14-generic
Package linux-ubuntu-modules-2.6.22-14-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-ubuntu-modules-2.6.22-14-generic 2
  Removing linux-ubuntu-modules-2.6.22-14-generic rather than change linux-image-2.6.22-14-generic
Investigating libmtp6
Package libmtp6 has broken dep on udev
  Considering udev 51 as a solution to libmtp6 1
  Removing libmtp6 rather than change udev
Investigating gthumb
Package gthumb has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to gthumb 1
  Removing gthumb rather than change libgphoto2-2
Investigating network-manager
Package network-manager has broken dep on hal
  Considering hal 19 as a solution to network-manager 1
  Removing network-manager rather than change hal
Investigating linux-image-generic
Package linux-image-generic has broken dep on linux-image-2.6.22-14-generic
  Considering linux-image-2.6.22-14-generic 6 as a solution to linux-image-generic 1
  Removing linux-image-generic rather than change linux-image-2.6.22-14-generic
Investigating brltty
Package brltty has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to brltty 1
  Removing brltty rather than change initramfs-tools
Investigating update-notifier
Package update-notifier has broken dep on hal
  Considering hal 19 as a solution to update-notifier 1
  Removing update-notifier rather than change hal
Investigating usplash-theme-ubuntu
Package usplash-theme-ubuntu has broken dep on initramfs-tools
  Considering initramfs-tools 37 as a solution to usplash-theme-ubuntu 1
  Removing usplash-theme-ubuntu rather than change initramfs-tools
Investigating foomatic-db-hpijs
Package foomatic-db-hpijs has broken dep on hpijs
  Considering hpijs 2 as a solution to foomatic-db-hpijs 1
  Removing foomatic-db-hpijs rather than change hpijs
Investigating gnome-volume-manager
Package gnome-volume-manager has broken dep on hal
  Considering hal 19 as a solution to gnome-volume-manager 1
  Removing gnome-volume-manager rather than change hal
Investigating hal-device-manager
Package hal-device-manager has broken dep on hal
  Considering hal 19 as a solution to hal-device-manager 1
  Removing hal-device-manager rather than change hal
Investigating linux-restricted-modules-generic
Package linux-restricted-modules-generic has broken dep on linux-restricted-modules-2.6.22-14-generic
  Considering linux-restricted-modules-2.6.22-14-generic 2 as a solution to linux-restricted-modules-generic 1
  Removing linux-restricted-modules-generic rather than change linux-restricted-modules-2.6.22-14-generic
Investigating sound-juicer
Package sound-juicer has broken dep on hal
  Considering hal 19 as a solution to sound-juicer 1
  Removing sound-juicer rather than change hal
Investigating f-spot
Package f-spot has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to f-spot 0
  Removing f-spot rather than change libgphoto2-2
Investigating hal-cups-utils
Package hal-cups-utils has broken dep on hal
  Considering hal 19 as a solution to hal-cups-utils 0
  Removing hal-cups-utils rather than change hal
Investigating xsane
Package xsane has broken dep on libsane
  Considering libsane 6 as a solution to xsane 0
  Removing xsane rather than change libsane
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 1 as a solution to rhythmbox 0
  Removing rhythmbox rather than change libmtp6
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on foomatic-db-hpijs
  Considering foomatic-db-hpijs 1 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change foomatic-db-hpijs
Investigating network-manager-gnome
Package network-manager-gnome has broken dep on network-manager
  Considering network-manager 1 as a solution to network-manager-gnome 0
  Removing network-manager-gnome rather than change network-manager
Investigating wine
Package wine has broken dep on libgphoto2-2
  Considering libgphoto2-2 8 as a solution to wine 0
  Removing wine rather than change libgphoto2-2
Investigating grub
Package grub has broken dep on volumeid
  Considering volumeid 20 as a solution to grub 0
  Removing grub rather than change volumeid
Investigating linux-generic
Package linux-generic has broken dep on linux-image-generic
  Considering linux-image-generic 1 as a solution to linux-generic 0
  Removing linux-generic rather than change linux-image-generic
Investigating brltty-x11
Package brltty-x11 has broken dep on brltty
  Considering brltty 1 as a solution to brltty-x11 -1
  Removing brltty-x11 rather than change brltty
Investigating hwdb-client-gnome
Package hwdb-client-gnome has broken dep on hwdb-client-common
  Considering hwdb-client-common 3 as a solution to hwdb-client-gnome 3
  Removing hwdb-client-gnome rather than change hwdb-client-common
Done
Starting
Starting 2
Investigating hpijs
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 10000
  Added hplip to the remove list
Package hpijs has broken dep on libsane
  Considering libsane 1 as a solution to hpijs 10000
  Added libsane to the remove list
Package hpijs has broken dep on hplip
  Considering hplip 2 as a solution to hpijs 10000
  Added hplip to the remove list
  Fixing hpijs via keep of hplip
  Fixing hpijs via keep of libsane
  Fixing hpijs via keep of hplip
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 0
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 0
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 0 as a solution to libsane 1
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 1
  Removing libgphoto2-2 rather than change udev
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 5 as a solution to libsane 1
  Removing libsane rather than change libgphoto2-2
Investigating hpijs
Package hpijs has broken dep on libsane
  Considering libsane 5 as a solution to hpijs 10000
  Added libsane to the remove list
  Fixing hpijs via keep of libsane
Investigating libsane
Package libsane has broken dep on libgphoto2-2
  Considering libgphoto2-2 5 as a solution to libsane 10000
  Added libgphoto2-2 to the remove list
  Fixing libsane via keep of libgphoto2-2
Investigating libgphoto2-2
Package libgphoto2-2 has broken dep on udev
  Considering udev 5 as a solution to libgphoto2-2 10000
  Added udev to the remove list
  Fixing libgphoto2-2 via keep of udev
Investigating udev
Package udev has broken dep on volumeid
  Considering volumeid 0 as a solution to udev 10000
  Added volumeid to the remove list
Package udev has broken dep on initramfs-tools
  Considering initramfs-tools 0 as a solution to udev 10000
  Added initramfs-tools to the remove list
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 2 as a solution to udev 10000
  Will not break libdevmapper1.02 as stated in Breaks field in udev
  Fixing udev via keep of volumeid
  Fixing udev via keep of initramfs-tools
Investigating udev
Package udev has broken dep on libdevmapper1.02
  Considering libdevmapper1.02 2 as a solution to udev 10000
  Will not break libdevmapper1.02 as stated in Breaks field in udev
Done
ERROR:root:Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
```

---

### Post by Xiong Chiamiov on 2008-04-25
Try
```

sudo apt-get update; sudo apt-get update

```

---

