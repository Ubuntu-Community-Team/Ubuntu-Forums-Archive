---
title: "HOWTO: CD eject script (solves gamin / gam_server problem)"
date: 2005-09-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Copter on 2005-09-24
hi!

** Features : **nice mac-like CD eject script binded to user defined key combination

**Problem : **fixes umount / eject CD / DVD problem caused by gamin on some mashines at Hoary 5.04

**Solution : **

first we need cd mount script
```

nano ~/cd_mount.sh
```in the editor put this
```

#! /bin/sh
mount /cdrom
```F3 (save), F2 (exit). nothing new here. now for the CD eject script
```

nano ~/cd_umount.sh
```in the editor put this
```

#! /bin/sh
killall cd_mount.sh
killall gam_server
umount -l /cdrom
sleep 2
eject /dev/hda
```now for the keyboard shortcuts (for KDE :D)
KMenu -> (right click) Edit Menu -> Utilities (or anywhere else)

-> New Item
name : CD mount
command : '/home/copter/cd_mount.sh'
dont enable launch feedback
current shortcut key : Win+M (or anything else)

-> New Item
name : CD umount and eject
command : '/home/copter/cd_umount.sh'
dont enable launch feedback
current shortcut key : Win+U (or anything else)

done :)

for some reason eject script doesnt work in all cases. but most of the time it works just fine. ofc paths of the files are designed for 'copter' user when mounting default cdrom (/dev/hda) in default (/cdrom) directory.

copter :]

---

