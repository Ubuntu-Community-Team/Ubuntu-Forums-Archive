---
title: "Problem when updating linux-modules via terminal.."
date: 2022-09-01
forum: New to Ubuntu
---

### Post by yatski on 2022-09-01
So.. I decided to venture to Terminal since graphical Software Updater suggested so in the error message. 
---
"Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 ```
The following packages have unmet dependencies:

linux-image-generic: Depends: linux-image-5.15.0-47-generic but it is not installed
                     Depends: linux-modules-extra-5.15.0-47-generic but it is not installed"
---
```
However, I ran to problem.
--```

"Preparing to unpack .../linux-modules-extra-5.15.0-47-generic_5.15.0-47.51_amd64.deb ...
Unpacking linux-modules-extra-5.15.0-47-generic (5.15.0-47.51) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.15.0-47-generic_5.15.0-47.51_amd64.deb (--unpack):
 unable to create new file '/var/lib/dpkg/info/linux-modules-extra-5.15.0-47-generic.list-new': Operation not permitted
Segmentation fault"
```
--
Is there anything I can do? I'm working as sudo.

(For the record, only thing closest to third party repository is [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) )

Edit: I ran 'sudo dpkg --configure -a' and got the following:
---- 
```
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-modules-extra-5.15.0-47-generic; however:
  Package linux-modules-extra-5.15.0-47-generic is not installed.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 5.15.0.47.47); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-5.15.0-47-generic:
 linux-headers-5.15.0-47-generic depends on linux-headers-5.15.0-47; however:
  Package linux-headers-5.15.0-47 is not installed.

dpkg: error processing package linux-headers-5.15.0-47-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-5.15.0-47-generic; however:
  Package linux-headers-5.15.0-47-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-modules-5.15.0-47-generic (5.15.0-47.51) ...
Setting up linux-image-5.15.0-47-generic (5.15.0-47.51) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.15.0-46-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.15.0-46-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.15.0-47-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.15.0-47-generic
Processing triggers for linux-image-5.15.0-47-generic (5.15.0-47.51) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-47-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-47-generic
Found initrd image: /boot/initrd.img-5.15.0-47-generic
Found linux image: /boot/vmlinuz-5.15.0-46-generic
Found initrd image: /boot/initrd.img-5.15.0-46-generic
Found linux image: /boot/vmlinuz-5.4.0-124-generic
Found initrd image: /boot/initrd.img-5.4.0-124-generic
Found linux image: /boot/vmlinuz-4.18.0-18-generic
Found initrd image: /boot/initrd.img-4.18.0-18-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
Errors were encountered while processing:
 linux-image-generic
 linux-generic
 linux-headers-5.15.0-47-generic
 linux-headers-generic
--
```

Edit 2:
I was also unable to update "linux kernel headers for development" at first, but succeeded after three tries with Software Updater.
However, I'm still unsure if everything is fine.

---

### Post by ActionParsnip on 2022-09-01
What is the output of:
```

df -h
uname -a
df -i

```
Thanks

---

### Post by yatski on 2022-09-01
---
heta@heta-vaio:~$ df -h
uname -a
df -i
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           584M  2,2M  582M   1% /run
/dev/sda2       439G   83G  334G  20% /
tmpfs           2,9G  160M  2,7G   6% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
/dev/sda1       511M  5,3M  506M   2% /boot/efi
tmpfs           584M  4,7M  579M   1% /run/user/1000
Linux heta-vaio 5.15.0-47-generic #51-Ubuntu SMP Thu Aug 11 07:51:15 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
tmpfs            746532   1318   745214    1% /run
/dev/sda2      29278208 418693 28859515    2% /
tmpfs            746532    265   746267    1% /dev/shm
tmpfs            746532      4   746528    1% /run/lock
/dev/sda1             0      0        0     - /boot/efi
tmpfs            149306    166   149140    1% /run/user/1000
--

---

### Post by ActionParsnip on 2022-09-01
[https://askubuntu.com/questions/898606/operation-not-permitted-while-installing-linux-headers-4-8-0-45](https://askubuntu.com/questions/898606/operation-not-permitted-while-installing-linux-headers-4-8-0-45)

Possibly that. You have free space which is cool

---

### Post by ActionParsnip on 2022-09-01
[https://forums.linuxmint.com/viewtopic.php?t=303821](https://forums.linuxmint.com/viewtopic.php?t=303821)

Are you using Sophos? Seems to be a recurring theme here.....

---

### Post by yatski on 2022-09-01
> **ActionParsnip said:**
> [https://forums.linuxmint.com/viewtopic.php?t=303821](https://forums.linuxmint.com/viewtopic.php?t=303821)

Are you using Sophos? Seems to be a recurring theme here.....

Yes.

---

### Post by ActionParsnip on 2022-09-01
Then disable Sophos, run the update then re-enable. Is it then OK?

---

### Post by yatski on 2022-09-01
> **ActionParsnip said:**
> Then disable Sophos, run the update then re-enable. Is it then OK?

For some reason I can't disable nor enable Sophos, even I'm on root.

Also, the Software Updater nor terminal aren't offering kernel updates anymore.

---

### Post by ActionParsnip on 2022-09-01
Seems to be
```

