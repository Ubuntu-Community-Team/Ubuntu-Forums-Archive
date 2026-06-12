---
title: "RAID 5 recovery from failed NAS w/iSCSI targets"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by brekon on 2013-04-22
Hey there,
Any help would be MUCH appreciated! It's a bit of a long story, but I'll try to include only relevant info...

Background:
I originally had a Thecus n4200pro with a 4-drive RAID 5 array, on this I had 3 iSCSI targets (which may not have been the best idea) which I initiated on a mac pro (10.6.8) -- also had ext3 partition and 2.1TB unallocated. Short version is drive 2 in the array failed, so I inserted a new drive to rebuild and during the rebuild, drive 4 disappeared (it didn't fail, it was just gone from the array -- and later on I found the data was intact). I RMAd the Thecus and am now left with these 4 drives (originally 4 2TB, the failed drive was replaced with a 3TB) -- one of which is empty as the rebuild never even occurred. I have backups of all of the data except for what's on 1 of the iSCSI targets (poor choice, I know).

What I've done/tried:
I popped the drives into my PC (Windows 7) hoping for a miracle. The drives appeared in disk management but were uninitialized (and I left them that way). I tried UFS Explorer RAID Recovery (read-only software) and was able to see the intact RAID with appropriate ext partitions as well as 3 "unknown partitions" -- assuming the iSCSI targets (good news, I think). Using the recover lost data function of UFS, I was able to see previews of the data on 1 of the unknown partitions (I only tried the 1), so I think it's safe to say the data is there and healthy(?). I was unable to actually recover the data or to create a usable disk image as it had an unknown file format/filesystem (I can't remember the exact error).

From here, I gave up on Windows and did a fresh install of ubuntu 11.10 (on a new/blank drive) to see what I could come up with there.

I haven't used any distro of linux in several years, so I'm quite rusty. I am able to see all of the drives in Disk Utility and Webmin -- including the iSCSI targets, although they show up as "unrecognized" in Disk Utility. The RAID shows up in multi-disk devices, although there are 5 of them (??): 

vg0 - 6TB LVM2 Volume Group: this is where I can see the 3 iSCSI partitions as unrecognized, 5 partitions in total and 2.1TB free space
md0 - 2.1GB RAID 1 Array [degraded] -- says swap space
md1 - 6.0TB RAID 5 Array [degraded] -- says not partitioned
md2 - 2.1GB RAID 1 Array [degraded] -- also says swap space
(the 5th is ubuntu)

I've been researching the forums here the past few days, but haven't been able to find a similar situation or to piece together relevant info from various posts, so I figured I would ask. I have been examining the drives/situation with mdadm, open-iscsi, and iscsiadm, but I'm unsure of what info is useful/relevant to post...

Many thanks!

---

### Post by brekon on 2013-04-23
Anyone have any ideas? ...free beers?

---

### Post by bruceq on 2013-06-11
Hello,

I just recovered from a similar scenario.  Had a NAS, Raid 5, with one iscsi target.  NAS failed, but Raid 5 was OK.  Here's what I did to recover the data on the iscsi target.  Hope this helps your situation.
Note:  the following just recovers the data on an iscsi target.  Warning:  The following circumvents the iscsi configuration.  It does not reconfigure the iscsi target(s).  In fact if you need to recover the iscsi target itself, (i.e. not just the data) don't do this.

1.  Installed Ubuntu 13.04 on an extra pc (I initially tried the Live CD/USB, but couldn't make it work).
2.  Installed and updated mdadm and lvm2.
3.  Shut down the computer.  Installed 4 of my 5 "Raid 5" disks, and booted.
4.  During boot, (had to keep pressing ESC key otherwise would freeze at purple screen) was asked if I wanted to start the Raid in "Degraded" mode.  I chose yes.
5.  Verified that my raid showed up in /dev as md? (in my case, my raid 5 set was /dev/md1 and I had another Raid 1 set /dev/md0).
6.  Verified that my lvm physical volumes, volume groups, and logical volumes existed with pvdisplay, vgdisplay, and lvdisplay (respectivelly).
7.  My iscsi volume group was located in /dev/vg0/iscsi0.
8.  As per ion-ral's suggestion at ([http://forum.proxmox.com/threads/3312-iscsi-storage-How-to-access-logical-volume-and-raw-files](http://forum.proxmox.com/threads/3312-iscsi-storage-How-to-access-logical-volume-and-raw-files)) I installed kpartx did the following:
8a.  sudo kpartx -l /dev/vg0/iscsi0
    kpartx looks for and creates device maps from partition tables.  The above command does not write any changes.  Instead it examines the iscsi volume group and lists what changes it would make.
    In my case there was the following
       vg0-iscsi0p1 : 0 262144 /dev/vg0/iscsi0 34
       vg0-iscsi0p2 : 0 15453188096 /dev/vg0/iscsi0 264192
    The second one was the one with my data.
8.b.  sudo kpartx -av /dev/vg0/iscsi0
    This command writes the changes listed by the previous command.
9.  Immediately two new "drives" showed up on the Ubuntu desktop.  I click on the second one and it automatically mounted, and there was my data!

Hope this helps,

Bruce

---

