---
title: "Apt upgrade hanging"
date: 2021-10-22
forum: New to Ubuntu
---

### Post by agreen0 on 2021-10-22
Hi all,

I currently have an ubuntu 20.04 system which I am trying to patch, it looks like previously the system was patched and it never finished. I am new to the company and have inherited the problem. I thought it might of been a corrupt kernel patch so I tried to remove it however its doing the same thing on the latest kernel.

Current kernel level is

5.4.0-42-generic

Below is the last entry in the apt history log

Start-Date: 2021-10-21  13:23:08
Commandline: apt remove linux-image-5.4.0-66-generic
Requested-By: id125984 (1001)
Install: linux-image-5.4.0-89-generic:amd64 (5.4.0-89.100, automatic), linux-modules-extra-5.4.0-89-generic:amd64 (5.4.0-89.100, automatic), linux-headers-5.4.0-89-generic:am
d64 (5.4.0-89.100, automatic), linux-modules-5.4.0-89-generic:amd64 (5.4.0-89.100, automatic), linux-headers-5.4.0-89:amd64 (5.4.0-89.100, automatic), linux-image-unsigned-5.
4.0-66-generic:amd64 (5.4.0-66.74, automatic)
Upgrade: linux-headers-generic:amd64 (5.4.0.66.69, 5.4.0.89.93), linux-image-generic:amd64 (5.4.0.66.69, 5.4.0.89.93), linux-generic:amd64 (5.4.0.66.69, 5.4.0.89.93)
Remove: linux-image-5.4.0-66-generic:amd64 (5.4.0-66.74), linux-modules-extra-5.4.0-66-generic:amd64 (5.4.0-66.74)

dpkg output

