---
title: "test disk"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by aakash_scsa_hellyeah on 2011-11-04
```

TestDisk 6.12

Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121602

The harddisk <1000 GB / 931 gib> seems too small! << 3620 GB / 3371 GiB>
Check the harddisk size : HD jumpers settings, BIOS detection....

The following partition can't be recovered :
        Partition              start                   End       Size in sectors
> HPFS - NTFS         224110  72  41  440149 142  5  3470670910

```

hello..
I am using windows 7 and accidently formatted my 585 Gb partition on 1000 Gb samsung hard drive, i tried using testdisk to recover my data, after perforning 'DEEPER SEARCH' task, testdisk ends up with message given above.. Please someone help, I need the complete data stored on that partition along with the same structure, I have heard abt some other programs that facilitates to recover data by selecting type of file to be recovered and leave rest of data unrecovered but I cannot compromise by giving any of those files..
PLEASE SOMEONE HELP..

---

### Post by Mark Phelps on 2011-11-04
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by mikechant on 2011-11-04
If your data is really valuable you should probably use a professional data recovery service (if Mark's suggestion does not help).

And please, please, back up your data in future (I assume you you have no backups?).

---