sudo /opt/sophos-av/bin/savdctl disable

```
If that works then run updates as normal

---

### Post by yatski on 2022-09-01
> **ActionParsnip said:**
> Seems to be
```

sudo /opt/sophos-av/bin/savdctl disable

```
If that works then run updates as normal

(I thank you for your patience! :) )

I get "Failed to disable on-access scanning."-error.

---

### Post by ActionParsnip on 2022-09-01
I'd see how you disable it and do that. Might be a service in systemd now. Not sure

---

### Post by yatski on 2022-09-01
> **ActionParsnip said:**
> I'd see how you disable it and do that. Might be a service in systemd now. Not sure

I finally managed to disable on-access scanning.(For some reason, it required me to do "sudo /opt/sophos-av/bin/savdstatus" first.)

However, I can't seem to fetch those kernel updates(either via Software Updater nor terminal) and genuinely fear my computer will not boot tomorrow.

---

### Post by Bashing-om on 2022-09-09
yatski' Hello :D

> 
However, I can't seem to fetch those kernel updates(either via Software Updater nor terminal) and genuinely fear my computer will not boot tomorrow.


I poke my nose into this and see what we can do.
1st up is to look at what there is installed (and maybe missing).
Post back the results of terminal commands:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```
and we see where we go from here.

-ubuntu: together we can-

---

