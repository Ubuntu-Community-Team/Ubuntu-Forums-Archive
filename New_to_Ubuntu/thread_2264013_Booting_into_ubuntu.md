---
title: "Booting into ubuntu"
date: 2015-02-04
forum: New to Ubuntu
---

### Post by no_name3 on 2015-02-04
Hi,
I have an HP Envy m6 sleekbook with windows 8, not 8.1. I made a partition of about 100GB, finally managed to install Ubuntu from a USB, and set ~17GB for swap space (8GB ram), and ~4GB for /home. The swap and /home were set as "Logical". The main partition was set as / and "Primary". I tried restarting and pressed enter on "OS Boot Manager" in BIOS or UEFI, but I didn't get an option to boot Ubuntu. What do I do to boot up Ubuntu?
Thanks.

---

### Post by grahammechanical on 2015-02-04
Windows 8 or Windows 8.1, it makes no difference. If Windows is installed in EFI mode (and it usually is) then Ubuntu has to be installed in EFI mode.

Your talk about "primary" and "logical" partitions is confusing me. As I understand things Windows 8 is usually installed on a disk with GPT (GUID partition table) and not on the old MBR partition tables with primary, extended and logical partitions.

> [COLOR=#252525][FONT=sans-serif]As of 2010[/FONT][/COLOR][COLOR=#252525][FONT=sans-serif], most current [/FONT][/COLOR][operating systems]("http://en.wikipedia.org/wiki/Operating_systems")[COLOR=#252525][FONT=sans-serif] support GPT. Some, including [/FONT][/COLOR][OS X]("http://en.wikipedia.org/wiki/OS_X")[COLOR=#252525][FONT=sans-serif] and [/FONT][/COLOR][Microsoft Windows]("http://en.wikipedia.org/wiki/Microsoft_Windows")[COLOR=#252525][FONT=sans-serif] on x86, only support booting from GPT partitions on systems with EFI firmware, but [/FONT][/COLOR][FreeBSD]("http://en.wikipedia.org/wiki/FreeBSD")[COLOR=#252525][FONT=sans-serif] and most [/FONT][/COLOR][Linux distributions]("http://en.wikipedia.org/wiki/Linux_distribution")[COLOR=#252525][FONT=sans-serif] can boot from GPT partitions on systems with either legacy BIOS firmware interface or EFI.[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

