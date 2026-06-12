---
title: "[SOLVED] Have I lost all my files on my external drive?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by RamR on 2008-10-20
I was working with files from my external drive and I accidentally deleted a few files.  I tried to use testdisk to recover the files.  Now I can't access any files or partitions from the external drive.

I'm panicking now.  Many important files on the drive.  

Please help.

---

### Post by RamR on 2008-10-20
Now I'm really worried.  I used gparted to look at the details of the hard drive and it looks like I may have re-formated by accident.  It's says that the drive is unallocated.

Is there any way to recover the data that if that is the case?

---

### Post by az on 2008-10-20
What did you do with testdisk?  Do you mean photorec?

Testdisk plays around with your partition table.  Photorec carves out files from a partition without using the filesystem; that's useful when you have deleted files or a corrupt partition.

Also, what filesystem was on the drive you deleted the files from?

---

### Post by RamR on 2008-10-20
Well, I thought I was recovering lost files but I obviously wasn't.  The file system was ext2/ext3 (if I remember correctly).

Please let me know if there is a possibility to recover the files>

---

### Post by caljohnsmith on 2008-10-20
Sounds like you accidentally messed up your external HDD's partition table when you tried to use testdisk. As az pointed out, testdisk is for fixing the partition table, while photorec is for recovering files; so photorec would be what you want. 

Probably you can still recover your partition table OK with testdisk if you haven't done anything else yet. So start testdisk again:
```
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partition. Also please let me know what your original partition structure looked like, i.e. how many partitions and what they were for. Let me know how it goes. :)

---

### Post by RamR on 2008-10-20
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT32 LBA                0   1  1  4902 254 63   78766632 [BACKUP]













*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

---

### Post by RamR on 2008-10-20
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63

The harddisk (250 GB / 232 GiB) seems too small! (< 291 GB / 271 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
D HPFS - NTFS          27850 254 63 35499 253 61  122881121










[ Continue ]

NTFS, 62 GB / 58 GiB

---

### Post by RamR on 2008-10-20
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63
     Partition               Start        End    Size in sectors
* FAT32 LBA                0   1  1  4902 254 63   78766632 [BACKUP]
L HPFS - NTFS           4903   1  1 15101 254 63  163846872 [My Pictures]
L HPFS - NTFS          15102   1  1 20201 254 63   81931437 [My Music]
L HPFS - NTFS          20202   1  1 27850 254 63  122881122 [My Videos]
L HPFS - NTFS          27851   1  1 30400 254 63   40965687 [Misc]








Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 40 GB / 37 GiB

---

### Post by RamR on 2008-10-20
That last post shows my partitions.  The first one (backup) is still ok and really is unimportant.  The other 4 are the ones that I need to recover.  My Pictures, My Music, My Videos and Misc.

Hopefully that's a good sign.

I haven't done anything from this point.  Waiting for help.  I'm afraid to mess it up further.

---

### Post by caljohnsmith on 2008-10-20
Unfortunately you caught me at the wrong moment because I have to go right now and won't be back until tomorrow morning, so I can help you then if you would still like my help recovering your partition table and then your files. I would highly recommend though not doing anything drastic in the meantime, or at least unless someone else who has experience with testdisk can guide you, as I think you have a good chance of getting your partitions and files back. Sorry I have to run, and try to just relax about it as much as you can. :)

---

### Post by RamR on 2008-10-20
Cheers.

I am at your mercy.  Will wait for further instructions or someone else who has knowledge of how to help me.

---

### Post by RamR on 2008-10-21
Hoping to hear from you as soon as you get the chance.

---

### Post by caljohnsmith on 2008-10-21
Hi RamR, it looks like since all the partitions in your post #8 don't overlap, it is safe to write that partition table to your HDD. Go ahead and get back to that point, make sure everything looks exactly the same as from your post #8, press "enter" to proceed, and after that there should be an option to write that partition table to your HDD (I don't remember the exact details, but it should be fairly self-explanatory). When you are done with that, reboot, and then please post the output of:
```
sudo fdisk -lu
```
And also pull up a file browser from your Ubuntu desktop "Places" menu, and see if you can browse any partitions on that HDD. Hopefully it will work. :)

---

### Post by RamR on 2008-10-21
Hi,

I'm at work now.  I won't be able to have a go at what you have said for 7 hours.  I am very anxious to see if it works.  I will reply as soon as I make the attempt.

In the meantime, if there is anything else that comes to your mind that might be helpful please let me know.  I will check this thread before proceeding once I get home.

Will you be around this afternoon/evening?

Also, when I write the partition table to the HDD am I supposed to write to the same place that it was before?  Or should I be writing to another drive?

Thanks again

---

### Post by caljohnsmith on 2008-10-21
You should go ahead and write the partition table to the same HDD where you are trying to recover your partitions, and actually I don't think testdisk gives you any other choice. :) If you want a little reassurance, I think it is highly likely that the new partition table should work just fine since your partition structure was so clear; it looks like that you fortunately haven't done alot (if any) repartitioning of that drive, otherwise testdisk usually finds old deleted partitions too and it gets complicated. 

That should hopefully at least get your partitions back, but recovering those deleted files is unfortunately a whole different matter. Since those are NTFS partitions, I would first recommend trying something like the free "[PC Inspector File Recovery]("http://www.pcinspector.de/download_all.htm?language=1")" or some other Windows recovery program since your partitions are NTFS (I assume you have Windows?). If that doesn't work, you can use "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")", but the problem with photorec is that it sometimes works too well: by default it recovers every single file it can find, so you'll need a large drive to save all its files too. After that it can take a long time sifting through all the recovered files for what you want. 

Good luck and let me know how it goes. :)

---

### Post by RamR on 2008-10-21
I do have windows.  Your words of encouragement are definitely reassuring.  I will let you know how it goes.

---

### Post by RamR on 2008-10-21
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f038f03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    18426554     9213246    7  HPFS/NTFS
/dev/sda2        60259815    76678244     8209215   83  Linux
/dev/sda3        76678245    78140159      730957+   5  Extended
/dev/sda4        18426555    60259814    20916630   83  Linux
/dev/sda5        76678308    78140159      730926   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x962c3f14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    78766694    39383316    c  W95 FAT32 (LBA)
/dev/sdb2        78766695   488392064   204812685    f  W95 Ext'd (LBA)
/dev/sdb5        78766758   242613629    81923436    7  HPFS/NTFS
/dev/sdb6       242613693   324545129    40965718+   7  HPFS/NTFS
/dev/sdb7       324545193   447426314    61440561    7  HPFS/NTFS
/dev/sdb8       447426378   488392064    20482843+   7  HPFS/NTFS

---

### Post by RamR on 2008-10-21
Writing the partitions back on the HDD has worked and all the files seem to be there as well.

Now, is it possible to recover the files that I originally was trying to get back?  Should I try to use photorec?

Thanks so much for all your help caljohnsmith.  You're a life saver.

---

### Post by caljohnsmith on 2008-10-21
That's great news testdisk worked to get your partitions back, RamR. :) So about using photorec, by using the "File Opts" menu, you can exclude those files with file extensions that you don't care about recovering. That's important because photorec will recover ALOT of files. But I would give PC Inspector a try first, then photorec. Good luck and let me know how it goes. :)

---

### Post by RamR on 2008-10-21
Well, I downloaded the PC Inspector in Windows but for some reason I can't install the program.  Then I tried photorec and can't get it to recover any files at all.

---

### Post by caljohnsmith on 2008-10-21
If you are using photorec correctly, it should recover lots of files and take a long time to scan (hour or more). Did you run it with:
```
sudo photorec