### Post by yatski on 2022-09-10
Okay, here is the massive dump... (I apologize Finnish dates. Hope this makes sense to you.)
```
heta@heta-vaio:~$ ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-
total 32
drwxr-xr-x  8 root root 4096 syys    1 09:40 .
drwxr-xr-x 16 root root 4096 elo    12 15:50 ..
drwxr-xr-x 24 root root 4096 elo    12 15:43 linux-headers-5.15.0-46
drwxr-xr-x  7 root root 4096 elo    12 15:44 linux-headers-5.15.0-46-generic
drwxr-xr-x 24 root root 4096 syys    1 10:10 linux-headers-5.15.0-47
drwxr-xr-x  7 root root 4096 syys    1 09:40 linux-headers-5.15.0-47-generic
drwxr-xr-x 24 root root 4096 elo    10 17:11 linux-headers-5.4.0-124
drwxr-xr-x  7 root root 4096 elo    10 17:13 linux-headers-5.4.0-124-generic
total 332
drwxr-xr-x  80 root root  4096 syys    1 09:39 .
drwxr-xr-x 126 root root 16384 syys    8 17:05 ..
drwxr-xr-x   2 root root  4096 huhti  25  2019 4.18.0-15-generic
drwxr-xr-x   2 root root  4096 touko  16  2019 4.18.0-17-generic
drwxr-xr-x   5 root root  4096 syys   29  2020 4.18.0-18-generic
drwxr-xr-x   2 root root  4096 kesä   19  2019 4.18.0-20-generic
drwxr-xr-x   2 root root  4096 kesä   25  2019 4.18.0-21-generic
drwxr-xr-x   2 root root  4096 kesä   29  2019 4.18.0-22-generic
drwxr-xr-x   2 root root  4096 elo     3  2019 4.18.0-24-generic
drwxr-xr-x   2 root root  4096 elo    14  2019 4.18.0-25-generic
drwxr-xr-x   2 root root  4096 syys    4  2019 5.0.0-23-generic
drwxr-xr-x   2 root root  4096 syys   19  2019 5.0.0-25-generic
drwxr-xr-x   2 root root  4096 loka    5  2019 5.0.0-27-generic
drwxr-xr-x   2 root root  4096 loka   23  2019 5.0.0-29-generic
drwxr-xr-x   2 root root  4096 marras 14  2019 5.0.0-31-generic
drwxr-xr-x   2 root root  4096 marras 15  2019 5.0.0-32-generic
drwxr-xr-x   2 root root  4096 joulu   4  2019 5.0.0-35-generic
drwxr-xr-x   2 root root  4096 tammi  19  2020 5.0.0-36-generic
drwxr-xr-x   2 root root  4096 tammi  30  2020 5.0.0-37-generic
drwxr-xr-x   5 root root  4096 elo    12 15:57 5.15.0-46-generic
drwxr-xr-x   5 root root  4096 syys    1 09:56 5.15.0-47-generic
drwxr-xr-x   2 root root  4096 helmi  19  2020 5.3.0-26-generic
drwxr-xr-x   2 root root  4096 maalis 18  2020 5.3.0-28-generic
drwxr-xr-x   2 root root  4096 huhti   1  2020 5.3.0-40-generic
drwxr-xr-x   2 root root  4096 huhti   8  2020 5.3.0-42-generic
drwxr-xr-x   2 root root  4096 huhti  30  2020 5.3.0-45-generic
drwxr-xr-x   2 root root  4096 touko  27  2020 5.3.0-46-generic
drwxr-xr-x   2 root root  4096 kesä   11  2020 5.3.0-51-generic
drwxr-xr-x   2 root root  4096 kesä   29  2020 5.3.0-53-generic
drwxr-xr-x   2 root root  4096 heinä   6  2020 5.3.0-59-generic
drwxr-xr-x   2 root root  4096 heinä  23  2020 5.3.0-61-generic
drwxr-xr-x   2 root root  4096 syys    4  2020 5.3.0-62-generic
drwxr-xr-x   2 root root  4096 maalis 22 11:20 5.4.0-100-generic
drwxr-xr-x   2 root root  4096 maalis 31 10:14 5.4.0-104-generic
drwxr-xr-x   2 root root  4096 huhti  20 10:36 5.4.0-105-generic
drwxr-xr-x   2 root root  4096 touko  11 12:19 5.4.0-107-generic
drwxr-xr-x   2 root root  4096 touko  24 11:16 5.4.0-109-generic
drwxr-xr-x   2 root root  4096 kesä    8 10:43 5.4.0-110-generic
drwxr-xr-x   2 root root  4096 kesä   16 12:58 5.4.0-113-generic
drwxr-xr-x   2 root root  4096 kesä   23 14:47 5.4.0-117-generic
drwxr-xr-x   2 root root  4096 heinä  12 10:16 5.4.0-120-generic
drwxr-xr-x   2 root root  4096 elo    10 17:15 5.4.0-121-generic
drwxr-xr-x   2 root root  4096 elo    12 16:20 5.4.0-122-generic
drwxr-xr-x   5 root root  4096 elo    10 17:13 5.4.0-124-generic
drwxr-xr-x   2 root root  4096 syys    9  2020 5.4.0-42-generic
drwxr-xr-x   2 root root  4096 syys   24  2020 5.4.0-45-generic
drwxr-xr-x   2 root root  4096 loka   14  2020 5.4.0-47-generic
drwxr-xr-x   2 root root  4096 loka   20  2020 5.4.0-48-generic
drwxr-xr-x   2 root root  4096 marras 11  2020 5.4.0-51-generic
drwxr-xr-x   2 root root  4096 marras 17  2020 5.4.0-52-generic
drwxr-xr-x   2 root root  4096 joulu   1  2020 5.4.0-53-generic
drwxr-xr-x   2 root root  4096 joulu  13  2020 5.4.0-54-generic
drwxr-xr-x   2 root root  4096 tammi   5  2021 5.4.0-56-generic
drwxr-xr-x   2 root root  4096 tammi   8  2021 5.4.0-58-generic
drwxr-xr-x   2 root root  4096 tammi  15  2021 5.4.0-59-generic
drwxr-xr-x   2 root root  4096 tammi  21  2021 5.4.0-60-generic
drwxr-xr-x   2 root root  4096 tammi  27  2021 5.4.0-62-generic
drwxr-xr-x   2 root root  4096 helmi  24  2021 5.4.0-64-generic
drwxr-xr-x   2 root root  4096 maalis 16  2021 5.4.0-65-generic
drwxr-xr-x   2 root root  4096 maalis 24  2021 5.4.0-66-generic
drwxr-xr-x   2 root root  4096 huhti  13  2021 5.4.0-67-generic
drwxr-xr-x   2 root root  4096 huhti  16  2021 5.4.0-70-generic
drwxr-xr-x   2 root root  4096 touko  11  2021 5.4.0-71-generic
drwxr-xr-x   2 root root  4096 kesä    3  2021 5.4.0-72-generic
drwxr-xr-x   2 root root  4096 kesä   23  2021 5.4.0-73-generic
drwxr-xr-x   2 root root  4096 heinä  21  2021 5.4.0-74-generic
drwxr-xr-x   2 root root  4096 elo    14  2021 5.4.0-77-generic
drwxr-xr-x   2 root root  4096 syys    8  2021 5.4.0-80-generic
drwxr-xr-x   2 root root  4096 syys   22  2021 5.4.0-81-generic
drwxr-xr-x   2 root root  4096 syys   28  2021 5.4.0-84-generic
drwxr-xr-x   2 root root  4096 loka   19  2021 5.4.0-86-generic
drwxr-xr-x   2 root root  4096 marras  9  2021 5.4.0-88-generic
drwxr-xr-x   2 root root  4096 marras 30  2021 5.4.0-89-generic
drwxr-xr-x   2 root root  4096 tammi   4  2022 5.4.0-90-generic
drwxr-xr-x   2 root root  4096 tammi  12  2022 5.4.0-91-generic
drwxr-xr-x   2 root root  4096 tammi  19  2022 5.4.0-92-generic
drwxr-xr-x   2 root root  4096 helmi   1  2022 5.4.0-94-generic
drwxr-xr-x   2 root root  4096 helmi   8  2022 5.4.0-96-generic
drwxr-xr-x   2 root root  4096 helmi  18  2022 5.4.0-97-generic
drwxr-xr-x   2 root root  4096 maalis  9  2022 5.4.0-99-generic
total 270464
drwxr-xr-x  4 root root     4096 syys    8 11:28 .
drwxr-xr-x 20 root root     4096 elo    12 15:50 ..
-rw-r--r--  1 root root   218350 huhti   5  2019 config-4.18.0-18-generic
-rw-r--r--  1 root root   261879 elo     4 20:16 config-5.15.0-46-generic
-rw-r--r--  1 root root   261841 elo    10 10:49 config-5.15.0-47-generic
-rw-r--r--  1 root root   237947 elo     4 04:48 config-5.4.0-124-generic
drwx------  3 root root     4096 tammi   1  1970 efi
drwxr-xr-x  5 root root     4096 syys    1 09:57 grub
lrwxrwxrwx  1 root root       28 syys    1 09:56 initrd.img -> initrd.img-5.15.0-47-generic
-rw-r--r--  1 root root 33143432 elo    12 15:49 initrd.img-4.18.0-18-generic
-rw-r--r--  1 root root 63294717 elo    12 15:59 initrd.img-5.15.0-46-generic
-rw-r--r--  1 root root 63321921 syys    8 11:28 initrd.img-5.15.0-47-generic
-rw-r--r--  1 root root 48803156 elo    12 15:59 initrd.img-5.4.0-124-generic
lrwxrwxrwx  1 root root       28 syys    1 09:56 initrd.img.old -> initrd.img-5.15.0-46-generic
-rw-r--r--  1 root root   182800 helmi   6  2022 memtest86+.bin
-rw-r--r--  1 root root   184476 helmi   6  2022 memtest86+.elf
-rw-r--r--  1 root root   184980 helmi   6  2022 memtest86+_multiboot.bin
-rw-------  1 root root  4269475 huhti   5  2019 System.map-4.18.0-18-generic
-rw-------  1 root root  6252303 elo     4 20:16 System.map-5.15.0-46-generic
-rw-------  1 root root  6245466 elo    10 10:49 System.map-5.15.0-47-generic
-rw-------  1 root root  4758850 elo     4 04:48 System.map-5.4.0-124-generic
lrwxrwxrwx  1 root root       25 syys    1 09:56 vmlinuz -> vmlinuz-5.15.0-47-generic
-rw-------  1 root root  8556280 huhti   5  2019 vmlinuz-4.18.0-18-generic
-rw-------  1 root root 11531520 elo     4 20:34 vmlinuz-5.15.0-46-generic
-rw-------  1 root root 11530816 elo    11 10:44 vmlinuz-5.15.0-47-generic
-rw-------  1 root root 13660416 elo     4 04:54 vmlinuz-5.4.0-124-generic
lrwxrwxrwx  1 root root       25 syys    1 09:56 vmlinuz.old -> vmlinuz-5.15.0-46-generic
ii  binutils-x86-64-linux-gnu                  2.38-3ubuntu1                              amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                 4.5ubuntu9                                 all          Linux image base package
ii  linux-firmware                             20220329.git681281e4-0ubuntu3.4            all          Firmware for Linux kernel drivers
ii  linux-headers-5.15.0-46                    5.15.0-46.49                               all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-46-generic            5.15.0-46.49                               amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ii  linux-headers-5.15.0-47                    5.15.0-47.51                               all          Header files related to Linux kernel version 5.15.0
ii  linux-headers-5.15.0-47-generic            5.15.0-47.51                               amd64        Linux kernel headers for version 5.15.0 on 64 bit x86 SMP
ri  linux-headers-5.4.0-124                    5.4.0-124.140                              all          Header files related to Linux kernel version 5.4.0
ri  linux-headers-5.4.0-124-generic            5.4.0-124.140                              amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                      5.15.0.47.47                               amd64        Generic Linux kernel headers
ii  linux-headers-generic-hwe-18.04            5.4.0.124.125                              amd64        Generic Linux kernel headers (dummy transitional package)
rc  linux-image-4.18.0-15-generic              4.18.0-15.16~18.04.1                       amd64        Signed kernel image generic
rc  linux-image-4.18.0-17-generic              4.18.0-17.18~18.04.1                       amd64        Signed kernel image generic
ii  linux-image-4.18.0-18-generic              4.18.0-18.19~18.04.1                       amd64        Signed kernel image generic
rc  linux-image-4.18.0-20-generic              4.18.0-20.21~18.04.1                       amd64        Signed kernel image generic
rc  linux-image-4.18.0-21-generic              4.18.0-21.22~18.04.1                       amd64        Signed kernel image generic
rc  linux-image-4.18.0-22-generic              4.18.0-22.23~18.04.1                       amd64        Signed kernel image generic
rc  linux-image-4.18.0-24-generic              4.18.0-24.25~18.04.1                       amd64        Signed kernel image generic
rc  linux-image-4.18.0-25-generic              4.18.0-25.26~18.04.1                       amd64        Signed kernel image generic
rc  linux-image-5.0.0-23-generic               5.0.0-23.24~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.0.0-25-generic               5.0.0-25.26~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.0.0-27-generic               5.0.0-27.28~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.0.0-29-generic               5.0.0-29.31~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.0.0-31-generic               5.0.0-31.33~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.0.0-32-generic               5.0.0-32.34~18.04.2                        amd64        Signed kernel image generic
rc  linux-image-5.0.0-35-generic               5.0.0-35.38~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.0.0-36-generic               5.0.0-36.39~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.0.0-37-generic               5.0.0-37.40~18.04.1                        amd64        Signed kernel image generic
ii  linux-image-5.15.0-46-generic              5.15.0-46.49                               amd64        Signed kernel image generic
ii  linux-image-5.15.0-47-generic              5.15.0-47.51                               amd64        Signed kernel image generic
rc  linux-image-5.3.0-26-generic               5.3.0-26.28~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-28-generic               5.3.0-28.30~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-40-generic               5.3.0-40.32~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-42-generic               5.3.0-42.34~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-45-generic               5.3.0-45.37~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-46-generic               5.3.0-46.38~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-51-generic               5.3.0-51.44~18.04.2                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-53-generic               5.3.0-53.47~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-59-generic               5.3.0-59.53~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-61-generic               5.3.0-61.55~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.3.0-62-generic               5.3.0-62.56~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.4.0-100-generic              5.4.0-100.113                              amd64        Signed kernel image generic
rc  linux-image-5.4.0-104-generic              5.4.0-104.118                              amd64        Signed kernel image generic
rc  linux-image-5.4.0-105-generic              5.4.0-105.119                              amd64        Signed kernel image generic
rc  linux-image-5.4.0-107-generic              5.4.0-107.121                              amd64        Signed kernel image generic
rc  linux-image-5.4.0-109-generic              5.4.0-109.123                              amd64        Signed kernel image generic
rc  linux-image-5.4.0-110-generic              5.4.0-110.124                              amd64        Signed kernel image generic
rc  linux-image-5.4.0-113-generic              5.4.0-113.127                              amd64        Signed kernel image generic
rc  linux-image-5.4.0-117-generic              5.4.0-117.132                              amd64        Signed kernel image generic
rc  linux-image-5.4.0-120-generic              5.4.0-120.136                              amd64        Signed kernel image generic
rc  linux-image-5.4.0-121-generic              5.4.0-121.137                              amd64        Signed kernel image generic
rc  linux-image-5.4.0-122-generic              5.4.0-122.138                              amd64        Signed kernel image generic
ri  linux-image-5.4.0-124-generic              5.4.0-124.140                              amd64        Signed kernel image generic
rc  linux-image-5.4.0-42-generic               5.4.0-42.46~18.04.1                        amd64        Signed kernel image generic
rc  linux-image-5.4.0-45-generic               5.4.0-45.49~18.04.2                        amd64        Signed kernel image generic
rc  linux-image-5.4.0-47-generic               5.4.0-47.51                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-48-generic               5.4.0-48.52                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-51-generic               5.4.0-51.56                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-52-generic               5.4.0-52.57                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-53-generic               5.4.0-53.59                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-54-generic               5.4.0-54.60                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-56-generic               5.4.0-56.62                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-58-generic               5.4.0-58.64                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-59-generic               5.4.0-59.65                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-60-generic               5.4.0-60.67                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-62-generic               5.4.0-62.70                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-64-generic               5.4.0-64.72                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-65-generic               5.4.0-65.73                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-66-generic               5.4.0-66.74                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-67-generic               5.4.0-67.75                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-70-generic               5.4.0-70.78                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-71-generic               5.4.0-71.79                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-72-generic               5.4.0-72.80                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-73-generic               5.4.0-73.82                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-74-generic               5.4.0-74.83                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-77-generic               5.4.0-77.86                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-80-generic               5.4.0-80.90                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-81-generic               5.4.0-81.91                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-84-generic               5.4.0-84.94                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-86-generic               5.4.0-86.97                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-88-generic               5.4.0-88.99                                amd64        Signed kernel image generic
rc  linux-image-5.4.0-89-generic               5.4.0-89.100                               amd64        Signed kernel image generic
rc  linux-image-5.4.0-90-generic               5.4.0-90.101                               amd64        Signed kernel image generic
rc  linux-image-5.4.0-91-generic               5.4.0-91.102                               amd64        Signed kernel image generic
rc  linux-image-5.4.0-92-generic               5.4.0-92.103                               amd64        Signed kernel image generic
rc  linux-image-5.4.0-94-generic               5.4.0-94.106                               amd64        Signed kernel image generic
rc  linux-image-5.4.0-96-generic               5.4.0-96.109                               amd64        Signed kernel image generic
rc  linux-image-5.4.0-97-generic               5.4.0-97.110                               amd64        Signed kernel image generic
rc  linux-image-5.4.0-99-generic               5.4.0-99.112                               amd64        Signed kernel image generic
ii  linux-libc-dev:amd64                       5.15.0-47.51                               amd64        Linux Kernel Headers for development
rc  linux-modules-4.18.0-15-generic            4.18.0-15.16~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-4.18.0-17-generic            4.18.0-17.18~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
ii  linux-modules-4.18.0-18-generic            4.18.0-18.19~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-4.18.0-20-generic            4.18.0-20.21~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-4.18.0-21-generic            4.18.0-21.22~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-4.18.0-22-generic            4.18.0-22.23~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-4.18.0-24-generic            4.18.0-24.25~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-4.18.0-25-generic            4.18.0-25.26~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-5.0.0-23-generic             5.0.0-23.24~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-5.0.0-25-generic             5.0.0-25.26~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-5.0.0-27-generic             5.0.0-27.28~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-5.0.0-29-generic             5.0.0-29.31~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-5.0.0-31-generic             5.0.0-31.33~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-5.0.0-32-generic             5.0.0-32.34~18.04.2                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-5.0.0-35-generic             5.0.0-35.38~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-5.0.0-36-generic             5.0.0-36.39~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-5.0.0-37-generic             5.0.0-37.40~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
ii  linux-modules-5.15.0-46-generic            5.15.0-46.49                               amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
ii  linux-modules-5.15.0-47-generic            5.15.0-47.51                               amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-26-generic             5.3.0-26.28~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-28-generic             5.3.0-28.30~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-40-generic             5.3.0-40.32~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-42-generic             5.3.0-42.34~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-45-generic             5.3.0-45.37~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-46-generic             5.3.0-46.38~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-51-generic             5.3.0-51.44~18.04.2                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-53-generic             5.3.0-53.47~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-59-generic             5.3.0-59.53~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-61-generic             5.3.0-61.55~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-62-generic             5.3.0-62.56~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-100-generic            5.4.0-100.113                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-104-generic            5.4.0-104.118                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-105-generic            5.4.0-105.119                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-107-generic            5.4.0-107.121                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-109-generic            5.4.0-109.123                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-110-generic            5.4.0-110.124                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-113-generic            5.4.0-113.127                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-117-generic            5.4.0-117.132                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-120-generic            5.4.0-120.136                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-121-generic            5.4.0-121.137                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-122-generic            5.4.0-122.138                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ri  linux-modules-5.4.0-124-generic            5.4.0-124.140                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-42-generic             5.4.0-42.46~18.04.1                        amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-45-generic             5.4.0-45.49~18.04.2                        amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-47-generic             5.4.0-47.51                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-48-generic             5.4.0-48.52                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-51-generic             5.4.0-51.56                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-52-generic             5.4.0-52.57                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-53-generic             5.4.0-53.59                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-54-generic             5.4.0-54.60                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-56-generic             5.4.0-56.62                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-58-generic             5.4.0-58.64                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-59-generic             5.4.0-59.65                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-60-generic             5.4.0-60.67                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-62-generic             5.4.0-62.70                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-64-generic             5.4.0-64.72                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-65-generic             5.4.0-65.73                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-66-generic             5.4.0-66.74                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-67-generic             5.4.0-67.75                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-70-generic             5.4.0-70.78                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-71-generic             5.4.0-71.79                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-72-generic             5.4.0-72.80                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-73-generic             5.4.0-73.82                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-74-generic             5.4.0-74.83                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-77-generic             5.4.0-77.86                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-80-generic             5.4.0-80.90                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-81-generic             5.4.0-81.91                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-84-generic             5.4.0-84.94                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-86-generic             5.4.0-86.97                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-88-generic             5.4.0-88.99                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-89-generic             5.4.0-89.100                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-90-generic             5.4.0-90.101                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-91-generic             5.4.0-91.102                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-92-generic             5.4.0-92.103                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-94-generic             5.4.0-94.106                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-96-generic             5.4.0-96.109                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-97-generic             5.4.0-97.110                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-99-generic             5.4.0-99.112                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.18.0-15-generic      4.18.0-15.16~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.18.0-17-generic      4.18.0-17.18~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.18.0-18-generic      4.18.0-18.19~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.18.0-20-generic      4.18.0-20.21~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.18.0-21-generic      4.18.0-21.22~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.18.0-22-generic      4.18.0-22.23~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.18.0-24-generic      4.18.0-24.25~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.18.0-25-generic      4.18.0-25.26~18.04.1                       amd64        Linux kernel extra modules for version 4.18.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.0.0-23-generic       5.0.0-23.24~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.0.0-25-generic       5.0.0-25.26~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.0.0-27-generic       5.0.0-27.28~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.0.0-29-generic       5.0.0-29.31~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.0.0-31-generic       5.0.0-31.33~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.0.0-32-generic       5.0.0-32.34~18.04.2                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.0.0-35-generic       5.0.0-35.38~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.0.0-36-generic       5.0.0-36.39~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.0.0-37-generic       5.0.0-37.40~18.04.1                        amd64        Linux kernel extra modules for version 5.0.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.15.0-46-generic      5.15.0-46.49                               amd64        Linux kernel extra modules for version 5.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-26-generic       5.3.0-26.28~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-28-generic       5.3.0-28.30~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-40-generic       5.3.0-40.32~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-42-generic       5.3.0-42.34~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-45-generic       5.3.0-45.37~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-46-generic       5.3.0-46.38~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-51-generic       5.3.0-51.44~18.04.2                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-53-generic       5.3.0-53.47~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-59-generic       5.3.0-59.53~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-61-generic       5.3.0-61.55~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-62-generic       5.3.0-62.56~18.04.1                        amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-100-generic      5.4.0-100.113                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-104-generic      5.4.0-104.118                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-105-generic      5.4.0-105.119                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-107-generic      5.4.0-107.121                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-109-generic      5.4.0-109.123                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-110-generic      5.4.0-110.124                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-113-generic      5.4.0-113.127                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-117-generic      5.4.0-117.132                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-120-generic      5.4.0-120.136                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-121-generic      5.4.0-121.137                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-122-generic      5.4.0-122.138                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ri  linux-modules-extra-5.4.0-124-generic      5.4.0-124.140                              amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-42-generic       5.4.0-42.46~18.04.1                        amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-45-generic       5.4.0-45.49~18.04.2                        amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-47-generic       5.4.0-47.51                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-48-generic       5.4.0-48.52                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-51-generic       5.4.0-51.56                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-52-generic       5.4.0-52.57                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-53-generic       5.4.0-53.59                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-54-generic       5.4.0-54.60                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-56-generic       5.4.0-56.62                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-58-generic       5.4.0-58.64                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-59-generic       5.4.0-59.65                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-60-generic       5.4.0-60.67                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-62-generic       5.4.0-62.70                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-64-generic       5.4.0-64.72                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-65-generic       5.4.0-65.73                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-66-generic       5.4.0-66.74                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-67-generic       5.4.0-67.75                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-70-generic       5.4.0-70.78                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-71-generic       5.4.0-71.79                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-72-generic       5.4.0-72.80                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-73-generic       5.4.0-73.82                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-74-generic       5.4.0-74.83                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-77-generic       5.4.0-77.86                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-80-generic       5.4.0-80.90                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-81-generic       5.4.0-81.91                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-84-generic       5.4.0-84.94                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-86-generic       5.4.0-86.97                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-88-generic       5.4.0-88.99                                amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-89-generic       5.4.0-89.100                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-90-generic       5.4.0-90.101                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-91-generic       5.4.0-91.102                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-92-generic       5.4.0-92.103                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-94-generic       5.4.0-94.106                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-96-generic       5.4.0-96.109                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-97-generic       5.4.0-97.110                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-99-generic       5.4.0-99.112                               amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu7                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                            3:6.04~git20190206.bf6db5b4+dfsg1-3ubuntu1 all          collection of bootloaders (common)
ii  syslinux-legacy                            2:3.63+dfsg-2ubuntu9                       amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by TheFu on 2022-09-10
If it were me, I'd clean up all the old kernels, modules, headers as my first step.  That would be using the purge option ... just to cleanup that junk.
Any kernel, kernel-headers, kernel-modules, that aren't 5.15.x, I'd purge. Heck, I'd purge any kernels (modules+headers too) that aren't from 2022. It isn't like you need those files. They are cruft in the file system and in the apt-cache.

This systems seems to be from 18.04 (or earlier), so perhaps it is time to do a clean install to remove all the conflicting tools?

Please always, always, always, use forum code tags when posting 
a) the terminal command, all options, and 
b) the output from those commands.

It will keep the columns, so things line up.  The 'df' output is very hard to read, for example.
BTW, 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
is a useful alias to have and use. It removes all the extra junk that isn't actually storage stuff.  Cruft gets in the way of understanding what is really happening and often hides the important stuff from our human brains. Avoid cruft.

Synaptic is the GUI way - be certain to choose "purge".  I'd use **sudo apt-get remove  --purge ..... ** myself.  apt-get supports globbing.  I'd try 
```
sudo apt-get autoremove  --purge
```
first, then again after removing the crufty kernels.

In general, I keep 3 kernels and try to ensure APT's list of packages doesn't show any 'rc' kernels, headers, or modules.  Those are removed, but not purged.  Purging will remove the record from the APT DB too.

---

### Post by Bashing-om on 2022-09-10
yatski; Yeah - you have the right of it - Lot's to clean up.

+10 to what TheFu advises :)

A handy dandy to remove the cruft - 'rc' marked packages; I do suggest a shotgun approach:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.
```
 
dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```
let&#8217;s remove all the packages marked as rc so we see through the cruft.
Looking at what I can see -- looks like to me all you want to keep are the 5.15.0-46 and 5.15.0-47 kernels.
However *DO* make sure of what kernel is booted:
```

uname -r

```
Do not mess with that booted kernel!

If you need further guidance in removals - please ask.


-help is what we do-

---

