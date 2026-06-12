---
title: "Bootloader not working/installing"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by JackMcKracken on 2008-06-03
Hi I just installed ubuntu on my secondary hard drive in order to run a dual boot with XP pro. However ubuntu 8.04 does not appear to have installed the bootloader or it is not working. Every time I restart the computer it goes directly to xp. I was sure to make sure the linux partition was set to primary so it is bootable. Anyone have any idea's or an easy work around for this?

---

### Post by me208 on 2008-06-03
Alright, go and download knoppix and burn it onto a CD/DVD and boot from it. Once fully loaded open a terminal emulator. Then determine your root partition, then mount it "dev" option enabled with write permissions. If the filesystem isn't mounted you'll need to mount it like this (be sure to change "hda1" and "hda" to match the location/device in your own system):

```
sudo mount -o dev,rw /mnt/hda1
```

if it's already mounted, remount it like this:

```
sudo mount -o remount,dev,rw /mnt/hda1
```

now restore grub like this:

```
sudo chroot /mnt/hda1 grub-install /dev/hda
```

if it doesn't work using chroot, try remounting as outlined above and do:

```
sudo grub-install -root-directory=/mnt/hda1 /dev/hda
```
(copied from a post by ozar on linuxfourms.net)

this should install grub onto your mbr.

If there are any issues I'm happy to help.

---

