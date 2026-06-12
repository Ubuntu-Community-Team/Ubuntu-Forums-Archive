---
title: "Help with fstab"
date: 2021-06-07
forum: New to Ubuntu
---

### Post by sross44 on 2021-06-07
Hi.... I'm trying to figure this all out and completely new to linux.  I have two external drives that I'm trying to permanently mount. They are /dev/sda1 and dev/sdb1. I've already mounted them as follows:

sudo mount /dev/sdb1 /media/Media_Drive
sudo mount /dev/sda1 /media/Media_Drive2

This worked great until I realized when I reboot the machine I had to do it all over again. How do I use fstab to permanently mount these to where I have them? 

Any help would be greatly appreciated as I'm lost and getting frustrated already. Thanks in advance and for the patience with me as noob to Ubuntu and linux as a whole

---

### Post by &amp;KyT$0P# on 2021-06-07
First run
```
lsblk -o +FSTYPE,UUID
```
Note the FSTYPE (filesystem type) and UUID associated with sda1 and sdb1. (Make sure your terminal window is definitely wide enough to see all the output.  This may involve re-running the command after resizing the terminal window.)

Then use that to construct your fstab lines in this format -
```
UUID=[COLOR="#FF0000"]<the_uuid>[/COLOR]   [COLOR="#FF0000"]/media/<Media_Drive_Whatever>[/COLOR]   [COLOR="#FF0000"]<the_filesystem_type>[/COLOR]   defaults   0  2
```
Replace the parts in red with the information you obtained for your specific setup.

**Caution: Messing up fstab or specifying partitions that aren't ALWAYS there _will_ leave you with an unbootable system.**  Make sure you have a known-good live USB of Ubuntu (or your preferred flavor) available to you BEFORE you edit [FONT=Courier New]/etc/fstab[/FONT] , so that you can fix your system should something go wrong.

Refer to [FONT=Courier New]man fstab[/FONT] for more info.

---

### Post by grahammechanical on 2021-06-07
I am assuming that sda1 has the label "Media_Drive2" and sdb1 has the label "Media_Drive. We find the file called fstab at /etc/

Here is the Wiki page that explains the various changes that we might want to make to that file which is a plain text file.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

We may need to create a mount point. That is a folder under root ( / ) that the partitions can be mounted in. We already have a /media directory (folder). 

```
sudo mkdir /media/Media_Drive
sudo mkdir /media/Media_Drive2
```

We need to know the UUID of both partitions.

```
sudo blkid
```

We need to edit /etc/fstab and to do that we need to be running a text editor as administrator.

This is what I use to automount a partition I have called Data. I put this in fstab

> # to automount Data partition
UUID=311676c4-ca3e-46d7-8b81-a1a577f601d7 /media/Data ext4 auto,users,rw,relatime 0 2

Regards

---

### Post by ajgreeny on 2021-06-07
Are those external drives permanently mounted or are they sometimes not attached?

The system folder /media is normally used only for temporary filesystems, do if those disks are always attached it may be better to mount them to /mnt  rather than /media but it's up to you.
Also if not always attached you will have to look into the **noauto** option in your fstab or boot will hang while looking for those missing disks.
I've  never needed to use that option so I don't know the details of its use.

---

### Post by TheFu on 2021-06-07
Another thread with lots of details and exact example: 
   [https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843](https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843)

The first questions are:
[LIST]
[*]Are the drives always connected or not.  /etc/fstab settings are for drives that are always connected and working at boot.
[*]What file system type does each partition have?  Linux much prefers native file systems like ext4, but it can deal with non-Linux file systems like NTFS, if necessary. Some things won't work correctly with NTFS, but for data that isn't specific to any userid, it is fine.  When mounted, run **df -hT -x squashfs -x tmpfs -x devtmpfs** to show the information about the type of file system, if you aren't 100% certain.
[/LIST]
The answers to those questions determine most of what we would suggest.

BTW, sdc and sdc1 are different devices.  sdc is the entire HDD - including the partition table.  sdc1 is the first, primary partition on the drive.  sdc2 would be the second primary partition on the drive.  Partitions should always be used, except for flash storage that gets a Linux boot image shoved onto it.  All other situations, use a partition and partition table.  Best if that partition table is GPT for about 5 reasons compared to the legacy MSDOS partition table method which has been patched and patched multiple times, but doesn't work with HDDs over 2TB.  GPT works well for all sizes of storage.

If the drives may be powered off or disconnected, then there are some better options than using the fstab.

While we can use the UUID and that has been how the system typically mounts storage, humans can deal with labels better.  If you put a LABEL onto each partition/file system, then it can be mounted using *LABEL=250G_HDD* instead of UUID=554810b2-a02a-4ac7-943e-96550f85ed75.  Which would you rather have?  LABELs need to be unique on the system, just like UUIDs. That's not hard for humans.  Personally, I use labels for flash USB storage and for temporary storage, but not for the others. Your choice.  Just another option.

Lastly, whenever editing system files, use **sudoedit /etc/fstab**. This is safer than any other method.

---

### Post by sross44 on 2021-06-07
The drives are always attached. I can mount them elsewhere. Just trying to get a feel for it all. This for a media server so they're always going to be here.

---

### Post by sross44 on 2021-06-07
Ok, so with them being perm attached, what's my best option. fstab, labels, etc? I appreciate everyone's help. I just don't want to screw up my system while learning haha.

---

### Post by CatKiller on 2021-06-07
> **sross44 said:**
> Ok, so with them being perm attached, what's my best option. fstab, labels, etc?
Then yes to having an entry in your filesystem table.

Use labels if they're useful, or UUIDs. The sd*x* nomenclature is just based on which one perks up first; they aren't permanent and can change between boots.

---

### Post by TheFu on 2021-06-07
> **sross44 said:**
> Ok, so with them being perm attached, what's my best option. fstab, labels, etc? I appreciate everyone's help. I just don't want to screw up my system while learning haha.

And which file system(s) do they have?

---

### Post by &amp;KyT$0P# on 2021-06-08
> **CatKiller said:**
> Then yes to having an entry in your filesystem table.

+1.

My warning above was **not** intended to warn you away from doing this.  It was only intended to tell you make sure you're prepared for in case something does go wrong.  Because if you do have a working live USB, it's easy to fix fstab-related issues: just boot from the live USB and fix or comment out the offending entry/entries and your system should be back to normal on next boot.

For any physical partition I recommend specifying it by UUID if you add it to fstab, which is the approach I outlined in my post #2 above, no matter whether you label your filesystems or not.

---

