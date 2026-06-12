---
title: "HDD problem | Internal HDD not detected after install ubuntu 14.04"
date: 2015-06-05
forum: New to Ubuntu
---

### Post by Laxses on 2015-06-05
Hello
i am a new ubuntu user and it's been 3 days since i installed it via Burned CD , i decided to erase my windows 7 os to ubuntu
still,there is a problem. before i installed it i have 2 detected internal HDDs and after i installed it, now i only have 1 detected internal HDD.
What should i do to make my other internal HDD detected to ubuntu ?

---

### Post by dino99 on 2015-06-05
the first step is to check the bios detection
the second one is to boot with gparted live to check also the detection, and possible warning/error with the hdd/partitions

then check the output of  > sudo blkid

---

### Post by Laxses on 2015-06-05
when i enter sudo blkid i got this

/dev/sda1: UUID="ac11fb8d-923c-4b49-8017-5a3f1d997e98" TYPE="ext4" 
/dev/sda5: UUID="497a7884-5b4a-4691-9592-196ac8cb6043" TYPE="swap" 

my bios can't detect my lost HDD too, is it possible that my HDD is "died" because installation ?

---

### Post by matt_symes on 2015-06-05
Hi

> my bios can't detect my lost HDD too, is it possible that my HDD is "died" because installation

Check the cabling to the hard drive, both power and data leads.

Kind regards

---

### Post by Laxses on 2015-06-05
the cable ? it's normal i think, maybe i will go back to windows and re-install ubuntu. it's safe to back and re-install right ? . i just want to check if i go back to windows , maybe my "lost" HDD will detected

---

### Post by matt_symes on 2015-06-05
Hi

> **Laxses said:**
> the cable ? it's normal i think, maybe i will go back to windows and re-install ubuntu. it's safe to back and re-install right ? . i just want to check if i go back to windows , maybe my "lost" HDD will detected

If you're not seeing it in your BIOS then Windows will not see it.

Try to be 100% sure that it's not the cabling. Check and then double check and then check again.

Try swapping over the cables, both power and data, on the hard drives. Is the other hard drive recognised then ? Try swapping out new data cables and power supply cables.

Can you try the hard drive in another PC ?

It's not impossible that the hard drive has died but is pretty unlikely.

I may be barking up the wrong tree with the cables but it is something i would eliminate.

Kind regards

---

### Post by oldfred on 2015-06-05
Are you sure you had two physical drives?

Windows confuses  things by calling partitions drives. So if you had two partitions you could have had a c: drive and d: drive. But really two partition which in Linux would be sda1 & sda2.

If you had two physical drives the second drive would also have been called d: drive. Which in Linux would be sda & sdb.

Or we do not know.

---

### Post by cariboo on 2015-06-05
It's fairly easy to check how many hard drives you have installed in your system. Use the following command to list the hard drives and their partitions:

```
sudo fdisk -l
```

On this system, a Toshiba Satellite, I ge the following results:

```
sudo fdisk -l
[sudo] password for cariboo: 
Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 4408DDE0-CAFD-11E4-8233-FA5C712669A1

Device         Start        End    Sectors   Size Type
/dev/sda1       2048    2099199    2097152     1G Windows recovery environment
/dev/sda2    2099200    2303999     204800   100M EFI System
/dev/sda3    2304000    2566143     262144   128M Microsoft reserved
/dev/sda4    2566144  419951225  417385082   199G Microsoft basic data
/dev/sda5  419952640  439481936   19529297   9.3G Linux filesystem
/dev/sda6  439482368  447295487    7813120   3.7G Linux swap
/dev/sda7  447295488 1465147391 1017851904 485.4G Linux filesystem
```

---

### Post by matt_symes on 2015-06-06
Hi

> **oldfred said:**
> Are you sure you had two physical drives?

Windows confuses  things by calling partitions drives. So if you had two partitions you could have had a c: drive and d: drive. But really two partition which in Linux would be sda1 & sda2.

If you had two physical drives the second drive would also have been called d: drive. Which in Linux would be sda & sdb.

Or we do not know.

That may well be bang on the money oldfred and if it is then it's a fine catch.

I assumed two physical drives but if the poster is using Windows misleading terminology then that could well be the case.

Kind regards

---

### Post by leunam12 on 2015-06-06
> **cariboo said:**
> It's fairly easy to check how many hard drives you have installed in your system. Use the following command to list the hard drives and their partitions:

```
sudo fdisk -l
```

On this system, a Toshiba Satellite, I ge the following results:

```
sudo fdisk -l
[sudo] password for cariboo: 
Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 4408DDE0-CAFD-11E4-8233-FA5C712669A1

Device         Start        End    Sectors   Size Type
/dev/sda1       2048    2099199    2097152     1G Windows recovery environment
/dev/sda2    2099200    2303999     204800   100M EFI System
/dev/sda3    2304000    2566143     262144   128M Microsoft reserved
/dev/sda4    2566144  419951225  417385082   199G Microsoft basic data
/dev/sda5  419952640  439481936   19529297   9.3G Linux filesystem
/dev/sda6  439482368  447295487    7813120   3.7G Linux swap
/dev/sda7  447295488 1465147391 1017851904 485.4G Linux filesystem
```
I don't know if this is the right place to post this question, I don't want to hijack this thread, I am not the op and I don't have his problem (I'll let the moderators decide), but I don't get all that information with fdisk.
This is what I get ```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 240.1 GB, 240057409536 bytes
256 heads, 63 sectors/track, 29071 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe9155ff3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   468862127   234431063+  ee  GPT

```
This is the result of lsblk```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1   8:1    0   300M  0 part 
&#9500;&#9472;sda2   8:2    0   100M  0 part /boot/efi
&#9500;&#9472;sda3   8:3    0   128M  0 part 
&#9492;&#9472;sda4   8:4    0   223G  0 part 
```
As you can see fdisk whines about not supporting GPT and it does not show the four partitions on sda.

---

### Post by oldfred on 2015-06-06
Fdisk does not work with gpt partitioned drives.
You have to use parted or gdisk.

sudo parted -l

But with gdisk you have to specify drive:
 sudo gdisk -l /dev/sda

---

### Post by leunam12 on 2015-06-06
Ok, thanks. I wonder why it worked for Cariboo.

---

### Post by oldfred on 2015-06-06
I have not tried fdisk recently. My main working install is 14.04 on desktop & 12.04 on laptop.

But I know they planned major updates to fdisk since all new computers are gpt. So he may be running 15.04 and may have a new fdisk version.

---

### Post by cariboo on 2015-06-07
> **leunam12 said:**
> Ok, thanks. I wonder why it worked for Cariboo.

I'm running Wily , with fdisk 2.26.2, so that may be the difference.

---

