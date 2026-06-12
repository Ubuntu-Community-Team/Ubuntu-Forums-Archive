---
title: "is the previous data all lost?"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by vishnu2 on 2014-02-09
i just installed ubuntu 13 on my pc by replacing windows 8.
is all the data stored in local disks C,D,E etc lost? because i can't find them anywhere in computer.
If it is. is there any way to gain it back?
sorry, i am just too new to ubuntu.

---

### Post by oldfred on 2014-02-09
If you said replace then entire drive was used. That also erased recovery and all partitions.

Stop using drive.
While some data has been overwritten, Ubuntu is relatively small. You will not recover a working system and not all data. But you can use tools that scan drive for anything that looks like a file and copies it to another drive. Takes a long time, new very large drives can take days, and you do not get full file names, just extensions. You have to manually rename, but photos & music have internal data that you can use to auto rename those.
This is a long process (I have done it on a smaller drive.)

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

First try testdisk & deeper search. It may find files that you can copy with full names.
      
 [URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL]Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Then you can use photorec which is part of testdisk.
      Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

Others have posted these as solutions using Windows.

 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - Getdataback often recommended
[http://www.runtime.org/data-recovery-products.htm](http://www.runtime.org/data-recovery-products.htm)
Also this one:
Then, I settled on Recuva, which isn't as pretty as the others, but it does the job well and is completely free. [URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

