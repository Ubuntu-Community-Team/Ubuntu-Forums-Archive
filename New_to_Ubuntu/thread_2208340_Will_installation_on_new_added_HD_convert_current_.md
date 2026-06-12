---
title: "Will installation on new added HD convert current drive for storage only."
date: 2014-02-27
forum: New to Ubuntu
---

### Post by Peter_Heft on 2014-02-27
I was given an Acer M1201 that I installed Ubuntu 12.04 on as stand alone OS on the current 160 GB HD. I like how it works and have ordered a 1Tb HD for it.  Will a reinstall of 12.04 offer me the choice of putting the OS on the new drive and converting the old drive to storage only?
What do I need to do to get there?  Will the BIOS care which port I plug the new drive into?   Is there anything else I should be aware of?  I do not need to save any data on the 160 HD, it can be wiped.  
Thanks for the help.
Peter

---

### Post by papibe on 2014-02-27
Hi Peter_Heft.

In the installation process you'll have the choice where to install the OS. I believe you won't have any problem recognizing your new drive since it is much bigger than the one you have.

(If I were you, I would not reformat your old drive, until you have successfully boot in your new HD and copy (rsync better) your data).

Then, you would need to enter the BIOS to change the boot order. You need to select your new drive on top, or instead of the old one.

You'll end up with a new system on the new drive, and an old drive with old partitions. In order to delete/reformat the old one use gparted. Since it won't be a OS drive, you'll be able to do it from your desktop (no need from a live CD/USB).

Hope it helps. Let us know if you have more questions.
Regards.

---

### Post by Peter_Heft on 2014-02-27
Thanks for the help.  Can't wait for the HD to show up and get going for real.
Peter

---

### Post by Peter_Heft on 2014-03-03
The HD showed up, I plugged it into the SATA port where the small drive had been.  That one got plugged in further away from the dvd drive connection, thinking that would be further down the boot order, or that it would boot from that original connection rather than that old drive.  When I tried to install it offerd to install in place of the old OS or next to or "other". I wasn't sure what next to meant having 2 drives, in other I could pick which drive to install on but there it wanted me to do the partitioning, which was beyond me.  I shut it down, unplugged the small HD, and tried again.  It only had one place to go and went there, when cued.  After install I shut it down again to reconnect the small HD and booted again.  It booted the new install.  I'll have to take a look at the BIOS just to see how it does see the boot order.  Now I just have to figure out what to format the drive as.
Thanks again
Peter

---

### Post by papibe on 2014-03-04
Glad to know you were able to get the config as you wanted it.

For the record, the option you should have chosen was called either 'Other options',  'Advance options' or 'Manual partitions'. That would have took you to another menu that would allow you to manually decide where to install, how to partition and what to leave as is. That options has several confirmations steps, so you don't accidentally format something you don't want.

In any case, I'm glad you have your 2nd HD installed and working ;)

Regards.

---

### Post by Peter_Heft on 2014-03-04
When I boot there is now a multiboot menu.  I have attached a jpg of monitor screen.  It lists the new install of Ubuntu on the 1TB HD,  Same new install (recovery mode), two previous versions of Ubuntu on the 160 GB drive and memory tests.
Will gparted get rid of that boot menu?  Does it make sense to keep the recovery mode of the new install, or the memory test?  If so, how.
Please tell me how to proceed since I would like to do it right the first time.
Bios did have the new drive second in the boot order after the dvd/cd drive.
Thanks,
Peter

---

### Post by papibe on 2014-03-04
> **Peter_Heft said:**
> Will gparted get rid of that boot menu?
No, it won't.

Once you get rid of your old partition do this to update your grub menu:
```
sudo update-grub
```
> **Peter_Heft said:**
> Does it make sense to keep the recovery mode of the new install, or the memory test?
It is the default behavior on Ubuntu, and in most Linux distributions.

Recovery mode is very important. It is a very important tool to recover from serious problems. For instance, lost of power during an upgrade, disk corruption, etc. Even from user's mistakes like changing the permissions to files on the root partition, losing the ability to sudo, or simply forgot your password.

Regarding old kernels, IMHO it is important to keep them. However, you really need one, or maybe a couple in case a kernel update screw the boot process. This is a very rare case, and it is more related to compatibility between proprietary graphic drivers and the kernel. I'm not referring to the ones on the old partition, but the ones will appear after a kernel upgrade.
> **Peter_Heft said:**
> Please tell me how to proceed since I would like to do it right thebe first time.
Once you reformat your old drive, update grub, and you'll be ready.

As for the old kernels, I'd keep them, and not worry much about them. They don't take that much space.

In a period of time, say 6 months to a year, it may offer some value to remove the oldest kernels. You would gain some disk space, and your boot menu would look shorter ;)

Does that help?
Regards.

---

### Post by Peter_Heft on 2014-03-04
I removed all partitions and created 1 new partition in ext4(?).  I updated grub.  I don't see any menu now when I boot. Recovery mode and memory test are accessible somehow? If boot fails? Did I get rid of the kernels when I deleted all of the partitions?

