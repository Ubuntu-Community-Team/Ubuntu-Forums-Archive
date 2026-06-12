---
title: "upgrading hardware. move hdd over?"
date: 2019-06-13
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2019-06-13
Major system upgrade incoming in a week or so. I can reinstall but I don't want to if I don't have to. Can I just put my hard drive in the new machine and it will work? Or should I do a fresh installation just to be sure?

---

### Post by Autodave on 2019-06-13
I have quite often moved a HD from one machine to another without any issue.  IF you are using the same GPU in new machine, there shouldn't be a problem.  However, if you are changing the GPU (especially say from Radeon to Nvidia or the other way around) I would remove any graphics drivers first.

---

### Post by Skaperen on 2019-06-13
just make sure the hard drive stays at the same relative position in the hard drive device name sequence.  do you have your install source handy to be able to boot up LIVE Ubuntu as a means to look around.  if your old machine has just one drive then obviously that drive comes up first as /dev/hda or /dev/sda.  the new machine without the old drive will have a first drive.  you want to make the old drive be the first drive to boot properly from it.  that may require changes in the disk setup in the new machine.  you may want to do a test of just the ol drive by itself in the new machine to see if that works.  there are reasons it may not.

if you need more help, please give us more details about the hardware, old and new, especially the hard drives, types, sizes, and how they are hooked up.  if the new one has a different kind of connector knowing the types can help us help you (photos if you don't know the types).

---

### Post by Tadaen_Sylvermane on 2019-06-13
I have a PXE install server available along with apt-cacher-ng on my server. It's really trivial to do for me, just thought it would save a few minutes. The name sequence concerns me though. I don't have any idea how to guarantee that. Upgrading the mobo, gpu, psu, case, dvd burner. Current cpu / gpu is an i5 3470 ivy bridge. Gpu will be an AMD Radeon RX 570 most likely. I plan on upgrading to an ssd but that will take time. Low on funds at the moment.

Might I be better served to just backup /home to my server and rsync it back in place?

---

### Post by CatKiller on 2019-06-13
> **Tadaen_Sylvermane said:**
> The name sequence concerns me though. I don't have any idea how to guarantee that. 

Use UUIDs rather than device names. It's been the default to do so for a long time. It's not just moving it into a new machine that can cause the ordering to change: it used to sometimes happen between boots. Hence, UUIDs are used instead, which are generated when the partition is created.

---

### Post by kpatz on 2019-06-14
If your fstab and grub config is using UUIDs it should boot up regardless of what "drive letter" it gets (sda, sdb etc.), though if you have more than one drive the BIOS will be set to boot from a particular one, usually the 1st one.

If it's not using UUIDs, as long as the drive comes up as /dev/sda it should still boot.  If it doesn't, you would have to boot a live CD/USB, mount the partition, edit the fstab, chroot and reinstall grub, and you should be golden.

Is this just an Ubuntu (or other Linux) install or is there also Windows on this drive?  Windows installs have a lot more difficulty being moved than Linux.

---

### Post by Tadaen_Sylvermane on 2019-06-14
Ok. I will try it. It's been UUID's since install. I'll backup my /home + a few other config files and try it. If it works, yay. If not, install shouldn't take more than 10 minutes to a half hour.

---

### Post by TheFu on 2019-06-14
> **Tadaen_Sylvermane said:**
> Ok. I will try it. It's been UUID's since install. I'll backup my /home + a few other config files and try it. If it works, yay. If not, install shouldn't take more than 10 minutes to a half hour.

And that's how it should be.  Always good to hear people having proper backups. We see so many in these forums who don't.

Just to chime in - using UUIDs isn't mandatory.  The correct answer is that NOT using /dev/sd* device names is the issue. There are multiple other methods to not use the device names/partitions directly by using and of these other options in the fstab.
```
$ tree -d /dev/disk/
/dev/disk/
&#9500;&#9472;&#9472; by-id
&#9500;&#9472;&#9472; by-label
&#9500;&#9472;&#9472; by-partlabel
&#9500;&#9472;&#9472; by-partuuid
&#9500;&#9472;&#9472; by-path
&#9492;&#9472;&#9472; by-uuid
```

by-label/ is handy for temporary/usb storage devices.
by-path/ is handy if you have lots of disks connected via different HBAs.
and
don't forget that LVM has their own guaranteed consistent, mapping from LV to storage. An fstab entry with
```
/dev/mapper/ubuntu--vg-home--lv /home     ext4 errors=remount-ro,noatime 0 2
/dev/disk/by-path/pci-0000:00:17.0-ata-1-part2 /boot ext2 defaults,noatime,        0       2

```
is just as unique as a UUID.  LVs do have UUIDs, if that is your poison. Use **blkid** command to get them.
My personal preference is to use the LVM mapper for LVs and use UUIDs for everything else.  On a new system, might need to run **sudo vgchange -ay** to see new LVM objects. ZFS probably has similar discovery needs as well.  I don't know anything about btrfs, but it might too.

---

