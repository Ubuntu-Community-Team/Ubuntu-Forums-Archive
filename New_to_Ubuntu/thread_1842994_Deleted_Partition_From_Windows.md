---
title: "Deleted Partition From Windows"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by EpikRageQuit on 2011-09-12
As the title says. I plan on giving my laptop to my  parents as I now have a new one. I have never disposed of Linux before so, I assumed I could just go in and delete the partition carrying the linux half and things would roll on as they were before my dual boot had started. This is not the case. I restarted my laptop to ascreen, saying "error: no such partition" followed by "grubrescue>" on the following line


ANY AND ALL HELP/ADVICE IS GREATLY APPRECIATED

---

### Post by oldfred on 2011-09-12
You still have grub2's boot loader in the MBR trying to boot from the partition you just deleted.

You need to restore the Windows boot loader to the MBR.

From Windows command line it is fixMBR in XP, or bootrec.exe fixMBR from Vista or 7.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  (have to run /r or /f as separate entries) rerun until no errors

If you do not have a Windows repairCD you should make one. You can do many things from any version of Windows to repair other versions. I used a Windows 7 repairCd to run chkdsk on my XP install.


Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Basher101 on 2011-09-12
ya beat me to it...but hey, at least more ppl are trying to help :3

---

### Post by collisionystm on 2011-09-12
Once you restore the Windows 7 MBR, use the windows 7 setup cd to expand your partition again. Unless you want to have 2 partitions.

---

### Post by EpikRageQuit on 2011-09-12
Thanks guys, this helps a lot. I guess I'm making a repair usb with my new laptop :)I'll be sure to post back as I run through!

---

### Post by EpikRageQuit on 2011-09-12
So i ran the commands. Am I all done if it says 0 kb in bad sectors? Is that what you meant by rerun until there is no errors?

---

### Post by EpikRageQuit on 2011-09-12
Everything Worked out. Thanks guys :D

---

