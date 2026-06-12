---
title: "[xubuntu] FAT32 USB not recognised [solved]"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by DoctorDunc on 2014-07-11
I have 2 USB pen drives: 
FLASH is 64GB, FAT32 and invisible to the desktop (unmounted)
KEY is 4GB, NTFS and Xubuntu picks it up straight away. All is as you'd expect.

 Gparted can see both and reports their types and sizes correctly.
Nemo file manager shows both (in Computer) but has no info for FLASH.
The removable disk settings are all ticked (or KEY wouldn't be showing).

I don't think this is a size issue because previously KEY was also FAT32 and invisible.

I have come across several posts relating to FAT32 but mainly formatting and nothing recent.  I can't see anything suitable to download in Ubuntu Software Centre but presumably I'm missing some drivers.

Where are they?

Cheers, DD

---

### Post by slooksterpsv on 2014-07-11
If you open up a terminal and try to mount it via terminal (you can use gparted to find out what dev point it's on e.g. sdb sdc sdd etc.)
via:

sudo mount /dev/sdc1 /mnt

Or if you wanted to make a directory and mount it:
sudo mkdir /media/64GBFlash
sudo mount /dev/sdc1 /media/64GBFlash

That should output some information. I believe the issue is with the FAT32 and the size of the drive. Can you take screenshots of gparted and post them, maybe we can see something that we're missing overall.

---

### Post by Vladlenin5000 on 2014-07-11
Is it really FAT32 or exFAT?

---

### Post by DoctorDunc on 2014-07-12
> **slooksterpsv said:**
> If you open up a terminal and try to mount it via terminal (you can use gparted to find out what dev point it's on e.g. sdb sdc sdd etc.)
I ran **sudo mount /dev/sdb1 /mnt** and it worked!  I can see all the folders. Now read the next post...

---

### Post by DoctorDunc on 2014-07-12
> **Vladlenin5000 said:**
> Is it really FAT32 or exFAT?
I'm sure it wasn't exFAT before.  It is now, though, I just reformatted KEY to FAT32, expecting it not to show but guess what...it just auto-mounted!

Summat weird going on here, back in a bit...

---

### Post by DoctorDunc on 2014-07-12
Maybe size does matter after all.  I've rebooted and KEY (now FAT32) is auto-mounting for fun but FLASH (still FAT32) is still not playing ball, although it will mount manually.  I could have sworn KEY wasn't showing before but it's fine now so what the hey, I'll take it.  

I suppose I just have to wait until someone writes a patch for large FAT32 drive support.  At least I know I should stick to NTFS if I want to share drives between Windows and Linux.

Thanks for your help, fellas. :D

DD

---

### Post by DoctorDunc on 2014-07-12
Update:

Embarrassingly, FLASH was probably exFAT all along!  I didn't want to try re-formatting it because there was so much data on it but now I've discovered that xubuntu reads NTFS straight off, I decided that I might as well have it like that.  But when I went to reformat it in Windows I was offered a default of exFAT or NTFS - only, no FAT32 - so it couldn't have been anything but exFAT.

So now I know something else: GParted reports exFAT as FAT32.  Aaargh!  We live, we learn, our hair falls out...

So good spot Vlad, I just didn't take it far enough.

DD

---

### Post by kurt18947 on 2014-07-13
If you choose to, there are two packages in the repository that enable reading & writing exFAT. They show up in Synaptic if I use "exFAT" as search criteria. I believe Microsoft has locked up exFAT pretty tight so not sure about legalities. No 'free lunches' like FAT32.

---

### Post by Vladlenin5000 on 2014-07-13
The reason I suspect it could be exFAT was the volume size limitation of 32GB for FAT32 as briefly explained here: [http://technet.microsoft.com/en-us/library/cc938432.aspx](http://technet.microsoft.com/en-us/library/cc938432.aspx)

I never tested the tools mentioned by kurt18947 - have no idea about its 'legal'status either - because for those larger drives I use either NTFS (in devices intended to be used also in Windows) or EXT4 right away.

---

### Post by kurt18947 on 2014-07-13
> **Vladlenin5000 said:**
> The reason I suspect it could be exFAT was the volume size limitation of 32GB for FAT32 as briefly explained here: [http://technet.microsoft.com/en-us/library/cc938432.aspx](http://technet.microsoft.com/en-us/library/cc938432.aspx)

I never tested the tools mentioned by kurt18947 - have no idea about its 'legal'status either - because for those larger drives I use either NTFS (in devices intended to be used also in Windows) or EXT4 right away.

The only reason I knew about them is I expect exFAT to become more common as flash storage continues to increase in capacity.  I too use NTFS when I have a choice though it sounds as though there are viable add-ons for Windows that enable reading and writing of ext* volumes & files on Windows.

---

### Post by DoctorDunc on 2014-07-13
Too late anyway, I've reformatted in NTFS and transferred the data.  It took ages so I'm not going back unless I have to.  Hey, it might even work at the library now (which is still on XP!).

Thanks for all the help :)

DD

---

### Post by kurt18947 on 2014-07-14
It might very well work at the library though I thought XP would read & write exFAT, or is that some sort of add-on?  I did make a disappointing for me discovery today.  i thought that by storing folders and files on an NTFS partition, linux ownership and permissions would not transfer.  I was wrong.  A folder that was created by a Win7 user and copied to an NTFS partition using Ubuntu is now owned by the user that copied the folder. I think I know how to fix the ownership problem but I chose NTFS thinking I'd avoid the ownership & permissions bump.

---

### Post by Vladlenin5000 on 2014-07-14
exFAT is supported in Windows only in XP SP3 / Vista SP1 and newer.

---

### Post by DoctorDunc on 2014-07-14
There is (or was) a patch for XP to read large (>32GB?) pen drives, which auto-installed when needed.  I even told them about it but inertia rules so I should be grateful that it's not all still running on 98 I suppose.

Thanks for the heads up on that NTFS permission issue, Kurt.

---

### Post by kurt18947 on 2014-07-19
> **DoctorDunc said:**
> There is (or was) a patch for XP to read large (>32GB?) pen drives, which auto-installed when needed.  I even told them about it but inertia rules so I should be grateful that it's not all still running on 98 I suppose.

Thanks for the heads up on that NTFS permission issue, Kurt.

Better late than never, I suppose :oops:.  I fixed my problem by installing ntfs-config from the repository and running it with sudo privileges.  It added the data drive to fstab and I was able to view and copy the files contained therein.

---

