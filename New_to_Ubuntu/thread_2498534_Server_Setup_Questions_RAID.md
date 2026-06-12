---
title: "Server Setup Questions RAID"
date: 2024-06-18
forum: New to Ubuntu
---

### Post by sberwitz on 2024-06-18
Sorry if this has already been answered, but any help is much appreciated.

I am setting up a server with Ubuntu to run urbackup as a BDR for my main server.  The server with Ubuntu has a boot drive and 4 1TB drive that I want to use in a RAID array.  I am a little confused on the drive selection during the installation process.  I was hoping someone could give me direction with regards to configuring the system and RAID in the installation process.  

Thanks!
SGB

---

### Post by TheFu on 2024-06-18
So, RAID and installs have changed drastically in the last few Ubuntu Server releases.  It is necessary to state specifically which release (use the number yy.mm) to be clear which you are trying to make work.

Typically, it is easiest to run the installation with just 1 drive connected, then add the drives to be used for RAID after the install.  You need to be clear about which sort of RAID you intend.  SW-RAID, HW-RAID, FakeRAID.  We can't guess.  Also, we would make recommendations based on the file system you plan to use and if you want/need a volume manager or not.  For someone new who has sufficient RAM (preferably ECC RAM), then ZFS would be the no-brainer choice for data in a RAIDz setup.  But we don't know what you have.   ZFS isn't really ready for the OS partitions. It definitely is ready for data partitions/volumes. That's an important distinction.  But if you are really new to Linux, using any volume manager can be a very steep learning mountain. 

I've never used urbackup and don't know what you mean by "as a BDR for my main server".  If you want a hot standby or cold standby server, there you'll still need normal, automatic, daily, versioned, backups outside and standby setup.  Most professional situations would run in a load-balanced architecture with storage system redundancy across multiple servers - something like CEPH or Sheepdog for the storage needs.  Additionally, everywhere I've worked since 2000 has defaulted to using virtual machines as the default install type unless the physical server was to be used as a VM host system, usually in a VM cluster.

Anyway, the recommendations will be different based on the details provided.

The simplest RAID setup would probably be mdadm with LVM on top.  That has been used for 25 yrs on Linux if HW-RAID with a quality HBA and an on-site replacement HBA of the exact same model isn't possible.  Since around 2005, HW RAID hasn't made much sense outside a datacenter environment with dedicated 24/7/365 support contracts - i.e. venders having spare hardware for everything within 30 minutes of the DC.  Most of the time, either RAID is provided by a storage frame on a SAN or if there isn't a SAN, then SW-RAID would be used.  

Fake-RAID is an abomination and the use cases for it are something a home user might have, but they should be smart enough to avoid FakeRAID.  FakeRAID has all the limitations of HW-RAID, but none of the performance.  SW-RAID provided crazy levels of flexibility that Fake and HW-RAID don't support.  I've migrated SW-RAID between systems and OSes without any issues.

---

