---
title: "Recover Acccidentaly Formatted External HDD with Encryption"
date: 2017-08-20
forum: New to Ubuntu
---

### Post by dan22644 on 2017-08-20
Hi all,

So I messed up. I found an old external hard drive that I thought had data on it, but I had completely forgotten that is was formatted in Ext3 (or maybe Ext4) and that I had Password protected it. I plugged it into my windows laptop as I had just moved and my PC I run Ubuntu on wasn't setup yet. It gave me a message, can't remember what it said, but it DEFINITELY did NOT say it was going to reformat the drive, but it did. About a tenth of a second later I remembered how I formatted the disk.

I immediately unplugged it and have been searching for a way to recover the data, but so far have not found what I need. Any ideas? I know the password to get into the drive, I just need to recover the formatting. I've done this in windows using an MBR recovery tool, but don't know the equivalent I need to recover my disk.

Also, the external HDD is just data files, not a bootable drive, no operating system.

Thanks!!

---

### Post by TheFu on 2017-08-21
I don't know what you mean by "password protected" - can you be more specific?  ecryptFS?  LUKs with dm-crypt? Something else?

Yes, you messed up.  I think that data is gone.  The only solution is to restore from a backup. Whenever encryption is involved, backups are mandatory.  There is little recourse when any corruption happens to encrypted storage.

MBR in Linux is the same as MBR in Windows. No different.  If you have a "machine readable" backup of the partition table, usually created by running sfdisk, then there is hope (1% hope).  Did you make one?  

BTW, having an sfdisk file as part of your daily backups, along with all the LVM and other file system data is highly recommended.

From the sfdisk manpage:
```
BACKING UP THE PARTITION TABLE
       It is recommended to save the layout of your devices.  sfdisk  supports
       two ways.

       Use  the  --dump option to save a description of the device layout to a
       text file.  The dump format is suitable for later  sfdisk  input.   For
       example:

              sfdisk --dump /dev/sda > sda.dump

       This can later be restored by:

              sfdisk /dev/sda < sda.dump

```
If you use GPT, then **sfdisk** cannot be used, but **parted** has a similar capability.

Sorry, but none of this helps after the fact.

There is a "Data Recovery" how-to on the help.ubuntu.com site which might be useful, but if you used the normal encryption tools, forgetaboutit.  That is the point, after all.

---

### Post by oldfred on 2017-08-21
Since they updated fdisk with 16.04 to work with gpt partitioned drives, the backup does now work with gpt drives.

sudo sfdisk -d /dev/sdb > parts_sdb.txt

Part of parts_sdb.txt (I have lots of partitions).
```
label: gpt
label-id: C82E4BFF-3941-4B0F-92E8-094230A7E19C
device: /dev/sdb
unit: sectors
first-lba: 34
last-lba: 1953525134

/dev/sdb1 : start=        2048, size=     1023437, type=C12A7328-F81F-11D2-BA4B-00A0C93EC93B, uuid=8EAB306C-97B9-4A07-A896-5AC4FB371311, name="EFI System Partition"
/dev/sdb2 : start=     1026048, size=        4096, type=21686148-6449-6E6F-744E-656564454649, uuid=453A2B90-05F4-4AC9-884C-6204A80FFC47
/dev/sdb3 : start=     1030144, size=    51199219, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=282E63CB-2BEC-4A38-9FA8-9C23D750F9B0, name="xenial_b"
/dev/sdb4 : start=    52230144, size=   819200000, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=0EECD036-A8EA-478A-991E-C23771339220, name="data"

```

gdisk is also used with gpt partitioned drives, but its backup is a binary file.

---

### Post by TheFu on 2017-08-21
I've  been left with an unusable disk after runing gdisk. I won't use that tool again.

Lots of people are still running 14.04 - including me.  Still waiting for issues with 16.04 to be so minimal as to warrant moving. At least there is a warning.  That wasn't always the situation.  
```
$ sudo sfdisk -dump /dev/sdd
unrecognized format - using sectors

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util sfdisk doesn't support GPT. Use GNU Parted.

# partition table of /dev/sdd
unit: sectors

/dev/sdd1 : start=        1, size=4294967295, Id=ee
/dev/sdd2 : start=        0, size=        0, Id= 0
/dev/sdd3 : start=        0, size=        0, Id= 0
/dev/sdd4 : start=        0, size=        0, Id= 0

```

 - gotta head outside ... eclipse has started here.

---

### Post by dan22644 on 2017-08-28
Didn't realize the MBR was the same, I will try my MBR recovery utility that has been successful in the past. Thanks!

---

### Post by HermanAB on 2017-08-29
Hmmm, chances are almost 100% that your data is irrecoverable.  With encryption enabled, it is pretty much an all or nothing effect in my experience.  Sorry about that.

---

