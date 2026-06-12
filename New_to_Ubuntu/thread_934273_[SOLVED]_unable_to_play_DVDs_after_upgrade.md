---
title: "[SOLVED] unable to play DVDs after upgrade"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by r3bol on 2008-09-30
Hey, I've just upgraded to 8.04 and can't play DVDs in VLC. 
I get this error...
Unable to open 'dvd:///dev/hdc'

Any idea what it means and how to fix it?

Thanks :)

---

### Post by mc4man on 2008-09-30
Leave the dvd in the drive and run this to see what your drive's node,/dev links and mount point are
```
sudo lshw -C disk
```

This also may be useful (run from a maximized window for readability
```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by r3bol on 2008-09-30
**sudo lshw -C disk**
returns...
*-disk                  
       description: ATA Disk
       product: SAMSUNG SP4002H
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: QU10
       serial: 0524J2FTA44555
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d991d991
  *-cdrom
       description: DVD writer
       product: GO-W0808A
       vendor: GIGABYTE
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/dvd2
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: USY1
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom2

and 


**cat /etc/udev/rules.d/70-persistent-cd.rules**
returns...
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# GIGABYTE_GO-W0808A (pci-0000:00:11.1-ide-1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-ide-1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-ide-1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-ide-1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-ide-1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# Mass_Storage (pci-0000:00:10.1-usb-0:2:1.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HUAWEI_Mass_Storage-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
# GO-W0808A (pci-0000:00:11.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="cdrw2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="dvd2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:11.1-scsi-1:0:0:0", SYMLINK+="dvdrw2", ENV{GENERATED}="1"

---

### Post by mc4man on 2008-09-30
go ```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```
and delete both entries. Leave like this
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
```

 Then reboot and it will be rewritten properly.

Also go into home folder and delete .vlc (if you have made any changes in vlc's settings they'll have to be redone (returning vlc to default state

---

### Post by r3bol on 2008-09-30
thanks, that worked great.

---

