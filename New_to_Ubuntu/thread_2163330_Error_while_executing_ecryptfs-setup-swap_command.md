---
title: "Error while executing ecryptfs-setup-swap command"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by dmitriano on 2013-07-18
Hi, experts!

today I got the following while executing ecryptfs-setup-swap command on my Ubuntu 12.04 Server:[INDENT][I]WARNING:
An encrypted swap is required to help ensure that encrypted files are not leaked to disk in an unencrypted format.

HOWEVER, THE SWAP ENCRYPTION CONFIGURATION PRODUCED BY THIS PROGRAM WILL BREAK HIBERNATE/RESUME ON THIS SYSTEM!

NOTE: Your suspend/resume capabilities will not be affected.

Do you want to proceed with encrypting your swap? [y/N]: y

INFO: Setting up swap: [/dev/dm-1]
 * Stopping remaining crypto disks...                                                                                         * cryptswap1 (stopped)...                                                                                            [ OK ]
 * Starting remaining crypto disks...                                                                                         * cryptswap1 (starting)..
 * cryptswap1 (started)...                                                                                            [ OK ]
swapon: /dev/mapper/gate-swap_1: swapon failed: Invalid argument
[/I][/INDENT]

what does this "swapon failed: Invalid argument" mean? How can I check whether my swap is encrypted or not?

**my /etc/fstab file contains the following (looks like there are two swaps):**

  # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
#                
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/gate-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=6ff98683-5ec4-4fb9-a6aa-fe5c218b94c9 /boot           ext2    defaults        0       2
/dev/mapper/gate-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

 **/etc/crypttab:**
  
#                 
cryptswap1 /dev/dm-1 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
 
**fdisk -l shows the following:**

  Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ccc39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758    78163967    38831105    5  Extended
/dev/sda5          501760    78163967    38831104   8e  Linux LVM

Disk /dev/mapper/gate-root: 37.6 GB, 37648072704 bytes
255 heads, 63 sectors/track, 4577 cylinders, total 73531392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/gate-root doesn't contain a valid partition table

Disk /dev/mapper/gate-swap_1: 2113 MB, 2113929216 bytes
255 heads, 63 sectors/track, 257 cylinders, total 4128768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/gate-swap_1 doesn't contain a valid partition table

Disk /dev/mapper/cryptswap1: 2113 MB, 2113929216 bytes
255 heads, 63 sectors/track, 257 cylinders, total 4128768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e749d91

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

 **free -m:**

               total       used       free     shared    buffers     cached
Mem:          1981       1840        141          0        337        985
-/+ buffers/cache:        517       1463
Swap:         2015          0       2015
 
It is not clear to me what actually happened with my old unencrypted  swap? Does it work now? What will happened with it if I reboot the  server?

  And finally, how to disable my old swap and get encrypted swap work?

---

