---
title: "dvdrw wont work at all"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by gregwnc on 2011-12-04
wont mount
been searching, maybe someone can enlighten me
i put a disk in , it wind up then stops 
hp pavilion dv6000 laptop


sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVDRAM_GSA-T40L (pci-0000:00:06.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"

# Cruzer (pci-0000:00:02.1-usb-0:4:1.0-scsi-0:0:0:1)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="SanDisk_Cruzer_1740100CF1038551-0:1", SYMLINK+="cdrom1", ENV{GENERATED}="1"



greg@earthstation:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/greg/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=greg)




does any of this help to start with

---

### Post by navaleshubham10 on 2011-12-04
are u using ubuntu 11.10
just click on dash home and type disk utilities and then click on dvd drive and then dere will be one option to mount the drive

---

### Post by gregwnc on 2011-12-04
the only one available is hard drive . does that mean my dvd is fried?
by the way thanks for the reply or possibly motherboard or cable for sata could be fried?

---

### Post by gregwnc on 2011-12-05
well this morning i turn on computer i had a cd in in it from last night ultraboot cd and when ubunyu was up i noticed it had reconised it and was in disk utility . so i ejected it and tried another but no go and disk utility did not change it still had ultra boot cd info so i tried to unmount and mount acked like it did but ultraboot info was still there so i tried eject button got this reply 
error (hl-dt-st hl-dt-st dvdram gsa-t40l)
inappropriate  10ct1 for device
i am going to try and reboot again to see what happens ubuntu10.10 did not have cd/dvd issues

---

