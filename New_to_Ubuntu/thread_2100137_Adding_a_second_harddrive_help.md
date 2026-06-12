---
title: "Adding a second harddrive help"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by socketnut on 2012-12-31
I have an older XP system and bought some components and assembled a new PC. I installed 12.04 on it and everything works well. I used an 128 GB SSD drive to hold operating system & programs. I put in a 500 GB Sata drive to put my data on. My disk utility recognizes it as unknown 500 GB but it allows me to format it in 2 locations on the screen, 1 way talks about master boot record, GUID partition, no partition or apple partition, other location shows various file formats. Then I believe I need to mount the drive and tell it when to turn on. I didn't find any Google hits that made sense so I'm asking for help. I'm not a gamer and have mostly audio and photo files to store.
Thanks,
Socketnut

---

### Post by mamamia88 on 2012-12-31
So you want to add an additional hardrive for storage only?  You probably want to have it permanently mounted every boot then correct?   You will need to format the harddrive to whatever filesystem you want and need to add an entry for it in /etc/fstab.   [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) you will need to use a tool called gparted to do so.  i suggest disconnecting sda which is your primary drive and partitioning with the gparted live cd so that you can't mess up your install by accident

---

### Post by oldfred on 2013-01-01
If you have XP, do not use gpt(GUID) as XP does not recognize it. Windows Vista or 7 will read NTFS formatted partitions in a gpt drive, but will only boot from a gpt drive with the new UEFI which is replacing BIOS.

I would use gparted to partition &  format it. You may want several partitions, one NTFS for shared data between Windows & Linux and another for Linux. Do you think you might install another operating system just to test? If so leave 25GB unallocated or create another 25GB Linux ext4 partition.

       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

    
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by socketnut on 2013-01-01
I do not plan on running any windows program on the new machine, just want to move over and store my audio & photo files. I believe I will need to change the format of my audio files for Linux to use but I need them available for my Apple "pod" as well.

---

