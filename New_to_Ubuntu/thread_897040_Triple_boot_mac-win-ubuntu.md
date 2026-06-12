---
title: "Triple boot mac-win-ubuntu"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by ben22 on 2008-08-21
Hi,

after installing macos-winxp-ubuntu and refit on a macbookpro I have the following problem:

From the rEFIt screen I choose windows, the next screen shows Grub to select ubuntu or windows (instead of booting up windows). Anyway, I choose windows and then get the error that the hal.dll cannot be found.

As for the installation I followed [https://help.ubuntu.com/community/MacBookPro#Easiest%20Triple%20Boot%20(Boot%20Camp](https://help.ubuntu.com/community/MacBookPro#Easiest%20Triple%20Boot%20(Boot%20Camp))

So I used the Bootcamp partition to install ubuntu on top.

rEFIt partition inspector produces:


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    256000039  Mac OS X HFS+
 3      256262184    342715308  Basic Data
 4      342715309    482369605  Basic Data
 5      482369606    488397134  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    256000039  af  Mac OS X HFS+
 3 *    256262184    342715308  07  NTFS/HPFS
 4      342715309    482369605  83  Linux

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 256262184:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 07  NTFS/HPFS, active

Partition at LBA 342715309:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 482369606:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap


thx for u help
ben

---

### Post by neurostu on 2008-08-22
Post in the mac forum... you will get more MAC people to read your post there... (they will know better then we do)

---

