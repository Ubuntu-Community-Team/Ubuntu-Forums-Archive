---
title: "Windows not booting after Ubuntu 16.04 installation"
date: 2018-02-05
forum: New to Ubuntu
---

### Post by aepvi123 on 2018-02-05
Hello,

I have installed Ubuntu 16.04 alongside Windows 10 (I am using NVIDIA GeForce GTX 1080i graphics Card). After installation of Ubuntu, I am unable to boot to Windows 10 anymore.

Reading few solutions from your forums, I updated grub and performed boot repair as well. But still the problem is not solved.

Below, is the link for the BootInfoScript :

[https://paste.ubuntu.com/26524601/](https://paste.ubuntu.com/26524601/)

Request your help to solve this issue.

-aepvi

---

### Post by oldfred on 2018-02-05
Was Windows 10 and upgrade from Windows 7, and in BIOS boot mode?

You have converted drive to gpt partitioning and Windows only boots in UEFI boot mode from gpt partitioned drives.

Logical Disk Manager metadata partition (Windows)
[https://en.wikipedia.org/wiki/Logical_Disk_Manager](https://en.wikipedia.org/wiki/Logical_Disk_Manager)

That indicates you converted MBR drive to dynamic which is proprietary to Windows.

---

### Post by aepvi123 on 2018-02-05
Thanks for the reply.

Windows 10 was not upgraded from Windows 7. It was newly installed. (But, does that matter?)

What could be a possible solution?

---

### Post by oldfred on 2018-02-05
You still need fast start up off.
But since you converted drive to gpt, Windows only boots in UEFI boot mode.
Or you may need to start over with one or the other installs, perhaps both. You may be able to convert gpt drive back to MBR, reinstall grub2 to allow it to boot in BIOS mode and run major Windows repairs from your Windows repair/recovery disk or perhaps install disk. That process may be more difficult that just starting over. But first decide if you want UEFI or BIOS.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 

BIOS/MBR is now 35 years old as it is from the original IBM PC released in the early 1980's. While many updates to try to keep it working it still is an old design.
UEFI is now about 5 years old on PCs as Windows 8 required it for all new systems from vendor, but it could be manually installed in old BIOS/MBR mode.

Best to have all systems in one boot mode or the other, with some advantages to the newer UEFI for newer systems.
And Windows only boots with BIOS from MBR and only from gpt with UEFI. Ubuntu can boot from newer gpt with BIOS or UEFI if correct supporting partitions are on drives.

How you boot install media, UEFI or BIOS is then how it installs. Then system has to be set to boot in that mode from UEFI/BIOS.

For more info on UEFI see link in my signature (it is a lot of info).

---

### Post by aepvi123 on 2018-02-07
Un-installing Ubuntu could solve the problem? If so, could you please tell me how?

Because I need to access Windows urgently, and can't afford to format it either.
[U]
[B]Additional Info:

[/B][/U]1. Windows 10 was running in 'UEFI and Legacy Mode', before I installed Ubuntu 16.04. (If my understanding is correct, Legacy Mode = BIOS).
2. I tried installing Ubuntu in 'UEFI and Legacy Mode' only first, but I kept getting this error : [I]&#8220;Executing 'grub-install /dev/nvme0n1' failed.&#8221;
[/I]Therefore, I tried installing Ubuntu in 'UEFI' Mode and it worked.
3. Also, please note that I am using NVIDIA GeForce GTX 1080 Ti graphics Card, because of which I had additional problems during Ubuntu installation (had to set nomodeset in Grub2 every time I booted from the Ubuntu bootable USB)

---

### Post by yancek on 2018-02-07
The link below is the Ubuntu documentation site on dual booting windows/Ubuntu EFI.  Lots of additional information if you scroll down the page including convefrting to Legacy mode or converting to UEFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-02-07
You installed Ubuntu in UEFI mode and converted drive to gpt.
But a BIOS install of Windows only boots from MBR partitioned drive.

Because you show the Logical Disk Manager, you also converted your MBR partitioning to Windows proprietary dynamic partitions which does not work with Linux.
That is probably why the Ubuntu installer let you convert to gpt, normally it issues a warning about a BIOS/MBR install and you have to then force the overwrite.

Not sure with dynamic partitions and converting back to MBR what is required.
Your Windows may not be repairable, and then you need to restore from your backup.

You can use Windows tools or Linux tools to convert back to MBR, but only Windows tools will also see and perhaps correct the dynamic partitions.

I might try these Windows repair tools.
       EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[URL="http://www.partitionwizard.com/free-partition-manager.html"]http://www.partitionwizard.com/free-partition-manager.html
[/URL][URL="http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html"]http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html
[/URL] 
[URL="http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html"]http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html
[/URL]
[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)

From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from) 
    [URL="http://www.partitionwizard.com/free-partition-manager.html"]
[/URL]

---

