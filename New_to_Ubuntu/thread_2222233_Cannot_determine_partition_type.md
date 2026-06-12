---
title: "Cannot determine partition type"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by Michael_Stein on 2014-05-05
Hi there,

I have been trying to learn sleuthkit forensic tools from [https://sysforensics.org/2012/02/](https://sysforensics.org/2012/02/). I downloaded some iso images to practice on from here: [http://www.dftt.org/test14/](http://www.dftt.org/test14/). It's called iso-dirtree.iso.

However when I try:

mmls /home/sansforensics/Desktop/Images/iso-dirtree.iso

it responds:

Cannot determine partition type.

What does it mean that it cannot determine the partition type? Also, how can I fix this?

I am VERY new to this, and it would really help if someone explained this to me.
Thanks in advance

---

### Post by pfeiffep on 2014-05-05
@ Michael Stein, Going out on a limb here ...... possibly the tool (with which I'm totally UNfamiliar) is looking for a boot device with  iso imaged burned onto it.

Make a bootable USB stick or bootable cd and point the tool there.  Burn the iso image do not extract.

---

### Post by Michael_Stein on 2014-05-05
Thank you for answering. But I'm not aquainted wtih the terminology that you are using. Could you please explain it in a way that's more understandable for beginners.

If there was a book called Forensics for Dummies, I would still need another book called Forensics for REAL Dummies.

---

### Post by pfeiffep on 2014-05-06
[COLOR=#000000]@Michael_Stein[/COLOR], I'm not familiar with mmls at all. I'll try to explain and provide references for additional clarification and research.

> [COLOR=#000000]mmls /home/sansforensics/Desktop/Images/iso-dirtree.iso[/COLOR]

[COLOR=#000000]it responds:[/COLOR]

[COLOR=#000000]Can not determine partition type.[/COLOR]

[COLOR=#000000]What does it mean that it cannot determine the partition type? Also, how can I fix this?[/COLOR]

mmls is expecting the contents of a volume _(_mmls displays the layout of the partitions in a volume system, which include partition tables and disk labels.) man page [here]("http://manpages.ubuntu.com/manpages/saucy/man1/mmls.1.html")

partition type refers to hard disc organization - think of a room full of file cabinets - read more [here]("http://www.aboutpartition.com/types-of-hard-drive-partitions/")

You might find this an interesting [read]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0CC8QFjAB&url=https%3A%2F%2Fdigital-forensics.sans.org%2Fcommunity%2Fpapers%2Fgcfa%2Fforensic-investigation-usb-flashdrive-image-cc-terminals_188&ei=bdRoU9nSBqjgsASAioKADQ&usg=AFQjCNFsI4nbVDxE0o9xHD0YNx2GF9sddg&bvm=bv.66111022,d.cWc")

Another site to [explore]("http://blog.creativeitp.com/posts-and-articles/linux/disk-analysis-with-fdisk-mmls-fsstat-and-fls/")

Possibly consider a moderator to move this thread to Ubuntu Specialized Support | Security Discussions

Forensics is not my strong point

---

### Post by Michael_Stein on 2014-05-06
Thank you. Will take a look at the various sites you have posted.

---

### Post by Danger_Monkey on 2014-05-07
Michael, a side note here.  If you are trying to get into the forensics field, you should get to know everything about the disks that you possibly can.  This means understanding how and why the data is written the way it is, and the methods that are used for erasure.  Get an old drive and take it apart.  And get used to taking copious notes, very detailed, about what you find.  If you go into LE or MIL forensics, you will need to be able to articulate exactly what you find.

---

### Post by Michael_Stein on 2014-05-07
Still trying to figure out why it doesn't have a valid partition table.

When I enter:

```
~$ df -h
```

I get:

```


Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       491G  6.2G  460G   2% /
udev            984M  4.0K  984M   1% /dev
tmpfs           200M  1.1M  199M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            998M  156K  997M   1% /run/shm
/dev/sdb1       493G   70M  467G   1% /cases
/dev/sr0        244M  244M     0 100% /media/1806_06052014

```

Now when I enter 

```
fdisk -l /dev/sr0
```

I get:

```
Disk /dev/sr0 doesn't contain a valid partition table
```

Why?

---

### Post by pfeiffep on 2014-05-07
I duplicated your commands with slightly different results. my /dev/sdi1 is a usb stick

```
pfeiffep@pete-HP:~$  df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       9.5G  4.6G  4.5G  51% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            5.9G   12K  5.9G   1% /dev
tmpfs           1.2G  1.3M  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            5.9G   52M  5.9G   1% /run/shm
none            100M   56K  100M   1% /run/user
/dev/sdb2       337G   75G  245G  24% /home
/dev/sdi1       3.7G  7.5M  3.4G   1% /media/pfeiffep/f41dba82-bb1c-4edf-ad9b-b4aa7faaefd0
pfeiffep@pete-HP:~$ fdisk -l /dev/sdi1
Cannot open /dev/sdi1
```

Using sudo ...
```
pfeiffep@pete-HP:~$ sudo fdisk -l /dev/sdi


Disk /dev/sdi: 4004 MB, 4004511744 bytes
218 heads, 51 sectors/track, 703 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000beea0


   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1            2048     7821311     3909632   83  Linux

```

---

