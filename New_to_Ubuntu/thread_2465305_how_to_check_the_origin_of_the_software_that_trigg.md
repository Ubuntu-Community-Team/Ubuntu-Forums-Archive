---
title: "how to check the origin of the software that triggered for an update"
date: 2021-07-29
forum: New to Ubuntu
---

### Post by naix83dn on 2021-07-29
Hi im running ubuntu 21.04, i have this 2 suspicious update today
[LIST=1]
[*]Debian base system master password and group files ```
* update-passwd.c: Skip debconf question when changing irc's home
    directory from /var/run/ircd to /run/ircd, since these are equivalent
    (LP: #1916651)
``` as far as i know, i dont have any irc client installed 
[*]Secure Boot chain-loading bootloader (Microsoft-signed binary) ```
Changes for shim-signed versions:
Installed version: 1.48+15.4-0ubuntu5
Available version: 1.50+15.4-0ubuntu7

Version 1.50: 

  * download-signed: Fetch signed artefacts from versioned URL instead
    of current/ symlink to work around caching (LP: #1936640)
``` 
[/LIST]

How do i check the origin of the running software that trigger this update ?

---

### Post by mikewhatever on 2021-07-29
The bug report is here: [https://bugs.launchpad.net/ubuntu/+source/base-passwd/+bug/1916651](https://bugs.launchpad.net/ubuntu/+source/base-passwd/+bug/1916651).

Apparently, "irc" is one of the many users on the system. To see them all, brace yourself, and run <cut -d: -f1 /etc/passwd>.
 
C'est la vie. If we had to install and configer every singe file, the experience would have been very tedious indeed.

---

### Post by grahammechanical on 2021-07-29
> Secure Boot chain-loading bootloader (Microsoft-signed binary)

In order to dual boot any Linux distribution with Microsoft Windows and have Secure Boot enabled the distribution must include boot code that Microsoft accepts as trusted. It just so happens that Microsoft will accept boot code that has been signed by Canonical the sponsor of Ubuntu. The distribution will also need some code called a "shim" that has been verified by Microsoft as trustworthy.

If these pieces of authenticated or signed code are not present or their certificates are not listed in the Microsoft secure boot database then the Linux operating system will be prevented by secure boot from loading.

> On Ubuntu, all pre-built binaries intended to be loaded as part of the  boot process, with the exception of the initrd image, are signed by  Canonical's UEFI certificate, which itself is implicitly trusted by  being embedded in the shim loader, itself signed by Microsoft.

[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)

> As the system boots, firmware loads the shim binary as specified in  firmware BootEntry variables. Ubuntu installs its own BootEntry at  installation time and may update it any time the GRUB bootloader is  updated. Since the shim binary is signed by Microsoft; it is validated  and accepted by the firmware when verifying against certificates already  present in firmware. Since the shim binary embeds a Canonical  certificate as well as its own trust database, further elements of the  boot environment can, in addition to being signed by one of the  acceptable certificates pre-loaded in firmware, be signed by Canonical's  UEFI key.

Regards

---

