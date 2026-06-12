---
title: "Mixup with boot partition after reinstall"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by xmbalmr on 2012-02-15
Recently I'd been trying to determine why the kernel updates have been installing but not showing up on GRUB leaving me running several versions behind. I finally discovered last night I am booting from the sda2 partition I originally setup as a boot partition when doing the initial install along with setting up the root file system in a LUKS encrypted container. Some time later when the upgrade from 11.04 to 11.10 stalled leaving me with a not too well working system I decided to reinstall on the existing partitions instead of delete/format/install. Currently when I run update-grub it updates a grub.cfg under /boot in the root directory instead of the grub.cfg in sda2, also when I attempt install new kernel versions they are being put into the /boot directory instead of sda2. I did find the link below on creating a boot partition after install but wanted to run it by someone to make sure I get it right. Thanks for any suggestions.

[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

---

### Post by oldfred on 2012-02-16
It seems to be fine.

What does your current fstab show? If booting from sda2, you should have an extra line mounting that partition as /boot. Best to use UUID:

sudo blkid

If you add the line to fstab, always run this to make sure the editing is ok or you might not be able to reboot.

sudo mount -a
#no error messages mean it remounted everything ok.

Then with /boot mounted in sda2 the update of grub should write into the correct boot partition not /boot folder.

sudo update-grub

I might check that it updated the grub.cfg in the /boot partition before rebooting.

---

### Post by xmbalmr on 2012-02-16
Thanks for the info, below is the current info from fstab. It definitely is booting and running the 3.0.0-12 and grub.cfg from there. Just to confirm once I add that to fstab grub and any kernel updates will then understand that boot is now sda2?

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/encrypted-root /               ext4    errors=remount-ro 0       1
/dev/mapper/encrypted-swap none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

---

### Post by oldfred on 2012-02-16
Your device mapper is RAID or LVM which I know nothing about and the encryption adds to the complexity. Are you even able to boot from a /boot folder that is inside the encryption? 
I assume that is why you have the /boot outside of the mapping/encryption.

---

### Post by xmbalmr on 2012-02-16
It's LVM, and correct about the separate unencrypted partition required due to the encrypted volumes. I've been through 4 or 5 complete installs with that setup over the last few years but as mentioned reinstalled on the existing encrypted partitions for the first time when this started so most likely missed defining where the boot partition was during the install an it just kept booting off sda2 that I had setup in the last full install. Seems like there should be an easy way to point everything over to sda2, just wanted to find the correct way before trying anything.

---

### Post by xmbalmr on 2012-02-19
That was much easier to fix than I thought it would be:

1) move files in /boot to a temp directory
2) edit fstab and add line below
UUID=1bd084a7-62e9-4a83-a0c7-356d90b6c45f  /boot   ext4   defaults 0  0
3) reboot and verify /boot now points to sda2
4) install latest kernel version and verify it's on sda2 and grub updated sda2/grub/grub.cgf
5) reboot

---

