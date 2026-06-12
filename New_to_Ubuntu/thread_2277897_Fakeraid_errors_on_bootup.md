---
title: "Fakeraid errors on bootup"
date: 2015-05-12
forum: New to Ubuntu
---

### Post by LinuxAlexs on 2015-05-12
Hi

I am using a fours hard drives  giving me two fakeraid disks, I have three Windows OS partitions and Linux as below (also a few other partitions kicking about).

```
alex@XPS-Studio:~$ sudo lsblk -f
NAME                              FSTYPE          LABEL     MOUNTPOINT
sda                               isw_raid_member           
&#9500;&#9472;isw_ifefcjibh_ARRAY0 (dm-0)                               
&#9474; &#9500;&#9472;isw_ifefcjibh_ARRAY0p1 (dm-1) vfat            BOOT      
&#9474; &#9500;&#9472;isw_ifefcjibh_ARRAY0p2 (dm-2) ntfs            DAW       
&#9474; &#9500;&#9472;isw_ifefcjibh_ARRAY0p3 (dm-3) ntfs            OS Games  
&#9474; &#9492;&#9472;isw_ifefcjibh_ARRAY0p4 (dm-4) ntfs            Dev       
&#9492;&#9472;isw_ifefcjibh_ARRAY1 (dm-5)                               
  &#9500;&#9472;isw_ifefcjibh_ARRAY1p1 (dm-6) ntfs            DATAPART1 
  &#9500;&#9472;isw_ifefcjibh_ARRAY1p2 (dm-7) swap                      [SWAP]
  &#9492;&#9472;isw_ifefcjibh_ARRAY1p3 (dm-8) ext3            Linux     /
sdb                               isw_raid_member           
&#9500;&#9472;isw_ifefcjibh_ARRAY0 (dm-0)                               
&#9474; &#9500;&#9472;isw_ifefcjibh_ARRAY0p1 (dm-1) vfat            BOOT      
&#9474; &#9500;&#9472;isw_ifefcjibh_ARRAY0p2 (dm-2) ntfs            DAW       
&#9474; &#9500;&#9472;isw_ifefcjibh_ARRAY0p3 (dm-3) ntfs            OS Games  
&#9474; &#9492;&#9472;isw_ifefcjibh_ARRAY0p4 (dm-4) ntfs            Dev       
&#9492;&#9472;isw_ifefcjibh_ARRAY1 (dm-5)                               
  &#9500;&#9472;isw_ifefcjibh_ARRAY1p1 (dm-6) ntfs            DATAPART1 
  &#9500;&#9472;isw_ifefcjibh_ARRAY1p2 (dm-7) swap                      [SWAP]
  &#9492;&#9472;isw_ifefcjibh_ARRAY1p3 (dm-8) ext3            Linux     /
sr0             
```                                            


.. the system appears to be working normally but is there any way to clear up the following errors in syslog, I haven't got a clue to be honest?

```
May 12 12:31:02 XPS-Studio kernel: [   24.559035] systemd-udevd[804]: conflicting device node '/dev/mapper/isw_ifefcjibh_ARRAY1p3' found, link to '/dev/dm-8' will not be created
May 12 12:31:02 XPS-Studio kernel: [   24.645422] systemd-udevd[804]: conflicting device node '/dev/mapper/isw_ifefcjibh_ARRAY1p2' found, link to '/dev/dm-7' will not be created
May 12 12:31:02 XPS-Studio kernel: [   25.085805] init: failsafe main process (985) killed by TERM signal
May 12 12:31:03 XPS-Studio kernel: [   25.223858] systemd-udevd[825]: conflicting device node '/dev/mapper/isw_ifefcjibh_ARRAY0p1' found, link to '/dev/dm-1' will not be created
May 12 12:31:03 XPS-Studio kernel: [   25.246758] systemd-udevd[812]: conflicting device node '/dev/mapper/isw_ifefcjibh_ARRAY0p4' found, link to '/dev/dm-4' will not be created
May 12 12:31:04 XPS-Studio kernel: [   26.311311] systemd-udevd[804]: conflicting device node '/dev/mapper/isw_ifefcjibh_ARRAY0p1' found, link to '/dev/dm-1' will not be created
May 12 12:31:04 XPS-Studio kernel: [   26.594261] systemd-udevd[807]: conflicting device node '/dev/mapper/isw_ifefcjibh_ARRAY0p2' found, link to '/dev/dm-2' will not be created


May 12 12:31:06 XPS-Studio dmraid-activate: ERROR: Cannot retrieve RAID set information for isw_ifefcjibh_ARRAY0
May 12 12:31:06 XPS-Studio dmraid-activate: ERROR: Cannot retrieve RAID set information for isw_ifefcjibh_ARRAY0



```

Many thanks...

---

### Post by dino99 on 2015-05-12
do you get the same errors if you choose 'upstart' to boot ?  (seems to be a systemd-udevd issue)

---

### Post by LinuxAlexs on 2015-05-12
Thanks for the response dino99

I did:

*initctl --version* and got initctl (upstart 1.12.1) so I assume it's installed.

I don't see it in the grub advanced menu however. I don't suppose you could give me specific instructions on how to run in grub?
From research I suppose I have to type in *init=/sbin/upstart* somewhere....?

Thanks..

---

