---
title: "Drives not mounting as expected"
date: 2017-06-30
forum: New to Ubuntu
---

### Post by mrfrodo2 on 2017-06-30
We are going to test SQL on linux and I've installed an ubuntu 16.0.4 server. I've attached 3 drives for data, log and tempdb and am attempting to get them mounted. I can create the partitions and file system on the disks as shown here (the devices added are sda, sdb and sdc):

```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME                      FSTYPE       SIZE MOUNTPOINT LABEL
fd0                                      4K
sda                                    1.5T
&#9492;&#9472;sda1                    btrfs        1.5T
sdb                                    400G
&#9492;&#9472;sdb1                    btrfs        400G
sdc                                    100G
&#9492;&#9472;sdc1                    btrfs        100G
sdd                                     60G
&#9500;&#9472;sdd1                    ext2         487M /boot
&#9500;&#9472;sdd2                                   1K
&#9492;&#9472;sdd5                    LVM2_member 59.5G
  &#9500;&#9472;ubuntu--16--vg-root   ext4        55.5G /
  &#9492;&#9472;ubuntu--16--vg-swap_1 swap           4G [SWAP]
sr0                                   1024M
```

As soon as I try to mount sdc1 as /mnt/sqltempdb (the mount point has already been created) I get the following results:

```
sudo mount /dev/sdc1 /mnt/sqltempdb
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME                      FSTYPE       SIZE MOUNTPOINT     LABEL
fd0                                      4K
sda                                    1.5T
&#9492;&#9472;sda1                    btrfs        1.5T /mnt/sqltempdb
sdb                                    400G
&#9492;&#9472;sdb1                    btrfs        400G
sdc                                    100G
&#9492;&#9472;sdc1                    btrfs        100G
sdd                                     60G
&#9500;&#9472;sdd1                    ext2         487M /boot
&#9500;&#9472;sdd2                                   1K
&#9492;&#9472;sdd5                    LVM2_member 59.5G
  &#9500;&#9472;ubuntu--16--vg-root   ext4        55.5G /
  &#9492;&#9472;ubuntu--16--vg-swap_1 swap           4G [SWAP]
sr0                                   1024M


```

Why is it mounting sda1 as /mnt/sqltempdb when I am specifying /dev/sdc1?

---

### Post by ajgreeny on 2017-06-30
Are you mounting the disks/partitions with /etc/fstab?  If so you should use the UUIDs of the partitions, not their sdx# nomenclature as that can change at boot.

You can find the UUIDs with ```
sudo blkid -c /dev/null
```

---

### Post by mrfrodo2 on 2017-06-30
I haven't gotten to the fstabs yet, I was trying to get the drives mounted and then I was going to set up fstabs to mount the drives automatically upon reboot.

---

### Post by ajgreeny on 2017-06-30
So how are you mounting the partitions; are you just clicking on the volume icons in the left hand pane of your file manager?

---

### Post by mrfrodo2 on 2017-06-30
I don't do gui :) this is all command line. In the info above I put the command.

sudo mount /dev/sdc /mnt/sqltempdb

But when I then listed everything out it showed sda mounted as /mnt/sqltempdb not sdc. I can always pull the UUID and try the mount that way.

---

### Post by mrfrodo2 on 2017-06-30
Ok, after running the command you indicated I get the following:

sudo blkid -c /dev/null
/dev/sda1: UUID="a7574784-d387-48a1-b1e5-5b976476ab29" UUID_SUB="e6f5e01f-8e5f-4981-8cde-4a1586db0eba" TYPE="btrfs" PARTUUID="5eb212fe-01"
/dev/sdb1: UUID="a7574784-d387-48a1-b1e5-5b976476ab29" UUID_SUB="405c471a-892b-45a7-af7e-8b1251c5f023" TYPE="btrfs" PARTUUID="6163874f-01"
/dev/sdc1: UUID="a7574784-d387-48a1-b1e5-5b976476ab29" UUID_SUB="36b70b89-cf32-40ee-84e5-5e887bb8fab2" TYPE="btrfs" PARTUUID="3f9f0939-01"
/dev/sdd1: UUID="782b9ae3-bcce-4bb9-953b-8eb9d038687b" TYPE="ext2" PARTUUID="e3208575-01"
/dev/sdd5: UUID="eJiLn4-KUod-HHny-WawI-j9ti-RRWA-Ze05dk" TYPE="LVM2_member" PARTUUID="e3208575-05"
/dev/mapper/ubuntu--16--vg-root: UUID="59130ece-e0c0-4f8c-b7fd-72d1d96cc30f" TYPE="ext4"
/dev/mapper/ubuntu--16--vg-swap_1: UUID="2c06f9d4-2868-4380-bd14-94519e57d791" TYPE="swap"

Why would all 3 devices, sda, sdb and sdc, all have the same UUID? They have different UUID_SUB, but that doesn't make any sense to me.

---

### Post by mrfrodo2 on 2017-06-30
That duplicated UUID was making it impossible to do anything with the drives.  Since this was a test system, and a VM at that so easily modified, I removed all 3 drives, then added them back to the VM 1 at a time. Now they each have different UUIDs and I'm able to proceed with modifying the fstab and mounting automatically using the UUID of each individual drive.

---

### Post by Habitual on 2017-06-30
Good job.

---

### Post by ajgreeny on 2017-07-03
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by mrfrodo2 on 2017-07-03
I'll mark it as solved. I did a bit more digging and even figured out how I got the same UUID on multiple devices, so I'll pass that along as well.

After attaching devices you can create file systems on them all at the same time by using the command:

sudo mkfs.btrfs /dev/sda /dev/sdb /dev/sdc

This command ends up giving all 3 devices the same UUID. Not sure why, but it does. I have googled the command and have even seen instructions on doing that exact thing, which is why I did it in the first place. It's almost like it pipes the UUID from the first part of the command into the 2nd and then into the 3rd such that all end up with the same UUID and that creates all kinds of problems.

---

### Post by sotiris2 on 2017-07-04
From [ btrfs wiki](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)

> 
# Create a filesystem across four drives (metadata mirrored, linear data allocation)
mkfs.btrfs /dev/sdb /dev/sdc /dev/sdd /dev/sde


So the filesystem is one in all 4 drives which is perhaps why they have same UUID. I guess while only only one of them, sda1 showed up mounted all were in use by the btrfs driver.

---

