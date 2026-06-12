---
title: "windows partition file problem"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by marianbv on 2013-01-07
so i installed xbuntu.
at option, i chosed : replace windows. got a warning that it will delete all my windows files documents and so.
i presume that means for the windows partition. (c)
sadly, it deleted all my other partition on my hdd  (d and e).

basically, now xubuntu stays on a fat 1 terra drive. no partition.
there is any way to get partition/files back ? (d and e ?)
any way. bootable cd/drive/utility's.
thanks.

---

### Post by Impavidus on 2013-01-07
Don't use the hard drive. Anything you write on that drive may corrupt data that's still present. There are recovery utilities available, which may recover quite a lot. Wait for others to give you more specific advice.

That is, switch off the machine and wait until you've a recovery cd ready and know what you're doing.

---

### Post by oldfred on 2013-01-07
You can try testdisk, but there are no guarantees that you can get everything back. A typical Linux install may put files any where on drive. 
The only way to be sure where or what partitions are used during an install is to use Something else or manual install. 

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

    
       Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

    
If testdisk does not work, then photorec may find files, but on a 1TB drive may take days to scan for each type of file.

---

### Post by marianbv on 2013-01-07
that machine is powered off.

right now i'm doing the same steps in a vmware on another machine.

partition c/d/e, c with windows, and after that install xubuntu over and see how i can recover pArtitions/fileS before doing that on my main machine.

will try testdisk and photorec.
if anyone have another sugestions please post it.

---

### Post by fantab on 2013-01-07
In future REMEMBER to back up all your important DATA before you do anything with your HDD or its partitions. Be patient and follow** oldfred's** post.

Good Luck...

---

### Post by marianbv on 2013-01-07
> **fantab said:**
> In future REMEMBER to back up all your important DATA before you do anything with your HDD or its partitions. Be patient and follow** oldfred's** post.

Good Luck...

thanks.
well, it may help if a bit cleared message could apear.
like instead on your are losing your windows files/folders (which usually means the os partition), something like  "partition table will be deleted, i will erase the whole drive.".

currently testdisk is running on a 60 gb drive, is a 40%, and it founded the first partition.
i made a 30 gb c drive, 15 gb d drive, 15 gb e drive.
will update how is going.
the other machine is at my workplace, so only tomorrow will be the "real" deal. judging by how is going on this 60 gb drive, it will take some hours to get the work done on the 1 terra drive.

---

### Post by marianbv on 2013-01-08
managed to recover all 3 partitions, the windows one is damaged, but that one was not important anyway. (i presume i could have recovered files with photorec, but i had no interest in that)

thanks all for help, especially oldfred.

---

### Post by oldfred on 2013-01-08
Glad you were able to resolve it.

Part of the issue is that in the Linux world we know a drive as a physical device and partitions as subdivisions on a drive. So if we say we are erasing the drive we mean the entire drive. But Windows also  uses drive for partitions - c: & d: drive may be either two partitions on one drive or two physical drives. So the translation of erase drive is not always clear to a Windows user. But if you try to get a developer to clarify that it is usually difficult.

---

