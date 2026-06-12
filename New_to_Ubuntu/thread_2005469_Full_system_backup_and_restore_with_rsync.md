---
title: "Full system backup and restore with rsync"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by tempore on 2012-06-17
I booted up a live CD and used Grsync to backup my entire installation. 

```

Use Grsync
    -Tick preserve permissions,group,owner
    Advanced option tab
        '-ax' 

Fix stab with correct UUID
    -sudo blkid

Mount disk
    -sudo mount /reformatted/disk /livecd/mnt

Bind /proc /sys /dev
    -sudo mount --bind /proc /mnt/proc
    -sudo mount --bind /sys /mnt/sys
    -sudo mount --bind /dev /mnt/dev

Chroot in
    -sudo chroot /mnt

Install and update grub
    -sudo grub-install /dev/yourhd
    -sudo update-grub

Exit chroot
    -exit

Unmount everything
    -sudo umount /mnt/proc
    -sudo umount /mnt/sys
    -sudo umount /mnt/dev
    -sudo umount /mnt
    -sudo umount /reformatted/disk

Reboot

```And it works! Now that I have that working, I was wondering if I could backup from a mounted, running system.

Edit: I would like to keep the whole system up to date as the LiveCD method keeps all settings/installed programs intact. What should I backup/avoid to not break anything from a mounted, running system.

---

### Post by tempore on 2012-06-20
Bump

---

