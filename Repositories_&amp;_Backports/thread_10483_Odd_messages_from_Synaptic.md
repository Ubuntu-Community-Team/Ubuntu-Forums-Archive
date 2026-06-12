---
title: "Odd messages from Synaptic"
date: 2005-01-08
forum: Repositories &amp; Backports
---

### Post by TheCool on 2005-01-08
While trying to make upgrades to my system, Synaptic keeps saying that I am out of space.

Synaptic paste

Preconfiguring packages ...
(Reading database ... 62963 files and directories currently installed.)
Preparing to replace linux-image-2.6.8.1-3-386 2.6.8.1-16 (using .../linux-image-2.6.8.1-3-386_2.6.8.1-16.1_i386.deb) ...
The directory /lib/modules/2.6.8.1-3-386 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.8.1-3-386 ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.8.1-3-386_2.6.8.1-16.1_i386.deb (--unpack):
 failed in buffer_write(fd) (8, ret=-1): backend dpkg-deb during `./lib/modules/2.6.8.1-3-386/kernel/fs/xfs/xfs.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /vmlinuz-2.6.8.1-3-386
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.8.1-3-386_2.6.8.1-16.1_i386.deb

Failed to apply all changes! Scroll in this buffer to see what went wrong.

df -h paste

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             135M  108M   21M  84% /
tmpfs                 316M     0  316M   0% /dev/shm
/dev/hda1              58M  2.3M   53M   5% /boot
/dev/mapper/vg-home    42G  1.4G   39G   4% /home
/dev/mapper/vg-opt    5.0G   33M  4.7G   1% /opt
/dev/mapper/vg-tmp    1.9G  8.2M  1.8G   1% /tmp
/dev/mapper/vg-usr    9.9G  1.4G  8.0G  15% /usr
/dev/mapper/vg-var    9.9G  138M  9.3G   2% /var

Looking over everything for dpkg, dselect, and apt, it should be using the /var partition to do all the work. As you can see I have quite a bit of space available on the var partition.

Any suggestions would be helpful.

---

