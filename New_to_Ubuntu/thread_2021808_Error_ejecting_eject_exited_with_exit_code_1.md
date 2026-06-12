---
title: "Error ejecting: eject exited with exit code 1:"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by IlikeMoose on 2012-07-09
i keep getting the following error code when trying to eject my cd-rom drive, the only way i can get it to eject is by powering off.

Error ejecting: eject exited with exit code 1: eject: unable to eject, last error: Inappropriate ioctl for device

mike@hackbox:~$ eject -rv
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/sr0'
eject: `/dev/sr0' is not mounted
eject: `/dev/sr0' is not a mount point
eject: `/dev/sr0' is not a multipartition device
eject: trying to eject `/dev/sr0' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: unable to eject, last error: Input/output error
mike@hackbox:~$ eject cdrom
eject: unable to eject, last error: Inappropriate ioctl for device

i know the drive works because i ripped 2 audio cd's last night, at first i thought the problem was rhythmbox but i uninstalled it and installed audacious and everything was working. this is the same cd-rom drive i used for the ubuntu install and i didn't have a single problem. please help me!!!!:(

---

