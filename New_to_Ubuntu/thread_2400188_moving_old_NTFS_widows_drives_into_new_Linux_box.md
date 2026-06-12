---
title: "moving old NTFS widows drives into new Linux box"
date: 2018-09-03
forum: New to Ubuntu
---

### Post by rocketshiptech on 2018-09-03
Hi guys,

A little help for a Windows Veteran/Linux Newb, please.

Me: 30 year windows developer, will not use Win10. So, this is the year for linux on the desktop!  (but I still need Win7).

Old production computer (win7) is dying. Building a new production computer; Ryzen7, 4Ghz, 16GB, 500Gb SSD.  Already setup  ubuntu and have win 7 running in VirtualBox. I even have that Virtual Win7 box on my local (windows) network.  All good.

Now its time to shut down the old machine and move its six(!) SATA hard drives to the new box, and this gives me pause.

Two are just normal &#8220;Basic&#8221; NTFS drives. But the rest are &#8220;dynamic&#8221; drives  setup as two RAID 0 mirrors (standard win7 drive mirroring).  Complications: as the machine is dying one mirror is degraded (only one drive working) and as I look at them in the box, they are all identical WD drives, and I have no idea which is which.

So I&#8217;m assuming Linux will mount these NTFS drives. (right?) my backslashes become forward slashes but other than that&#8230;? Is the basic vs dynamic formatting going to be a problem? 

I&#8217;m very confused about the file system. All my drives are going to be inside the /dev folder now, right? Or the /mnt  folder?   Am I going have to manually mount them? Every time??

Is there drive mirroring in the OS? Do I have to install a (presumably free) add on?

I find a lot of instructions online about installing Linux in windows boxes, but I haven&#8217;t found anything about moving Windows drives physically into a Linux box.

AHA TIA 
:)

---

### Post by ajgreeny on 2018-09-03
Windows dynamic drives are not usable in Linux, I'm afraid and will not be seen by the system properly so you will have to do something with them, probably format them, in order to make them of any use to you.

The mounting of all those drives will not be a problem (once they're usable in Linux) as they can easily be mounted at boot time by adding appropriate entries in the /etc/fstab file, see [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

However, I am unable help with RAID as it's not something I have ever used, so I do not know how RAID impinges on, or works with that fstab file; wait for more knowledgable answers before you start doing anything.

---

### Post by Impavidus on 2018-09-04
You can mount the basic NTFS partition. If there is file system damage or Windows didn't shut down properly (Win7 still shuts down properly by default), you may have to mount them read-only, but as long as the damage isn't too bad they can be mounted. On the other hand, Linux can't handle Windows dynamic partitions.

Devices like hard drives are in /dev, but that's just the raw drive, all 10[sup]12[/sup] bytes on a row for low-level operations. To make them more useful, the filesystem on the drive must be mounted, which can be done wherever you want, but /mnt and /media are common places. Mounting will interpret the data on the partition as a hierarchical structure and attach it to the root file system.

RAID/drive mirroring is supported in Linux. I don't know the details as I never used it. It may not work the same way as in Windows.

Linux can read and write NTFS partitions, but it can't fix damaged NTFS partitions. If you use NTFS, you should have Windows available to fix or defrag it. I don't know if the Windows in the virtual machine can do that. It needs access to the raw bytes on the disk.

---

### Post by rocketshiptech on 2018-09-04
Thanks guys, this has been helpful.

In the mean time, I just tried plugging in any old (windows) SATA drive I had handy.

Ubuntu puts the new drive in the "Other Locations" section of "files" (Nautilus?).  I can browse to it. (I didn't seem to need to do any mounting) a few minutes later, a mac-style drive icon appeared on my desktop (not sure if that was related to my browsing or not.)

Part of my confusion had been because the ubuntu installer had given my boot HD the volume label "Computer" so I thought that was a parallel the the "My Computer"  icon not just a drive.

I found instructions about giving vbox access to "raw disks" so that' next. Then testing chksdk (actually scandisk)

No support for "dynamic" disks is fine. I can break those mirrors and convert them to basic disks before I pull them from the Win7 Box. (next I'll start googling linux raid)

What would be the correct (preferred) format for linux drives?

---

### Post by Yellow Pasque on 2018-09-04
> What would be the correct (preferred) format for linux drives? 

mdadm is probably what you want to google and read about if you're referring to making software RAID volumes in Linux. If that's not what you meant, please clarify.

---

### Post by rocketshiptech on 2018-09-04
> **Temüjin said:**
> mdadm is probably what you want to google and read about if you're referring to making software RAID volumes in Linux. If that's not what you meant, please clarify.

Two questions really. One, you just answered. Software RAID for linux.

but 2: If NTFS is only partially supported, what drive _format_ should I using?

---

### Post by SeijiSensei on 2018-09-04
You should always opt to the default, ext4, unless you have some particular need for another format.  NTFS does not support file-system primitives in *nix like permissions.

It won't matter to the Win7 system in the VM either.  In VirtualBox, you'll need to install the extension pack, then configure "Shared Folders" to see devices on the host computer outside the virtual machine.

---

### Post by rocketshiptech on 2018-10-02
Thanks again guys, in the end I bought new drives and  used webmin to configure the RAID.  All good.

---

