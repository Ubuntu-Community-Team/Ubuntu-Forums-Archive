---
title: "partition problem"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by house7777777 on 2014-01-06
i have a computer with windows 64 bit ultimate.
i went to install Ubuntu with a usb drive from the bios menu
normaly in the installation there is 3 options 
 1 install over every thing
2 install with windows 
3 or partion table 
but
i only had options 1 and 3
so i went into the partion table and found 1tb of un allocated space
since my hard drive is 1 tb i took 100 gb of space and made a partition for ubuntu
then i went to proceed it said i needed a another partition so of about 30mbs or so i created it
then a message came up.saying something about a boot loader grub i think, so i continued then the installation process stoped
and an error came up

now i can't access my windows or linux i think i paritioned the boot loader or something :):mad:


i want some files from windows that i forgot to back up . any ideas on how i recover the files......  i tryed using stellar phoenix windows data recovery and easeus data recovery professional with it pluged into the computer by usb they did'nt work ... any ideas plz.:(:(:(............

---

### Post by oldfred on 2014-01-06
If those tools do not see Windows then I do not know if this may help or not.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by ghicksrn on 2014-01-06
Do you have a startup disc for Windows? You may be able to go to another computer and create a Windows start or repair disc. Google has found that for me before from the Microsoft site. Then I was able to repair my Windows OS. I don't like Windows so much, but still need it occasionally. I tend to use Microsoft to repair Windows whether I like it or not. 

The best option if you just want your files and not to repair the Windows OS, is to just use the Ubuntu live disc and mount your Windows partition and then transfer the files to USB or disc.

---

### Post by house7777777 on 2014-01-07
[http://paste.ubuntu.com/6708412 /]("http://paste.ubuntu.com/6708412/")    (boot info)

---

### Post by house7777777 on 2014-01-07
[http://paste.ubuntu.com/6708531/](http://paste.ubuntu.com/6708531/)    (boot repair)

---

### Post by oldfred on 2014-01-07
There is no Windows install.
You have a very large Linux partition with Ubuntu, and a small efi partition.
You also have a Windows boot loader in the MBR for BIOS boot of Windows but it will not work.

You also show Windows efi boot files in efi partition. So was Windows originally UEFI booting or BIOS booting? It looks like it was UEFI or else you would not have had Windows efi files.
But Window requires several other partitions to work correctly and none of those are shown.
Normally the efi partition is first or often second with a Windows recovery partition first. And Windows has to have it system reserved unformatted space.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

With a large drive it is better for both Windows & Ubuntu to have smaller system files and have data in larger data partition(s). If data is NTFS then you can use it in both systems.


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another, also should be first or second partition or near front of drive)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by house7777777 on 2014-01-07
ì am confused me being a absolute beginner and all, your telling me that i can't get my windows files back because i messed it up to much (partitioned the space where windows 7 was)
.so how do i get them back (my files)? what information do you  need to know to find out can you? is this a pointless exercise where I'm trying to a needle in a heroin addict ?

---

### Post by oldfred on 2014-01-07
You cannot recover a bootable Windows.
But if you have vital data that you did not back up, there are several recovery possiblities. They may take a lot of time and some for NTFS are not free.

I would first try testdisk to see if it can see old partition table and NTFS partition. Deeper search may show files with file names if that part of drive did not get overwritten. It that does not work then photorec which is free, but many say the Windows NTFS specific tools work better but may not be free.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Tools that scan drive looking for anything that looks like a file take very long times especially for a large drive like yours, plus you have to have another drive large enough to recover you data. 
      
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)


 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)

---

### Post by house7777777 on 2014-01-07
when i try to recover with test disk it goes into a loop after a number of files 
. i have been able to get some from my windows partition but not the ones i want is there any reason it would go into a loop?

---

### Post by oldfred on 2014-01-08
Not heard of that issue with testdisk. But once some data gets written over it just may not be able to proceed beyond some point as that data is then corrupt.

---

### Post by house7777777 on 2014-01-09
i'v managed to fix the loop problem when it loops i stop the programe and turn it on and start where i left off and it works so far its been on for about 17hours with about 40 hours to go.

---

### Post by oldfred on 2014-01-09
I hope testdisk is finding files. As then you get full file names. If not it is another 40 or 50 hours to run photorec and you only get file extensions and have to spend many hours resolving which file is which. 
With photorec it also recovered all the deleted versions of my text files and I had to do a lot of file compares to see if I could find the more current version.

---

### Post by house7777777 on 2014-01-10
i think after that a don't have what i want so I'm closing this

---

