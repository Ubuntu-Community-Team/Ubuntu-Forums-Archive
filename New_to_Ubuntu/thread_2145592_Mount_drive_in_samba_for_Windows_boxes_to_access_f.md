---
title: "Mount drive in samba for Windows boxes to access from network + weird drive names"
date: 2013-05-15
forum: New to Ubuntu
---

### Post by marcerickson on 2013-05-15
I'm an experienced Windows desktop admin but a newbie Linux admin.  The more I read the documentation, the more confused I get.  So I'm throwing it out there.

There are two issues (at least) here: first is that sdb1 has an odd name - the UUID: ef24b4c2-a9e1-436f-a461-44cb65ff00b9.  When I open Computer the drive is named CERC SATA1.5/6ch Mirr: 1.0 TB Filesystem (that's the RAID card - sdb is a 1 TB RAID 1 mirror).  When I double click on it to mount and open it, the window's title bar says it's named ef24b4c2-a9e1-436f-a461-44cb65ff00b9.

Here is my fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the  universally unique identifier for a
# device; this may be used with UUID= as  a more robust way to name devices
# that works even if disks are added and  removed. See fstab(5).
#
# <file system> <mount point>    <type>  <options>       <dump>   <pass>
proc            /proc           proc    nodev,noexec,nosuid  0       0
# / was on /dev/sda6 during  installation
UUID=6d60131f-1238-499c-946d-a85b7ae34a7b /                ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during  installation
UUID=1d2b5ab4-a392-44fd-a65e-36fda6940081 /boot            ext4    defaults        0       2
# /home was on /dev/sda7 during  installation
UUID=dd067363-ee07-4e09-9a9b-3d4df2e3ba2c /home            ext4    defaults        0       2
# swap was on /dev/sda5 during  installation
UUID=1d3e3433-3c6b-4c1f-a404-b5ef67e579a8 none             swap    sw              0       0

Here is the output of blkid:
xxxx@xxxxxxxxxxxxx:~$ sudo blkid
[sudo] password for xxxx: 
/dev/sda1:  SEC_TYPE="msdos" LABEL="DellUtility" TYPE="vfat" 
/dev/sda2:  UUID="1d2b5ab4-a392-44fd-a65e-36fda6940081" TYPE="ext4" 
/dev/sda5:  UUID="1d3e3433-3c6b-4c1f-a404-b5ef67e579a8" TYPE="swap" 
/dev/sda6:  UUID="6d60131f-1238-499c-946d-a85b7ae34a7b" TYPE="ext4" 
/dev/sda7:  UUID="dd067363-ee07-4e09-9a9b-3d4df2e3ba2c" TYPE="ext4" 
/dev/sda8:  UUID="DEA48EA4A48E7F31" TYPE="ntfs" 
/dev/sdb1:  UUID="ef24b4c2-a9e1-436f-a461-44cb65ff00b9" TYPE="ext3"

I can't share the drive by right clicking on it and clicking Properties.  If I create a folder on the drive, I can't share it the same way.  Also, there is ~50GB of space being used by a folder "Lost and found" that is owned by root so I cannot change permissions, ownership, or delete it (which is what I really want to do).

I did create a share in smb.conf so I think I can do so again - if I can get the issues with the mirrored drives resolved.

Thanks to all who offer help.

---

