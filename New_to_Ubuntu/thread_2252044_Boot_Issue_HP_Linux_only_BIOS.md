---
title: "Boot Issue HP Linux only BIOS"
date: 2014-11-08
forum: New to Ubuntu
---

### Post by Diegovic on 2014-11-08
Hi,
I hope this is the right place for this post.
I'm having problem with my 14.04 installation on a HP Elitebook2530p notebook (Ubuntu only, no other OS loaded). When the lapton runs out of battery in standby mode, GRUB gets somehow damage and I'm booted to the GRUB rescue prompt.

I run GRUB Repair which reported No Changes to be made to my PC providing this report: [http://paste.ubuntu.com/8887902/](http://paste.ubuntu.com/8887902/)

Can anyone please provide some clue on the next steps to take as I'm relatively new to Ubuntu?

Thanks in advance
Diego

---

### Post by oldfred on 2014-11-08
Your BIOS promoted flash drive to sda, and then 160GB drive is sdb.

And for whatever reason, your sdb1 has no UUID and script cannot open it.

Did system get shut down abnormally.

You may need fsck after  abnormal shutdown. I would try that first.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Diegovic on 2014-11-09
Thanks a lot for your answer.
Yes, the problem was generated after an unexpected power loss. Basically the system run out of batteries during suspend mode.

I tried to perform what suggested but had a little luck. See what happened:
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef03e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   308563967   154280960   83  Linux
/dev/sdb2       308566014   312580095     2007041    5  Extended
/dev/sdb5       308566016   312580095     2007040   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sdb1 
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo dmesg | tail
[13642.416114] Descriptor sense data with sense descriptors (in hex):
[13642.416116]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[13642.416129]         00 00 08 05 
[13642.416135] sd 2:0:0:0: [sdb]  
[13642.416139] Add. Sense: Unrecovered read error - auto reallocate failed
[13642.416142] sd 2:0:0:0: [sdb] CDB: 
[13642.416144] Read(10): 28 00 00 00 08 00 00 00 08 00
[13642.416154] end_request: I/O error, dev sdb, sector 2053
[13642.416158] Buffer I/O error on device sdb1, logical block 0
[13642.416172] ata2: EH complete

As I need the PC back, I'll try a fresh re-install now. But it would be good what shall be done in case of a future similar issue.

Thanks again,
Diego

---

### Post by grahammechanical on 2014-11-09
> [COLOR=#000000]When the lapton runs out of battery in standby mode,[/COLOR]

> [COLOR=#000000]it would be good what shall be done in case of a future similar issue.[/COLOR]

Does it need to be said?

Suspend should be thought of as "suspend to RAM." Many of the hardware components are powered down but not the memory chips (RAM). So, what is going to happen if there is a complete lost of power when the OS has been suspended and the state of the OS is held in system memory?

On the other hand, hibernate is "suspend to Disk." The state of the OS is store in the swap partition which must be large enough to hold everything in RAM. 

Unfortunately, it seems that Linux has its work cut out with both suspend and hibernate. The safest answer to your question is to shut down rather then suspend if there is the slightest risk of a total lost of power.

[https://help.ubuntu.com/community/PowerManagement/Hibernate](https://help.ubuntu.com/community/PowerManagement/Hibernate)

[https://help.ubuntu.com/14.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/14.04/ubuntu-help/power-hibernate.html)

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

[https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)

Regards.

---

