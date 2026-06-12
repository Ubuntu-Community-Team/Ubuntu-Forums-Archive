---
title: "Installing Ubuntu from usb"
date: 2022-08-16
forum: New to Ubuntu
---

### Post by arminimra on 2022-08-16
Is it possible that during the installation of Ubuntu from the USB flash drive and during partitioning, the partitions inside the USB flash drive were mistakenly formatted and damaged?

---

### Post by SeijiSensei on 2022-08-16
If, when you get to the storage management phase you somehow point the root to the USB device, then yes, I think it's possible.

Usually the USB device will be /dev/sda and the main disk drive /dev/sdc. During installation you can specify the root of the new installation's directory structure. If you point the root directory, "/", to /dev/sda then it will overwrite the USB device.

I'd just rebuild the USB device and reinstall. If you're installing to an empty drive, or you want to overwrite entirely what's there, just choose the defaults. If you're trying to install Ubuntu alongside Windows in a "dual-boot" arrangement, you may need to use the "manual" option during the disk phase.

---

### Post by ajgreeny on 2022-08-16
> **arminimra said:**
> Is it possible that during the installation of Ubuntu from the USB flash drive and during partitioning, the partitions inside the USB flash drive were mistakenly formatted and damaged?
I don't think that would be possible as during installation the USB will be the OS actually running, therefore mounted, and when using Linux you can not format the partition(s) on that USB.

However, I am not quite sure of the reason for you question.
Having used the USB to install Ubuntu are you now finding that the USB disk is no longer usable and you can not write any files to it any more?

Depending on what application you used to create the install USB, and if that really is the problem you now have, it may simply mean that you need to either reformat the USB, or if that is not immediately possible, perhaps create a new partition table on it first using gparted, then create a new partition.

---

### Post by sudodus on 2022-08-16
How did you create the USB boot drive? Which iso file? Which tool or method?

How did you boot into the USB boot drive? If you booted with the boot option **toram**, then it is possible to write into your boot drive. But if you did not, or don't know how to do that, you need not worry about that.

If you have a persistent live drive, and unplugged it without unmounting before, you might have corrupted it. This should not happen with a live-only drive.

Please describe in a detailed way what you wanted to do and what happened and how your computer is behaving now. This is partly asking the same questions as in the previous reply (by ajgreeny).

---

### Post by guiverc on 2022-08-16
Ubuntu is available in many forms, for desktops, servers, with even *flavors* being available, and they exist for many different releases (and various architectures).

In all *five* different installers exist, and yes I've been able to write to a thumb-drive with some of them, but in most it's not possible.  In most cases though the ISO is written in a RO (*read-only*) format so no changes are possible anyway (*and attempts during installation just result in errors*) so details would be needed.

In general no, but yes it's possible if the user approaches it in varies ways, or uses a non-standard form of ISO write the default write will protect against.  You gave few details though, no Ubuntu product details, no release, no ISO choice, no clues on how written to media etc.

---

