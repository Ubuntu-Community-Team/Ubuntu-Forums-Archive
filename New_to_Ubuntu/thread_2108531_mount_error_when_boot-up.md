---
title: "mount error when boot-up"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by luciazhang on 2013-01-24
[SIZE=2]Hi Guys,
[SIZE=2]I a[/SIZE]m using UBUNTU 12.04LTS, 64bit Desktop Version.

[SIZE=2][SIZE=2]I [SIZE=2]assigned 100G [SIZE=2]of emp[SIZE=2][SIZE=2]ty[/SIZE] disk[SIZE=2] for Ubuntu installa[SIZE=2]tion. B[SIZE=2]ut it always [SIZE=2]report[SIZE=2]s [SIZE=2]"no[SIZE=2] s[SIZE=2]pace[/SIZE][/SIZE]".  [SIZE=2]I[SIZE=2] found there[SIZE=2] were 79[SIZE=2]G le[SIZE=2]ft on host[SIZE=2]. So I c[SIZE=2]op[SIZE=2]ied [SIZE=2]the "root.disk[SIZE=2]" file in host [SIZE=2]and named "extra.di[SIZE=2]sk[/SIZE]"[SIZE=2], mounting the home folder[SIZE=2]s into th[SIZE=2]is extra.disk.[SIZE=2] T[SIZE=2]he spac[SIZE=2]ing problem seems [SIZE=2]solved[SIZE=2], but boot[SIZE=2]up error comes up......

[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=3][COLOR=Red]Error  while mounting . . . .
press S to skip or M to Manual edit.[/COLOR][/SIZE]

[SIZE=2]Here is my **[COLOR=Red]f[SIZE=2]disk[SIZE=2] -l: [/SIZE][/SIZE][/COLOR]**[/SIZE]
[SIZE=2]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x077ec3a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848   186099711    92946432    7  HPFS/NTFS/exFAT
/dev/sda2       186099712   724721663   269310976    7  HPFS/NTFS/exFAT
/dev/sda3       724721664  1953521663   614400000    f  W95 Ext'd (LBA)
/dev/sda5       724723712   904945663    90110976    7  HPFS/NTFS/exFAT
/dev/sda6       904947712  1953521663   524286976    7  HPFS/NTFS/exFAT
[/SIZE]
Her[SIZE=2]e is what i got[SIZE=2][SIZE=2][SIZE=2] when typ[SIZE=2]ing [/SIZE][/SIZE][/SIZE][/SIZE]commnd "**[COLOR=Red]gksudo gedit /etc/fstab[/COLOR]**":[/SIZE]

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc        proc  nodev,noexec,nosuid     0  0  
/host/ubuntu/disks/root.disk  /            ext4  loop,errors=remount-ro  0  1  
/host/ubuntu/disks/swap.disk  none         swap  loop,sw                 0  0  
/dev/sda5                     /media/sda5  ntfs  defaults                0  0  

[SIZE=2]P[SIZE=2]lz [SIZE=2]h[SIZE=2]elp me[SIZE=2], tell me what i [SIZE=2]should do next!!!!!!!!!!!!!

[SIZE=2]Lucia[/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by Bashing-om on 2013-01-24
luciazhang; Hi ! Welcome to the forum.

Houston, we have a problem.
Compare my "fdisk" output to yours:
> sysop1@1204-a:~$ sudo blkid
[sudo] password for sysop1: 
/dev/sda1: UUID="3fa74832-fcbc-475a-baee-66339bbc5c1e" TYPE="ext4" 
/dev/sda2: UUID="52cf8e71-3688-40b2-af66-18f1a443faaf" TYPE="ext4" 
/dev/sda5: UUID="d620587e-8686-421d-bf30-caf01109e53a" TYPE="ext4" 
/dev/sda6: UUID="b9105f87-6282-4bcc-bd50-70583ede412a" TYPE="ext4" 
/dev/sda7: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda8: UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda9: UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sdb1: UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: UUID="5bae8c40-b15d-42f8-9fc9-0cf087f338d4" TYPE="ext4" 
/dev/sdc5: UUID="5600e3b4-ca64-4836-a1cc-86d5b763346d" TYPE="swap" 
sysop1@1204-a:~$ Mine is all 'buntu (ext4)..but notice yours is all windows (ntfs).

So what is required is to identify what all the ntfs partitions are. Pare the disk down to:
option 1: 3 primary partitions for windows and an extended partition, in the extended partition install ubuntu.
option 2: pare the disk down to 2 primary partitions for windows, 1 primary partition for ubuntu, an extended partition for swap.

Windows wants to be in the first partitions in order to be happy.

Then again, you may have what is termed as a "wubi" install. Which is ubuntu running inside of windows. If that be so, I can not help you, I have no knowledge or experience with the "wubi" installation. 
> [SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2] [SIZE=2]I[SIZE=2] found there[SIZE=2] were 79[SIZE=2]G le[SIZE=2]ft on host[SIZE=2].[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2] indicates that you have a "wubi" install, others will advise.

[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][INDENT][INDENT][SIZE=2]best regards 

[/SIZE][/INDENT][/INDENT]

---

