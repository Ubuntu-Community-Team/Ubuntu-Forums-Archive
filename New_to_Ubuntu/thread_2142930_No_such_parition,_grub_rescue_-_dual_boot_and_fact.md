---
title: "No such parition, grub rescue - dual boot and factory reset"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by ArjunGupta on 2013-05-07
Hi
                            I have a sony viao laptop with windows 7. I have no access to  Windows CD/DVD now. I dual booted with Ubuntu 13.04 and everything was  working fine. I then copied all my data from windows C drive to Ubuntu  and then formatted the C drive in windows (restored it to factory  settings). I know this was a big mistake I did. 
  Now as I said I have no windows cd/dvd but I have ubuntu live on a  flash drive. My biggest concern is to retrieve my data anyhow. 
  **"If I reinstall unbuntu, will I be able to recover my data as it is?"**
  I would be really thankful for immediate help on the problem. I have  searched and found a lot of solutions on internet but I don't want to  risk my data at all. 
  Looking forward to replies and solutions.
  Thank you

---

### Post by oldfred on 2013-05-07
A Windows restore makes the drive as it was when purchased. Many delete all data in Windows and convert partition table back to Windows and all other partitions are gone.

Since that was done there probably is no way to get all data back. You may be able to get some.

First try testdisk. It finds old partitions and deeper search may show files, it depends on which sectors of drive were overwritten. It that does not work, you may be able to use photorec which is part of testdisk. Photorec scans drive for anything that looks like a file. It only recovers files by extensions or type as filename table is gone. Some files like photos have internal data to allow renaming.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")

            Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

    
 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

