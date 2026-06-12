---
title: "Windows7/Ubuntu Dual Windows load first no matter what"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by Felos on 2013-03-23
First, pardon my english. First time posting about anything. I just installed ubuntu 12.04 in a partition of my hdd that already had windows 7. Seems like the windows loader (mbr?) is being read first and I don't even get to the grub menu. I guess that's happening because I chose to set the mountpoint of ubuntu on sda6 and the windows loader is on sda1. So how can I move the grub or the windows loader to make grub loader being read first upon booting?

---

### Post by oldfred on 2013-03-23
Computers boot from BIOS to MBR and in MBR is code to find the rest of the boot process as MBR is tiny.

You need to install grub2's boot loader to the MBR. If you install anything to the Windows PBR - partition boot sector you will corrupt the Windows boot process as it goes BIOS -> MBR -> PBR then the ntldr or bootmgr to boot.

Best to see details. This may fix some issues.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Felos on 2013-03-24
[http://paste.ubuntu.com/5642541/](http://paste.ubuntu.com/5642541/) here you go.

edit: fixed whatever it was with boot-repair, so thank you very much :)

---

### Post by oldfred on 2013-03-24
Glad you got it working.

You installed grub to sdb, even though your install is in sda. But since Windows is also in sda that is fine as then you have each boot loader in a separate drive.
With multiple drives, I prefer to have an operating system on every drive and each system configured to fully boot just from that drive and load data from other drives.
Then when one drive fails, I can still boot other drive. Of course I still have backups and repair flash drives also.

So next time you reconfigure you may want to think about where you have installed your operating systems?

---

