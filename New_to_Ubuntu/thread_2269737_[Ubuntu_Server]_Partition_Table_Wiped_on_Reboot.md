---
title: "[Ubuntu Server] Partition Table Wiped on Reboot"
date: 2015-03-17
forum: New to Ubuntu
---

### Post by Lee_Bhogal on 2015-03-17
Hi All,

New to the forums and new to Ubuntu Server.  I have a real odd issue and one that is tough to troubleshoot.  Occasionally, after I reboot my server, the boot fails.  No errors, it just hangs on the POST screen after the BIOS splash screen with a flashing cursor.

If I unplug my second hdd [/dev/sdb] and reboot, i get the error 'BOOD DISK FAILURE, PLEASE INSERT SYSTEM DISK AND REBOOT'.  I cannot get into grub.

I have used the LiveCD to attempt repair. I got through to the partition manager and the 2nd HDD shows its partition table fine, but the primary HDD [/dev/sda] shows as completely blank, not even showing free space at this point.

This is happening on 14.04 and 14.10.
The only thing I can think that is causing this is the OpenVPN. It appears to happen after I connect a client device for the 1st time (but this may be purely coinsidental). 

It usually happens after about a day of operation. 

Has anyone else come across this?

{update} This is now happening across 2 harddrives as well as Ubuntu Desktop 14.04

Thanks

Lee

---