I had no rights on the new partition since it is owned by root. I used nautilus to change permissions.

Yes, it certainly helped. Thanks again,
Peter

---

### Post by papibe on 2014-03-04
I think grub is set not to wait for input, if you have only 1 option in the menu. If you want to get access to the grub menu, hold the key SHIFT while booting.

You deleted all kernels that were on the old drive. I believe there were in /dev/sdb1.

Are you creating a permanent mount point for the new partition (old drive)? or are you just double clicking the disk on nautilus to get access to it?

Regards.

---

### Post by Peter_Heft on 2014-03-04
Thanks for following up and helping and teaching.  Since I am just going to use the new partition to store some files as backup double clicking seems OK.  I'm glad that it doesn't automatically mount when I boot, but I assume that is a choice even if I create a mount point.
Thanks again.
Peter

---

### Post by papibe on 2014-03-04
For the purpose you have designed, it works either way.

When you double click on it, it is usually mounts on something like:
```
/media/4d24bd2d-a7d8-4cc8-91a0-2af78e095130
```
Over time I found out that it is easier to write scripts to something simpler like:
```
/media/Backup
or
/data
```
If that would interest you:
[LIST]
[*]create the mount point (the directory)
[*]change its ownership to your user.
[*]create an entry in /etc/fstab (read [here]("https://help.ubuntu.com/community/Fstab")) using the option 'noauto' so that it doesn't mount automatically.
[/LIST]

Hope it helps.
Regards.

---

### Post by Peter_Heft on 2014-03-04
Might as well keep learning.  I'll take a stab at it in a couple of days.
Thanks,
Peter

---

### Post by Peter_Heft on 2014-03-24
sudo lshw   gives me the following output of the HD to be used for some backup storage
*-disk
             description: ATA Disk
             product: ST3160815AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 4.AD
             serial: 5RX4M4Z9
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00007503
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/backup storage
                version: 1.0
                serial: 8a3ee92c-cb1a-4d23-ac99-c0e3e46abbba
                size: 149GiB
                capacity: 149GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-03-04 19:20:10 filesystem=ext4 label=backup storage
 lastmountpoint=/media/backup storage modified=2014-03-24 13:27:02 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2014-03-24 13:27:02 state=mounted

The mountpoint doesn't look like the alphabet soup example you had listed as possible, or is that designation somewhere else?  I had read somewhere that how mounted would effect read/write speed, so it is significant.  Do I need to fix/specify mountpoint or is it somehow OK?
 
I looked at    [http://ubuntuforums.org/showthread.php?t=2179424](http://ubuntuforums.org/showthread.php?t=2179424)    which tells how but is not clear to me.  Seems like 3 answers are included to the 1 questions.

Another minor point Properties in the file system says that 8.1 GB are used.  The only thing in there is lost+found and that is empty.
Thanks,
Peter

---

### Post by papibe on 2014-03-26
It looks like the drive was set up with a label: 'backup storage'. Thus when you double click on it, it's being mounted in:
```
/media/backup storage
```
Does that work for you?

(you don't need to create neither an fstab entry nor a mountpoint.)

Regards.

---

### Post by oldfred on 2014-03-27
Different tools show different amounts of space used. Some include journal others may not. Linux also hides 5% for userspace. That is to help prevent you from crashing system when full. But with new TB size drives that 5% may be too much if you maintain system and keep track of use. It can be reset to other values. If just a data partition you may not need the 5% at all.
Also depending on what tools you use, you may be into the difference between binary and decimal or GiB or GB sizes.

You can manually mount partitions with Nautilus with defaults. It uses label, UUID or other info as name to mount as. I do prefer to label all partitions particularly those I may not auto mount with fstab.
If a partition you regularly use, it is easier to add entry to fstab to mount on every boot.
You need to create mount point which can be anything, give yourself ownership & permissions and edit fstab with correct settings.

I follow these instructions which are really the same as your link above:
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

Linux also does not like spaces. You have to escape with /040 or use quotes in commands. I just changed to use CamelCase, under_score or justonename for labels or mount points. Linux also is case sensitive where Windows is not.

---

### Post by Peter_Heft on 2014-03-29
Thank you both for the input.  It seems that I do need to create a mountpoint and change the name to get rid of the space    The partition is still empty so there is no danger of loosing anything.  Fstab is the tool of choice.    I'll have to figure out how to get it done.    My brain is not as sharp as it used to be, but exercise is good for it.                 
 Peter

---

### Post by Peter_Heft on 2015-01-03
Sorry I never closed this.  I kept going back and not quite figuring out what to do.  I finally used Disk Utility to change the name of the partition to just "backup".  So it mounts at /media/backup.  I must own it because I can delete or modify files in it.  What finally got me to do something was that I had not backed anything up before today.
Thanks again.

---