[COLOR=#242424][FONT=&amp]dpkg --list | egrep '^iF'[/FONT][/COLOR]
[COLOR=#242424][FONT=&amp]iF linux-image-5.4.0-89-generic 5.4.0-89.100 amd64 Signed kernel image generic

Processes 

[/FONT][/COLOR]00:00:00 /usr/bin/dpkg --status-fd 41 --configure --pending
root      540510  540461  0 Oct21 ?        00:00:00 /bin/sh /var/lib/dpkg/info/linux-image-5.4.0-89-generic.postinst triggered linux-update-5.4.0-89-generic
root      540511  540510  0 Oct21 ?        00:00:00 sh /usr/lib/linux/triggers/5.4.0-89-generic
root      540512  540511  0 Oct21 ?        00:00:00 run-parts --report --exit-on-error --arg=5.4.0-89-generic --arg=/boot/vmlinuz-5.4.0-89-generic /etc/kernel/postinst.d
root      540564  540512  0 Oct21 ?        00:00:00 /bin/sh -e /etc/kernel/postinst.d/initramfs-tools 5.4.0-89-generic /boot/vmlinuz-5.4.0-89-generic
root      540566  540564  0 Oct21 ?        00:00:00 /bin/sh /usr/sbin/update-initramfs -c -k 5.4.0-89-generic -b /boot
root      540568  540566  0 Oct21 ?        00:00:00 /bin/sh /usr/sbin/mkinitramfs -o /boot/initrd.img-5.4.0-89-generic.new 5.4.0-89-generic
root      549330  540568  0 Oct21 ?        00:00:00 /bin/sh /usr/share/initramfs-tools/hooks/mdadm
root      549445  549330  0 Oct21 ?        00:00:00 /bin/sh /usr/share/mdadm/mkconf
root      549451  549445  0 Oct21 ?        00:00:00 /sbin/mdadm --examine --scan --config=partitions

Would be eternally helpful if someone can assist, thanks in advance
[COLOR=#242424][FONT=&amp]
[/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-10-22
What is the output of:
```

lsb_release -a; uname -a; df -h

```
Thanks

---

### Post by Impavidus on 2021-10-22
Seeing a bit more of the dpkg --list output may help. Try```
dpkg --list | grep -v '^ii\|^rc'
```That should show all packages not properly installed/removed, not just those with status iF.

Also a list of currently installed kernel packages, including metapackages and headers:```
dpkg --list linux-*
```

---

### Post by agreen0 on 2021-10-22
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04 LTS
Release:        20.04
Codename:       focal
Linux busadv-dev 5.4.0-65-generic #73-Ubuntu SMP Mon Jan 18 17:25:17 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  1.5M  1.6G   1% /run
/dev/sda4        23G   13G  8.2G  62% /
tmpfs           7.9G     0  7.9G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda2       7.3G  3.0G  3.9G  44% /home
/dev/loop0       56M   56M     0 100% /snap/core18/2074
/dev/sda3        42G  680M   39G   2% /var/www
/dev/sdb1        20G  4.0G   15G  22% /var/mysql
/dev/loop1       56M   56M     0 100% /snap/core18/2128
/dev/loop2       62M   62M     0 100% /snap/core20/1169
/dev/loop3       74M   74M     0 100% /snap/lxd/21624
/dev/loop4       62M   62M     0 100% /snap/core20/1081
/dev/loop5       73M   73M     0 100% /snap/lxd/21723
/dev/loop6       33M   33M     0 100% /snap/snapd/13270
/dev/loop7       33M   33M     0 100% /snap/snapd/13640
tmpfs           1.6G     0  1.6G   0% /run/user/1004
```

---

### Post by agreen0 on 2021-10-22
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version                           Architecture Description
+++-=====================================-=================================-============-===============================================================================
iF  linux-image-5.4.0-89-generic          5.4.0-89.100                      amd64        Signed kernel image generic
it  linux-image-unsigned-5.4.0-66-generic 5.4.0-66.74                       amd64        Linux kernel image for version 5.4.0 on 64 bit x86 SMP


```
```
dpkg --list linux-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version      Architecture Description
+++-=====================================-============-============-==============================================================
ii  linux-base                            4.5ubuntu3.1 all          Linux image base package
un  linux-doc                             <none>       <none>       (no description available)
ii  linux-firmware                        1.187        all          Firmware for Linux kernel drivers
un  linux-firmware-raspi2                 <none>       <none>       (no description available)
un  linux-firmware-snapdragon             <none>       <none>       (no description available)
ii  linux-generic                         5.4.0.89.93  amd64        Complete Generic Linux kernel and headers
un  linux-headers                         <none>       <none>       (no description available)
un  linux-headers-3.0                     <none>       <none>       (no description available)
un  linux-headers-5.4.0-39-generic        <none>       <none>       (no description available)
un  linux-headers-5.4.0-40-generic        <none>       <none>       (no description available)
ii  linux-headers-5.4.0-42                5.4.0-42.46  all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic        5.4.0-42.46  amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
un  linux-headers-5.4.0-52-generic        <none>       <none>       (no description available)
un  linux-headers-5.4.0-53-generic        <none>       <none>       (no description available)
un  linux-headers-5.4.0-56-generic        <none>       <none>       (no description available)
un  linux-headers-5.4.0-58-generic        <none>       <none>       (no description available)
un  linux-headers-5.4.0-59-generic        <none>       <none>       (no description available)
un  linux-headers-5.4.0-60-generic        <none>       <none>       (no description available)
ii  linux-headers-5.4.0-62                5.4.0-62.70  all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-62-generic        5.4.0-62.70  amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-65                5.4.0-65.73  all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-65-generic        5.4.0-65.73  amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-66                5.4.0-66.74  all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-66-generic        5.4.0-66.74  amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-89                5.4.0-89.100 all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-89-generic        5.4.0-89.100 amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                 5.4.0.89.93  amd64        Generic Linux kernel headers
un  linux-image                           <none>       <none>       (no description available)
rc  linux-image-5.4.0-39-generic          5.4.0-39.43  amd64        Signed kernel image generic
rc  linux-image-5.4.0-40-generic          5.4.0-40.44  amd64        Signed kernel image generic
ii  linux-image-5.4.0-42-generic          5.4.0-42.46  amd64        Signed kernel image generic
rc  linux-image-5.4.0-52-generic          5.4.0-52.57  amd64        Signed kernel image generic
rc  linux-image-5.4.0-53-generic          5.4.0-53.59  amd64        Signed kernel image generic
rc  linux-image-5.4.0-56-generic          5.4.0-56.62  amd64        Signed kernel image generic
rc  linux-image-5.4.0-58-generic          5.4.0-58.64  amd64        Signed kernel image generic
rc  linux-image-5.4.0-59-generic          5.4.0-59.65  amd64        Signed kernel image generic
rc  linux-image-5.4.0-60-generic          5.4.0-60.67  amd64        Signed kernel image generic
ii  linux-image-5.4.0-62-generic          5.4.0-62.70  amd64        Signed kernel image generic
ii  linux-image-5.4.0-65-generic          5.4.0-65.73  amd64        Signed kernel image generic
rc  linux-image-5.4.0-66-generic          5.4.0-66.74  amd64        Signed kernel image generic
iF  linux-image-5.4.0-89-generic          5.4.0-89.100 amd64        Signed kernel image generic
ii  linux-image-generic                   5.4.0.89.93  amd64        Generic Linux kernel image
un  linux-image-unsigned-5.4.0-39-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-40-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-42-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-52-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-53-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-56-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-58-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-59-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-60-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-62-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-65-generic <none>       <none>       (no description available)
it  linux-image-unsigned-5.4.0-66-generic 5.4.0-66.74  amd64        Linux kernel image for version 5.4.0 on 64 bit x86 SMP
un  linux-image-unsigned-5.4.0-89-generic <none>       <none>       (no description available)
un  linux-initramfs-tool                  <none>       <none>       (no description available)
un  linux-kernel-log-daemon               <none>       <none>       (no description available)
rc  linux-modules-5.4.0-39-generic        5.4.0-39.43  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-40-generic        5.4.0-40.44  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-42-generic        5.4.0-42.46  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-52-generic        5.4.0-52.57  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-53-generic        5.4.0-53.59  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-56-generic        5.4.0-56.62  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-58-generic        5.4.0-58.64  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-59-generic        5.4.0-59.65  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-60-generic        5.4.0-60.67  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-62-generic        5.4.0-62.70  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-65-generic        5.4.0-65.73  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-66-generic        5.4.0-66.74  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-89-generic        5.4.0-89.100 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-39-generic  5.4.0-39.43  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-40-generic  5.4.0-40.44  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-42-generic  5.4.0-42.46  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-52-generic  5.4.0-52.57  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-53-generic  5.4.0-53.59  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-56-generic  5.4.0-56.62  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-58-generic  5.4.0-58.64  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-59-generic  5.4.0-59.65  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-60-generic  5.4.0-60.67  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-62-generic  5.4.0-62.70  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-65-generic  5.4.0-65.73  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-66-generic  5.4.0-66.74  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-89-generic  5.4.0-89.100 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
un  linux-restricted-common               <none>       <none>       (no description available)
un  linux-source-5.4.0                    <none>       <none>       (no description available)
un  linux-tools                           <none>       <none>       (no description available)
lines 47-91/91 (END)
ii  linux-image-generic                   5.4.0.89.93  amd64        Generic Linux kernel image
un  linux-image-unsigned-5.4.0-39-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-40-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-42-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-52-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-53-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-56-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-58-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-59-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-60-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-62-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-65-generic <none>       <none>       (no description available)
it  linux-image-unsigned-5.4.0-66-generic 5.4.0-66.74  amd64        Linux kernel image for version 5.4.0 on 64 bit x86 SMP
un  linux-image-unsigned-5.4.0-89-generic <none>       <none>       (no description available)
un  linux-initramfs-tool                  <none>       <none>       (no description available)
un  linux-kernel-log-daemon               <none>       <none>       (no description available)
rc  linux-modules-5.4.0-39-generic        5.4.0-39.43  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-40-generic        5.4.0-40.44  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-42-generic        5.4.0-42.46  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-52-generic        5.4.0-52.57  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-53-generic        5.4.0-53.59  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-56-generic        5.4.0-56.62  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-58-generic        5.4.0-58.64  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-59-generic        5.4.0-59.65  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-60-generic        5.4.0-60.67  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-62-generic        5.4.0-62.70  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-65-generic        5.4.0-65.73  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-66-generic        5.4.0-66.74  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-89-generic        5.4.0-89.100 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-39-generic  5.4.0-39.43  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-40-generic  5.4.0-40.44  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-42-generic  5.4.0-42.46  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-52-generic  5.4.0-52.57  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-53-generic  5.4.0-53.59  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-56-generic  5.4.0-56.62  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-58-generic  5.4.0-58.64  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-59-generic  5.4.0-59.65  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-60-generic  5.4.0-60.67  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-62-generic  5.4.0-62.70  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-65-generic  5.4.0-65.73  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-66-generic  5.4.0-66.74  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-89-generic  5.4.0-89.100 amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
un  linux-restricted-common               <none>       <none>       (no description available)
un  linux-source-5.4.0                    <none>       <none>       (no description available)
un  linux-tools                           <none>       <none>       (no description available)
```

---

### Post by agreen0 on 2021-10-22
Just to advise I have now resolved the issue. For anyone else who has a similar issue please see the steps below.

1, rebooted however it fell over in a heap which was what I expected. I could of edited grub to point to old kernel but just went with the reboot option
2, Booted off old kernel
3, Run dpkg --configure -A 
4, Re run apt upgrade

This solved the issue for me.

Thanks to you all that assisted me with this issue

---

### Post by Impavidus on 2021-10-22
Well, that was easy. Usually when such problems occur it's because dpkg somehow fails to install the packages and dpkg --configure -a just spews error messages. In your case, maybe it was just interrupted or whatever caused dpkg to fail has gone away, so it ran now successfully.

---

