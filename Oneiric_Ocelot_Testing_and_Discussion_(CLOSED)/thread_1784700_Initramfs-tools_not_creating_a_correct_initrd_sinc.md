---
title: "Initramfs-tools not creating a correct initrd since two kernels back"
date: 2011-06-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by NachoMas on 2011-06-17
Hi all,

I have an up to date oneiric box but running on a kernel 2.6.37-12-generic-pae since I have been unable to create a valid initrd boot image for newer kernels. I am using an unencrypted /boot partition and a LUKS encrypted partition that is it then split in LVM volumes for /, /home and swap. After I create the initrd image with:

sudo update-initramfs -k 3.0-0-generic-pae -c (for the latest kernel)

when I reboot and choose the 3.0.0 kernel, everything looks fine until I open up the LUKS volume and then cryptroot reports that it cannot find the lvm volumes. the script that complains is /scripts/local-top/cryptroot. If I boot with the 2.6.37-12 initrd image then everything works fine. 

the HD looks like this:
/dev/sda1: unencrypted ext4 /boot
/dev/sda2: encrypted luks that contains:



LV Name                /dev/CaliopeVG/CaliopeRoot
  VG Name                CaliopeVG
  LV UUID                5jXXlV-uISc-gzer-oL5G-4qn1-yR3Y-07bNjh

LV Name                /dev/CaliopeVG/CaliopeSwap
  VG Name                CaliopeVG
  LV UUID                l5E11R-E4Yl-06y1-eZN4-SSy2-o0wD-gG0bUI

LV Name                /dev/CaliopeVG/CaliopeHome
  VG Name                CaliopeVG
  LV UUID                1l2utr-lAI5-VJdx-9PTF-SPMX-HAPF-XxxKQ5

interesting enough, when I make a 'sudo blkid' I get:

/dev/sda1: UUID="2087a2c2-60ad-417a-8cb9-78917385aa60" TYPE="ext4" 
/dev/sda2: UUID="52de79d0-1119-4aad-81a7-68415e70283d" TYPE="crypto_LUKS" 
/dev/mapper/pvcrypt: UUID="PU0IXc-mALj-s2UQ-O4h9-1X3t-Zrq6-MEDh0P" TYPE="LVM2_member" 
/dev/mapper/CaliopeVG-CaliopeRoot: UUID="7961dc60-0ca8-486b-baf1-5efb68463b6d" TYPE="ext4" 
/dev/mapper/CaliopeVG-CaliopeSwap: UUID="fb8aa423-a6da-4def-baf2-159423c4b9fe" TYPE="swap" 
/dev/mapper/CaliopeVG-CaliopeHome: UUID="e3734e06-0bd1-4751-9b9e-bbabca83ea7a" TYPE="ext4"

This is the content of my fstab:

/etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
#/dev/mapper/CaliopeVG-CaliopeRoot /               ext4    errors=remount-ro 0       1
UUID=7961dc60-0ca8-486b-baf1-5efb68463b6d / ext4 errors=remount-ro 0
# /boot was on /dev/sda1 during installation
UUID=2087a2c2-60ad-417a-8cb9-78917385aa60 /boot           ext4    defaults        0       2
#/dev/mapper/CaliopeVG-CaliopeHome /home           ext4    defaults,user_xattr        0       2
UUID=e3734e06-0bd1-4751-9b9e-bbabca83ea7a /home ext4 defaults,user_xattr 0 2
#/dev/mapper/CaliopeVG-CaliopeSwap none            swap    sw              0       0
UUID=fb8aa423-a6da-4def-baf2-159423c4b9fe none swap defaults 0 0
#

and /etc/crypttab contains:

pvcrypt UUID=52de79d0-1119-4aad-81a7-68415e70283d none luks,retry=1,lvm=CaliopeVG

the problem seems to be related to a race condition in lvm2 that I have read some bug reports about, but I have tried everything and I'm not able to fix it.

I have also compared the (uncompressed) content of initrd.img-2.6.37-12-generic-pae and initrd.img-3.0-0-generic-pae and I cannot see any difference in the cryptroot script, so I'm starting to get baffled by this problem.

Any hints on where to look or how to fix this?
Thanks for any help!
/Nacho

---

