---
title: "Adding a new hard drive - MBR/GRUB Issues"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by nigelcrawfordhotm on 2014-04-01
I have been dual booting Ubuntu and Windows 7 for some time from the same hard drive, but I am running out of space.  My shiny new HD arrives from Amazon today and I'm trying to come up with a strategy to split the two OS's between the two drives without having to do a clean install.  Here's what I was thinking:


[LIST=1]
[*]Clone the old drive to the new drive using a bootable utility on a CD
[*]Boot up Ubuntu from a live CD, run GParted
[*]Delete the Windows partition from one drive, Ubuntu from the other.  Resize the partitions
[/LIST]

My question is how do I repair the MBR and GRUB?  I see something like this: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) but given that I will clone the MBR from one drive to the other will this work?

I just want to make sure that I am doing things correctly before I start deleting things!  Thanks in advance!

EDIT: This worked, albeit with a few issues caused by Windows (there's a surprise!).  Ubuntu booted fine after all of this, but Windows wouldn't boot without being on SATA channel 1 and not running through the MBR repair process using the Windows installation disc.  It just meant that I had to do the GRUB reinstallation using the Boot Repair Disc twice.  Thanks for all of your suggestions.

---

### Post by kc1di on 2014-04-01
Boot-repair will reinstall grub to the MBR whichever drive it's on.  So should work for you - Good Luck.

---

### Post by nigelcrawfordhotm on 2014-04-01
> **kc1di said:**
> Boot-repair will reinstall grub to the MBR whichever drive it's on.  So should work for you - Good Luck.

Thank you!

---

### Post by oldfred on 2014-04-01
Cloning will cause issues with duplicate UUIDs. It really is more for restoring to the same drive as then the same UUID would be correct. Or where you do not use old drive and just want new larger drive with old data.

Not sure about Windows on a cloned drive. Backup & restore may be better if not a clone. Or you may be able to make sure it boots from new drive and delete old copy on old drive so you do not have duplicates.

You cannot have both drives with same UUID connected at same time when you boot as it may boot which ever drive/partition it sees first and may not update correct version. 
But you can change UUIDs, reinstall grub2's boot loader (purge & reinstall as it must update all settings with new UUID) and edit fstab. Often just easier to do a new install with Ubuntu.

 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by monkeybrain20122 on 2014-04-01
You only need to change uuid if you intend to boot the original and the clone off the same machine, but my understanding is that you want to delete the original with a live usb after making the clone. In that case I don't think it is necessary to change uuid.

But here is how I change uuids (i do boot clones off the same machine for testings and try runs before doing something risky)

Boot to a live usb (or another Linux system on same or different machine, just not the original one), attach the drive with the clone in it. Then run gparted, go to the drive with the clone and use the gparted option to change uuid of the partition(s). 

Then detach and reattach the drive. 
Open the terminal and run
```
sudo blkid
```
and note the uuids of the partitions

Now edit /etc/fstab  and /boot/grub/grub.cfg **of the clone** and change the uuids to the outputs of blkid
If you use gedit to edit grub.cfg it is best to use the replace all function. 

You have to be careful that you are editing the correct files, they are system files **of the clone**, if you are not careful you may end up editing the corresponding files of the running system instead. When done boot into the clone and run
```
sudo update-grub
```
(Though this may not be necessary)

I also use different labels for the same partitions in the original and the clone. Changing labels can be done with gparted as well.

If you use swap, after booting into the clone, run again
```
sudo blkid
```
note the output for the swap partition's uuid
edit /etc/fstab (if necessary) and /etc/initramfs-tools/conf.d/resume 
make sure that the swap uuid in both match the output of blkid
Then run 
```
sudo update-initramfs -u
```
Then  reboot.

P.S.. I don't dual boot with Windows so I have only done this with Linux systems. There may be some additional things you have to do for Windows, I don't know.

---

