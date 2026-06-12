---
title: "Do-release-upgrade from 20 to 22 fails because of /boot/efi"
date: 2024-05-28
forum: New to Ubuntu
---

### Post by sedberg1 on 2024-05-28
Running 20.04 on a physical server.  Was able to perform apt -y update and apt -y upgrade successfully.  However, when running do-release-upgrade, I get this:

EFI System Partition (ESP) not usable


Your EFI System Partition (ESP) is not mounted at /boot/efi. Please
ensure that it is properly configured and try again.

I see an entry in /etc/fstab for /boot/efi:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/ubuntu-vg/ubuntu-lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-RMSohpSQTjqNzaOwImYacuk2XqhOriWOekCoG6uyzlNquzTiPPCRBWq8PSri53In / ext4 defaults 0 1
# /boot was on /dev/md126p2 during curtin installation
/dev/disk/by-id/md-uuid-40b533a3:c2adde52:2f037f32:62351b0f-part2 /boot ext4 defaults 0 1
# /boot/efi was on /dev/md126p1 during curtin installation
/dev/disk/by-id/md-uuid-40b533a3:c2adde52:2f037f32:62351b0f-part1 /boot/efi vfat defaults 0 1

However, it doesn't look like it actually mounts:

root@cu-mlearn:/boot/efi# ls -a
.  ..
root@cu-mlearn:/boot/efi#

Ran an ls /dev/disk/by-id and don't see that UUID that is in /etc/fstab.  So I'm guessing it has the wrong UUID?  Maybe that's why it didn't mount?  Probably wrong with that conclusion.  

Any help is appreciated.  Thanks.

---

### Post by yancek on 2024-05-28
> ls /dev/disk/by-id 

I don't know why the UUID would change.  I just upgraded from 20.04 to 22.04 and didn't have a problem.  If you run the command above or blkid, what UUID do you see for that partition, /dev/md126p1?  I would make a backup of the fstab file and then change the UUID to the correct one for that partition and reboot.  Or, an easier method is to just comment out the current line for the /boot/efi partition by placing a # at the beginning of the line as shown below and change the UUID to the correct one on the a new line

> # /dev/disk/by-id/md-uuid-40b533a3:c2adde52:2f037f32:62351b0f-part1 /boot/efi vfat defaults 0 1
/dev/disk/by-id/md-uuid-insert new uuid here-part1 /boot/efi vfat defaults 0 1



---

### Post by sedberg1 on 2024-05-29
This is what I get from blkid.  I see a /dev/md0 but not a /dev/md126p1

root@cu-mlearn:/home/srvcansible# blkid
/dev/sda2: UUID="dd747c57-fafd-44c1-8f0b-29548ed314b3" TYPE="ext4" PARTUUID="64d04fdd-9cfc-49ac-ac89-de423135fdf3"
/dev/sdb1: UUID="705C-EFD4" TYPE="vfat" PARTUUID="69485852-e536-4f4e-aefe-07473d3bae8f"
/dev/sdb2: UUID="26e2a572-1f05-4cd6-9c2c-c1e8ad69e2ff" TYPE="ext4" PARTUUID="5f84b163-eef7-4ab0-b8ba-c5c6d0ee06e2"
/dev/sdb3: UUID="yoqpiL-1ddL-dYsb-vHDi-TWdq-IspD-dgICo4" TYPE="LVM2_member" PARTUUID="c07427f4-14d3-4ea0-9e8b-d47bb913a551"
/dev/sdc: UUID="dc4d3ce2-b9a4-e48b-1bbe-f9cafc458b52" UUID_SUB="528b3917-7cd6-0812-bb5d-81cf61ed02fe" LABEL="cu-mlearn:0" TYPE="linux_raid_member"
/dev/sde: UUID="dc4d3ce2-b9a4-e48b-1bbe-f9cafc458b52" UUID_SUB="a5b5d532-bfcd-abbf-0b29-f3278362108b" LABEL="cu-mlearn:0" TYPE="linux_raid_member"
/dev/sdd: UUID="dc4d3ce2-b9a4-e48b-1bbe-f9cafc458b52" UUID_SUB="07568abd-4a16-4f9c-a04a-b51ea6fbd41e" LABEL="cu-mlearn:0" TYPE="linux_raid_member"
/dev/md0: UUID="bc0109fe-4ff5-42ef-9e44-9c2c7d795cb1" TYPE="ext4"
/dev/mapper/ubuntu--vg-ubuntu--lv: UUID="1433bf2c-01cc-4960-a43b-c6d31f4ee3d5" TYPE="ext4"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/sda1: PARTUUID="3082381a-57ee-49bf-99d2-a494c9699863"
/dev/sda3: PARTUUID="1ff0b975-e212-4cbd-8b52-915118c6f253"

---

### Post by yancek on 2024-05-29
The only entry I see that looks like an EFI partition is sdb1 so you might try substituting that UUID or comment out the current line and repeat it below with the only change being the UUID (705C-EFD4).

>  /dev/disk/by-id//705C-EFD4 /boot/efi vfat defaults 0 1


Or you could try something like below.  

>  UUID=705C-EFD4 /boot/efi       vfat    umask=0077      0       1

You could put both entries in fstab and just leave one uncommented to  test boot then comment it out if it fails and try the second.  I see you  are using LVM which I don't use but I understand it requires a separate  /boot partition so I don't know if that will be a problem.  Is your  /boot partition separate and does it mount?

---

