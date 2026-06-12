---
title: "Drives not showing up in Ubuntu properly"
date: 2014-12-02
forum: New to Ubuntu
---

### Post by icestorm2 on 2014-12-02
Before I installed Ubuntu on my laptop, there were three drives listed on Windows:  

C (69.7 GB)
D (69.5 GB)
E (~149 GB)

Now there are only two:  

/dev/sda (160 GB)
/dev/sdb (160 GB)

and when I view it in windows, I only get C and D showing up.


What I imagine happened is sda=C&D, and sdb=E, so as soon as Installed Ubuntu on sdb, windows couldn't see it anymore.  Is this accurate?

---

### Post by Bashing-om on 2014-12-02
icestorm2; UHmmm ..

What Windows calls a 'drive' is actually a partition.
In ubuntu drives are listed as
sda = 1st hard drive recognized by the operating system
sdb = 2nd hard drive 
sdc = 3rd
and so on.
Partitions in linux
sda1 would be the 1st (1) partition on that 1st hard drive
sda5 5th partition on 1st hard drive
sdb3 3rd partition of 2nd hard drive
sdc8 8th partition on 3rd hard drive

Windows does not talk to linux, and will not see the linux partitions with out added utilities to do so.

To see a picture of what is -> fire up GParted from the liveDVD.

[INDENT][INDENT]hope this helps a bit to clear the mud
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-12-02
When you installed Ubuntu what option did you choose? Install Alongside? Or Something Else?

Windows file manager will not recognise a Linux partition but there may be a Windows disk utility that will show the partitions on the disk even if it shows them as "unknown."

69.7 + 69.5 does not = 160. What did you have in these partitions? Linux will recognise Windows partitions. So, File Manager is not showing two Windows partitions as 1 combined partition. File Manager does not do that.

Here is something else that does not add up. 69.7 + 69.5 + 149 = 288.2. Whereas, 160 + 160 = 320. You have gained 33 GB of disk space!

The information does not compute.

Oh, by the way in Ubuntu the File Manager shows the partitions but the location of Ubuntu is listed as Computer in 14.04. Use the Disks utility. That will show partitions. Should have at least 1 partition for Ubuntu (mounted as file system root ) and another for Swap.  A Windows partition will show up as HPFS/NTFS (Bootable).

But everything depends upon what instructions you gave to the Installer.

Regards.

---

### Post by icestorm2 on 2014-12-02
Thanks!  That cleared things up.

---

### Post by mcduck on 2014-12-02
> **grahammechanical said:**
> 
69.7 + 69.5 does not = 160.

...however 69,7GiB + 69.5GiB is around 150GB (140GiB), add a hidden system restore partition or something and that pretty much adds up to 160GB drive.

---

