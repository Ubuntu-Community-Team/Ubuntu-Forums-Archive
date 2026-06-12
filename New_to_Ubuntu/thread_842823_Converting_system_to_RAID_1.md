---
title: "Converting system to RAID 1"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by lil_elvis2000 on 2008-06-27
Hello,
  I have a new Xubuntu system and am wanting to make a RAID 1 for the documents stored in the /home folder. Contains users and clients documents.
  So I have two identical SATA drives. one contains the data and the other is new and currently unused (it actually is formatted as ufs2 from a BSD system I shutdown). I have been looking up an down for tips on building a RAID 1 in this scenario...and havn't had any luck.
  Does anyone have any such links or instructions to help me out.

I have:
   sda1   / 
   sda...  other partitions on sda

the two identical drives are:
   sdb1   /home
   sdc1   /mnt  - the ufs drive mounted read-only temporarily

Thanks.

---

### Post by Xerp on 2008-06-27
Thats mdraid you'll be wanting then. There is some starter info here:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by lil_elvis2000 on 2008-06-28
Hmm. doesn't look I have the hardware for fakeRAID. I don't think I have a SATA raid controller...

I have looked at mdadm...seems I need to repartition and reformat the disks to "use for RAID" and then put the data
on.

Well. I'll have to restore the files from backup after I do all this.

Am I right? I need to use parted and redo sdb and sdc as a volume for RAID. and then reformat each as ext3. And then create the RAID 1 and then put on the data?

Would it be possible to just set sdb as RAID first, then create the RAID 1 in a crippled mode. Copy over the data from sdc. format sdc as RAID, then insert it into the RAID 1?

---

### Post by lil_elvis2000 on 2008-07-02
I managed by following these instructions essentially:
  [http://www.linuxconfig.org/Linux_Software_Raid_1_Setup](http://www.linuxconfig.org/Linux_Software_Raid_1_Setup)

---

