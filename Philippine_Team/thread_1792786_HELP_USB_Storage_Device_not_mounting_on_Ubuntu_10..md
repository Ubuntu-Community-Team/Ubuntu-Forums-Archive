---
title: "HELP: USB Storage Device not mounting on Ubuntu 10.10"
date: 2011-06-28
forum: Philippine Team
---

### Post by killer_d76 on 2011-06-28
Magandang araw mga kaibigan kailangan ko ng tulong!.. kasi kaka-install ko lang ng Ubuntu 10.10 sa Acer Aspire One D255E Series ko.. as usual the installation went smoothly and I successfully installed all the necessary updates, pero isa lang ang problema ko nang mag-plug ako ng usb storage device ayaw mag-mount automatically pero recognized naman sya thru lsusb

[PHP]arvin@arvin-AOD255E:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 18a5:0302 Verbatim, Ltd 
Bus 001 Device 002: ID 064e:d214 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
arvin@arvin-AOD255E:~$ 
[/PHP]

[PHP]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084d75

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30020   241127424   83  Linux
/dev/sda2           30020       30402     3068929    5  Extended
/dev/sda5           30020       30402     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 4008 MB, 4008706048 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070234

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3913161    c  W95 FAT32 (LBA)
arvin@arvin-AOD255E:~$[/PHP]

pero kapag sinubukan kong i-mount eto yung result..

[PHP]arvin@arvin-AOD255E:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/arvin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=arvin)
arvin@arvin-AOD255E:~$ [/PHP]

I will appreciate all your help! thank you! ;)

---

### Post by killer_d76 on 2011-06-30
SOLVED! - all i did was re-install and for some reason it was working ;)

---

