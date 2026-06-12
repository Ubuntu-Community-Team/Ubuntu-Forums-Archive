---
title: "boot a dd copy of a partition"
date: 2016-02-29
forum: New to Ubuntu
---

### Post by crip720 on 2016-02-29
I did a dd copy of sda7( bootable ubuntu 15.10) to an external hard drive sdc. Would like to know what to use to make sdc boot.  Did update-grub.  Do I use boot-repair, system rescue, or something else?  Laptop has Win 8.1/10 and Ubuntu 15.10 on internal HD, and 14.04 on another external HD(sdb).  dd command used was dd if=/dev/sda7 of=/dev/sdc  .  Thank you, Colin.

---

### Post by yancek on 2016-02-29
You're copying a partition to a drive when you should have copied the partition (sda7) to a partition on the external, example sdc1.  
What happens, what output do you get when you run update-grub from whichever system on your other drive controls booting?  I would not expect it to work because your grub.cfg menuentry for the system on sdc will still be pointing to the system on sda7.  You would need to boot another Linux system, mount the partition on sdc and with root privileges change its grub.cfg file to point to the correct partition.  Might have to change the UUID entries also.  If your windows systems use UEFI, that adds another complication to the problem, maybe?  I don't use UEFI so can't suggest any solution.

---

### Post by crip720 on 2016-02-29
The output from update-grub just lists 14.04, Win loader(?), and 15.10 on sda7. 15.10 on sdc does not show up in update-grub. All commands have been done thru 14.04.  sdc is mounted, and I do have UEFI, with secure boot off.  Have not rebooted system yet.  Would need instructions for changing cfg.files or UUID entries.  Thank you.

---

### Post by sandyd on 2016-02-29
> **crip720 said:**
> I did a dd copy of sda7( bootable ubuntu 15.10) to an external hard drive sdc. Would like to know what to use to make sdc boot.  Did update-grub.  Do I use boot-repair, system rescue, or something else?  Laptop has Win 8.1/10 and Ubuntu 15.10 on internal HD, and 14.04 on another external HD(sdb).  dd command used was dd if=/dev/sda7 of=/dev/sdc  .  Thank you, Colin.

Does not work well as you are dd-ing a partition directly to a disk instead of writing it to another partition.

What I recommend to copy it properly:

1. Start up Gparted.
2. Select the external disk (make sure it is the correct disk or you will wipe out your computer). There should not be any locks on any of the partitions on the disk.
3. Select Device -> Create Partition Table. You're using a computer with support for UEFI, you should have support for GPT. If not, just create it with MBR

You now have a nice clean external disk for installation and now need to create your partitions.

All partitions created **must be equal or greater size** then the original partitions. Begin with creating the root partition.

If you have any of the following partitions, they will have to be created on the target disk as well:
[LIST]
[*]home
[*]swap
[*]boot
[/LIST]

Now, you can DD the corresponding partitions to the target disk.

After DDing the partitions, you need to update the fstab on the duplicated install.

Run
```

sudo blkid
```

You now have a list of partitions on your system along with the UUIDs for each partition. Go to the target disk partition that contains the root filesystem and update /etc/fstab with the relevant details. Then, use boot-repair to install grub back on the target disk.

(Most) filesystems can be expanded if you DD-ed the original partitions to a larger partition on the target drive, that should probably be done before rebooting.

---

### Post by crip720 on 2016-03-01
I have UUID number and I am ready to update /etc/fstab.  Would like to know what to add.  An example I found at ask ubuntu looks like this  (
UUID=31f39d50-16fa-4248-b396-0cba7cd6eff2     /media/Data   auto    rw,user,auto    0    0) 
 
Is this what I use or what? Just add this to fstab? They are using gedit. My setup is a single partition containing Ubuntu 15.10.  Thank you,Colin.

---

### Post by Bucky Ball on 2016-03-01
You seem to be missing what we're saying. You copied a partition to a disk. Go back and start again. Create a partition on the disk you are copying to that is the same size or larger than the one you are copying. Then, if the new partition is say sdc5, you would:

>  dd if=/dev/sda7 of=/dev/sdc5

Understand? You need to do this before twiddling with the fstab or anything else. ;)

---

### Post by crip720 on 2016-03-02
Thanks for your input, did not fully understand Sandyd's post.  Redid sdc with two partitions and after copying into one, update-grub found the new partition.  Disk utility is showing two extra hard drives that are not real, but giving serial numbers for them and showing no media.

---

### Post by Bucky Ball on 2016-03-02
Good news! Thanks for marking as solved and enjoy. :)

---

