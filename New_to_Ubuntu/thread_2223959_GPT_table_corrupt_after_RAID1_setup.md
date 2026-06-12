---
title: "GPT table corrupt after RAID1 setup"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by Markardi on 2014-05-13
So I'm completely new to Ubuntu and am trying to set up a  backup/media server at home.  I saw the guide on Lifehacker and figured  I'd give it a try.
  My system is an i3 3225 on an Intel DH77DF mobo with 8GB of ram.   There's a 64GB mSATA SSD as the boot drive and two 4TB WD Red drives for  the RAID1 configuration.
  I installed Ubuntu 14.04 LTS in UEFI mode on the SSD without issues  but as soon as I create the software RAID1 (and it finishes syncing  after 9 hours), gparted gives me the following errors:
  
Libparted Bug Found!
  End of file while reading Invalid argument 
  
The primary GPT table is corrupt, but the backup appears OK, so that will be used.
  
These appear twice as almost for each 4TB drive.
  
Am I doing something wrong when creating the RAID?  The RAID also appears as md127 if that helps.
  Thanks, 
Mark
  
PS - This RAID setup has been a huge pain so far and I could write a  good rant but I'll refrain for now.  For example, mdadm wasn't initially  installed so I had to figure that out.  This was also after the fact I  found out BIOS RAID is really FakeRAID.

---

### Post by Markardi on 2014-05-22
Alright, so some time has passed and nothing has come up.  I've been doing some reading and it looks like the way to create the raid1 is to partition the drives first and make the raid1 of that.  
This however doesn't sit well with me as it means I have to create multiple raids for the multiple partitions I want.  It seems like this could cause a bigger chance of errors to occur.

I want the whole drives to be mirrored so I only want one raid.  Is there a way to do that?  Can someone direct me to a guide to create the raid1 before the partitions are created? 

Thanks.

---

### Post by Luke M on 2014-05-23
I've never used mdadm, but I was curious so I did some searching, and found this:

[https://raid.wiki.kernel.org/index.php/Partitioning_RAID_/_LVM_on_RAID](https://raid.wiki.kernel.org/index.php/Partitioning_RAID_/_LVM_on_RAID)

> 
A RAID device can only be partitioned if it was created with an --auto option given to the mdadm tool. This option is not well documented, but here is a working example that would result in a partitionable device made of two disks -- sda and sdb: 

  mdadm --create --auto=mdp --verbose /dev/md_d0 --level=mirror --raid-devices=2 /dev/sda /dev/sdb

Issuing this command will result in a /dev/md_d0 device that can be partitioned with fdisk or parted. The partitions will be available as /dev/md_d0p1, /dev/md_d0p2 etc.


---

### Post by steeldriver on 2014-05-23
Can you post a link to the guide you used?

It may just be mdadm is happier if you create a partition table / label for each disk - even if you then actually create just a single partition spanning the whole device. That shouldn't limit your options for partitioning the *array* once it's created. Alternatively you could use LVM on top of the RAID array.

---

