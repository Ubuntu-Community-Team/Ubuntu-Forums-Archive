---
title: "Ubuntu will not boot after clean install and restart"
date: 2015-08-29
forum: New to Ubuntu
---

### Post by james165 on 2015-08-29
Hey,

I am very new to Ubuntu. I have installed it a few times on my computer and had no issue. Now that I am going to school for IT, it doesn't want to work of course. I installed it along side windows 7 and did a split partition. I did not change any of the recommended install setting, and at the end it requires that you restart your computer. After the restart I can't find it anywhere in the boot manager, or anywhere that I know of. I tried putting my disk in that I used to install it and it asks me to try Ubuntu or install Ubuntu. It is an ISO torrent downloaded from the Ubuntu site. Thank you in advance for the help.:D

---

### Post by oldfred on 2015-08-29
What brand/model System?
Is system newer UEFI or older BIOS?
And did you install in the same mode as Windows?
Windows 7 is usually BIOS with MBR(msdos) partitioning, but a few were UEFI.

Post this, you can install into Ubuntu live installer.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by james165 on 2015-08-29
Its a cyberpowerpc/ windows 7 ultimate. How do I tell if it is UEFI or older BIOS. I do remember seeing UEFI in my boot manager. Windows 7 was already installed. I installed ubuntu through the boot manager off of a DvD. I am doing those other steps. I will get back to you soon.

---

### Post by james165 on 2015-08-29
Another problem has arisen. When go to Try Ubuntu the internet does not connect to my computer through my LAN cable and I have no wireless capabilities with this tower. Is there any other way I can get the boot info without internet?

---

### Post by james165 on 2015-08-29
I somehow got internet on Ubuntu here is the boot-info [http://paste.ubuntu.com/12225795/](http://paste.ubuntu.com/12225795/)

---

### Post by oldfred on 2015-08-29
You really need Internet, and normally wired Internet works using DHCP unless you have your network configured some other way.
It does create a file, and you can copy file to a flash drive, or if you enabled persistence with the installer flash drive, you have some space to store a few things on the installer flash drive.

       [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
            [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
    
Then from Windows you can copy file either to pastebin, or post it here. Sometimes it is too long to post. And you need to use code tags to preserve formatting with # icon in forum's advanced editor. You can attach files also in advanced editor with paperclip icon.

---

### Post by yancek on 2015-08-29
There is not EFI partition showing in the boot repair output but you do have windows code in the master boot record and a default windows system can't boot any Linux.  You must have changed the default location to install the Grub bootloader otherwise it would be on the MBR.  What you would need to do is to install Grub to the mbr.  Look at the bottom of the boot repair output.  It has a Suggested Repair which would do just that.

---

### Post by james165 on 2015-08-29
It seems to be working now. It finds the partition automatically on startup. Thank you very much Oldfred and Yancek!

---

### Post by oldfred on 2015-08-29
Ubuntu may be working but Windows will not. You somehow are using a Windows boot loader in MBR and grub in the Windows partition sda2. It may be booting since boot files are in sda1, but you have a invalid sda2 NTFS. You will not be able to run chkdsk or make repairs to it.
Restore grub to MBR and repair Windows partition boot sector.

```
    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda2 
                       and looks at sector 1849450216 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

```

Windows has to have its own partition boot sector with Windows code in it not grub. And Windows will not even recognize that as a NTFS partition even though partition table say NTFS. But NTFS keeps a backup and testdisk can restore from the backup if backup valid.

       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by james165 on 2015-08-30
Hey sorry about the late reply OldFred. I am not sure where you are getting that from but I ran testdisk and all the partitions say they are good and I can also boot up my windows instead of my Ubuntu and it appears to be working as well. If it shouldn't be working and it is, is there something else I should be worried about? Although I did notice when I booted windows it wasn't from the windows boot manager, it was from the Ubuntu "boot manager" (Ill call it that for lack of knowledge of what it is called). That seems a little strange because I am pretty sure that when I had it installed last time windows would boot normally and I had to boot Ubuntu from the windows boot manager.

---

### Post by oldfred on 2015-08-30
Grub should never be installed to the partition boot sector (PBR) of a NTFS partition.
That seems to be then how you are booting.

Windows boots by reading MBR, and finding partition with boot flag and jumping to that partition to find more boot code in PBR. But you are finding grub in PBR and grub does not use boot flag, but  looks for Windows boot files.

       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

Grub2 also says it should not be installed to a PBR. It is much larger than grub legacy and does not really fit. They have to convert to blocklists or hard coded addresses to find the rest of grub in Ubuntu. And if a grub file is moved by an update, then it will break as address is wrong. Or it is fragile. Best to always have both Ubuntu live installer & Windows repair flash drive handy the way you have installed.

Testdisk may say it is valid as grub in a PBR can be valid, it just is not valid for NTFS. If backup is valid that should be recovered. But once you do that, you will not be able to boot until you install grub to MBR of drive or to sda, not PBR of partition like sda1, sda2 etc.

---

### Post by james165 on 2015-08-30
If I do not fix this is there major reprocutions? I am trying to read the article but I am just too new for it to make sense and feel confident to fix it without causing anymore problems. Will future problems arise with Ubuntu if I don't fix it? Is it worth it to try and fix it with my primitive skills or should I wait until I am bit more familiar with this system?

---

### Post by oldfred on 2015-08-30
The issue will probably be first with Windows. Any abnormal shut-down or partition size change requires running chkdsk. And it probably will not even recognize your main install as NTFS.

Or a major update to grub will move a file & grub in a partition boot sector will then not work.

If it is working you can use it. But you must have both a Working live Ubuntu installer of your current version of Ubuntu and a currant version of Windows repair CD or flash drive. You can make the Windows repair disk from your Windows. You cannot fix most Windows issues from Ubuntu, so you must have Windows repair tools.

---

