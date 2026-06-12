---
title: "ext2 disk drive (multiple partitions) not reeconised"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by julietteg on 2013-01-10
Hi

Hi

i had a Lacie drive but as it did not work anymore i have decided to instal linux in a virtual box and connect my drive via USB.

i can see it with Terminal (mac)

/dev/disk1

#: TYPE NAME SIZE IDENTIFIER

0: FDisk_partition_scheme *2.0 TB disk1

1: Linux 2.0 TB disk1s2

2: Linux_Swap 263.1 MB disk1s5

3: Linux 8.2 MB disk1s6

4: Linux 8.2 MB disk1s7

5: Linux 871.8 MB disk1s8

6: Linux 896.5 MB disk1s9

7: Linux 8.2 MB disk1s10

i can see the partition in my guest (linux) ubnuntu 12.10
(see attached)
but strangely, when i have a look into /dev, i cannot see them...

when mounting them, i have the following error :
wrong fs type, bad option, bad superblock

i typed this:
sudo fsck /dev
it seems to be a directory that connot be read ;-(

i cannot format my drive as i will like to keep the data!

any ideas?

juliette

---

### Post by cmoraes on 2013-01-10
Try 
 
sudo mount -t ext3 /dev/sdb2 /p2

---

### Post by julietteg on 2013-01-10
same error message

---

### Post by bab1 on 2013-01-10
> **julietteg said:**
> Hi

Hi

i had a Lacie drive but as it did not work anymore i have decided to instal linux in a virtual box and connect my drive via USB.

i can see it with Terminal (mac)

/dev/disk1

#: TYPE NAME SIZE IDENTIFIER

0: FDisk_partition_scheme *2.0 TB disk1

1: Linux 2.0 TB disk1s2

2: Linux_Swap 263.1 MB disk1s5

3: Linux 8.2 MB disk1s6

4: Linux 8.2 MB disk1s7

5: Linux 871.8 MB disk1s8

6: Linux 896.5 MB disk1s9

7: Linux 8.2 MB disk1s10

i can see the partition in my guest (linux) ubnuntu 12.10
(see attached)
but strangely, when i have a look into /dev, i cannot see them...

when mounting them, i have the following error :
wrong fs type, bad option, bad superblock

i typed this:
sudo fsck /dev
it seems to be a directory that connot be read ;-(

i cannot format my drive as i will like to keep the data!

any ideas?

juliette

It looks like you are trying to fsck /dev/sdb2 so you need to state that (the specific partition on the device sdb) like this```
sudo fsck /dev/sdb2
```

Partitions (/dev/sdb[1-10] reside on devices (/dev/sdb).  You mount or fsck partitions not devices.

I understand that you don't want to format the partition (/dev/sdb2).  Can you mount any of the other partitions (/dev/sdb[6-10])?  Each one has to be mounted (and/or fsck'd) separately.  In other words; you can fsck /dev or /dev/sdb.

---

### Post by julietteg on 2013-01-11
Hi

i have some error messages when i mounted partitions...
the format is for sure ext2....

---

### Post by bab1 on 2013-01-11
> **julietteg said:**
> Hi

i have some error messages when i mounted partitions...
the format is for sure ext2....

What do you get when you use this command```
sudo fsck /dev/sdb2
```

---

### Post by julietteg on 2013-01-12
Hi

no, same error...
see attached

---

### Post by bab1 on 2013-01-12
> **julietteg said:**
> Hi

no, same error...
see attached
There is a difference.  It provides a few more details.  It appears that sdb2 is part of a RAID array.  This adds complexity to the situation as the data needs to be reassembled as it is striped across the disks.  Essentially you have to ***reassemble the RAID BEFORE you can use fsck***.  You don't fsck the individual disks.

Are these devices part of a RAID setup that you created?

---

### Post by julietteg on 2013-01-13
hi

i technically did not do anything.

my Lacie disk (4 terra) did not work anymore therefore as it was not covered by the warranty anymore, i opened it and i find 2 disks (2 terra).
but yes, it was a raid....

i have not created the partitions....

how do i reassemble the raid?

juliette

---

### Post by bab1 on 2013-01-13
> **julietteg said:**
> hi

i technically did not do anything.

my Lacie disk (4 terra) did not work anymore therefore as it was not covered by the warranty, i opened it and i find 2 disks (2 terra)

i have not created the partitions....

juliette
Ah, but the original Lacie device came with RAID, correct?

[COLOR="Blue"]Edit; Is the data backed up somewhere?  If it is we can always remove the original partitions and reformat the 2 disks.[/COLOR]

---

### Post by bab1 on 2013-01-13
> **julietteg said:**
> it was a raid....

juliette
That says it all.  Unless the data is truly valuable then I would just reformat the disks.  It sounds like you have 4TB of space to play with now.

If you feel you need the data then there are apps that will look for complete files still on the disks, but with some RAID configurations it will be pretty hard to recover anything.  As I said the data is striped across both disks, meaning no disk holds a complete file system.

---

### Post by julietteg on 2013-01-13
when i asked lacie, they said it was NAS...
is it the same as RAID?

if i remember well : when i configured my drive, i had the choice to to a RAID (and therefore have 2terra of storage instead of 4terra). but i did not do it... i had 4 terra of storage, no duplicated data.. if that make sense..

juliette

---

### Post by bab1 on 2013-01-13
> **julietteg said:**
> when i asked lacie, they said it was NAS...
is it the same as RAID?

juliette
Not sure what you asked Lacie.  The term NAS stands for Network Attached Storage.  The term RAID stands for Redundant Array of Inexpensive Disks.  The NAS is what the device is used for whilst RAID is a method of preparing the disks for formatting.  A NAS does not need to be RAID formatted.

---

### Post by julietteg on 2013-01-13
Hi

Apparently some others had the same issue with a Lacie nas
and they use a tool called mdadm.... 

did you heard about it?

juliette

---

### Post by bab1 on 2013-01-13
> **julietteg said:**
> Hi

Apparently some others had the same issue with a Lacie nas
and they use a tool called mdadm.... 

did you heard about it?

juliette

The *mdadm* utility  manages RAID arrays.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://en.wikipedia.org/wiki/Mdadm") for more info.  Also look at your jpg attachment again.  Do you see the references to RAID?

I think we know what the problem is.  We just need to decide what we want to do and what your overall plan is.  What are you using in place of the Lacie NAS?  What were you using now in its p[ace?  Are you okay with loosing the data?  Are you going to get any warranty help for, LaCie?  What do you want to do with the 2 drives?  Are you trying to repair the LaCIe NAS itself?

The question really is what are we to do about moving forward with resolving the problem you have?

[COLOR="Blue"]Edit:  IMO the RAID array can't be restored with *madam*.[/COLOR]

---

### Post by julietteg on 2013-01-14
Hi

to answer your questions ;
What are you using in place of the Lacie NAS? What were you using now in its p[ace? I bought another drive (3terra). it is working perfectly...
Are you okay with loosing the data? NO
Are you going to get any warranty help for, LaCie? my drives are not covered by warranty anymore
What do you want to do with the 2 drives? recover my data... then maybe format them and use them as normal drive
Are you trying to repair the LaCIe NAS itself? repair? no... i just want to have my data back!

juliette

---

### Post by bab1 on 2013-01-14
> **julietteg said:**
> Hi

to answer your questions ;
What are you using in place of the Lacie NAS? What were you using now in its p[ace? I bought another drive (3terra). it is working perfectly...
Are you okay with loosing the data? NO
Are you going to get any warranty help for, LaCie? my drives are not covered by warranty anymore
What do you want to do with the 2 drives? recover my data... then maybe format them and use them as normal drive
Are you trying to repair the LaCIe NAS itself? repair? no... i just want to have my data back!

juliette
I hate to say it but most likely the data is lost.  You can try using a low level file recovery program such as [**_[COLOR="Blue"]PhotoRec[/COLOR]_**]("http://www.cgsecurity.org/wiki/PhotoRec").

I assume you're not backing up your data rght now.  I highly recommend  you implement one now to guard against this happening again in the future.

---

