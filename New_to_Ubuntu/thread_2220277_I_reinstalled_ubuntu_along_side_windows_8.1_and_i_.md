---
title: "I reinstalled ubuntu along side windows 8.1 and i lost all my data ..!! Help pls"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by bruk2 on 2014-04-27
Sup fellas ..  i reinstalled ubuntu 14.04 on my Aspire E1-571 pc pre installed windows 8 but upgraded to 8.1. the reason i reinstalled ubuntu was because i couldn't boot in to it after my first succefull installation. i selected 'reinstalle ubuntu' option instead of 'something new' and it wiped off all my documents from the pc and my windows too.  i didn't back up any of my data. right now there is no bootable file when i boot in UEFI bios mood . it can't even boot from USB key being in UEFI biso mood ..it dispalys 'there is no bootable device' . but when i chose  'legacy' bios option it can boot in to ubuntu 14.04. guys i really need your help ASAP ..how can i recover my data being on ubuntu 14.04 ?? how can i install back windows 8 ??  ..

---

### Post by oldfred on 2014-04-28
Stop trying to write to hard drive, if you want to attempt to extract any data. But at this point you cannot recover a bootable Windows and may only be able to get some data back as some was overwritten. And the process is long and tedious. (I have done it with photorec). Always best to have good backups before any major system change.

You are not the first with this issue, see first paragraph in link in my signature.

You can try using photorec. It scans drive for anything that looks like a file. You need space on another drive to recover data to. And it does not recover full file name just extension.

Some with NTFS suggest this instead:
 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

      
 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)

You can contact vendor and see if they offer recover set of DVDs for your system. Some do and only charge a nominal shipping charge. One user bought from a local store and they still had same model for sale and tech made recovery set of DVDs. Good customer service but not many stores will do that.
Otherwise you have to purchase a new full install of Windows.

      
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)

---

