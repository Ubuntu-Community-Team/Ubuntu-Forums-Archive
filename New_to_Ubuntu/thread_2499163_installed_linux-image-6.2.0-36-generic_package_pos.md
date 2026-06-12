---
title: "installed linux-image-6.2.0-36-generic package post-removal script subprocess returne"
date: 2024-07-16
forum: New to Ubuntu
---

### Post by finallyjj on 2024-07-16
So I ugraded from 20.04 o 22.04 then 23.10, and somewhere in the process something got corrupted (?). Anyway now, whenever I install/remove/upgrade anything using apt, it gets stuck on this error. Here's an example:

```

sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-6.2.0-36-generic
The following packages have been kept back:
  grub-common grub-efi-amd64-bin grub-efi-amd64-signed grub-pc grub-pc-bin grub2-common
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
8 not fully installed or removed.
After this operation, 13.9 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 437568 files and directories currently installed.)
Removing linux-image-6.2.0-36-generic (6.2.0-36.37) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.2.0-36-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
/etc/grub.d/09_lowlatency: 1: version_find_latest: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-6.2.0-36-generic (--remove):
 installed linux-image-6.2.0-36-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-6.2.0-36-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Here's some more information I've seen asked for in similar threads:

```

ls -lah /boot/*
-rw-r--r-- 1 root root 256K Jun 15  2023 /boot/config-5.15.0-76-generic
-rw-r--r-- 1 root root 270K Oct  2  2023 /boot/config-6.2.0-36-generic
-rw-r--r-- 1 root root 270K Nov 14  2023 /boot/config-6.2.0-39-generic
-rw-r--r-- 1 root root 273K Nov 14  2023 /boot/config-6.5.0-14-generic
-rw-r--r-- 1 root root 275K Jan 11  2024 /boot/config-6.5.0-17-generic
-rw-r--r-- 1 root root 275K Jun  7 14:59 /boot/config-6.5.0-44-generic
lrwxrwxrwx 1 root root   27 Jul 14 14:44 /boot/initrd.img -> initrd.img-6.5.0-44-generic
-rw-r--r-- 1 root root  36M Dec  8  2023 /boot/initrd.img-5.15.0-76-generic
-rw-r--r-- 1 root root  66M Dec  8  2023 /boot/initrd.img-6.2.0-39-generic
-rw-r--r-- 1 root root  55M Jul 15 15:14 /boot/initrd.img-6.5.0-14-generic
-rw-r--r-- 1 root root  55M Jul 15 15:15 /boot/initrd.img-6.5.0-17-generic
-rw-r--r-- 1 root root  56M Jul 15 15:14 /boot/initrd.img-6.5.0-44-generic
lrwxrwxrwx 1 root root   27 Jul 14 08:00 /boot/initrd.img.old -> initrd.img-6.5.0-17-generic
-rw-r--r-- 1 root root 136K Aug 19  2023 /boot/memtest86+ia32.bin
-rw-r--r-- 1 root root 137K Aug 19  2023 /boot/memtest86+ia32.efi
-rw-r--r-- 1 root root 145K Aug 19  2023 /boot/memtest86+x64.bin
-rw-r--r-- 1 root root 146K Aug 19  2023 /boot/memtest86+x64.efi
-rw------- 1 root root 6.0M Jun 15  2023 /boot/System.map-5.15.0-76-generic
-rw------- 1 root root 7.8M Oct  2  2023 /boot/System.map-6.2.0-36-generic
-rw------- 1 root root 7.8M Nov 14  2023 /boot/System.map-6.2.0-39-generic
-rw------- 1 root root 8.2M Nov 14  2023 /boot/System.map-6.5.0-14-generic
-rw------- 1 root root 8.2M Jan 11  2024 /boot/System.map-6.5.0-17-generic
-rw------- 1 root root 8.2M Jun  7 14:59 /boot/System.map-6.5.0-44-generic
lrwxrwxrwx 1 root root   24 Jul 14 08:00 /boot/vmlinuz -> vmlinuz-6.5.0-44-generic
-rw------- 1 root root  12M Jun 15  2023 /boot/vmlinuz-5.15.0-76-generic
-rw------- 1 root root  14M Nov 14  2023 /boot/vmlinuz-6.2.0-39-generic
-rw------- 1 root root  14M Nov 14  2023 /boot/vmlinuz-6.5.0-14-generic
-rw------- 1 root root  14M Jan 11  2024 /boot/vmlinuz-6.5.0-17-generic
-rw------- 1 root root  14M Jun  7 15:39 /boot/vmlinuz-6.5.0-44-generic
lrwxrwxrwx 1 root root   24 Jul 14 08:00 /boot/vmlinuz.old -> vmlinuz-6.5.0-17-generic


ls: cannot open directory '/boot/efi': Permission denied
/boot/grub:
total 2.4M
drwxr-xr-x 6 root root 4.0K Jul 16 12:50 .
drwxr-xr-x 4 root root 4.0K Jul 15 15:15 ..
drwxr-xr-x 2 root root 4.0K Sep  2  2021 fonts
-rw-r--r-- 1 root root  712 Aug 19  2021 gfxblacklist.txt
-r--r--r-- 1 root root  12K Dec 19  2023 grub.cfg
-rw------- 1 root root 3.6K Jul 16 12:50 grub.cfg.new
-rw-r--r-- 1 root root 1.0K Jul 16 11:13 grubenv
drwxr-xr-x 2 root root 4.0K Oct 16  2023 locale
drwxr-xr-x 3 root root 4.0K Oct  5  2021 themes
-rw-r--r-- 1 root root 2.4M Jul 15 15:14 unicode.pf2
drwxr-xr-x 2 root root  20K Oct 16  2023 x86_64-efi

```

```

apt list --installed linux-image* linux-generic*
Listing... Done
linux-generic/mantic-updates,mantic-security,now 6.5.0.44.44 amd64 [installed]
linux-image-5.15.0-76-generic/now 5.15.0-76.83 amd64 [installed,local]
linux-image-6.2.0-36-generic/now 6.2.0-36.37 amd64 [installed,local]
linux-image-6.2.0-39-generic/now 6.2.0-39.40 amd64 [installed,local]
linux-image-6.5.0-14-generic/now 6.5.0-14.14 amd64 [installed,local]
linux-image-6.5.0-17-generic/now 6.5.0-17.17 amd64 [installed,local]
linux-image-6.5.0-44-generic/mantic-updates,mantic-security,now 6.5.0-44.44 amd64 [installed,automatic]
linux-image-generic/mantic-updates,mantic-security,now 6.5.0.44.44 amd64 [installed,automatic]

```

I've tried both removing and purging ```
inux-image-6.2.0-36-generic/now 6.2.0-36
``` but it gets stuck with the same error. Thanks in advance.

---

### Post by Holger_Gehrke on 2024-07-16
How did you manage to go from 22.04 to 23.10 ? I'm asking because AFAIK there's no official way to do that, you should have gone from 22.04 to 22.10 to 23.04 to 23.10 (and since 22.10 and 23.04 are not LTS versions and went out of support after 9 months, you can't really do that ...).

Holger

---

### Post by finallyjj on 2024-07-16
I'm... not quite sure. However I did the upgrade a good while ago, maybe even a year ago, then for external reasons I barely got to use my computer so I only now noticed this issue. I attribute it to the upgrade because I recall it giving some errors and talking about a partial upgrade, and to this day the software updater says "not all updates can be installed" and prompts me with a partial upgrade, which fails for the same reasons as everything else

---

### Post by guiverc on 2024-07-16
> **Holger_Gehrke said:**
> How did you manage to go from 22.04 to 23.10 ? I'm asking because AFAIK there's no official way to do that, you should have gone from 22.04 to 22.10 to 23.04 to 23.10 (and since 22.10 and 23.04 are not LTS versions and went out of support after 9 months, you can't really do that ...).

Holger

Ubuntu LTS releases will *release-upgrade* to the next non-LTS, or Ubuntu 22.04 LTS will upgrade to 22.10, but when 22.10 is EOL it'll *release-upgrade *from 22.04 to 23.04, then 23.10 ... (*not anymore though; [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) shows Supported:0*)

That change was made some time ago (*before then it worked as you're expecting, 22.10 or 24.04.1 only*) ... where I was alerted to this by [Brian Murray]("https://launchpad.net/~brian-murray")

---

