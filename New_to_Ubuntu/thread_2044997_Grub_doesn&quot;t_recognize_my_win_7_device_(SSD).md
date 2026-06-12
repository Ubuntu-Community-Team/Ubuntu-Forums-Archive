---
title: "Grub doesn&quot;t recognize my win 7 device (SSD)"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by sportsfreund20 on 2012-08-20
Hello Linux-experts,

I have a problem with grub, the bootmanager. At first I installed Windows 7 on my  400 GB HDD  without problems. After that I installed on my  120GB SSD Ubuntu Linux 12.04 from a CD.

So my partitions look like that: 
/dev/sbd1   =  ntfs  = 119.24 GB  (Used 28.26) 
/dev/sda1   =  ext4  = 368.63 GB  (Used 9.96GB)
/dev/sda2   = extended = 3.98 GB (Used -)
    /dev/sda5   = linux-swap  = 3.98 GB (Used -)

(see: [http://pastebin.ubuntu.com/1157608/](http://pastebin.ubuntu.com/1157608/) )

Unfortunately I can only boot ubuntu now.  Grub doesn't even show me a possibilty to choose between ubuntu and win 7. 

So I logged in to the bios-menue to boot from the SSD manually. 
-> it says "error unknown filesystem grub rescue".

Somebody from the irc chat for ubuntu told me, that according to the result.txt posted at [http://pastebin.ubuntu.com/1157608/](http://pastebin.ubuntu.com/1157608/), the grub bootmanager doesn't even recognize the SSD. So I should install another bootmanager called "refind boot manager" ([http://rodsbooks.com/refind/getting.html](http://rodsbooks.com/refind/getting.html)). 

Question: is it really necessary ? can't I repair the grub manager somehow, since i am the nearly the only one who has this problem?? 

thank you. for your help! 

sportsfreund20

---

### Post by oldfred on 2012-08-20
Did sda or another drive in sda exist when you installed Windows to sdb and was sda the boot drive in BIOS?

Windows normally installs in two partitions, a small 100MB boot/repair partition and the main install. Your main install in sdb1 is missing the two boot files that are normally in the 100MB boot partition. We have seen when installing Windows 7 to sdb, that it puts the boot partition on sda.

You can repair the Windows install in sdb1, if you have a Windows repairCD/USB or a full install DVD to run the Windows repairs. You need the boot flag on sdb1 and should set BIOS to boot sdb first so the Windows boot loader is in the MBR of sdb.

Boot files you are missing the two in red:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You can from Windows add the boot flag with set active on. Or use gparted or Disk Utility from Ubuntu to add boot flag to sdb.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

You also still have wubi installed in the Windows NTFS partion. When you use Windows to rebuild the BCD it will not add the wubi boot. If you want to still boot wubi then you have to manually add it to the BCD or you can just uninstall wubi if you are only now using your full install.

---

### Post by sportsfreund20 on 2012-08-21
Dear oldfred,

thank you for the quick and helpful reply. 

Unfortunately I am still a little confused. You say, I need to restore the 100MB boot partition in sbd1 with Win 7 Dvd. 

But how can I restore the boot partition, except with the command prompt ("BootRec.exe /fixMBR") and overwritting grub? 

Because I want to still use grub and linux.

best regards,

sportsfreund20


PS.: when I type in "BootRec.exe/FixBoot" it says, free translated: 
"On the Device is no recognized Filesystem. Please be sure, al necessary filesystem-drivers are loaded and the device is not damaged"

---

### Post by oldfred on 2012-08-21
It has to have boot flag as that is how Windows knows what partition to boot from or repair. And you need to make sure it is working on the Windows drive not the Ubuntu drive. Best to unplug the current sda, but I think setting BIOS to default to boot sdb works.

You want to make sdb a full Windows bootable system on its own. But then changing back to sda to boot in BIOS, you can boot Ubuntu and run sudo update-grub to add the Windows entry to the grub menu.

The repairs will not create a new 100MB Windows boot partition but will put the boot files into the main partition. Windows works fine that way. The reasons for the separate boot partition were so you could encrypt the main partition or if main has issues you may be able to at least get to the repair console. Without separate boot it does become important to have a repairCD or USB.

---

