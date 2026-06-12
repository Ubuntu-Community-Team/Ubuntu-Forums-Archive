---
title: "No Kernel, No backup kernel"
date: 2013-07-12
forum: New to Ubuntu
---

### Post by rcolitz on 2013-07-12
I am using Ubuntu 10.04 LTS and I was doing an update and the computer restarted and the messages say No kernel or backup kernel. I cannot get the OS to load at all. I had to boot up into parted magic in order to attempt to recover the files.

---

### Post by Cheesehead on 2013-07-12
Check your grub configuration.

---

### Post by ajgreeny on 2013-07-12
In view of the fact that Ubuntu 10.04 is now end-of-life, you may find it easier in the long run to simply reinstall a newer version.  However if you want to try to repair your current OS I think you may have to boot to a live system, mount your installed OS root partition, then use chroot to install a kernel, or at least fully configure your current one. I have never used it nor do I know a lot about using it, but with 10.04 not now supported it may not be possible in a simple manner.

I will leave you to search for more details on how exactly to do that, or if it is even possible or worth considering.

If it were me, I would just reinstall 12.04, (xubuntu, if unity is not your choice.)

---

### Post by coldcritter64 on 2013-07-13
> **ajgreeny said:**
> In view of the fact that Ubuntu 10.04 is now end-of-life, you may find it easier in the long run to simply reinstall a newer version.  However if you want to try to repair your current OS I think you may have to boot to a live system, mount your installed OS root partition, then use chroot to install a kernel, or at least fully configure your current one. I have never used it nor do I know a lot about using it, but with 10.04 not now supported it may not be possible in a simple manner.

I will leave you to search for more details on how exactly to do that, or if it is even possible or worth considering.

If it were me, I would just reinstall 12.04, (xubuntu, if unity is not your choice.)

OP this is it, in the code box below is the method for chrooting into the broken install, this is used from a live cd terminal, it is likely to work best if you use a Lucid cd; This was taken off these forums for use with Lucid at that time. 2 methods are shown here, I personally use the second. I'm still using the same information with newer installs. I'm on Ubuntu 12.04 here and have used this to do repairs these days.

I do agree with ajgreeny's comments regarding upgrading to a currently supported version though. If you haven't already updated your sources list to old-releases.ubuntu.com, the old releases repository, you will have problems accessing the files you need to download to do your repairs. Regard coldcritter64

```
# =============
# Setup CHROOT
# =============
## copy and paste 7 commands below:
## Change /dev/sdxY to actual partition value eg. /dev/sda5 before using the relevant command with it in.

sudo mount /dev/sdxY /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt/ /bin/bash

# =============
# Remove CHROOT
# =============
## Ctrl+d to exit chroot, then, (Don't forget this step -- important or resolv.conf gives an error)

sudo umount /mnt/etc/resolv.conf
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

# Credit to UF user VMC. From information posted at http://ubuntuforums.org/showpost.php?p=8883297&postcount=3

# +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

# OR

# =============
# Setup CHROOT (in 2 steps with 1 line of command)
# =============
## Change /dev/sdxY to actual partition value eg. /dev/sda5 before using the relevant command with it in.

sudo mount /dev/sdxY /mnt/ && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt/ /bin/bash

# =============
# Remove CHROOT (in 2 steps with 1 line of command)
# =============
## Ctrl+d to exit chroot, then, (Don't forget this step -- important or resolv.conf gives an error)

sudo umount /mnt/etc/resolv.conf && sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt


# Credit to UF user VMC. From information posted at http://ubuntuforums.org/showpost.php?p=8883297&postcount=3

# +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
```

---

### Post by Impavidus on 2013-07-13
10.04 server edition is still supported, so the kernel packages should still be there on the normal server. If this is not a server edition, I recommend you install 12.04.

---

