---
title: "How would i duel boot windows onto ubuntu."
date: 2016-05-23
forum: New to Ubuntu
---

### Post by hayden14 on 2016-05-23
I have Ubuntu and i had windows 10 but it deleted all of it. i have a windows 8 disk but i don't know how to duel boot from Ubuntu because all the videos i find are duel booting from windows. I have a SSD i want both windows and Ubuntu on.

---

### Post by oldfred on 2016-05-23
Depends a lot on how you installed Ubuntu. UEFI or BIOS?
And Ubuntu can be installed to gpt partitioned drive to boot in BIOS mode.

But Windows only boots from gpt partitioned drives with UEFI.
And Windows only boots from MBR partitioned drives with BIOS.
And how you boot install media is then how it installs, UEFI or BIOS, so be sure to boot in mode that matches partitioning or Windows will erase drive.

Post this:
sudo parted -l

---

