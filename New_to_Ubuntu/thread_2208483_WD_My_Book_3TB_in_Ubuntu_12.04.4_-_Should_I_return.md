---
title: "WD My Book 3TB in Ubuntu 12.04.4 - Should I return it?"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by cbaykal on 2014-02-28
Hi all,

I have just bought a new "WD My Book Desktop Storage 3TB USB 3.0".
I need your immediate assistance to set it right for using it both in Windows 7-64bit and Ubuntu (12.04-32bit or higher).

Unfortunately, I searched about WD 3TB and ubuntu after I bought it - dumb move.
I have not opened it yet, just to save my right to return it back.

I have to say that I am not interested in the ecryption of data, but more interested in the readability/accessibility of data.
It can be in multiple partitions, if it would help me for safe use.

Should I reformat it first? with which utility/software? in which OS and how?.
or should I just return it and buy a 2TB seagate or some other brand?
 
Thanks a lot in advance
Manufacturer Product Code WDBFJK0030HBK-NESN

Note: I actually bought a Seagate 3TB previously and I am using it, but nowadays it doesnt work right on ubuntu and I want to backup my data to some other place. That is why I bought this. I do not want to deal with another external drive problem. It just has to work.

---

### Post by sandyd on 2014-02-28
see [http://ubuntuforums.org/showthread.php?t=1506476&p=9441162&viewfull=1#post9441162](http://ubuntuforums.org/showthread.php?t=1506476&p=9441162&viewfull=1#post9441162)

It doesnt seem to work without modifying it

---

### Post by Habitual on 2014-02-28
Although, I am **not** using Ubuntu or any of it's derivatives, I believe you have to get rid of the partition that came "on it" and create a new one using a filesystem supported by either OS.
That seems to be NTFS.

Mine didn't work either when I got it, even though it "read" as NTFS in gparted (but don't believe it)

---

### Post by cbaykal on 2014-03-01
Thanks for the replies
I guess I have to return it back.

---

### Post by Mark Phelps on 2014-03-01
I don't know if ALL the WD Passport drives come this way, but we get a LOT of complaints from folks that discovered that theirs came with solftware preloaded that requires booting into Windows to access the drive. If this is firmware built into the drive I/O interface, then there's no way around it.

Personally, I would avoid WD and look for some other brand that does not preload the drive with encryption software.

---

### Post by artie3 on 2014-03-05
I had the same issue with a WD 1 TB drive, I was stunned!! I'm not sure why they make such a crippled product. But, the fix is easy. 

Format the entire drive as EXT4, which will wipe out all the windows crap. You will have a USB drive without any software or backup utility programs. But, you simply drag and drop to store or retrieve files. Mine works like a champ!!

After I realized the problem was in the software, I bought a used WD 1 TB drive on ebay for $12. It was new, and the owner sold it 'as is' because it didn't work. I reformatted it and now I have a second 1TB drive-so I use it to backup my backups!! If you have time to spare, set up a custom search on ebay and they'll notify you if 'as is' appears in an auction for a WD drive.

Enjoy.

Artie

---

### Post by Habitual on 2014-03-05
> **artie3 said:**
> Format the entire drive as EXT4, which will wipe out all the windows crapEXT4 is no go for his OP said
> **cbaykal said:**
> I need your immediate assistance to set it right for using it both in Windows 7-64bit and Ubuntu (12.04-32bit or higher).
NTFS...

Delete the partition on the unit using gparted and re-create a new NTFS partition.

See 
[http://askubuntu.com/questions/346562/how-to-create-ntfs-partition-in-ubuntu-13-04](http://askubuntu.com/questions/346562/how-to-create-ntfs-partition-in-ubuntu-13-04)
[https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions](https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions)

---

### Post by DogMatix on 2014-03-05
I have a WD MyBook which is used on both Linux and Windows. I re-formatted it as NTFS and its been reliable ever since.

---

### Post by nunecas123 on 2014-03-06
Do what the others said. FAT is not that good for backups, but at least it is compatible with a lot of system. It's something you should consider too. ;)

---

