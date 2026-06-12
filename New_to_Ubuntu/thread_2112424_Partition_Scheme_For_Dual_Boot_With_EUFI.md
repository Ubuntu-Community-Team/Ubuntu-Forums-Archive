---
title: "Partition Scheme For Dual Boot With EUFI"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by spikoley on 2013-02-04
What would be the best partition scheme for a dual boot of Windows 7 and Ubuntu 12.10?  I haven't worked with UEFI before.  Do I need any special partitions?  The drive is 500Gb.

---

### Post by spikoley on 2013-02-04
I forgot to mention that this is a new install with a Windows 7 CD.  Do I need the ESP partion or any of the others in the attachment?

---

### Post by oldfred on 2013-02-04
Most Windows 7 installs were BIOS, are you installing in UEFI mode?

Both Ubuntu & Windows have to have install media DVD/Flash booted in UEFI mode to install in UEFI mode.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)
            You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
With UEFI, both Windows & Ubuntu will use the same efi partition which should be first on drive and 200MB or so.

If you just let Windows do its default install, it will use entire drive. So then use Windows Disk Tools to resize Windows an reboot so it can run chkdsk and make repairs. 

Then you can install Ubuntu into the unallocated space. Best to also create a shared NTFS data partition for any data you may want in both systems.
Default install is just / (root) and swap.

With gpt partitioning which is used with UEFI all partitions are primary so there is no issue with additional partitions other than how much space you want to allocate.

Preinstalled Windows 8, so you would not have Vedor recovery nor vendor tools.
       Asus N56VJ-SH71-CD - shows partitions after install
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

---

### Post by NikTh on 2013-02-04
Maybe a separate /boot partition here, would be a good idea ? 

I'm not sure.. just saying.

---

