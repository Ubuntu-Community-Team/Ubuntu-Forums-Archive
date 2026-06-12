---
title: "Convert NTFS to linux file system"
date: 2023-04-17
forum: New to Ubuntu
---

### Post by desatir73162 on 2023-04-17
Hi there
I have to hard drive installed. SSD for OS and HDD for my personal files. The question is how to change HDD from NTFS to linux file system without data loss?

thanks in advanced.

---

### Post by QIII on 2023-04-17
Do you have a particular reason you would like to change it?  Is is working as it is?

---

### Post by desatir73162 on 2023-04-17
> **QIII said:**
> Do you have a particular reason you would like to change it?  Is is working as it is?
I feel it is faster with linux file system

---

### Post by QIII on 2023-04-17
"Speed" is probably not the best of reasons.  As far as not losing your data, the easiest way to address that is just to leave things alone.  You might want to research the differences between NTFS and ext4, just so you know what the pros and cons are.

The best way to do what you are asking without the threat of a significant emotional event is to copy your data to a different storage device, use parted/Gparted to reformat the original drive as ext4 and then copy your data back to the original drive.

In doing that you both make a backup of your data (which you need to do anyway in this endeavor) and you can freely re-format the original device.

---

### Post by ActionParsnip on 2023-04-17
Format the drive to Ext4 / XFS / Whatever then restore your backups to the new file system

---

### Post by TheFu on 2023-04-17
> **desatir73162 said:**
> Hi there
I have to hard drive installed. SSD for OS and HDD for my personal files. The question is how to change HDD from NTFS to linux file system without data loss?

thanks in advanced.

[LIST=1]
[*]Backup any data you don't want to lose.
[*]Reformat the existing NTFS file system to one of the many native Linux file system, ext4 is the normal answer, but there are others for special needs.
[*]Mount the new file system where you need it, change the permissions and ownership for your needs.
[*]Modify the /etc/fstab with a new line to have the file system mounted at boot.
[*]Add the new file system mount location to your backup tool/script, so that data isn't lost.
[*]Verify that both the backups and mount work after a reboot, fix issues, if needed
[/LIST]

Be happy.

---

### Post by Impavidus on 2023-04-17
You didn't mention what operating system is on the computer. Windows cannot access Linux filesystems, or at least not without jumping through a lot of hoops. Ubuntu can access Windows filesystems, but only if clean and cannot defrag them or repair them if broken. So if this computer runs both Windows and Ubuntu and you want to access the data from both, NTFS is best. If the computer runs Ubuntu only, use a Linux filesystem. Ext4, unless you have a specific reason to use a different one.

I'm not aware of any tools that can convert from NTFS to ext4 and I doubt such tools exist, given that the filesystems are very different, Microsoft has little interest in making such a tool and other parties have limited knowledge of NTFS. And if anything goes wrong, all data are lost. So copy the files to some other drive, format the HDD and copy the files back. See it as a test of your backup routine.

---

### Post by MAFoElffen on 2023-04-20
Nowadays, storage is a lot cheaper. You buy another drive and copy data to it. Create a partition on it, formatted as anything, and copy the data to it. Reformat the original partition as ext4 and copy the data back. 

There was a procedure for this,... It really isn't a conversion. But it  was around when storage devices were still expensive, compared to now.

The older procedure was to shrink the NTFS partition and create an EXT4 formatted partition. If the NTFS partition is larger than the ext4 partition, then you have to do it in steps. Move (copy/delete old files after their copy) as much of the data to the new partition as it can hold. If you run into space issues on the new partition, reshrink the NTFS partition and grow the EXT4 partition. Repeat the steps until all the data is moved to the EXT4 partition. Then delete the empty NTFS partition.

---

