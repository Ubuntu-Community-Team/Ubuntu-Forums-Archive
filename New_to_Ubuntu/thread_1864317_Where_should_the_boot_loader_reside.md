---
title: "Where should the boot loader reside?"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by wapfu on 2011-10-18
two hard drives.
Sda has windows
sdb will have linux

When asked for the location of the boot laoder will this be on the hard drive or in the partion of windows?
I have 4 choices
SATA drive a
the partion for windows on sda
SATA drive b
the partion for linux on sdb

i ask this from the do something else option on the live CD.
If I reinstall Ubuntu to the second hard drive leaving fromat unticked and select /

I am left with the option of location of boot loader which I have originally just left at the SATA drive a option of the four.

I am writing this from memory from windows but if I have chosen the wrong boot loader position could this be one of my woes?

---

### Post by fantab on 2011-10-18
> **wapfu said:**
> two hard drives.
Sda has windows
sdb will have linux

When asked for the location of the boot laoder will this be on the hard drive or in the partion of windows?
I have 4 choices
SATA drive a
the partion for windows on sda
SATA drive b
the partion for linux on sdb

i ask this from the do something else option on the live CD.
If I reinstall Ubuntu to the second hard drive leaving fromat unticked and select /

I am left with the option of location of boot loader which I have originally just left at the SATA drive a option of the four.

I am writing this from memory from windows but if I have chosen the wrong boot loader position could this be one of my woes?

Since you have two HDD and /dev/sda has windows installed already and Since you plan to use /dev/sdb for LINUX, I would suggest you [B]install GRUB (Boot Loader) on /dev/sdb.

[/B]You can also install it to /dev/sda but then it will overwrite Windows's MBR. Its your choice[B].

[/B]If you choose /dev/sdb then **don't forget to change in BIOS the HDD order to boot /dev/sdb first**, otherwise your system will boot to first HDD ie. /dev/sda or Windows every time you boot.

---

### Post by wapfu on 2011-10-18
Cheers and thank you

---