```
And when you do the "search" you have to pick the partition to search, and after that I think you have to tell it where to put the recovered files.

---

### Post by RamR on 2008-10-21
OK, I have a pile of files that were recovered.  But I can't open the folders, they are locked.

---

### Post by caljohnsmith on 2008-10-21
OK, first navigate to the directory where all the recovered files are, and then do:
```
sudo chown <user>:<user> -R *
```
And replace <user> with your user name.

CAUTION: Make sure you are in the recovered files directory when you run that command, because it recursively changes ownership of everything in the current directory and everything below it.

---

### Post by RamR on 2008-10-21
When I do this I get "Permission denied" for each of the folders that were created in recovery.

---

### Post by caljohnsmith on 2008-10-21
My mistake, I corrected my previous post. :)

---

### Post by RamR on 2008-10-21
Cheers... that worked... now I have a lot of sifting through files.  Just one last question, has the recovery process actually copied over all pdf files that were in that partition or just the deleted ones?  If so, is it true that existing files were simply copied and not moved?  If this is the case then it should simply be a matter of finding the handful of files I deleted yesterday right?

---

### Post by caljohnsmith on 2008-10-21
I'm not positive, but I believe photorec copies everything it can find when it scours the disk sector-by-sector, so that would mean existing files as well as deleted files. And it just copies them, it doesn't move them. 

And in case this helps you, if you are looking for pdf files through all those directories, you could use:
```
find . -iname "*.pdf" | tee ~/Desktop/pdf_files.txt
```
And run that command from the top directory where all the files are. It will make a "pdf_files.txt" file on your desktop that has the path to all the pdf files it finds. Let me know how it goes.

---

### Post by RamR on 2008-10-21
Thanks a lot for everything... Now I have a fair bit few files to weed through.  Everything is recovered though and I have learned a lot in the process.

---

### Post by bobpur on 2008-10-21
After all of the effort expended to recover those files you may want to consider some form of backup. Maybe, putting everything on cd's, dvd's or an external drive.

Oops! That was an external drive that you had problems with, wasn't it? Well, cd's or dvd's then. :) Sorry 'bout that! It's been a long day.

---

