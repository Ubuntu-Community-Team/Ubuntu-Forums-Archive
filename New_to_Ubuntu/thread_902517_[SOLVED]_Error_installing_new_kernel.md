---
title: "[SOLVED] Error installing new kernel"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by %hMa@?b&lt;C on 2008-08-27
when trying to install via update-manager I get the following error
```
(Reading database ... 180991 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-19-generic 2.6.24-19.36 (using .../linux-image-2.6.24-19-generic_2.6.24-19.41_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-19-generic ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```
and
```
E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_amd64.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2

```


solution: ran apt-get clean

---

